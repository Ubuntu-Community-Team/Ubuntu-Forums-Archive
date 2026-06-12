---
title: "[HowTo] Lightweight X11 Desktop Environment - LXDE is back!"
date: 2008-02-25
forum: The Cafe
---

### Post by PCMan on 2008-02-25
[COLOR="Red"]Warning: This article is already out of date.
Please use the new apt repo to install LXDE instead.
[http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde](http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde)
[/COLOR]

Lightweight X11 Desktop Environment, as known as LXDE, is a project launched in 2006 aimed to provide a modern lightweight desktop environment for X11.
It tries hard to get maximal usability from minimal resource usage, and provide a usable desktop for low end machines.

The development was paused for one year, but glad to say, we are back again, with a lot of improvements.

Homepage:  [http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)

The official homepage sucks, but the software rocks!

Here is a screenshot:
[LIST]
[*]The lightweight yet feature-rich file manager with tabs on the left side is PCManFM.
[*]The image viewer on the right side is GPicView, which features lightening fast startup and simple user interface.
[*]The desktop panel at the bottom of the screen is LXPanel. It provide a good-looking and feature-rich panel. The menu is automatically generated from *.desktop files installed by every packages. The configuration can be done through preference dialog, and there is no need to edit the config file.
[*]The window manager used here is OpenBox, with hotkeys and menu well-configured.  Alt+F2 for "Run" dialog. Ctrl+Esc for the start menu.
[/LIST]

[IMG]http://pcman.sayya.org/lxde/lxde.png[/IMG]



[LIST]
[*]The logout screen is provided by the session manager - LXSession.
[*]It's completely standard compliant. It can handle autostart spec of freedesktop.org. It can also remember the applications used  in the previous session, and restart them on the next login.
[/LIST]

[IMG]http://pcman.sayya.org/lxde/logout.png[/IMG]


The main difference between this project and others is, all the components are "desktop-independent" and loosely-coupled. They don't depend on each other, and the dependencies of the whole environment is kept minimal.  If you only like the panel or the file manager, just get it installed, and it won't ask you to install the whole desktop environment.

Currently it's still under heavy development, and there is still much to do.  So there are no deb packages for the latest version.
The installation guide on the official website is already out of date, so here is an automated script.

[http://lxde.svn.sourceforge.net/viewvc/*checkout*/lxde/trunk/install-lxde-ubuntu.sh](http://lxde.svn.sourceforge.net/viewvc/*checkout*/lxde/trunk/install-lxde-ubuntu.sh)

To run the script, put it in a newly created directory, then:
```

> chmod +x install-lxde-ubuntu.sh
> sudo ./install-lxde-ubuntu.sh

```
The script will help you install the whole desktop from source code, and get all settings done. It grabs the latest source code directly from our svn repository, and install all the packages require to compile LXDE via apt-get for you. (NOTICE: Most of these packages are only required when building the programs from source code but not required to run the programs) Then, the script will compile all of the source code automatically, then get them installed (root access via sudo is required).

After the automatic installation, you can login to LXDE from gdm via selecting LXDE in the session menu.

Have fun!

---

### Post by D-EJ915 on 2008-02-25
good to see work continuing on this!

---

### Post by Vitamin-Carrot on 2008-02-25
wow,

I like the linux community.

There is just a whole bunch of cool stuff happening all the time.
If I wasn’t careful I would suffer sensory overload and fall into a coma

---

### Post by Dr Small on 2008-02-25
I might try this, but what files / directories do I delete if I don't like it?

---

### Post by K.Mandla on 2008-02-25
Fantastic! I'm going to give this a test run later and maybe use it on my OLPC machine. Good to see LXDE getting updates! :D

---

### Post by regomodo on 2008-02-25
aha! lxde isn't orphaned after all. I tried it a while back and liked quite a lot about it.

---

### Post by zmjjmz on 2008-02-25
So your using Openbox instead of IceWM now?
Oh well, it looks great.
With this new upgrade, did the specs change at all? 
I think it would be great to get this on an old computer...

---

### Post by PCMan on 2008-02-26
> **zmjjmz said:**
> So your using Openbox instead of IceWM now?
Oh well, it looks great.
With this new upgrade, did the specs change at all? 
I think it would be great to get this on an old computer...

Yes, we are using OpenBox now.
Although it uses a little bit more resources than icewm, it provides something important to a modern desktop that icewm lacks.

1. The most noticeable one is startup notification.
When you open a file in file manager, you'll see some visual feedback (the busy mouse cursor) from OpenBox.
This one is really needed for desktop environment.
In the few window managers supporting this (metacity, kwin, openbox), OpenBox is the only one that's lightweight enough.

2. OpenBox is configurable via GUI, using ObConf.

3. It by far looks much nicer and stylish, but the resource usage is still reasonable.

4. It doesn't have too much unnecessary dependencies.

Of course, you can still use icewm if you like, but I'll provide configuration for OpenBox by default.

---

### Post by edredon on 2008-02-26
trouble: i don't see lxde in gdm after installing AND restarting gdm in ubuntu gutsy gibbon.

i see gnome/openbox, kde/openbox and openbox itself as new items :S

---

### Post by Scarath on 2008-02-26
Hi, nice to see new lightweight environment, although looking at the website I dont know why I would choose this over Openbox. However if everything is much easier to set up that Openbox I guess it would be good for some.

---

### Post by K.Mandla on 2008-02-26
> **Scarath said:**
> Hi, nice to see new lightweight environment, although looking at the website I dont know why I would choose this over Openbox. However if everything is much easier to set up that Openbox I guess it would be good for some.
I think maybe you misunderstand; I believe the scripted installation uses Openbox with these packages added as a lightweight desktop environment. If I'm correct, the window manager is still Openbox, but the panel, session manager, etc., are LXDE's.

I'm sure PCMan can set us straight if we're both off course. :)

