---
title: "Ubuntu-like GNOME on Raspberry Pi OS Lite (NO SNAP)"
date: 2024-11-20
forum: Tutorials
---

### Post by Wobbo on 2024-11-20
I've been a long-time Ubuntu user for over a decade. Recently, I've decided to avoid snap packages due to personal preferences and performance issues, especially on older hardware and Raspberry Pi. Here, I will guide you through customizing Debian GNOME on Raspberry Pi 4 and 5 using Raspberry Pi OS Lite without snap. If you go to the end of the steps list, there is a copy/paste command list for easy terminal use. *[COLOR=#c5c4c4]3.4. Command List for Easy Copying[/COLOR]*


One notable difference with Ubuntu on Raspberry Pi is the limited video quality for services like YouTube, and Netflix isn’t playable. With this guide completed, however, Raspberry Pi 4 can smoothly play YouTube at 1080p (30fps) and supports Netflix, though with minor stuttering. Raspberry Pi 5 can handle YouTube in 4K (30fps) and play Netflix seamlessly.


Additionally, Ubuntu and Debian share the same software foundation, ensuring a consistent user experience. A minor distinction is the default web browser: Ubuntu comes with Firefox, while Raspberry Pi OS uses Chromium. Personally, I prefer replacing the default video player Totem with Celluloid, as it is lighter and performs better on the Raspberry Pi.


**Basic**
Install [Raspberry Pi OS **_Lite_** (64-bit)]("https://www.raspberrypi.com/software/operating-systems/#raspberry-pi-os-64-bit"). If you are using the Raspberry Pi Imager on Windows to install Raspberry Pi OS Lite, I recommend filling in the Customization Settings. This allows you to pre-configure settings like the hostname, enable SSH, set up a username and password, and configure your Wi-Fi details. 


**1.1. Installation Debian GNOME**
Enable SSH to make it easier to copy commands from the forum and paste them into the Raspberry Pi. For detailed instructions, see the SSH guide on the [Raspberry Pi website]("https://www.raspberrypi.com/documentation/computers/remote-access.html#ssh").


```
sudo raspi-config
```
Enable SSH go to [COLOR=#c5c4c4]*3. Interface Options > SSH*[/COLOR]
[IMG]https://wobbo.org/screenshots/2024-06-29 21-01-00 003.png[/IMG]


To find your local IP address on Raspberry Pi OS Lite, you can use the **[COLOR=#2e8b57]ifconig[/COLOR]** command in the terminal. Look for either [COLOR=#2e8b57]**eth0**[/COLOR] (for a wired connection) or [COLOR=#2e8b57]**wlan0**[/COLOR] (for a wireless connection). Under the relevant section, locate the line starting with inet to find the IP address currently used by your Raspberry Pi. This IP address will typically begin with  [COLOR=#2e8b57]**192.168**[/COLOR]. If both eth0 and wlan0 are present, the system usually prioritizes eth0 for network connections. This is the address you will use to connect via SSH.


During the installation of Debian GNOME, I will indicate when you need to reboot. You do not need to reboot until I tell you.  To connect to your Raspberry Pi from an Ubuntu computer using SSH. Every time you reboot you need to connect SSH. Open a terminal and run:
```
ssh <username>@<RaspberryPi_IP_Address>
```
```
sudo apt update && sudo apt full-upgrade
sudo reboot
```


Just to start up clean: 
```
sudo apt autoremove && sudo reboot 
```


**1.2. Installing GNOME Core**
Install only gnome-core for a clean, minimalist setup:
```

sudo apt install gnome-core

```




**1.3. Language Settings**
By default, UK English is selected. I disable this and choose US English and my own language. To adjust the commands for configuring other languages, you can modify the examples provided in this reply: [Language commands]("https://forums.raspberrypi.com/viewtopic.php?t=373028&start=25#post_content2270117")


```

sudo dpkg-reconfigure locales

```
I turn off [COLOR=#c5c4c4][s]en_GB.UTF-8 UTF_8[/s] [/COLOR]and turn on [COLOR=#c5c4c4]*en_US.UTF-8 UTF-8*[/COLOR]


[[IMG]https://wobbo.org/screenshots/2024-06-29 21-01-00 001.png[/IMG]]("https://wobbo.org/screenshots/2024-06-29 21-01-00 001.png")
**1.4. Ubuntu Design**
Install the Ubuntu theme for GNOME:


```

sudo apt install yaru-theme-gnome-shell yaru-theme-gtk yaru-theme-icon yaru-theme-sound yaru-theme-unity fonts-ubuntu fonts-ubuntu-title fonts-ubuntu-console

```


**1.5. Chromium as Web Browser**
Remove Firefox and install Chromium:
```

sudo apt remove firefox-esr
sudo apt install rpi-chromium-mods
```


**1.6. Media Player**
Replace Totem with Celluloid for better codec support. This is a personal video player. Totem doesn't work well. It's annoying with the pre-decided streaming services in your favorites list that you can't change. I chose Celluloid because it has no issues with codecs and is a GNOME program. Oddly, when you install Celluloid, you also get the mpv program. After installing Celluloid, I remove mpv.


```

sudo apt remove totem
sudo apt install celluloid rhythmbox
sudo apt remove mpv

```


I recommend installing additional GStreamer plugins. These plugins provide support for a wide range of video and audio formats.
```
sudo apt install gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-alsa gstreamer1.0-pulseaudio gstreamer1.0-x
```


**1.7. Change User Name**
Update the display name of the user. When you're finally done with the installation, you'll eventually need to log into your OS. Just like in Ubuntu, your name appears on the screen. But because you installed GNOME-core, you never filled this in. If you want to do this, here's how:
```

sudo usermod -c "Your Name" username

```


For example: *[COLOR=#c5c4c4]sudo usermod -c "Mr. Wobbo" wobbo[/COLOR]*


**1.8. Creating Standard Folders**
With GNOME-core, not all user folders are created. In Ubuntu, the standard folders get appropriate icons. To add these folders and icons, you do the following. Create the standard folders and set the paths. 
```

mkdir -p ~/{Desktop,Documents,Downloads,Music,Pictures,Videos,Public,Templates}
mkdir -p ~/.config/
nano ~/.config/user-dirs.dirs

```


And paste in user-dirs.dirs the following (for English):
```

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_TEMPLATES_DIR="$HOME/Templates"

```
Save and exit press [COLOR=#2e8b57]**Ctrl + X**[/COLOR]. 


[[IMG]https://wobbo.org/screenshots/2024-06-29 21-01-00 002.png[/IMG]]("https://wobbo.org/screenshots/2024-06-29 21-01-00 002.png")


**1.9. Printing, Office Suite and Text Editor**
Install LibreOffice:
```

sudo apt install libreoffice-writer libreoffice-calc libreoffice-impress libreoffice-gtk3 libreoffice-gnome libreoffice-style-* libreoffice-help-en-us libreoffice-l10n-en-us hyphen-en-us hunspell-en-us

```


Install scanner:
```

sudo apt install simple-scan

```


Install text editer:
```

sudo apt install gnome-text-editor

```
*[COLOR=#c5c4c4]Previously ubuntu used gedit.[/COLOR]*


I am using an HP printer/scanner:
```

sudo apt install hplip

```


**1.10. Remove greeter Debian banner**
To remove the banner 'Debian' from the GDM3 greeter, follow these steps:
```
sudo nano /etc/gdm3/greeter.dconf-defaults
```
In the file, place a [COLOR=#2e8b57]**#**[/COLOR] at the beginning of the line:```
#logo='/usr/share/images/vendor-logos/logo-text-version-64.png'
``` Save and exit press [COLOR=#2e8b57]**Ctrl + X**[/COLOR]. 


[[IMG]https://wobbo.org/screenshots/2024-11-14 RPi login.png[/IMG]]("https://wobbo.org/screenshots/2024-11-14 RPi login.png")




**1.11. Booting the System**
Set GNOME as the default desktop environment and reboot:
```

sudo apt install gnome-tweaks
sudo systemctl set-default graphical.target
sudo reboot

```








**2.1. Debian Desktop to Ubuntu Desktop**
From now on, no more terminal commands are needed. There are some things that are not available by default or need to be adjusted to mimic Ubuntu. In Debian GNOME, you can't use the Desktop. The menu dock is very different. The theme needs to be adjusted, for example, the font.




**2.2. GNOME Addons**
I use Chromium Shell to add GNOME Extensions. Go to [Chromium GNOME Shell Integration]("https://chromewebstore.google.com/detail/gnome-shell-integratie/gphhapmejobijbbhgpjhcjognlahblep") and add it to your extensions. 
Next, you can add the following GNOME extensions: [Desktop Icons NG (DING)]("https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/") and [Dash to Dock]("https://extensions.gnome.org/extension/307/dash-to-dock/").


[[IMG]https://wobbo.org/screenshots/2024-06-29 21-01-00 004.png[/IMG]]("https://wobbo.org/screenshots/2024-06-29 21-01-00 004.png")
**2.3. Setup Desktop Icons and Tweaks**
Configure `Desktop Icons NG (DING)` and Tweaks:


[[IMG]https://wobbo.org/screenshots/2024-06-29 21-01-00 Setting.png[/IMG]]("https://wobbo.org/screenshots/2024-06-29 21-01-00 Setting.png")




**2.4. Chromium Video Fix**
Turn off video acceleration to ensure proper video playback. Open Chromium '*Settings*', go to '*System*', and turn off '*Use graphics acceleration when available*'. ][COLOR=#c5c4c4]chrome://settings/system[/COLOR]
[IMG]https://wobbo.org/screenshots/2024-07-27%2020-10-40.webp[/IMG]


**2.5. Chromium Settings**
Configure Chromium to integrate smoothly with the OS. If you set it up this way, it will match the style.


[[IMG]https://wobbo.org/screenshots/2024-06-29 21-01-00Chromium.png[/IMG]]("https://wobbo.org/screenshots/2024-06-29 21-01-00Chromium.png")
**2.6. Others** 
Almost all appearance themes fit neatly into the general settings. For example, LibreOffice automatically uses the Ubuntu theme. If you use Gedit, you need to manually set the dark mode. There are parts of GNOME Settings where some elements should be orange, but they remain Debian's official blue. I don't know how to change that. There are some personal settings that might differ from the Ubuntu defaults. My Debian GNOME runs much faster than Ubuntu. Despite my preference, you can still install *snap* on this setup. I always test the game '0 A.D.' to check performance.








**3.1. Conclusion**
Are there things I missed or could improve? Let me know.
This process transforms your Raspberry Pi into a fast, *snap*-free, Ubuntu-like environment, perfect for those who prefer a traditional .deb-based setup. This is ideal for users with older hardware or those who prefer control over automatic updates.


**3.2 My Opinion on snap**
When *snap* was introduced, I found it frustrating, especially since it seemed like every installation created an unwanted *snap* folder. The move to *snap*-only for some essential applications like Firefox, without the option for a .deb installation, reinforced my decision to seek an alternative.


**3.3. Differences in GNOME Versions**
It's important to note that different versions of GNOME have different features and performance characteristics. For example, Ubuntu 22.04 LTS uses GNOME 42, while the latest version, Ubuntu 24.04, has GNOME 46. Raspberry Pi OS is currently at GNOME 43.8. 


**3.4. Command List for Easy Copying**
```
# If you are using SSH
sudo raspi-config
ifconfig
ssh <username>@<RaspberryPi_IP_Address>


# 1. Installation Debian GNOME
sudo apt update && sudo apt full-upgrade
sudo apt autoremove && sudo reboot 


# 2. Installing GNOME Core
sudo apt install gnome-core


# 3. Language Settings
sudo dpkg-reconfigure locales


# 4. Ubuntu Design
sudo apt install yaru-theme-gnome-shell yaru-theme-gtk yaru-theme-icon yaru-theme-sound yaru-theme-unity fonts-ubuntu fonts-ubuntu-title fonts-ubuntu-console


# 5. Media Player
sudo apt remove firefox-esr
sudo apt install rpi-chromium-mods


# 6. Media Player
sudo apt remove totem
sudo apt install celluloid rhythmbox
sudo apt remove mpv
sudo apt install gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-tools gstreamer1.0-alsa gstreamer1.0-pulseaudio gstreamer1.0-x


# 7. Change User Name
sudo usermod -c "Your Name" username


# 8.1 Creating Standard Folders
mkdir -p ~/{Desktop,Documents,Downloads,Music,Pictures,Videos,Public,Templates}
mkdir -p ~/.config/
nano ~/.config/user-dirs.dirs


# 8.2 copy/past in user-dirs.dirs
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_TEMPLATES_DIR="$HOME/Templates"


# 9. Printing and Office Suite
sudo apt install libreoffice-writer libreoffice-calc libreoffice-impress libreoffice-gtk3 libreoffice-gnome libreoffice-style-* libreoffice-help-en-us libreoffice-l10n-en-us hyphen-en-us hunspell-en-us
sudo apt install gnome-text-editor
sudo apt install simple-scan
sudo apt install hplip


# 10. Remove greeter Debian banner
sudo nano /etc/gdm3/greeter.dconf-defaults
#logo='/usr/share/images/vendor-logos/logo-text-version-64.png'


# 11. Booting the System
sudo apt install gnome-tweaks
sudo systemctl set-default graphical.target
sudo reboot
```

---

