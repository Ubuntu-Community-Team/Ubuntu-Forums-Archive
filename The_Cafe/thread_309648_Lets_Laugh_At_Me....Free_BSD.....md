---
title: "Lets Laugh At Me....Free BSD...."
date: 2006-11-29
forum: The Cafe
---

### Post by spockrock on 2006-11-29
Ok I thought I would try to expand my horizons, and learn FreeBSD, so before I trash my windows partition on my secondary box...not that I would of really cared...but a friend was like do it in vmware, and then once you get it installed, and I figured hey good idea, don't wanna trash my linux partition by mistake.

so I throw open vmware, create a virtual machine.....tell it to boot off the iso image.  ok I boot, the installer is kinda like the ubuntu alternate installer(thats what I use anyways so I feel comfortable), ok, great I think I got everything figured out.  So its installing and I scratch my head saying, hey, ummm what window manager/desktop environment is it installing I didn't really pick.  So I finish the install, and it turns out, I have just terminal, ok so i log in, startx and I get twm.  wow...sufficed to say, ok greeeeaaaatttt.....so I message my buddy, hey, what am I doing wrong, how would I install fluxbox on this, I am stuck in twm, and its infuriating....sorry but twm, ugh.... man..... so he tells me how to kinda use ports, but now its giving, me an error about not connecting...GRR...so I say eff it, lets just re-install, this time just default, no more tinkering, first lets get a proper install before I tinker....so, well, so I default install, it boots, I get terimal again, so I log in, and then startx and bah, twm again.

LOL on me, so I am brushing up on FreeBSD, not gonna give up on it yet, but seriously am I just spoiled installing Ubuntu (I guess any linux distro and windows for that fact) first time installs work fine.  Or does anyone else feel the FreeBSD installer is incredibly silly.

---

### Post by Beamerboy on 2006-11-29
> **spockrock said:**
> Ok I thought I would try to expand my horizons, and learn FreeBSD, so before I trash my windows partition on my secondary box...not that I would of really cared...but a friend was like do it in vmware, and then once you get it installed, and I figured hey good idea, don't wanna trash my linux partition by mistake.

so I throw open vmware, create a virtual machine.....tell it to boot off the iso image.  ok I boot, the installer is kinda like the ubuntu alternate installer(thats what I use anyways so I feel comfortable), ok, great I think I got everything figured out.  So its installing and I scratch my head saying, hey, ummm what window manager/desktop environment is it installing I didn't really pick.  So I finish the install, and it turns out, I have just terminal, ok so i log in, startx and I get twm.  wow...sufficed to say, ok greeeeaaaatttt.....so I message my buddy, hey, what am I doing wrong, how would I install fluxbox on this, I am stuck in twm, and its infuriating....sorry but twm, ugh.... man..... so he tells me how to kinda use ports, but now its giving, me an error about not connecting...GRR...so I say eff it, lets just re-install, this time just default, no more tinkering, first lets get a proper install before I tinker....so, well, so I default install, it boots, I get terimal again, so I log in, and then startx and bah, twm again.

LOL on me, so I am brushing up on FreeBSD, not gonna give up on it yet, but seriously am I just spoiled installing Ubuntu (I guess any linux distro and windows for that fact) first time installs work fine.  Or does anyone else feel the FreeBSD installer is incredibly silly.
You should try out Desktop FreeBSD.  It is more inline with desktop linux distros like Ubuntu etc. and includes xorg during install.

The version you installed is pretty much designed for servers not desktops.

Paladine

---

### Post by calx on 2006-11-29
I did almost the same thing, installed FreeBSD on an old laptop, realised all I had was a wireless card for network access that of course worked immediately in Ubuntu. My BSD career lasted about 30 mins :rolleyes:

---

### Post by spockrock on 2006-11-29
> **Beamerboy said:**
> You should try out Desktop FreeBSD.  It is more inline with desktop linux distros like Ubuntu etc. and includes xorg during install.

The version you installed is pretty much designed for servers not desktops.

Paladine

