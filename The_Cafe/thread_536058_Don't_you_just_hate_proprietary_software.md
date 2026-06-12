---
title: "Don't you just hate proprietary software?"
date: 2007-08-27
forum: The Cafe
---

### Post by charlieg on 2007-08-27
So I'm trying to install a custom kernel on Ubuntu.on a laptop with an nvidia graphics chipset.

Grab the nvidia drivers from [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html") and follow their instructions "sh nvidia_driver_download.run"

*"ERROR: You appear to be running an X server; please exit X before installing."*

WTF?  Why?  Why must I exit X?  What the hell is that about?  Crappy proprietry software.  That kind of error belongs in the Windows world.

---

### Post by LaRoza on 2007-08-27
> **charlieg said:**
> So I'm trying to install a custom kernel on Ubuntu.on a laptop with an nvidia graphics chipset.

Grab the nvidia drivers from [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html") and follow their instructions "sh nvidia_driver_download.run"

*"ERROR: You appear to be running an X server; please exit X before installing."*

WTF?  Why?  Why must I exit X?  What the hell is that about?  Crappy proprietry software.  That kind of error belongs in the Windows world.

Exit X by pressing "Ctrl Alt Backspace".

You have to exit X for a very logical reason, not anything to do with the quality of software.

---

### Post by Freddy on 2007-08-27
> **LaRoza said:**
> Exit X by pressing "Ctrl Alt Backspace".

You have to exit X for a very logical reason, not anything to do with the quality of software.
Won't "Ctrl Alt Backspace" merely restart the X server? I does for me atleast :).

---

### Post by MetalMusicAddict on 2007-08-27
Your issue has nothing to do with the title. Its user error.

---

### Post by bake7221 on 2007-08-27
I'm not 100% sure, but I think if you type sudo /etc/init.d/kdm stop (if you're using kde) or sudo /etc/init.d/gdm stop (if you're using gnome) and that'll stop X ... to restart just type the same thing but instead of stop type start ... :)

---

### Post by cmat on 2007-08-27
You should use the drivers in the repos. Exiting X is important if you do it manually. Just be grateful the nVidia even provided a video driver at the quality they have too.

---

### Post by happysmileman on 2007-08-27
I agree, the ones in the repos never worked for me, I need one of the legacy drivers and the repos just doesn't work for some reason... NVidia are very good at providing that installer, and at the login screen there should be an option to do a console login, do that and install it

---

### Post by Lord Illidan on 2007-08-27
While it's true that the exiting X server is not that good imho, for graphics drivers to be changed the X server must be restarted anyway, even if they are opensource..The ubuntu devs package it in a deb, which installs the kernel modules, but you still have to restart X to feel the change.

Interestingly, in Windows one didn't have to restart to feel the change, if you ignore the restart prompts, you feel the speed rightaway.

---

### Post by Nano Geek on 2007-08-27
**sudo /ect/init.d/gdm stop**

---

### Post by dasunst3r on 2007-08-27
You have to stop X in order to install the driver because you are changing a pretty foundational portion of the system.  Before you install this driver, be sure to have the packages *kernel-headers* and *build-essential* installed.  Just in case, run this in the terminal: *sudo apt-get install kernel-headers build-essential*.

After that's finished, log out, press *Ctrl+Alt+F1* to get to a terminal.  Log in and issue the command *sudo /etc/init.d/gdm stop*.  This will kill off X and allow you to install the driver.

As far as proprietary software goes, I only hate those that don't "play nicely with others," if you will.

---

### Post by cmat on 2007-08-27
> **Lord Illidan said:**
> 
Interestingly, in Windows one didn't have to restart to feel the change, if you ignore the restart prompts, you feel the speed rightaway.

Your screen goes black for a few seconds during the install. Mine stayed black even after I restarted.](*,)

---

### Post by toupeiro on 2007-08-27
Heaven forbid the GUI umbilical cord doesn't ruin linux one day...

---