---

### Post by PCMan on 2008-02-26
> **K.Mandla said:**
> I think maybe you misunderstand; I believe the scripted installation uses Openbox with these packages added as a lightweight desktop environment. If I'm correct, the window manager is still Openbox, but the panel, session manager, etc., are LXDE's.

I'm sure PCMan can set us straight if we're both off course. :)

OpenBox is a window manager, and LXDE is a set of programs integrated to form a basic lightweight desktop environment.
Besides, LXSession handles session management. It respect the autostart specs of freedesktop.org, and restart the apps you used in previous session automatically. OpenBox is handy, but it doesn't have a panel. For hackers, a window manager such as twm is enough. However, for the general population, this is not the case. LXDE tries to provide these basic components of modern desktop environment, and tries to keep it small end efficient at the same time. For Machines like Asus EeePC and OLPC, I think LXDE is very suitable. Some tweaks might be needed, though.  I cannot test it on OLPC since I don't have one, but I'll get it tested on EeePC recently. There are already packages of PCManFM & GPicView provided by xepc.org project for the official version Xandros Linux in EeePC.

---

### Post by johnraff on 2008-02-26
Download the script, open it in a text editor and have a look at what it does - nothing alarming I think, though  quite a lot of developer-type stuff (eg subversion) gets put in for a "lightweight" installation.

It does indeed install the latest version of Openbox and Obconf.

