---
title: "The Ultimate Minimal Ubuntu Installation Guide (i3 or OpenBox)"
date: 2017-05-17
forum: Tutorials
---

### Post by vandelsand on 2017-05-17
[FONT=arial][COLOR=#000000]Let’s install Ubuntu - minimal edition (using i3 Window Manager or OpenBox)

Disclaimer: a minimal version of Ubuntu is not for everyone. Ubuntu, the full distro, is the best place for a beginner to start. Minimal versions are stripped down and do not include many of the tools you might want as a beginner.
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]I love Ubuntu, and I am a fan of minimal builds. Sometimes the out-of-the-box feeling that you get with Ubuntu or a flavor thereof feels bloated. This is why I choose to run a minimal build. Also, I like cutting edge, which is hard to get with a non-rolling release distro. That being said, I will be using the MOST current versions of Ubuntu for this tutorial, which at the time of writing this is 17.04, Zesty Zapus. This should, however, be almost identical for 16.04 and 16.10.[/COLOR]

[COLOR=#000000]What you need:[/COLOR]
[COLOR=#000000]A computer with a linux distro on it, or a live distro on a USB stick[/COLOR]
[COLOR=#000000]An 8 GB partition, at least (the bigger the better; 8 GB will not be enough to do much). I don’t recommend overwriting your whole computer, and I recommend having another distro or Windows available for troubleshooting.[/COLOR]
[COLOR=#000000]Disk Image Mounter (available from gnome-disk-utility) or a similar program and an archive mounter/extractor (these are found on full versions of Ubuntu already)[/COLOR]
[COLOR=#000000]A wired internet connection (yes, a plug into your computer)[/COLOR]
[COLOR=#000000]A USB stick / flash drive / thumb drive[/COLOR]

[U][B][COLOR=#000000]Sections:[/COLOR]
[/B][/U][COLOR=#000000]Getting the mini.iso file[/COLOR]
[COLOR=#000000]Installing your minimal Ubuntu[/COLOR]
[COLOR=#000000]Partitioning[/COLOR]
[COLOR=#000000]First Boot[/COLOR]
[COLOR=#000000]Get a working distro[/COLOR]
[COLOR=#000000]Second boot, the fun begins
[/COLOR]Moving away from minimal - Theming

[U][B][COLOR=#000000]Getting the mini.iso file[/COLOR]
[/B][/U]
[COLOR=#000000]The very most minimal build of Ubuntu is from the mini.iso file, which is around 60 megabytes (give or take). The 17.04 version is available at:[/COLOR]
[URL="http://archive.ubuntu.com/ubuntu/dists/zesty/main/installer-amd64/current/images/netboot/"]
[/URL][[COLOR=#000000]http://archive.ubuntu.com/ubuntu/dists/zesty/main/installer-amd64/current/images/netboot/[/COLOR]]("http://archive.ubuntu.com/ubuntu/dists/zesty/main/installer-amd64/current/images/netboot/")

[COLOR=#000000]This ISO is really just a text based front end. You will need an internet connection that plugs into your computer for the install, just a heads up. The mini.iso downloads and builds Ubuntu onto whatever partition you tell it to, and then installs grub.[/COLOR]

[COLOR=#000000]Now you need to get the mini.iso you have downloaded onto a USB for installation. How do you do this? Well from a full Linux machine, or even a live version of Ubuntu, you need to do the following:[/COLOR]

[COLOR=#000000]If you have a modern machine, say, within the last 5 years, you probably have UEFI. The mini.iso does not yet support UEFI out of the box, but it REALLY does.[/COLOR]

[COLOR=#000000]1a. Open the mini.iso with Archive Mounter or Disk Image Mounter and extract the files to a folder. I used a folder named mini on my desktop.[/COLOR]

[COLOR=#000000]1b. These files will be locked (aka you don’t have permission to mess with them). Open a terminal and open your file manager using 

```
sudo -H thunar
```

 On Xubuntu the file manager is thunar, so make sure you don't write thunar if you don't use thunar (I usually use nautilus, this is just a live Xubuntu environment). (Ubuntu's Unity and Gnome use nautilus, on Cinnamon it is nemo, and there are others.) Right click on the original folder you made (remember, I made mini on my desktop) and go to properties. The third tab is permissions. Set all the permissions to read and write for your user. Also, set them recursively (all the way down through the folders).[/COLOR]

[ATTACH=CONFIG]275156[/ATTACH]

[COLOR=#000000]2. Navigate to this folder. There is a boot folder and then a grub folder (inside boot) of the extracted ISO; there you should find a file named efi.img.[/COLOR]

[COLOR=#000000]3a. Open it with Disk Image Mounter (or another IMG mounting program). Navigate to this mounted drive (or folder).[/COLOR]

[ATTACH=CONFIG]275157[/ATTACH]

[COLOR=#000000]3b. Navigate to the newly mounted drive, probably in the left pane.[/COLOR]

[COLOR=#000000]4. Here you will find a folder called efi. This folder (and its contents) is what you need. All you have to do is copy the efi folder from here to the root of the original extracted ISO (at the same level as the boot folder from ISO). (then unmount this mounted IMG file)[/COLOR]

[COLOR=#000000]5. Now you have at least two folders in your root extracted folder, boot and efi, as well as a bunch of other files. [/COLOR]

[ATTACH=CONFIG]275158[/ATTACH]

[COLOR=#000000]6a. Just copy all these files to a FAT32 formatted USB drive. OR[/COLOR]

[COLOR=#000000]6b. You can burn all these files to an ISO with Brasero and sudo dd that ISO to your USB. But 6a is easier.[/COLOR]

[COLOR=#000000]7. Reboot and boot from this newly created USB, like when you originally installed Ubuntu. Also, make sure you plug in that ethernet cable now.[/COLOR]

[U][B][COLOR=#000000]Installing your minimal Ubuntu[/COLOR]
[/B][/U]
[COLOR=#000000]Put the USB into the computer and boot just like when you would normally install Ubuntu. Hopefully you will find the minimal ISO boots and you can start the installation. Answer the questions, they're pretty easy and straightforward.[/COLOR]

[COLOR=#000000]Choose your languages, keyboard, and location. Make your hostname whatever you want. I like mui for minimal Ubuntu install, but ubuntu is perfectly fine.[/COLOR]

[COLOR=#000000]Probably don’t change the mirror, it will fill it in based on the locations you selected.[/COLOR]

[U][B][COLOR=#000000]Partitioning[/COLOR]
[/B][/U]
[COLOR=#000000]I only give myself about 25 -30 GB of space for the root (/) partition. I give myself 100 GB for my /home partition. On my 250 GB SSD, this setup gives me about 120 GB left for other distros and Windows.[/COLOR]

[COLOR=#000000]If you’re confused about partitioning, check here first for a refresher:[/COLOR]

[[COLOR=#1155cc]https://help.ubuntu.com/community/HowtoPartition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

[COLOR=#000000]The installer should select your EFI partition automatically for grub, don’t worry about that. [/COLOR]

[COLOR=#000000]I recommend manual partitioning.[/COLOR]

[IMG]http://imgur.com/yazWeU7.png[/IMG]

[COLOR=#000000]For the screen where you edit your partitions, you’ll need at the very least a root partition. I recommend at least 8 GB. No name is required. Use as EXT4, but other filesystems are available if you like. For root, the mount point should be /. Nothing else is required, so just go down to done setting up this partition.

[/COLOR][IMG]http://imgur.com/W3nzhBx.png[/IMG]

[COLOR=#000000]If you want, you can have other partitions. But this is the easiest partition scheme. If you plan to have a lot of files, like gaming on Steam or videos and music, I recommend your root partition be large. Personally, as I wrote before, I split my home and root so that I can make new distros I install use the same /home partition.[/COLOR]

[COLOR=#000000]Finish and write changes to disk. If you want a swap partition, go ahead. But I don’t use swap anymore because I have 16 GB of RAM and I only ever “poweroff” my machine, I don’t sleep or suspend. So I am comfortable with a setup having no swap partition. If your machine has [/COLOR][COLOR=#000000]less [/COLOR][COLOR=#000000]than 8 GB of RAM, I would recommend a swap partition. But that is not a scientific recommendation.[/COLOR]

[IMG]http://imgur.com/u0akJnX.png[/IMG]

[COLOR=#000000]When configuring updates, that’s up to you. I do no automatic updates because I usually do manual updates incessantly anyway. Like I said, I like to be up to date.[/COLOR]

[COLOR=#000000]Software selection - If you want the bare minimum Ubuntu like I do, uncheck the only checked software. There should be no checks. Otherwise, look over the things you want and select them. The more you select here, the more packages will be installed (in this picture, Xubuntu desktop is selected, but for minimal do not select any).
[/COLOR]
[ATTACH=CONFIG]275161[/ATTACH]

[COLOR=#000000]If you select nothing on this tab, you will get a Ubuntu build with approximately 238 packages. Pretty sweet if you ask me.[/COLOR]

[COLOR=#000000]The rest of the installation process is very straight forward. When it is finished, remove your USB and reboot into your new Ubuntu machine.[/COLOR]

Pictures from the installation media (not the desktop files portion) were borrowed from [https://onetransistor.blogspot.com/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html](https://onetransistor.blogspot.com/2015/12/install-ubuntu-minimal-cd-uefi-enabled.html)
[COLOR=#000000]
[U][B]First Boot
[/B][/U][/COLOR]
[COLOR=#000000]Upon your first boot into Ubuntu, you will probably not have a working setup (it works, but looks like it does not). So, to prevent this initial scare, during your grub screen press “e” on the first option (which should be Ubuntu). [/COLOR]

[COLOR=#000000]On the linux line, one of the longer one lines that take more than one line, past half way down, you will see “$vt_handoff”. Ensure you remove this portion of the line and press F10 to boot into your new build. You will be presented with tty1 and you may see some errors, but probably without any real issues.[/COLOR]

[COLOR=#000000]Congratulations![/COLOR]

_**[COLOR=#000000]Get a working distro[/COLOR]**_

[COLOR=#000000]Lets fix that grub so you don’t have to press “e” every time you restart your machine. [/COLOR]

```
[COLOR=#000000]sudo apt install nano[/COLOR]
```

[COLOR=#000000]nano is my preferred command line interface (CLI) text editor. Feel free to use any other if you like. If you're using a GUI already, or if you're editing this partition from a working machine, SSH, or some other GUI, you can feel free to use gedit, geany, mousepad, or any other GUI text editor. Unfortunately, that isn't going to work well without a working GUI environment (namely X).[/COLOR]

```
[COLOR=#000000]sudo nano /etc/default/grub[/COLOR]
```

[COLOR=#000000]On the “GRUB_CMDLINE_LINUX_DEFAULT” entry remove “quiet” and “splash”. Mine is just left with =””.[/COLOR]

In the command line interface nano, Ctrl+O saves and Ctrl+X closes and will take you back to the CLI.

[COLOR=#000000]Now update your grub with [/COLOR]

```
[COLOR=#000000]sudo update-grub && sudo update-grub2[/COLOR]
```

[COLOR=#000000]Voila. You shouldn’t have that issue anymore.[/COLOR]

[COLOR=#000000]Now what you want is a nice, small, working distro. You have that, technically, but you need to get a more usable interface going. You need a display manager, at least a window manager (or a full desktop environment, networking packages, some common drivers, probably a compositor, and a display server.[/COLOR]

[COLOR=#000000]For your display manager I recommend lightdm. This is a very friendly, lightweight display manager. With that I also recommend the gtk greeter and the settings package. I will list the commands after all my recommendations.[/COLOR]

[COLOR=#000000]For your window manager I recommend i3 (with preference for i3-gaps). OpenBox is also a good option for a lightweight, minimalist window manager. If you prefer your windows to move around and adjust size with the mouse, probably go with OpenBox. If you are looking to move to a more exciting, [/COLOR][COLOR=#000000]*tiling*[/COLOR][COLOR=#000000], window manager, you should check out i3.[/COLOR]

[COLOR=#000000]For networking I prefer wicd. Usually I would go with Network Manager, but it has been giving me hard time lately. Though, Network Manager does have a nice CLI end called nmtui. wicd is lighter though.[/COLOR]

[COLOR=#000000]ubuntu-drivers-common will detect and install additional Ubuntu driver packages for you. (gpu-manager is a good example)[/COLOR]

[COLOR=#000000]mesa-utils and mesa-utils-extra have miscellaneous Mesa GL utilities, useful for more advanced processes using GPUs (i.e. GLX extension on xserver-xorg and glxinfo)[/COLOR]

[COLOR=#000000]compton is a lightweight compositor for X11, based on xcompmgr.[/COLOR]

[COLOR=#000000]For a file manager I prefer nautilus. But a lighter choice may be thunar. For a terminal emulator, I prefer gnome-terminal. Again, there are lighter choices.[/COLOR]

[COLOR=#000000]And finally, xorg is the X.Org X Window System (pretty standard right now) and xserver-xorg is the server side of it.[/COLOR]

[COLOR=#000000]Lets install:[/COLOR]

[COLOR=#000000]i3 minimal, like i prefer:[/COLOR]

```
[COLOR=#000000]sudo apt install lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings i3 wicd ubuntu-drivers-common mesa-utils mesa-utils-extra compton xorg xserver-xorg nautilus gnome-terminal[/COLOR]
```

[COLOR=#000000]OpenBox minimal:[/COLOR]

```
[COLOR=#000000]sudo apt install lightdm lightdm-gtk-greeter lightdm-gtk-greeter-settings openbox obconf obmenu wicd ubuntu-drivers-common mesa-utils mesa-utils-extra compton xorg xserver-xorg nautilus gnome-terminal[/COLOR]
```

[COLOR=#000000]From my personal experience, you want to install the recommendations.[/COLOR]

[COLOR=#000000]Some notes: if you have an nvidia GPU, also:[/COLOR]

```
[COLOR=#000000]sudo apt install nvidia-375[/COLOR]
```

[COLOR=#000000]If you have an Intel processor, which you probably do, I recommend using Intel’s proprietary microcode, which is not open source.[/COLOR]

```
[COLOR=#000000]sudo apt install intel-microcode[/COLOR]
```

[COLOR=#000000]If you are using a desktop and are going to keep the ethernet cord plugged in, SKIP this section. If you want to use a wifi dongle or wifi in general, I like to disable the ethernet port (I really only use a laptop and can reenable it if need be.[/COLOR]

```
[COLOR=#000000]sudo nano /etc/network/interfaces[/COLOR]
```

[COLOR=#000000]To disable the ethernet port (somewhat superficially) put a # (the hash) symbol next to each line here, except the source line.[/COLOR]

[COLOR=#000000]Now reboot with:[/COLOR]

```
[COLOR=#000000]sudo poweroff --reboot[/COLOR]
```

[COLOR=#000000]And bask in your glory.[/COLOR]

_**[COLOR=#000000]Second boot, the fun begins[/COLOR]**_

[COLOR=#000000]CONGRATS, you’ve made it.[/COLOR]

[COLOR=#000000]If you’re using i3, you need to read the user guide over at i3.[/COLOR]

[[COLOR=#1155cc]https://i3wm.org/docs/userguide.html[/COLOR]]("https://i3wm.org/docs/userguide.html")

[COLOR=#000000]It will help get you started and mastering the keyboard in no time.[/COLOR]

[COLOR=#000000]If you're using i3, I recommend putting[/COLOR]

```
[COLOR=#000000]exec --no-startup-id compton -b[/COLOR]
```

[COLOR=#000000]Into your config file, that will enable compositing at boot. Also [/COLOR]
[COLOR=#000000]
```
exec --no-startup-id wicd-client --tray
```[/COLOR]

[COLOR=#000000]Will put a wifi applet in your tray. As will volumeicon (which you will need to install as volumeicon-alsa).[/COLOR]

```
[COLOR=#000000]exec --no-startup-id volumeicon[/COLOR]
```

[COLOR=#000000]But I won’t get too deep into i3 and configs for this tutorial. [/COLOR]

[COLOR=#000000]If you’re using OpenBox, I recommend finding obmenu-generator. That will create fun, dynamic, pipe menus for you on the go.[/COLOR]

[COLOR=#000000]For both i3 and OpenBox I recommend using nitrogen for your wallpaper. There are other options, however.

[U][B]Moving away from minimal - Theming
[/B][/U]
What you have created is a nice, working minimal Ubuntu build with less than 800 packages. But lets get it looking better. For this we will install a whole mess of themes and some appearance tweaking tools.

Top GTK Themes Download - 
WARNING - Using the "Top GTK Themes Download" defeats the idea of a minimal build because it installs many files, themes, and stuff you're not going to use (you can only use one theme at a time!). But it isn't that much. If you want a bunch to look at and choose from, follow this small section. If not, install one theme you like and move onto the applying themes section.

Navigate to your downloads file
[SIZE=2]
```
cd ~/Downloads/
```

Install git and get to downloading (doesn't take long):

[/SIZE][/COLOR]```
[SIZE=2]sudo apt install git && git clone https://github.com/tliron/install-gnome-themes[/SIZE]
```[SIZE=2]

Now navigate to those files:

[/SIZE]```
cd ./install-gnome-themes/
```

And run their install script this will take approximately 5 minutes

```
./install-gnome-themes
```

Script information borrowed from: [http://ubuntuhandbook.org/index.php/2017/05/install-top-gtk-themes-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2017/05/install-top-gtk-themes-ubuntu-16-04/)

How to apply these themes

BOOM! You have a ton of themes. But how do you implement these themes, you may ask? Well I recommend using all of the following programs for changing themes on i3: lxappearance, gtk-chtheme, and qt4-qtconfig. lxappearance is a nice program from LXDE that switches your GTK+ themes. gtk-chtheme is a little program for changing your GTK+ 2.0 themes. The third program, qt4-qtconfig is a QT 4 configuration tool. You will see how they work in a minute.

Lets install them:

```
sudo apt install lxappearance gtk-chtheme qt4-qtconfig
```

Now, if you're using i3, use alt+d to run dmenu at the top of your screen and open lxappearance. You should have listed the themes your previously downloaded and installed with the script. Select a theme you like here (I like Candra-Theme-3.20-Dark and Darker). Press apply. Go to the icon theme tab and select the icons you like and apply. That should be basically it for lxappearance.

Now close this and alt-d to open gtk-chtheme. Whatever theme you choose in lxappearance, pick the same one here. Apply. Okay and close. Now alt-d to open qt4-qtconfig, which you may notice has installed itself as qtconfig-qt4. 

The first drop down menu is Select GUI Style. Select GTK+ here. Then go to file, save. Then file, exit.

Its that easy! Make sure you do the same for icon packs. I like Numix but it is getting a little old. For Numix icon pack all you need to do after install is set it in lxappearance.[/FONT]

---

### Post by twistyduck on 2018-01-20
Hi vandelsand,

Thanks for a fantastic guide, very clear and informative.

Regarding the black screen boot issue, I have [posted a question on Ask Ubuntu]("https://askubuntu.com/questions/997965/how-to-boot-using-splash-quiet-after-a-minimal-installation-with-no-selected-p").

I'd be very grateful if you had any feedback, or perhaps you are curious yourself.

Obviously not having a friendly boot process isn't the end of the world, but there are practical advantages if you're using encrypted LVM and it's a good opportunity to improve my Linux knowledge.

---