### Post by Lord Illidan on 2007-08-27
> **cmat said:**
> Your screen goes black for a few seconds during the install. Mine stayed black even after I restarted.](*,)

Hehe..Yes, but mine didn't..:P Not that I am using Windows anymore, but chalk one up to the guy!

---

### Post by FuturePilot on 2007-08-27
> **Lord Illidan said:**
> 

Interestingly, in Windows one didn't have to restart to feel the change, if you ignore the restart prompts, you feel the speed rightaway.
Not me. My screen was stuck in the wrong res, even after I installed the driver. I had to restart.

But this issue has nothing to do with the fact that the drivers are proprietary.

---

### Post by Perfect Storm on 2007-08-27
> **dasunst3r said:**
> 
As far as proprietary software goes, I only hate those that don't "play nicely with others," if you will.

I second that.
Nvidia have played very nice towards Linux.

---

### Post by FuturePilot on 2007-08-27
> **Artificial Intelligence said:**
> I second that.
Nvidia have played very nice towards Linux.

I'll have to +1 that. Nvidia has been very nice to Linux and provide a pretty decent driver.

---

### Post by charlieg on 2007-08-27
I know that I'll have to restart X... hell, I'll have to restart everything is I'm running a **custom kernel** but why should I have to quit X just to compile the drivers?

I know my way around Linux (Gentoo for 3 years, Ubuntu for 3 years) and this is the first time I've hit this kind of "You must quit X to install this driver" message.  I shouldn't have to quit X to install the driver.  All it is doing is placing the driver in the appropriate place and then (possibly - don't know yet) modifying xorg.conf for me (which coincidentally I don't want it to do).

It's just ludicrous to assert I must quit X to compile a driver.  It's like saying "please go offline" to compile a network driver...

This is not user error.  It's not an error.  It's just a retarded message.

---

### Post by Andrewie on 2007-08-27
> **Lord Illidan said:**
> While it's true that the exiting X server is not that good imho, for graphics drivers to be changed the X server must be restarted anyway, even if they are opensource..The ubuntu devs package it in a deb, which installs the kernel modules, but you still have to restart X to feel the change.

Interestingly, in Windows one didn't have to restart to feel the change, if you ignore the restart prompts, you feel the speed rightaway.

actually that isn't true, I need to restart windows to see any change. This is with my Geforce Go 6100 (laptop), and a s3 video card on my desktop.

---

### Post by Andrewie on 2007-08-27
> **charlieg said:**
> I know that I'll have to restart X... hell, I'll have to restart everything is I'm running a **custom kernel** but why should I have to quit X just to compile the drivers?

I know my way around Linux (Gentoo for 3 years, Ubuntu for 3 years) and this is the first time I've hit this kind of "You must quit X to install this driver" message.  I shouldn't have to quit X to install the driver.  All it is doing is placing the driver in the appropriate place and then (possibly - don't know yet) modifying xorg.conf for me (which coincidentally I don't want it to do).

It's just ludicrous to assert I must quit X to compile a driver.  It's like saying "please go offline" to compile a network driver...

This is not user error.  It's not an error.  It's just a retarded message.

3 years of experience eh ;) The drivers move around a few files so if x is running they won't be able to do that. There was article about this a awhile ago. This files are being used by x when its running

---

### Post by charlieg on 2007-08-27
> **Andrewie said:**
> 3 years of experience eh ;) The drivers move around a few files so if x is running they won't be able to do that. There was article about this a awhile ago. This files are being used by x when its running
You have no clue what you are talking about.  Please stop making completely false assertions.  It confuses people who don't know better.

---

### Post by Anthem on 2007-08-27
No, I don't hate non-Free software.  I think that in the long term, open-source will eventually weed most other things out, but that's just because it will get better, faster.

---

### Post by PatrickMay16 on 2007-08-27
> **charlieg said:**
> So I'm trying to install a custom kernel on Ubuntu.on a laptop with an nvidia graphics chipset.

Grab the nvidia drivers from [here]("http://www.nvidia.com/object/linux_display_ia32_100.14.11.html") and follow their instructions "sh nvidia_driver_download.run"