Anyway you can always copy/paste it into a terminal and do it bit by bit if you want. (for example, I already have the latest Openbox and don't really need to uninstall and reinstall it...)

---

### Post by PCMan on 2008-02-26
> **johnraff said:**
> __________________
1999 Fujitsu desktop (450MHz P3, 128MB RAM)
Interesting....
I would like to know if LXDE work on your box.

BTW, the first release of PCManFM was developed on a 
laptop with P III 600 MHz + 256 MB SDRAM.

Later, I got PCManFM 0.3.2 series tested on my first computer, Pentium II 266 MHz + 192 MB RAM, and it's generally OK. Moreover, I installed LXPanel, PCManFM, and IceWM on a box with VIA 400 MHz CPU + 256 MB RAM, and it worked, too.

However, I don't have a chance to test the latest LXDE on these old machines, and my Celeron 800 MHz machine was finally broken in 2006. I want to get them tested on OLPC and EeePC most, though.

---

### Post by edredon on 2008-02-26
> **edredon said:**
> trouble: i don't see lxde in gdm after installing AND restarting gdm in ubuntu gutsy gibbon.

i see gnome/openbox, kde/openbox and openbox itself as new items :S

nothing?

---

### Post by mperry on 2008-02-26
Hello and thanks for this announcement.  I had not heard of this project before and I have an older Sharp Actius MM10 Transmeta powered laptop which suffers a bit with modern environments.  Seems even xubuntu taxes it more but openbox runs very nicely.  I would like something inbetween that offered a set of applications, a bit less on the resource side, etc.  The laptop has 256mb of memory and a 15g drive.  Wifi, sound, everything now works.   Your web page shows that a system with 256mb of memory should run reasonably well.

I'm gonna give it a try tonite at home and see what turns up.  Thanks for maintaining the project and hopefully offering me a reasonable alternative.  The ultraportable sharp is not supposed to be like my T43 with gnome or kde on it.  Supposed to be a lean mean email and chat, lightweight web monster.

---

### Post by johnraff on 2008-02-26
> **PCMan said:**
> Interesting....
I would like to know if LXDE work on your box.
I'm using Xubuntu feisty most of the time and it's quite usable, if not exactly speedy... Looks nice, and has lots of convenient features.

However I am interested in something lighter and a bit faster if I can do it without losing too much convenience or appearance. (of course *too much* is a purely personal judgement) 

I've got a laptop with 260MHz Celeron and 195MB RAM that I'm using a 1.5GB partition on to try out different setups before changing this "main" box too much. Right now that's got openbox, pcmanfm (older version) and lxpanel already installed, but not thoroughly tested yet. I'm kind of stuck for desktop icons as I see you don't recommend using that feature of pcmanfm at the moment.

I've also got an installation of lxde - the older version with icewm - on this 450MHz / 128MB box. It works, but, again, when pcmanfm was drawing the desktop it seemed to be constantly using the cpu. I thought it might be the fault of icewm, and I didn't like the look of icewm so much anyway, and was thinking of trying lxde with openbox instead...

So... yes I will give the new version of lxde a try on this machine.
It looks like what I was aiming for anyway :)
I'll uninstall all the old lxde stuff and start again from the installation script ( even though it will install a lot of extra stuff I might not really need after that ).

Thanks for all your work on this lightweight software! 
(gpicview is my default image viewer- it's really fast, though I'd like to see the basic info like size in px, size in KB somewhere handy...)

---

### Post by K.Mandla on 2008-02-27
> **PCMan said:**
> OpenBox is a window manager, and LXDE is a set of programs integrated to form a basic lightweight desktop environment.
Besides, LXSession handles session management. It respect the autostart specs of freedesktop.org, and restart the apps you used in previous session automatically. OpenBox is handy, but it doesn't have a panel. For hackers, a window manager such as twm is enough. However, for the general population, this is not the case. LXDE tries to provide these basic components of modern desktop environment, and tries to keep it small end efficient at the same time. For Machines like Asus EeePC and OLPC, I think LXDE is very suitable. Some tweaks might be needed, though.  I cannot test it on OLPC since I don't have one, but I'll get it tested on EeePC recently. There are already packages of PCManFM & GPicView provided by xepc.org project for the official version Xandros Linux in EeePC.
That's what I had thought. Thanks.

I put lxpanel, GPicView and PCManFM on my OLPC and they all worked fine, of course. The only problem -- and this isn't the fault of any of your software -- is that GTK2 applications always seem very slow on that machine. 

Personally I think that's the fault of an undersized processor/video card combination working on a (technically) enormous screen (1200x900, which I never had when I was working with Pentium II-era hardware ... I never got 1280x1024 until I was in P3-type machines). 

So yes, lxpanel and PCManFM and GPicView work great under Arch on that machine, but the entire system is slow with GTK2 applications, so I probably won't keep them. I just get better performance from things like the Xfe suite, Xpaint, dillo-i18n and so forth.

I do plan on using them on other, faster machines though. :) Thanks a bunch for writing them!

---

### Post by kerry_s on 2008-02-27
> **edredon said:**
> nothing?

