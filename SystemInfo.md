## system software

- sway [window manager]
- foot [terminal emulator]
- tmux [terminal multiplexer]
- nautilus-gnome-disks [disk management]
- keepassxc[password manager]
- Minbrowser , chromium , Firefox [browser]
- thunar [file manager]
- Neovim, sublime text [text editor]
- stacer [system cleanup]
- qbittorrent [torrent cient]
- hyprpicker [color picker]
- grimshot [screenshot tool]
- xfce4-appfinder , wmenu [appfinder]
- evince [pdf viewer]
- ristretto [image viewer]
- mpv [video player]
- amberol [music player]
- git hosting [radicle]

### Fresh Install [Arch Linux]

yay -S sway foot i3status nautilus-gnome-disks polkit-gnome fish ttf-nerd-fonts-symbols ttf-fira-code fastfetch neovim sublime-text tmux papirus-icon-theme nwg-look kvantum qt5ct qt6ct starship brightnessctl xorg-xwayland xorg-xhost obsidian keepassxc qbittorrent hyprpicker grimshot man ttf-font-awesome firefox google-chrome clang evince timeshift ristretto inkscape npm yarn nodejs libreoffice-still ranger htop alacritty xdg-desktop-portal-gtk wayland-protocols ttf-jetbrains-mono-nerd ttf-jetbrains-mono meson ninja lite-xl min-browser

## install and setup wmenu from source [https://git.sr.ht/~adnano/wmenu]

> increase the size of zram [swap] if used the archinstall script by default the swap will be 2GB but you can increase it:
> go etc/systemd/zram-generator.conf
> add <zram-size=8192> to get 8GB of swap
> save the file and restart

### How to change the default entry to boot

There is a default entry inside /efi/loader/loader.conf that determine the default boot entry.

On a new install, it will look something like this:

default 665eca4ae83246df8ec17d1cbc6a1763\*

That first string of characters is you entry token which identifies the install. That is important if you are dual-booting with another Linux, otherwise it can be replaced with \*. That line supports wildcards and so if you want to boot the LTS kernel by default you could use something like this:

default 665eca4ae83246df8ec17d1cbc6a1763\*lts.conf

Alternatively, if you want to boot the mainline kernel by default, something like this should work:

default 665eca4ae83246df8ec17d1cbc6a1763-\*-arch?-?.conf

These changes will take effect on the next reboot and nothing else is required except modifying the file.

### Pacman

> pacman $
> pacman -Qdt [show the unused dependencies]
> pacman -Syu [update]

### gnome apps dark mode

xdg-desktop-portal-gtk.service [install this]
include /etc/sway/config.d/\* [add this to your sway config]
export XDG_CURRENT_DESKTOP=sway [add this to your bashrc]

> see if the xdg-desktop-portal-gtk is running using [systemctl --user]
> if not do the above restart check again and restart using
> [systemctl --user restart xdg-desktop-portal-gtk]

gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark' [run in terminal]