*"ERROR: You appear to be running an X server; please exit X before installing."*

WTF?  Why?  Why must I exit X?  What the hell is that about?  Crappy proprietry software.  That kind of error belongs in the Windows world.
Get this: you need to exit X before installing a new X driver. How about that!

---

### Post by Lord Illidan on 2007-08-27
> **Andrewie said:**
> actually that isn't true, I need to restart windows to see any change. This is with my Geforce Go 6100 (laptop), and a s3 video card on my desktop.

Well, with a 6800 card here, I used to notice the CPU tearing up to 100% moving windows on the desktop..after installing the drivers, it went down a lot, and was much smoother..

---

### Post by kellemes on 2007-08-27
OP seems to be confusing compiling a package with running the automatic installer, this installer wants to compile **and** install.. and for this x needs be preferably stopped or at least restarted afterwards.

---

### Post by cybrid on 2007-08-27
In response to the thread's title. I'll say that the reason why I hate propietary software is because it has forced programmers to reinvent the wheel a lot of times; to loose entire projects  because the company behind them went down. I't has also locked down other companies and governments into their software . . .  That's why. Oviously, having to restart the X server to install a graphics driver isn't an issue to hate propietary software. It's like blaming a tire manufacturer for forcing you to remove the damaged tire before putting in the new one.

---

### Post by popch on 2007-08-27
> **cybrid said:**
> It's like blaming a tire manufacturer for forcing you to remove the damaged tire before putting in the new one.

Or blaming him for suggesting that you stop the car before changing tyres?

---

### Post by charlieg on 2007-08-27
I don't know what's happened to the Linux scene.  I have NEVER had to stop using my Linux desktop to install a driver before.  Even worse, people seem to accept this is ok?  Is the Linux desktop going backwards?

---

### Post by FuturePilot on 2007-08-27
> **charlieg said:**
> I don't know what's happened to the Linux scene.  I have NEVER had to stop using my Linux desktop to install a driver before.  Even worse, people seem to accept this is ok?  Is the Linux desktop going backwards?

AFAIK, ever since Nvidia released a driver for Linux you needed to shutdown X to install it.

---

### Post by PatrickMay16 on 2007-08-27
> **charlieg said:**
> I don't know what's happened to the Linux scene.  I have NEVER had to stop using my Linux desktop to install a driver before.  Even worse, people seem to accept this is ok?  Is the Linux desktop going backwards?

Is it really that much of a bother to save your work, and shut down X for a few minutes? If you want to complain about something, you should complain about a REAL problem; the state of bloat in the linux desktops of today. Ubuntu no longer comfortable with 512MB of RAM, and that is ridiculous.

---

### Post by LaRoza on 2007-08-27
> **PatrickMay16 said:**
>  you should complain about a REAL problem; the state of bloat in the linux desktops of today. Ubuntu no longer comfortable with 512MB of RAM, and that is ridiculous.

Try Xubuntu, Arch, Zenwalk, or others.

Not all OS's are mean to work on every computer, some require more resources. Actually, Feisty did work for me with less than 512 MB of RAM, but I wasn't trying to do anything memory intensive.

Linux is about choices, you can get a light OS that works with 64 MB of RAM (Zenwalk did), and on that uses 1 GB of RAM (anything with a DE like Beryl, or Compiz).

---

### Post by charlieg on 2007-08-27
> **FuturePilot said:**
> AFAIK, ever since Nvidia released a driver for Linux you needed to shutdown X to install it.
Not true - I used to compile kernels all the time with Gentoo and never had to quit X to install nvidia's proprietry driver.  It was handled differently, admittedly, but it shows it definitely can be done and there is no excuse for nvidia mandating you quit X to install this.

And people say it's expected?  So, did you quit X when you upgraded Breezey->Dapper->Feisty->Gutsy?  No, you quit when the upgrade was complete (well I did) when you wanted to run your upgraded software.  You did not need to quit everything first.