[http://www.freebsd.org/where.html](http://www.freebsd.org/where.html)

went there and grabbed the i386 version, how do I know what is the desktop version?? Got both disks....but still I am frazzled by the installer, like i can partition, and mount the home folder to that partition.... I just cant figure out how to get a decent window manager on it...

---

### Post by Beamerboy on 2006-11-29
> **spockrock said:**
> [http://www.freebsd.org/where.html](http://www.freebsd.org/where.html)

went there and grabbed the i386 version, how do I know what is the desktop version?? Got both disks....but still I am frazzled by the installer, like i can partition, and mount the home folder to that partition.... I just cant figure out how to get a decent window manager on it...
[http://www.pcbsd.org/](http://www.pcbsd.org/)

---

### Post by kvonb on 2006-11-29
PCBSD is the very best for desktop BSD.

[www.pcbsd.org](www.pcbsd.org)

It is very polished and has a simple package management system, I ran this as my main server for a few months as pppoe was very simple to setup as opposed to earlier Linux distros (mainly because I cut my teeth on FreeBSD not Linux).  I only replaced it with Ubuntu because I wanted to keep all my systems the same, and of course Ubu is just WAY better ;).

FreeBSD alone can be a bit much, and a steep learning curve.

Linux (and more specifically Ubuntu), is the best for general everyday desktop use though as it offers a lot more packages and mainly support for hardware.

If I had to drop Ubuntu for any reason I would go straight back to PCBSD.

Regards, KEv :)

---

### Post by vayu on 2006-11-29
My first OSS OS was Ubuntu.  I had always wanted to use FreeBSD.  After about 6 months of Ubuntu, I tried FreeBSD.  There are many things I like about it much more than Ubuntu.  You install what you want and only what you want. No bloat. It's fast, it's got many areas that seem more logical to me.  Compiling the kernel is a breeze.  

However, you need to have a lot of time!

While it will run almost anything there are many things you can't get without knowing a lot more than I do.  I did get it setup to 95% of what I had with Ubuntu, but it took a long time.  When Compiz came out I ended up going back to Ubuntu full time. (I always kept it on my laptop)

I love FreeBSD, I still have it on one of my partitions.  I booted into it today as a matter of fact.  I wanted to get some videos I stored on there.  Turns out I'll have to recompile my kernel to get mkisofs to burn a dvd.  I know exactly what to do, but I just don't have the time or desire to do that right now.  Ubuntu works so much more effortlessly.  It's kind of like the difference between having a Toyota and an MG.  One you drive and drive, the other you tinker and tinker.

I'll go back at some point (when I have more time!).

---

### Post by Beamerboy on 2006-11-29
I have run a freebsd production level server for 4 years now, it is sat in a dc in San Diego.  I upgraded some hardware in it this summer andhad to shut it down to do so, which was a shame since it had 504 days uptime.

However, I am in the process of migrating all the services from the freebsd server to my Edgy (Server Edition) server here in the UK now that I have enough upstream bandwidth to run the services I need.

Freebsd is rock solid, but it really is designed to be implimented as a robust server OS.  PCBSD, although I have never usedit, is supposed to be pretty good according to friends I know who run it.

Paladine

---

### Post by spockrock on 2006-11-29
> **Beamerboy said:**
> [http://www.pcbsd.org/](http://www.pcbsd.org/)

thankyou......

> **kvonb said:**
> PCBSD is the very best for desktop BSD.

[www.pcbsd.org](www.pcbsd.org)

It is very polished and has a simple package management system, I ran this as my main server for a few months as pppoe was very simple to setup as opposed to earlier Linux distros (mainly because I cut my teeth on FreeBSD not Linux).  I only replaced it with Ubuntu because I wanted to keep all my systems the same, and of course Ubu is just WAY better ;).

FreeBSD alone can be a bit much, and a steep learning curve.

Linux (and more specifically Ubuntu), is the best for general everyday desktop use though as it offers a lot more packages and mainly support for hardware.

If I had to drop Ubuntu for any reason I would go straight back to PCBSD.

Regards, KEv :)

thanks for the information....pcbsd it is...

---

### Post by mips on 2006-11-30
> **vayu said:**
>   There are many things I like about it much more than Ubuntu.  You install what you want and only what you want. No bloat. It's fast, it's got many areas that seem more logical to me.   


Just for the record, everything you described there can be done with ubuntu or most distros for that matter. In Ubuntu all you need is the alternate install cd or the server install cd. 

Dunno about compiling the kernel though.

---

### Post by slimdog360 on 2006-11-30
Similar to what I did the first time I installed. Now a days I just grab kde off the second install cd and install everything off the mark.

---

### Post by xhaan on 2006-11-30
> **spockrock said:**
> Ok I thought I would try to expand my horizons, and learn FreeBSD, so before I trash my windows partition on my secondary box...not that I would of really cared...but a friend was like do it in vmware, and then once you get it installed, and I figured hey good idea, don't wanna trash my linux partition by mistake.

