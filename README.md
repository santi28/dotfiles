# Santiago's Dotfiles

Personal configuration files for macOS development environment managed with [GNU Stow](https://www.gnu.org/software/stow/). This repository contains carefully curated dotfiles to enhance productivity and create a consistent development experience.

## 📁 Structure

```
dotfiles/
├── .config/
│   └── aerospace/
│       └── aerospace.toml      # AeroSpace window manager configuration
├── .vimrc                      # Vim editor configuration
├── .zshrc                      # Zsh shell configuration
└── README.md                   # This file
```

> **Note**: This repository uses GNU Stow for symlink management, allowing for clean and organized dotfile deployment.

## 🛠️ Components

### Shell Configuration (.zshrc)
- **Framework**: Oh My Zsh with `robbyrussell` theme
- **Features**: 
  - Clean and minimal prompt
  - Git integration through Oh My Zsh
  - Enhanced terminal experience

### Editor Configuration (.vimrc)
- **Features**:
  - Syntax highlighting enabled
  - Minimal but functional Vim setup

### Window Manager (.config/aerospace/aerospace.toml)
- **Tool**: [AeroSpace](https://github.com/nikitabobko/AeroSpace) - Tiling window manager for macOS
- **Key Features**:
  - 10 workspaces with Alt+1-0 navigation
  - WASD-style window focus (Alt+W/A/S/D)
  - Window manipulation mode (Cmd+M)
  - Custom gaps and borders integration
  - Multi-monitor support
  - Auto-start at login

#### AeroSpace Key Bindings

**Workspace Navigation:**
- `Alt + 1-0`: Switch to workspace 1-10
- `Alt + Shift + 1-0`: Move current window to workspace 1-10

**Window Focus:**
- `Alt + W`: Focus window above
- `Alt + S`: Focus window below  
- `Alt + A`: Focus window left
- `Alt + D`: Focus window right

**Window Movement:**
- `Alt + Shift + W/S/A/D`: Move window in direction
- `Alt + F`: Toggle fullscreen
- `Alt + R`: Reload AeroSpace configuration

**Window Manipulation Mode (`Cmd + M`):**
- `+/-`: Resize window
- `Arrow keys`: Navigate windows
- `Alt + Arrow keys`: Move window and exit mode
- `Esc`: Return to main mode

## 🚀 Installation

### Prerequisites
- macOS
- [GNU Stow](https://www.gnu.org/software/stow/)
- [Oh My Zsh](https://ohmyz.sh/)
- [AeroSpace](https://github.com/nikitabobko/AeroSpace)
- [Borders](https://github.com/FelixKratz/JankyBorders) (optional, for window borders)

### Quick Setup

1. **Install GNU Stow:**
   ```bash
   # Using Homebrew
   brew install stow
   ```

2. **Clone the repository:**
   ```bash
   git clone https://github.com/santi28/dotfiles.git ~/dotfiles
   cd ~/dotfiles
   ```

3. **Backup existing configurations (optional):**
   ```bash
   # Backup existing files if they exist
   [ -f ~/.zshrc ] && mv ~/.zshrc ~/.zshrc.backup
   [ -f ~/.vimrc ] && mv ~/.vimrc ~/.vimrc.backup
   [ -d ~/.config/aerospace ] && mv ~/.config/aerospace ~/.config/aerospace.backup
   ```

4. **Deploy dotfiles with Stow:**
   ```bash
   # From the dotfiles directory, stow all configurations
   stow .
   
   # Or stow individual configurations
   # stow zsh vim aerospace
   ```

5. **Install dependencies:**
   ```bash
   # Install Oh My Zsh (if not already installed)
   sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   
   # Install AeroSpace (using Homebrew)
   brew install --cask nikitabobko-aerospace
   
   # Install JankyBorders (optional, for window borders)
   brew tap FelixKratz/formulae
   brew install borders
   ```

6. **Apply changes:**
   ```bash
   # Reload shell configuration
   source ~/.zshrc
   
   # Start AeroSpace
   open -a AeroSpace
   ```

## 🔄 Managing Dotfiles with Stow

### Adding New Configurations
1. Add the configuration file to the appropriate location in the dotfiles directory
2. Run `stow .` to create symlinks
3. Update this README with the new configuration details

### Updating Configurations
Simply edit the files in the dotfiles directory. Changes are immediately reflected since Stow creates symlinks.

### Removing Configurations
```bash
# Remove all symlinks
stow -D .

# Remove specific configuration symlinks
# stow -D zsh vim aerospace
```

## 🎨 Customization

### Modifying AeroSpace Configuration
The AeroSpace configuration includes:
- **Gaps**: Customizable spacing between windows
- **Workspaces**: 10 workspaces with monitor assignments
- **Key bindings**: WASD-style navigation and manipulation
- **Borders**: Integration with JankyBorders for visual feedback

To modify the configuration, edit `.config/aerospace/aerospace.toml` and reload with `Alt + R`.

### Adding More Configurations
To add new dotfiles:
1. Add the configuration file to the appropriate location in this repository
2. Run `stow .` from the dotfiles directory to create the symlinks
3. Update this README with the new configuration details

> **Tip**: Use `stow -n .` to preview changes before applying them.

## 🔧 Troubleshooting

**Stow conflicts:**
- If Stow reports conflicts, backup and remove existing files before running `stow .`
- Use `stow -n .` to preview what Stow will do without making changes

**AeroSpace not starting:**
- Ensure AeroSpace is installed and has accessibility permissions
- Check System Preferences > Security & Privacy > Accessibility

**Oh My Zsh theme not loading:**
- Verify Oh My Zsh installation: `echo $ZSH`
- Restart terminal or run `source ~/.zshrc`

**Borders not working:**
- Install JankyBorders: `brew install FelixKratz/formulae/borders`
- Grant accessibility permissions if needed

**Symlinks not working:**
- Verify Stow is installed: `stow --version`
- Check that you're running `stow .` from the dotfiles directory
- Ensure target directory permissions allow symlink creation

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Feel free to fork this repository and adapt these configurations for your own use. If you have suggestions for improvements, please open an issue or submit a pull request.

---

*Last updated: July 25, 2025*