I continued my rant here:
[http://thefreedesktop.blogspot.com/2007/08/linux-desktop-going-backwards.html](http://thefreedesktop.blogspot.com/2007/08/linux-desktop-going-backwards.html)

---

### Post by sugarland2k on 2007-08-27
Or you could just use the Envy package for the Nvida video drivers.  A bit of a cheat and your mileage may vary but it worked great for me...

Good luck:)

---

### Post by PatrickMay16 on 2007-08-27
> **LaRoza said:**
> Linux is about choices, you can get a light OS that works with 64 MB of RAM (Zenwalk did), and on that uses 1 GB of RAM (anything with a DE like Beryl, or Compiz).

With Ubuntu Hoary, you could have a fully featured Gnome desktop and do image and audio editing and web browsing all at once just fine with 512MB RAM. Now with feisty, this is not the case any more. Looks like the choices are diminished.

---

### Post by LaRoza on 2007-08-27
> **PatrickMay16 said:**
> With Ubuntu Hoary, you could have a fully featured Gnome desktop and do image and audio editing and web browsing all at once just fine with 512MB RAM. Now with feisty, this is not the case any more. Looks like many of the choices aren't there any more.

I am assuming you want the latest release of a given distro, the latest Zenwalk release worked with 64 MB of RAM. 

If you just want a varient of Ubuntu, look at what Ubuntu's target is. It is not intended for older computers, although it does work on them, it is intended for newer computers.

Xubuntu is intended for the lower end machines you mention.

---

### Post by forrestcupp on 2007-08-27
> **charlieg said:**
> I don't know what's happened to the Linux scene.  I have NEVER had to stop using my Linux desktop to install a driver before.  Even worse, people seem to accept this is ok?  Is the Linux desktop going backwards?

Well, actually it's going forward and you're doing things backwards.  Instead of worrying about making 3rd party installers work better, the Ubuntu devs have been working on things like the Restricted Drivers Manager that automatically installs the nvidia proprietary drivers for you in a GUI without quitting X.  I'm pretty sure the drivers in the Gutsy repos are the latest.

You don't even need Envy or Automatix for this anymore.

---

### Post by igknighted on 2007-08-27
> **forrestcupp said:**
> Well, actually it's going forward and you're doing things backwards.  Instead of worrying about making 3rd party installers work better, the Ubuntu devs have been working on things like the Restricted Drivers Manager that automatically installs the nvidia proprietary drivers for you in a GUI without quitting X.  I'm pretty sure the drivers in the Gutsy repos are the latest.

You don't even need Envy or Automatix for this anymore.

None of this helps the OP as he is running a custom kernel, not one from the repos.  It would certainly be nice if RDM would compile the module rather than grab one from the repos (or if we used DKMS for these third party modules), but oh well.

As for the OPs issue... i agree 100% that the nvidia installer is terrible.  The ATI installer is a nice little GUI wizard that you click through and it does everything in X.  Obviously you need to restart X to enable the new driver, but much easier than nvidias.  None the less, if you are NVIDIA why do you want to make ease of use features for the type of users that use nvidia's installer?  Users who need easy GUI installers should install via the repos anyways.  Those who need the installer know their way around and aren't as bothered by the CLI.  Since I am going to restart X right afterword to ensure that the install was successful, why would I care if I used an ncurses GUI or an X server during the install.

---

### Post by Lord Illidan on 2007-08-27
> **igknighted said:**
> None of this helps the OP as he is running a custom kernel, not one from the repos.  It would certainly be nice if RDM would compile the module rather than grab one from the repos (or if we used DKMS for these third party modules), but oh well.

As for the OPs issue... i agree 100% that the nvidia installer is terrible.  The ATI installer is a nice little GUI wizard that you click through and it does everything in X.  Obviously you need to restart X to enable the new driver, but much easier than nvidias.  None the less, if you are NVIDIA why do you want to make ease of use features for the type of users that use nvidia's installer?  Users who need easy GUI installers should install via the repos anyways.  Those who need the installer know their way around and aren't as bothered by the CLI.  Since I am going to restart X right afterword to ensure that the install was successful, why would I care if I used an ncurses GUI or an X server during the install.

