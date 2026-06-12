---
title: "Server -or- Desktop choice from GRUB?"
date: 2008-11-29
forum: Server Platforms
---

### Post by engbyrew on 2008-11-29
Hi all.
I have a specific configuration I want, but cannot figure exactly how to make it happen. I am new to GRUB programming and multiple versions on the same machine.

What I want:
To be able, upon boot, to choose the server-only mode (i.e. LAMP + FTP) without a GUI for good resource utilization, OR one of the other desktops like KDE, Gnome, etc. This way I can use the GUI for setting up and programming my site, and put it up in server only mode.

Notes:
-I have already loaded Kubuntu ( I can delete if needed).
-I tried loading Ubuntu Server from the CD (with Kubuntu already loaded), but it wanted me to partition, I would like to use the same linux base in both modes so I do not have excess.
-I am guessing about using GRUB to do this, anything that would give me the same results would be fine.

I hope someone can help and I would appreciate it very much!

Thanks folks!
-Rich-

---

### Post by Philio on 2008-11-29
Just to clarify - There are 2 separate editions of Ubuntu which install different features.

Desktop edition gives you a GUI.
Server edition is just the basics (or what you want for a headless server).

Ideally if your running a server you want to use the server edition, although you can install the GUI on top if you really want a GUI it's easier to install the desktop edition.

What your suggesting regarding grub and booting in text or gui mode would involve passing the kernel the runlevel to enter on boot.

You can do this by editing /boot/grub/menu.lst and copy/pasting the existing lines for the current kernel, something like this below (note this is from server edition and desktop edition differs):

```
title           Ubuntu 8.10, kernel 2.6.27-9-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-server root=UUID=cda77d03-0c7a-4bce-8795-237ed0caf160 ro quiet splash
initrd          /boot/initrd.img-2.6.27-9-server

```

At the end of the kernel line you can enter a number to specify a runlevel, basically you would end up with something like this:

```
title           Ubuntu 8.10, GUI
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-server root=UUID=cda77d03-0c7a-4bce-8795-237ed0caf160 ro quiet splash 2
initrd          /boot/initrd.img-2.6.27-9-server

title           Ubuntu 8.10, CLI
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-9-server root=UUID=cda77d03-0c7a-4bce-8795-237ed0caf160 ro quiet splash 3
initrd          /boot/initrd.img-2.6.27-9-server

```

I'm not sure which runlevel is which on Ubuntu, I know RH distros use 3 and 5 for text/gui but not sure if it's the same on Ubuntu - you would need to find this out.

Also there is a bit of a downside to this method, you would need to manually edit your menu.lst every time there is a kernel update.

---

### Post by amac777 on 2008-11-29
I think the solution by Philio will work with small addition. After you have edited the  grub menu.lst file to include the runlevel 3 sections as Philio said, also run this command to modify run level 3 to not load the graphical interface (GDM):

```
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K30gdm
```

That command changes the "S" (start) to a "K" (kill) for GDM, which will prevent GDM from loading in run level 3.

---

### Post by Philio on 2008-11-29
> **amac777 said:**
> I think the solution by Philio will work with small addition. After you have edited the  grub menu.lst file to include the runlevel 3 sections as Philio said, also run this command to modify run level 3 to not load the graphical interface (GDM):

```
sudo mv /etc/rc3.d/S30gdm /etc/rc3.d/K30gdm
```

That command changes the "S" (start) to a "K" (kill) for GDM, which will prevent GDM from loading in run level 3.

I had wondered if Ubuntu had specific run levels intended for text, gui etc.

I just remember that RH (long time ago - prior to it becoming Fedora) used to use 3 and 5 specifically.

I'm on my desktop PC now and can see from looking at the contents of /etc/rc*.d RL2 is the default, so easier to keep this for GUI, then any of 3/4/5 would be fine for CLI with the above modification or using the update-rc.d equivalent.

---

### Post by amac777 on 2008-11-29
Oops. It does not work. I tried doing what is specified above on my system because it would be useful to have a command line only entry in grub. But no matter what I specified as the runlevel on the grub line, Ubuntu always uses runlevel 2.....

So I did some searches and found it's a bug:

Ubuntu uses runlevel 2 no matter what you specify.

Couple of links..
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=661357](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=661357)
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/85014)

So... Back to the drawing board.

---

### Post by Philio on 2008-11-29
Ooops double post!

---

### Post by Philio on 2008-11-29
Not necessarily!

Modifying /etc/event.d/rc-default would definitively work!

I am guessing the version there shown is not working, from all the responses, however it wouldn't be too difficult to make it work.

---

### Post by engbyrew on 2008-11-29
Thanks Philio and amac777.
I didn't think that with my first step into grub editing I would step on a bug.
Anyway, I'm still reading the links and bug posts.

One reason I am interested in loading the server version instead of just taking my KDE install and changing the run level is that the server version installs all the items I need and configures them with proper security, etc. rather than me trying to figure it all out.

Would it be easier to start over and load the server version, then add the GUI's I want and simply ALWAYS boot into server mode, then load the GUI I want from a command line?

If so, how would I start the GUI from a command line?

Thanks again,
-Rich-

---

### Post by amac777 on 2008-11-30
From my understanding, you can install the server packages on the desktop version, or you can install the desktop packages on the server version. In both cases, the result will be the same. So I don't think there is any point to reinstalling your system using the other version - unless your current installation is broken in some way that you can't fix or you want to start over with a clean setup.

What kind of a server are you trying to setup?

About your idea of stopping the GUI and then starting it only when you want from the command line, that should work. Do this to not load GDM on startup:

```
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K30gdm
```

To run the GUI from the command line, you should be able to just login in text mode and then use "startx" to start up X with the current settings for that user. Or you can start GDM so you can login using that and select your session like normal:

```
sudo /etc/init.d/gdm start
```

By the way, if you want to go back to the graphical login, you can use this command to make sure GDM loads automatically on startup:

```
sudo mv /etc/rc2.d/K30gdm /etc/rc2.d/S30gdm
```

---

### Post by Philio on 2008-11-30
Yer I agree it would probably be easier just to disable gdm at startup and use startx.

---

### Post by engbyrew on 2008-11-30
Thanks for the tips,
I'll try them today and close the thread if I get it going.
I guess I don't mind it starting in CLI automatically since it will be in this state 99% of the time.
I will be using this as a test web server and an FTP server for bouncing files when I assist others in the Windows world using LogMeIn Free, which does NOT have file transfer capability.
I do a lot of remote help for Windows. 
See... Micro$oft is good for something, it pays my bills!
Thanks again...
-Rich-

---

### Post by Primefalcon on 2009-01-20
the command startx will start the graphical user interface

---

