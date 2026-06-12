---
title: "Ubuntu 12.04 login password error!"
date: 2015-04-15
forum: Virtualisation
---

### Post by jorge20 on 2015-04-15
Hi, i logged into Ubuntu forums just to ask for help to solve this problem!
I have a virtual machine in VirtualBox 4.3.20 with Yocto Project installed in it, WITHOUT any login password, it starts automathically. I been working in this virtual machine a few months without any problem. Suddenly yesterday i started the machine and there was a loggin screen with my username 'jorge' and a guest session.
If i enter the correct password there is a quick relaunch with a black screen and goes back to that login screen. 
This is what i can read on the screen:

coul not write bytes: broken pipe
*Starting NFS kernel daemon
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Starting the VirtualBox Guest Additions ..done
Starting VirtualBox Gest Additions service ..done
saned disabled; edit /etc/default/saned
*Check battery state ...[ok]

I've read a lot of people with similar problems but no one with this one. I've tried to:
[COLOR=#000000]create a new user
also doing
sudo rm .Xauthority
[/COLOR]also
sudo apt-get purge nvidia-current
[COLOR=#111111][FONT=Consolas]sudo apt-get install nvidia-current
also
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo apt-get -f install (without any error)
also
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo apt-get install --reinstall ubuntu-desktop
also
[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]su[/FONT][/COLOR][COLOR=#000000][FONT=dejavu sans mono]**do** mv -v /etc/X11/xorg.conf /etc/X11/xorg.conf.old[/FONT][/COLOR][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][COLOR=#111111] (another problem: [/COLOR][/FONT][COLOR=#000000][FONT=verdana]cannot stat 'etc/X11/xorg/conf' : no such file or directory)[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]also i've heard something about the contrats of the screen, but i can only select 'High Contrast' and nothing happens
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]
I don't want to erase the virtual machine and reinstall it again! (maybe it's the best solution)
Any help will be grateful! Thanks!

[/FONT][/COLOR]

---

### Post by howefield on 2015-04-15
Thread moved to the "*Virtualisation*" forum.

---

