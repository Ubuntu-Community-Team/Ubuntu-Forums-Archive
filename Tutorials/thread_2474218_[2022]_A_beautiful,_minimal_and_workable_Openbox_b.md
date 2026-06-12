---
title: "[2022] A beautiful, minimal and workable Openbox based session [on new/old machines]"
date: 2022-04-24
forum: Tutorials
---

### Post by sbnwl on 2022-04-24
[I][B]Openbox is a simple, lightweight and highly configurable window  manager and could be set up as a desktop-environment, like KDE and Gnome. This post shares a guide (including configuration files) to quickly set up a clean and the most lightweight graphical environment on laptops, desktops and servers.
[/B]
The best part is that you could install it alongside Gnome, KDE, Cinnamon, or any other desktop environment without interference. Follow the procedure to install fresh breeze of Openbox based session on Ubuntu and all of its derivatives.[/I] 
> * If one can deal with other package management systems such as **dnf**, **pacman** or **eopkg**, then this tutorial could also be  implemented in **Fedora**, **Arch** Linux or any other Linux distribution.*
[I]The purpose of this post is to prepare a clean, simple, productive, yet snappy and responsive desktop environment for the users, while also maintaining a  beautiful, aesthetically pleasant (yes, I care for this) desktop with  modern touch/effects around the desktop objects and windows. This  could especially revive your old machines with low resources, and also feels enjoyable on new machines.
[/I][HR][/HR][CENTER]**The following steps summarize the procedure to setup the desktop environment**[HR][/HR][LEFT]**1.** To begin with, one has to install some packages first. Open a terminal and issue the following commands:
```

sudo apt-get install openbox tint2 xfce4-panel xfce4-notifyd xfce4-whiskermenu-plugin wget unzip scrot xclip plank compton feh conky-all curl gnome-screensaver volumeicon-alsa lxappearance arandr

```
[/LEFT]
[/CENTER]
**2.** Now we need to write some configuration files to use with some  of the above packages, though I am not actually going to do it here.  Instead I let you **download my own files** in a zip package. 
[[I]The  whole point of supplying the configuration stuff in one zip file is to  make the entire procedure simpler for everybody to implement by issuing the following set of commands]
[/I]```

wget --no-check-certificate -r 'https://drive.google.com/uc?export=download&id=1Wu71sJwFgxr7oHdKA3u4mDyLLUWM93oA' -O OpenboxInstall.zip
mv OpenboxInstall.zip ~/

```
**3. **Make sure that the downloaded *OpenboxInstall.zip* file is in your home directory.[B]
[**Caution: If your operating system is Xubuntu or you are already  using the XFCE desktop, then first backup your original ~/.config/xfce4  directory since we are making changes to this directory.**]
[/B] Extract this zip file such that the extracted contents merge with the  existing folders and overwrites any existing files within the merged  folders. The following command will do this for you in one go:  
```

cd ~/
unzip -o OpenboxInstall.zip

```
The -o option makes sure it overwrites the files without prompting. By now, It's all done!

**4.** *This step is optional***, ***only for those who like to switch to other themes for any reason*[B]. 
[/B]Download and install[COLOR=#000000] [Moka]("https://github.com/snwh/moka-icon-theme"), [arc]("https://github.com/horst3180/arc-icon-theme") or [/COLOR][COLOR=#000000][MAC-iOS]("https://dl.opendesktop.org/api/files/download/id/1474772478/Mac%20iOS%20Icon%20theme%20v2.tar.xz") icon themes. Also install the [arc gnome shell theme]("https://github.com/horst3180/arc-theme"). 
First install the *arc-theme*:
[/COLOR]```

wget https://github.com/horst3180/arc-theme/archive/master.zip
unzip -o master.zip
mkdir -p ~/.themes/arc-theme
mv ./arc-theme-master/common/* ~/.themes/arc-theme
rm -r arc-theme-master [COLOR=#000000][FONT=&amp]master.zip
[/FONT][/COLOR]
```
Then install the *moka icon* theme:
```

wget https://github.com/snwh/moka-icon-theme/archive/master.zip
unzip -o master.zip
mkdir -p ~/.local/share/icons
mv ./moka-icon-theme-master/Moka ~/.local/share/icons
rm -r moka-icon-theme-master master.zip

```
Then install the *arc icon* theme:
```

wget https://github.com/horst3180/arc-icon-theme/archive/master.zip
unzip -o master.zip
mkdir -p ~/.local/share/icons
mv ./arc-icon-theme-master/Arc ~/.local/share/icons
rm -r arc-icon-theme-master master.zip

```

Now, either open *lxappearance* (in terminal) or the *gnome-tweaks* and set the *shell theme* as *arc*, and *icon theme* also as *arc*.

**5.** Log out of the current session. On the login screen, select the *Openbox Session* and then log into your account. 
(*Just look for the "openbox gear" at the bottom right location of login screen and select it before logging into your account.*)

At this point, right-click on the desktop and click '*Terminal emulator*'. In the terminal, type *lxappearance* and hit the return key. A theme configuration window will open. One must select a theme of choice and apply. Logout by using right-click and clicking '*Exit*'. Now login back. Everything is transformed into a beautiful desktop by now.

If all gone well, a beautiful and extremely fast Desktop Session should be ready to serve you! 
:popcorn:



[HR][/HR]
**Want to make it more useful and stylish?** Follow here:
**1.** Ulauncher as a desktop launcher is perfect choice. Follow the steps below to install the Ulauncher:
(*use Ctrl+Space to ignite after installation*)
```

wget https://github.com/Ulauncher/Ulauncher/releases/download/5.14.4/ulauncher_5.14.4_all.deb
sudo apt install ./ulauncher_5.14.4_all.deb
rm ulauncher_5.14.4_all.deb

```
After installation, open the terminal and type ulauncher and hit the return key. Then press Ctrl+Space key combination and a rectangular window of Ulauncher will appear. Click the gear icon at the top right corner of the window, and a preference window will show up. Set it to '*Launch at Login*'. Also set the Color Theme as '*Elementary Dark*' if you wish. Now onward, the Ulauncher (menu) window can be launched at wish by hitting the Ctrl+Space key combination. 
**2.** Ubuntu Yaru theme packages released recently with Ubuntu 22.04 are just awesome! Here is how to install yaru GTK, icon and shell themes:
```

wget http://launchpadlibrarian.net/596607270/yaru-theme-gtk_22.04.4_all.deb
wget http://mirrors.edge.kernel.org/ubuntu/pool/main/y/yaru-theme/yaru-theme-icon_22.04.4_all.deb
sudo apt install ./yaru-theme-icon_22.04.4_all.deb ./yaru-theme-gtk_22.04.4_all.deb

```



**Restoration Step (Be careful, don't follow without reading)**
> To undo the changes reversibly to your openbox session, or to renew the Openbox configuration (in case you messed up while playing yourself with  the configuration files) the following commands maybe handy for you:
```

cd ~/.config/ && rm -rf openbox tint2 xfce4 plank
cd ~/.local/share/ && rm -rf xfce4 plank
cd ~/ && rm .compton.conf .conkyrc

```
> 
** Sources and References:**
1. Theme Mistral-Thin at: [https://www.box-look.org/p/1169127/](https://www.box-look.org/p/1169127/)

---

### Post by mIk3_08 on 2022-07-03
Thanks for sharing. I may try this one soon. Regards and cheers.

---

### Post by sbnwl on 2023-02-08
Let me know how it went.

---

