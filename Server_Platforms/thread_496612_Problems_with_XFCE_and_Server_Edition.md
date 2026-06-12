---
title: "Problems with XFCE and Server Edition"
date: 2007-07-09
forum: Server Platforms
---

### Post by eglasg on 2007-07-09
I am having trouble getting any sort of GUI to work with Ubuntu Server Edition 7.04. It seems that each time I install a graphical environment (I read that a gui can be added by installing xubuntu-desktop or kubuntu-desktop, etc) the resolution never gets set right.The x server config in the installer does ask me which display resolutions I want to have supported and I always check 1280x1024 which is the resolution I would like to use. However, upon a restart the resolution used is 640x480, the lowest possible. I have tried to change the resolution from the display settings area, but in XFCE, the only available resolution is "default" and in KDE, the slider is stuck at 640x480. It may be the hardware I have, but I am not too sure.

I understand that it is not advisable to have a graphical environment on a server, but I don't think I could get much done without it. I don't use Linux on a daily basis and I am only using it now because I would like to experiment with hosting my own website or other server applications in a very secure environment. Not to mention the fact that it is free.

Thanks in advance for any and all help!

EDIT: I suppose I should mention that I did try a clean Kubuntu install from a cd and the screen resolution is set at 1280x1024 like it should be. I could create a LAMP installations myself from that system, but I like the pre-configured style of the Server Edition and I hope that I could stick with that, but it may not be possible.

---

### Post by koenn on 2007-07-09
If you want a server, don't install the (x)ubuntu-desktop package. It pulls in all the applications associated with Ubuntu Desktop (openoffice, firefox, games, ... the works)
What you want is to install just the packages you need for a graphical environment : 
-  xserver-xorg   (or 'xorg' in newer releases ?)
-  x-window-system-core
-  xterm

That's enough to display GUI's, but it's nicer if you add a window manager. I like fluxbox myself, but if you want to go with 'main' packages, there's xfwm4 (xubuntu's window manager)

In this setup, you'd start the gui environment from a console, with 'startx'
To boot straight into a GUI environment, you need a display manager, eg xdm or gdm.

If you want even more GUI stuff, run
```
apt-cache search xfce*
```. It will show a load of packages associated with the xfce / xfwm gui envronment. 


Then, for your resolution problem, usually xorg tries to use the best possible resulution/color depth, so if it falls back to 600x480, there's a problem. 

For starters, you could configure xorg to use 600x480, if it works, try 800x600, etc. Keep the color depts also conservative (try 800x600 8 or 16 colors before you try 800x600 24/32 colors). And so on.

the command to reconfigure xorg is ```
dpkg-reconfigure xserver-xorg
```.
It also lets you select  which Xserver to use - this is related to what video hardware you have.  You'd either pick the one that matches yopur hardware (it should be autodetected, but who knows ...), or you could try VESA

The alternative is to edit /etc/X11/xorg.conf, which can be tricky.

---

### Post by eglasg on 2007-07-09
Reconfiguring xorg is what did it. I guess it autoconfigured something wrong and wouldn't let me set the right resolution.

I decided to go with IceWM because it comes with an XP look-alike skin which is familiar to me. That appears to be working fine, but I was wondering how I might get some icons on the desktop like there was when I installed the xubuntu desktop (one for the hard drive, cd, home folder, etc.). There doesn't even seem to be a way to browse through the filesystem without going through terminal.

---

### Post by koenn on 2007-07-09
you sound way out of your depth.
to browse the file system, you need a file browser. xubuntu uses thunar, I assume you can just install it from the repo's.

---

### Post by eglasg on 2007-07-09
> **koenn said:**
> you sound way out of your depth.

Yes, this is probably true. I have had very little experience with linux. I should probably start with a desktop install to get the basics, but I am not interested in using linux as a desktop platform. I only need it because it makes a great server platform (security and it runs on the older hardware machine that I want to put to some good use) and I don't have to pay a ton just to get an OS.

 I know it is probably quite frustrating answering such novice questions and I really appreciate your help.

---

### Post by koenn on 2007-07-10
we've all been there. 
What I did to get some hands-on experience with non-GUI linux, was try to come up with small projects that I could try at home, always opted for text-based installed as opposed to GUI installer, then figure out what text files to edit to get where I wanted. 

[http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/intro.htm) was such a (bit more advanced) exercise, involving dns, dhcp, samba, apache, mysql, and so on. Have a look, see what I mean.

---

### Post by RedSquirrel on 2007-07-10
> **eglasg said:**
> Reconfiguring xorg is what did it. I guess it autoconfigured something wrong and wouldn't let me set the right resolution.

I decided to go with IceWM because it comes with an XP look-alike skin which is familiar to me. That appears to be working fine, but I was wondering how I might get some icons on the desktop like there was when I installed the xubuntu desktop (one for the hard drive, cd, home folder, etc.). There doesn't even seem to be a way to browse through the filesystem without going through terminal.

So your resolution is OK now?

For a file manager: If you still have Xubuntu installed, then you can use Thunar in IceWM if you like. It should be in the menu.

If there's nothing interesting in your menu, do this:

```
sudo apt-get install menu
sudo update-menus

```That should setup your "Programs" entry in your IceWM menu.

You can also run Thunar from the command line with:

```
thunar &
```pcmanfm is another file manager that people seem to like.

I don't use desktop icons at all, so I'm not sure what IceWM users like to use for that.

I think you should be able to get to know the server edition and linux, but it will take time and patience. You will probably get stuck once in a while, but there are lots of answers on ubuntuforums. I would advise you to do a search when you have a question and then if you can't find an answer, don't hesitate to ask.

Good luck. :)


@koenn: Yes, on the newer editions (edgy and feisty) it is called xorg. ;)

```
sudo apt-get install xorg xterm
```

---

### Post by eglasg on 2007-07-10
[QUOTE=koenn][http://users.telenet.be/mydotcom/how...xsbs/intro.htm](http://users.telenet.be/mydotcom/how...xsbs/intro.htm) was such a (bit more advanced) exercise, involving dns, dhcp, samba, apache, mysql, and so on. Have a look, see what I mean.[/QUOTE]
Thanks for that link, I'll check it out soon.

[QUOTE=RedSquirrel]So your resolution is OK now?[/QUOTE]
Yes, I managed to do something in the configuration script that fixed whatever problem there was.


I had wiped the install that had the xubuntu package on it, since it was going to be hard to make sure everything was removed that I didn't want. I found this page in the wiki that had suggestions for people doing installs on machines with lower memory(or those wanting to use less memory) and it had suggestions for file managers and I just picked one at random (it happened to be XFE). It's different to encounter the modular environment where you can choose a window manager and file manager separately.

I have installed webmin because in my searches for adding a gui to server edition, people suggested to just use that and not worry about a locally installed gui system. Although, that may not be the best way to learn linux, I hope that it'll help me learn a lot more about servers.

From what I have seen, these forums and the people on them are very helpful. The linux community never ceases to amaze me.

---