so I throw open vmware, create a virtual machine.....tell it to boot off the iso image.  ok I boot, the installer is kinda like the ubuntu alternate installer(thats what I use anyways so I feel comfortable), ok, great I think I got everything figured out.  So its installing and I scratch my head saying, hey, ummm what window manager/desktop environment is it installing I didn't really pick.  So I finish the install, and it turns out, I have just terminal, ok so i log in, startx and I get twm.  wow...sufficed to say, ok greeeeaaaatttt.....so I message my buddy, hey, what am I doing wrong, how would I install fluxbox on this, I am stuck in twm, and its infuriating....sorry but twm, ugh.... man..... so he tells me how to kinda use ports, but now its giving, me an error about not connecting...GRR...so I say eff it, lets just re-install, this time just default, no more tinkering, first lets get a proper install before I tinker....so, well, so I default install, it boots, I get terimal again, so I log in, and then startx and bah, twm again.

LOL on me, so I am brushing up on FreeBSD, not gonna give up on it yet, but seriously am I just spoiled installing Ubuntu (I guess any linux distro and windows for that fact) first time installs work fine.  Or does anyone else feel the FreeBSD installer is incredibly silly.

Yeah. You have to select what packages you install. You also have to choose whether you install from discs or a net install, and also have to set up your connection to do a net install. There's several WM's to choose from, plus Gnome, KDE and XFCE.

Also keep in mind that BSD is not Linux. BSD can run Linux apps with a compatibility layer, but it isn't perfect.

---

### Post by ade234uk on 2006-11-30
FreeBSD is great for servers. I think its one of the best for reliability.

---

### Post by spockrock on 2006-11-30
> **xhaan said:**
> Yeah. You have to select what packages you install. You also have to choose whether you install from discs or a net install, and also have to set up your connection to do a net install. There's several WM's to choose from, plus Gnome, KDE and XFCE.

Also keep in mind that BSD is not Linux. BSD can run Linux apps with a compatibility layer, but it isn't perfect.

right but I never see where it asks me to install the window manager...I get the packages list, pick gnome, but I never get it.....

---

### Post by rharris on 2006-12-01
From the FreeBSD handbook............

5.7.1.2 Installing GNOME

The easiest way to install GNOME is through the “Desktop Configuration” menu during the FreeBSD installation process as described in Section 2.9.13 of Chapter 2. It can also be easily installed from a package or the ports collection:

To install the GNOME package from the network, simply type:

# pkg_add -r gnome2

To build GNOME from source, use the ports tree:

# cd /usr/ports/x11/gnome2
# make install clean

Once GNOME is installed, the X server must be told to start GNOME instead of a default window manager.

The easiest way to start GNOME is with GDM, the GNOME Display Manager. GDM, which is installed as a part of the GNOME desktop (but is disabled by default), can be enabled by adding gdm_enable="YES" to /etc/rc.conf. Once you have rebooted, GNOME will start automatically once you log in -- no further configuration is necessary.

GNOME may also be started from the command-line by properly configuring a file named .xinitrc. If a custom .xinitrc is already in place, simply replace the line that starts the current window manager with one that starts /usr/X11R6/bin/gnome-session instead. If nothing special has been done to the configuration file, then it is enough simply to type:

% echo "/usr/X11R6/bin/gnome-session" > ~/.xinitrc

Next, type startx, and the GNOME desktop environment will be started.

    Note: If an older display manager, like XDM, is being used, this will not work. Instead, create an executable .xsession file with the same command in it. To do this, edit the file and replace the existing window manager command with /usr/X11R6/bin/gnome-session:

% echo "#!/bin/sh" > ~/.xsession
% echo "/usr/X11R6/bin/gnome-session" >> ~/.xsession
% chmod +x ~/.xsession

Yet another option is to configure the display manager to allow choosing the window manager at login time; the section on KDE details explains how to do this for kdm, the display manager of KDE.


Cheers...........

Rob

---

### Post by dca on 2006-12-01
You know, BSD and Linux are BOTH great for servers...  You have to take a step back and look at it practically.  If you're installing on a laptop or desktop for personal or quasi-business use look at what works the best.  I don't think anyone would argue that on the desktop/laptop Ubuntu seems to do it all...  Ubuntu boots on my laptop listed below (default install of 6.06) in less than fifty seconds to login prompt.  Fedora Core 6 on same laptop w/ all the non-essential or server services stopped still clocked in at 1min 44 secs, and openSuSE 10.1....  Well I'm still waiting, don't get started on how long YaST2 takes to initialize, oooh look my cakes done baking...
 
Heck, I've never seen a Linux distro, one CD work out of the box so well...  
 
 
Then again, if you just want to learn.  I guess there's fun in finding the nuances and differences between Linux & BSD...

---