In this I tend to agree with you.

---

### Post by kellemes on 2007-08-27
> **LaRoza said:**
> Try Xubuntu, Arch, Zenwalk, or others.

Not all OS's are mean to work on every computer, some require more resources. Actually, Feisty did work for me with less than 512 MB of RAM, but I wasn't trying to do anything memory intensive.

Linux is about choices, you can get a light OS that works with 64 MB of RAM (Zenwalk did), and on that uses 1 GB of RAM (anything with a DE like Beryl, or Compiz).

Total agree here..
People, Ubuntu != GNU/Linux!!

---

### Post by 23meg on 2007-08-27
[QUOTE=PatrickMay16]With Ubuntu Hoary, you could have a fully featured Gnome desktop and do image and audio editing and web browsing all at once just fine with 512MB RAM. Now with feisty, this is not the case any more. Looks like the choices are diminished.[/QUOTE]

More like, looks like a regression has been introduced with your specific configuration. With 512MB of RAM, I've always been able to do those things at quite high system loads, and I'm still able to. It has nothing to do with choice, and certainly doesn't apply globally.

---

### Post by cybrid on 2007-08-27
> **PatrickMay16 said:**
> Is it really that much of a bother to save your work, and shut down X for a few minutes? If you want to complain about something, you should complain about a REAL problem; the state of bloat in the linux desktops of today. Ubuntu no longer comfortable with 512MB of RAM, and that is ridiculous.

My current linux box is an AMD XP 3200 (Barton) with 512 Mb DDR400  and works fine; I'd just wish to change my ati card for a nvidia. For normal tasks (web browsing, media playback, image editing...), the system works fine. In fact, just booted (no firefox or other app opened) it barely eats 150Mb of RAM. 

I think that amount of consumed memory to be very little for a modern os like ubuntu. Compare it to what Windows XP or Tiger eat; and let's not talk  about vista....

---

### Post by forrestcupp on 2007-08-27
> **igknighted said:**
> None of this helps the OP as he is running a custom kernel, not one from the repos.  It would certainly be nice if RDM would compile the module rather than grab one from the repos (or if we used DKMS for these third party modules), but oh well.
Good point.  I didn't think about the custom kernel.

> None the less, if you are NVIDIA why do you want to make ease of use features for the type of users that use nvidia's installer?  Users who need easy GUI installers should install via the repos anyways.  Those who need the installer know their way around and aren't as bothered by the CLI.  Since I am going to restart X right afterword to ensure that the install was successful, why would I care if I used an ncurses GUI or an X server during the install.
Yet another good point.  If you are compiling a custom kernel, you're not a novice user who needs mindless setups.  If you *do* need mindless setups, then you shouldn't be messing with compiling custom kernels to begin with; you should just use the built in mindless GUI utilities.

---

### Post by charlieg on 2007-08-27
> **forrestcupp said:**
> If you are compiling a custom kernel, you're not a novice user who needs mindless setups.  If you *do* need mindless setups, then you shouldn't be messing with compiling custom kernels to begin with; you should just use the built in mindless GUI utilities.
Where did I ask for a mindless GUI utility?  Please don't put words in my mouth.

I have no object to doing the installation in a terminal.

My sole objection is having to quit my desktop session just for this driver.  I should be able to do it from within my X session, then restart my laptop to get into my new environment.  The nvidia driver compiles itself, checks for X conflicts, copies itself into one or two locations (kernel module for a kernel which I was not running) and asks to modify xorg.conf (which I decline).  Any knowledgeable Unix/Linux user will tell you it has no business demanding I quit X just to perform these tasks.  It should work fine within a terminal in X and then I should reboot when I'm ready to get my new kernel / modules.

---

### Post by 23meg on 2007-08-27
You know that the driver doesn't consist of just a kernel module, which is open source by the way, don't you?

---

