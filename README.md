# My Custom Tmux Configuration

This repository contains my custom **tmux configuration** that enhances
usability, enables mouse support, and integrates the beautiful
[Catppuccin theme](https://github.com/catppuccin/tmux). It also includes
vim-style pane navigation keybindings for intuitive window management.

## Features

- **Mouse Support**: Enables mouse support for selecting and resizing panes.
- **Extended Scrollback History**: Sets a large scrollback buffer (10,000 lines)
  for easier history navigation.
- **Catppuccin Theme**: Uses the Catppuccin theme for a visually pleasing status
  bar with modules for CPU, battery, uptime, and more.
- **Vim-style Pane Navigation**: Intuitive navigation between panes using
  `Ctrl + h/j/k/l` (left, down, up, right).

## Setup

1. **Install Tmux**: Ensure that you have tmux installed on your system. If not,
   install it with:

   ```bash
   # On macOS
   brew install tmux

   # On Debian/Ubuntu
   sudo apt-get install tmux

   # On Fedora
   sudo dnf install tmux
   ```

2. **Clone the Catppuccin Theme**: Install the
   [Catppuccin theme for tmux](https://github.com/catppuccin/tmux) by cloning it
   into your tmux plugins directory:

   ```bash
   mkdir -p ~/.config/tmux/plugins
   git clone https://github.com/catppuccin/tmux ~/.config/tmux/plugins/catppuccin
   ```

3. **Copy this Configuration**: Copy the contents of the `.tmux.conf` file in
   this repository into your own `.tmux.conf` file, typically located at
   `~/.tmux.conf`:

   ```bash
   cp .tmux.conf ~/.tmux.conf
   ```

4. **Reload Tmux Configuration**: Either restart tmux or, from within a tmux
   session, reload the configuration:
   ```bash
   tmux source-file ~/.tmux.conf
   ```

## Key Bindings

- **Pane Navigation (Vim-style)**:

  - `Ctrl + h`: Move to the left pane
  - `Ctrl + j`: Move to the pane below
  - `Ctrl + k`: Move to the pane above
  - `Ctrl + l`: Move to the right pane

- **Mouse Support**: Mouse support is enabled, so you can use the mouse to
  select, resize, and scroll within panes.

## Configuration Details

```bash
# Enable mouse support
set -g mouse on

# Increase scrollback history to 10,000 lines
set -g history-limit 10000

# Run the Catppuccin theme
run ~/.config/tmux/plugins/catppuccin/tmux/catppuccin.tmux

# Status bar configuration
set -g status-right-length 100
set -g status-left-length 100
set -g status-left ""
set -g status-right "#{E:@catppuccin_status_application}"
set -agF status-right "#{E:@catppuccin_status_cpu}"
set -ag status-right "#{E:@catppuccin_status_session}"
set -ag status-right "#{E:@catppuccin_status_uptime}"
set -agF status-right "#{E:@catppuccin_status_battery}"

# Vim-style pane navigation
bind -n C-h select-pane -L
bind -n C-j select-pane -D
bind -n C-k select-pane -U
bind -n C-l select-pane -R
```

## Additional Notes

- **Customizable Status Bar**: The status bar includes useful system information
  such as CPU usage, session details, uptime, and battery status.
- **Automatic Theme Loading**: The Catppuccin theme loads automatically upon
  tmux startup.

Enjoy a streamlined and visually pleasing tmux experience with this
configuration!
