---
title: "Virtualbox will not go full screen in 12.04"
date: 2014-03-24
forum: Virtualisation
---

### Post by riverguy99 on 2014-03-24
There are many threads on this topic, but no fixes and all are old threads.  Perhaps there's some new info?  I just installed the latest version of VB and it works great. BUT I cannot get VB to go full screen in 12.04. I've read about installing Guest Additions, but there seems to be much confusion about that, too. Is there any recent info on this that suggests a fix?

Thanks for considering this!

---

### Post by QIII on 2014-03-24
What confusion are you finding about Guest Additions?  It has to be installed before you can run in full screen mode.

Start the VM.  Go to the Machine tab and select "Install Guest Additions".  Restart the VM.  I usually copy VBoxLinuxAdditions.run (I think that is what it is called, but I'm not at a Linux machine -- if you are running a different OS, use the appropriate Guest Additions file.) from the "virtual CD" to my /home in the guest and make it executable. Install the build-essential package (Ubuntu) or whatever package supplies similar functionality in other OSes. Also, if using Ubuntu, install linux-headers.  Then run VBoxLinuxAdditions.run.  Then reboot the VM.

I would also recommend installing the VBox Extension Pack on the host.

---

### Post by JKyleOKC on 2014-03-24
> **QIII said:**
> I would also recommend installing the VBox Extension Pack on the host.I believe that it's necessary to do this in order to install the Guest Additions packages. At any rate, I've always installed the extension pack first, immediately after installing VBox itself.

---

### Post by ajgreeny on 2014-03-24
> **JKyleOKC said:**
> I believe that it's necessary to do this in order to install the Guest Additions packages. At any rate, I've always installed the extension pack first, immediately after installing VBox itself.
+1

Same here!  And I think it is essential to install the guest additions to the VM in order to get fullscreen as well as the bi-directional clipboard and shared folders to work

And don't forget, you will probably need to reinstall the guest additions in the guest VM each time you have a kernel upgrade

---

### Post by JKyleOKC on 2014-03-24
> **ajgreeny said:**
> And don't forget, you will probably need to reinstall the guest additions in the guest VM each time you have a kernel upgradeThis will be true for the VMs themselves, but I've not needed to reinstall any of them after kernel upgrades for the host itself. Most of my VMs are Windows, though; very few are Linux.

---

### Post by ajgreeny on 2014-03-25
> **JKyleOKC said:**
> This will be true for the VMs themselves, but I've not needed to reinstall any of them after kernel upgrades for the host itself. Most of my VMs are Windows, though; very few are Linux.

Very true!  The kernel of the host does not matter at all, it's just the guests, and most of mine are linux, not Windows, as I test the new versions of Trusty that way.

My only contact with windows now is a VM of WinXP that I boot to update my satnav for about two minutes then shutdown again, and what a painful, slow operation it is running XP !

---

### Post by riverguy99 on 2014-03-25
> **QIII said:**
> What confusion are you finding about Guest Additions?  It has to be installed before you can run in full screen mode.

Start the VM.  Go to the Machine tab and select "Install Guest Additions".  Restart the VM.  I usually copy VBoxLinuxAdditions.run (I think that is what it is called, but I'm not at a Linux machine -- if you are running a different OS, use the appropriate Guest Additions file.) from the "virtual CD" to my /home in the guest and make it executable. Install the build-essential package (Ubuntu) or whatever package supplies similar functionality in other OSes. Also, if using Ubuntu, install linux-headers.  Then run VBoxLinuxAdditions.run.  Then reboot the VM.

I would also recommend installing the VBox Extension Pack on the host.


Thanks for the assistance! The confusion is from the posts talking about various bugs with getting XP to run full screen in VB on 12.04 in particular. 

But on to installing Guest Additions and your suggestion. When I open VB, on the resulting*** VirtualBox Manager*** screen, there is no "Machine" tab.  All thre is is this: ***New, Settings, Start, and Discard***.  I'm hoping I'm doing something wrong here (surprise?), because when I just looked into installing Guest Additions  from the Software Center I got a notice that ***I had to uninstall  VirtualBox first!***  I've already got XP all set up and running in VB.  Do  I REALLY have to start from scratch here?

---

### Post by QIII on 2014-03-25
The Machine tab will be on the window of the running VM.

You don't install the Guest Additions on the host.  You install it in the Guest.

---

### Post by riverguy99 on 2014-03-25
Thank you so much!  I can only dream of the day when I can do all this stuff on my own!  It installed and seems to work.  Full screen works now, but for some reason I can't run the install software for my HP2207 display. That will be my next fun project!

---

### Post by JKyleOKC on 2014-03-25
> **riverguy99 said:**
> Full screen works now, but for some reason I can't run the install software for my HP2207 display. That will be my next fun project!If the display is working properly, you don't need that install software. It's for Windows and won't run at all in Linux, but the Linux distributions usually take care of all the jobs that such software does for Windows.

---

### Post by QIII on 2014-03-25
Your VM doesn't know your particular display exists.  It goes through a hardware abstraction layer that uses  rudimentary graphics controller and passes it to the host.  Graphics performance on Virtualbox VMs is not good.

---

### Post by riverguy99 on 2014-03-27
Well, folks, I kinda back-pedaled on this one and redid the install to dual boot.  The only thing I need XP for anyway is to manage my Web sites, and I do that infrequently enough that it is not that much of a bother to reboot.  At least that way I have both displays at their best resolution.  

Since I have yet to find a driver that will let my HP 2207 display run at its design resolution, I still have to deal with looking at everything in HUGE mode when in Ubuntu, but I guess I'll figure it out some day.  This is such a common display it amazes me that nobody seems to be able to direct me to a driver that will allow it to work right.  

Thanks for all the suggestions, and if any body knows of a way to get an HP 2207 working right,, I'd love to hear about it.

---

### Post by JKyleOKC on 2014-03-27
> **riverguy99 said:**
> Since I have yet to find a driver that will let my HP 2207 display run at its design resolution, I still have to deal with looking at everything in HUGE mode when in Ubuntu, but I guess I'll figure it out some day.  This is such a common display it amazes me that nobody seems to be able to direct me to a driver that will allow it to work right.It's possible that your choice of video interfaces, which contain the video drivers, may be what's limiting you. If you're still configured for the VESA interface, that's a bare-bones "one size fits all" lowest-common-denominator one that "works" on almost all monitors, but doesn't work extremely well on any of them since it has no way to access their unique features.

The interface choice is usually based on the video card rather than on the monitor; it's been years since I had an HP monitor (CRT rather than flat panel) and at that time they weren't especially feature-rich. Modern monitors usually include a table known as EDID that tells the drivers what parameters they can accept, but many EDID packages fail to be interpreted properly by the driver software and when that happens, the usual result is extremely limited resolution (800x600 or 640x480 as maximum, for instance, and hardly ever better than 1024x768). Since many developers these days use much higher resolution to design their desktop windows, we often find that necessary buttons are off the screen!

Complicating matters is that several groups are trying to develop and popularize video systems to replace the aging X-Windows approach that has been standard since sometime in the 1980s, not to mention internal conflict between the original developers of X-Windows and the Xorg fork of that system.

Tell us what your video adapter is -- Nvidia, ATI, Intel, or something else -- including model number, and some of us will probably be able to walk you through diagnostic procedures to get more desirable results from your system!

---

