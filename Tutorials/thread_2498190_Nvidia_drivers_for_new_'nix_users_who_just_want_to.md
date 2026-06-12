---
title: "Nvidia drivers for new 'nix users who just want to game already!!!"
date: 2024-06-03
forum: Tutorials
---

### Post by Mandle on 2024-06-03
NVIDIA DRIVERS FOR NEW 'NIX USERS WHO JUST WANT TO GAME ALREADY!!! (there's some pics on the [reddit]("https://www.reddit.com/r/linux4noobs/comments/1d6w301/ubuntu_xubuntu_kubuntu_2404_nvidia_guide/") version that i haven't quite figured out here yet, if you need some visuals) [https://www.reddit.com/r/linux4noobs/comments/1d6w301/ubuntu_xubuntu_kubuntu_2404_nvidia_guide/](https://www.reddit.com/r/linux4noobs/comments/1d6w301/ubuntu_xubuntu_kubuntu_2404_nvidia_guide/)
I take no responsibility if you break your system. If you've done a fresh install, this should work fine. If you have already tried to install and fail, you may have mixed results. If you post your error, i might be able to help, but websearch, discord, irc and forums will get you there faster. And you don't have to install the 550 driver. You can install 535 by just replacing the numbers. (although setting drm I think may be slightly different)
(and yes, I ramble a bit, but it's pretty much all important and useful.)
If you think your drivers are already setup, you'll want to try 3 things.
```
sudo dmesg | grep drm
```
should be no errors
```
glxinfo | grep OpenGL
```
should see nvidia, not mesa
and if you start nvidia settings from the start menu, you should be able to save to xorg.conf, type your password, and save without errors.
DISABLE SECURE BOOT
This has trolled me for days. You can enable it later if you want to, but for now, just to cut down on "issues" disable it. To do so, you need to boot into bios, and look around till you find secureboot, and shut it off. Depending on your system, esc, f1, f2 f10, f12 or del, when spammed on the keyboard at boot time, will log you into bios. One of those keys. Personally, i've been doing it so long, it's two 3 finger salutes. (ctrl alt del being a 3 finger salute :-)== It will often say on the boot screen as well. If you want to enable it, i believe searching "uefi secureboot ubuntu" should bring you to the appropriate place.
I am assuming a few things with this guide. First, you have a basic knowledge of what a terminal or command line console is. CMD or command in windows. It is possible to do nearly all of this with the gui, but new users need some familiarity with the terminal, and this guide is a pretty good starting point if you're new to linux. And just the basics is totally enough. Lots of gui apps. But terminal is great for troubleshooting an issue. There are 7 commands and 3 reboots. The first 2 commands and reboot aren't absolutely necessary, but on a fresh install, you should probably do this first no matter what.
So lets get started.
After you've done your install, open a terminal. Ubuntu and xubuntu, start button start typing term, should be the first option. Kubuntu, term will work as well, but konsole is the app installed by default. Other flavours of buntu should have similar experiences. Type the commands and your password when it asks.  Wait for each line to complete before moving to the next step. This should take a few minutes at most.
First, we want to update and sync our repositories,(repo's) and then upgrade our packages. Copy and paste the next 2 lines 1 at a time, press enter the first time, it should ask for your password. press enter when done.
```
sudo apt update
sudo apt upgrade
```
1st reboot
When you do the upgrade command, it will ask if you want to continue. You can take a look at what it's upgrade, and say yes. I prefer doing it via command line personally, but there is also a gui that may have already popped up for you, asking to upgrade. That should be ok as well. I have had some issues in the past, but that was many years ago. But I mainly do it from terminal. Also, so that if you get an error, it's much easier to recover.
on login open up a terminal again, and copy paste this in to install the nvidia drivers.
```
sudo apt install nvidia-driver-550 nvidia-utils-550 nvidia-settings
```
2nd reboot
in terminal we create xorg.conf with this.
```
sudo nvidia-xconfig
```
then we need to enable drm at boot time. we can call this voodoo magic for now. see here if you know or want to know some voodoo. as for grub, it's your boot manager. we're going to add some options, and then update grub so it uses those options and your driver works properly.
```
sudo nano /etc/default/grub
```
modify this line and add these 2 options ```
nvidia-drm.modeset=1 nvidia_drm.fbdev=1
```
GRUB_CMDLINE_LINUX_DEFAULT="nvidia-drm.modeset=1 nvidia_drm.fbdev=1"
```
sudo update-initramfs -u
sudo update-grub
```
Nvidia-settings has a long running permissions issue.  If you start nvidia settings, and you can't save xorg.conf, even after you typed the password, fix with this. Since we're not starting nvidia settings yet, lets just go ahead type that in.
```
sudo chmod u+x /usr/share/screen-resolution-extra/nvidia-polkit
```
3rd reboot
if you check your log like this
```
sudo dmesg | grep drm
```
you should have no errors now.  if you do, something is not right.
if you
```
glxinfo | grep OpenGL
```
and if you can run nvidia settings from the menu, and save to xorg.conf, perfect.

you should see nvidia and not mesa listed on a few lines that show up. if you see mesa, somethings gone wrong.Double check everything, missing =.-_ capitalization punctuation. dmesg and journalctl to check your logs. Google any errors you see.Check on the discords, irc, reddit, medium, forums for help. Don't be afraid to ask for help if you can't figure it out.
The reason I put so many reboots, is just to check sanity. If it stops booting or spits out some sort of error, it's easier to solve, if you know what step you were at. But the only real reboot that's absolutely necessary is going to be the last one.
But there you go. If everything went as planned, you can run
glxgears
to see some moving gears. and verify.
STEAM EA APP EVERYTHING ELSE
Steam has a few native titles. but you'll have to enable proton compatibility in any windows only title right click properties>compatibility> enable.
Experimental works well for me. but you can always play around. Bottles is the other opp for windows games I recommend. You can find it on flatpak(something else you'll need going forward for things like discord as well)
You can also try Lutris. I have had success with it in the past, but it seems like a more complicated setup. So far, Bottles has done everything I've asked of it. Same with nearly all my steam titles(not the one in flatpak. especially if you want to use vr Use ```
sudo apt install steam-installer
```). EA app works fine through bottles. Quick install shortcuts already setup for most gaming apps in bottles as well.
VR is working as well. Various options available depending on your head set. i've got a guide soon for those with wmr headsets.
And the choice is always yours. This might not work for you. Maybe you want nouveau drivers. But as the title says, this is for gamers who want to game now, as opposed to when they finally figure out how to install their drivers and game.and nothing wrong with nouveau other then it needs more work if you want to game. I'm looking forward to better support from that direction, seeing as how nvidia hired the previous maintainer, and he release a set of about 150 commits. sooooo who knows. I'm kind of sus about it too, but so far progress anyway... maybe one day, we can have a fully open source driver, like in the days of old, when open source nvidia drivers worked how they were supposed to.

---