pick openbox, the install is a custom openbox.

---

### Post by PCMan on 2008-02-27
Here is an exciting screenshot.

This is the preview of our completely new desktop icons in development.
At this time, It's not usable, but it will, in the next major release of PCManFM.
Although looks good, this one is really too basic now.
However, it's not a bad idea to show our users a promising roadmap.

Cheers!

[IMG]http://pcman.sayya.org/lxde/desktop_icons.png[/IMG]

---

### Post by Gen2ly on 2008-02-27
nice to see all's back in action.  I like PCman and wondered if it would be developed again.  it seems as if it can be configured to be a pretty lightweight file manager.  I hope it sees further development.

---

### Post by johnraff on 2008-02-28
> **PCMan said:**
> This is the preview of our completely new desktop icons in development.
At this time, It's not usable, but it will, in the next major release of PCManFM.Great news! (I can't live without icons somehow... :( )
Any idea when the new version will be out?

---

### Post by edredon on 2008-02-28
> **kerry_s said:**
> pick openbox, the install is a custom openbox.

picking openbox leads to an openbox session, not customized at all. i guess lxde should be an option in gdm... but it's not...

---

### Post by ajkiwi88 on 2008-02-29
hey
how do i install it? do i just run the code from the first post in the terminal? as im confused
many thanks
andy

---

### Post by smartboyathome on 2008-02-29
Download the file he linked to in the first post, save it in your home folder, then run the code he posted in a terminal to install it.

---

### Post by johnraff on 2008-03-01
Don't forget to make a new directory first, and move the script you downloaded into it before starting.

Don't forget also that you'll be running the script *as root* so make sure you're comfortable with what it's going to do before hitting that enter key!

---

### Post by ajkiwi88 on 2008-03-01
hey done that an only got open box in the gdm menu??
tried opening openbox and it only runs a standard openbox session

---

### Post by webaake on 2008-04-01
I've recently installed Openbox 3.4.6.1 and lxpanel latest source from tar. This seems to work great on my 400 Mhz PPC.

However, after studying the the install script mentioned at the beginning of this thread I concluded that it is not usable on Apple PPC since it uses i386-deb packages for some applications.

So, in order to completely install LXDE what should I download and compile assuming all other dependencies and libraries are in place already? (lxpanel and openbox compiled just fine)

And, how do I replace the old gnome/xfce system apps at startup with these new LXDE apps, since I cannot use the install script mentioned above?

I have no problems using the terminal and pico/nano and I can find my way around the root file structure. Openbox and lxpanel are in the start up session already.

Thx for any help!

---

### Post by Fragadelic on 2008-04-01
Thanks for starting things up again especially since I just came across the project.

Looks like the website has been updated and there are current deb files there now.  Install was very easy on a stripped down xubuntu install.

I made a small home server using lxde as the desktop for administration through webmin via iceape.

Very nice little DE and has become my favourite small DE/WM combo.

---

### Post by Biased turkey on 2008-04-02
> **edredon said:**
> trouble: i don't see lxde in gdm after installing AND restarting gdm in ubuntu gutsy gibbon.

i see gnome/openbox, kde/openbox and openbox itself as new items :S

I have the same problem, I downloaded and run the LXDE install script without any problem, but  could someone please tell me how to start LXDE ?

Jacques

---

### Post by PCMan on 2008-04-02
> **Biased turkey said:**
> I downloaded and installed lxde, but could someone please tell me how to start lxde ? ( I don't see it in the windows manager list when I login )

Jacques

Please use this apt repo instead.
[http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde](http://ubuntuforums.org/showthread.php?t=738958&highlight=lxde)

The info in this thread is already out-of-date.

---

### Post by webaake on 2008-04-02
The repo is only for i386 platforms, is it not?

---

### Post by chris4585 on 2008-05-01
```
Errors were encountered while processing:
 /var/cache/apt/archives/openbox_3.4.6.1-0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can i fix this?

sorry to waste space i believe i fixed it.

---

### Post by thahir1986 on 2010-07-03
now i'm using lxde for my old pc....it's really awesome

---

