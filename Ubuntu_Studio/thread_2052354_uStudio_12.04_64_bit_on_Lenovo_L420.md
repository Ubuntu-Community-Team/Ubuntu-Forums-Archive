---
title: "uStudio 12.04 64 bit on Lenovo L420"
date: 2012-09-03
forum: Ubuntu Studio
---

### Post by Ck.asdf on 2012-09-03
I recently installed Ubuntu Studio 12.04 64 bit on my laptop, installed all the updates, and started using it for basic stuff prior to using it for media production.  Several issues have presented themselves, and I don't know what to do to proceed.  Additional note: some of the problems mentioned below also happened when I tried to install regular Ubuntu 12.04 64bit.

Sometimes when starting up, the boot hangs on the Ubuntu loading screen, never gets to the login screen.

While using the computer, I have had several instances in which the computer completely freezes up.  No keyboard or mouse input, including trying to switch to a TTY session (ctrl shift F1-6).  I haven't tried it recently, but I think one time it locked up, I tried to connect to it via SSH, and it wouldn't respond.

I cannot put the computer to sleep.  Or more accurately, I can put it to sleep, but upon trying to wake it up, the speakers pop and the system restarts.

When I try to restart the system, sometimes it will hang then, too.  For instance, after I installed the updates, Ubuntu requested I restart the computer.  I had to hard reboot it, because it got stuck.

I very much miss Ubuntu/Linux, and I suspect Lenovo is to blame for a lot of my problems in the past year or so, but until I can get things stable, I can't use it. :(

---

### Post by smartboyhw on 2012-09-03
> **Ck.asdf said:**
> I recently installed Ubuntu Studio 12.04 64 bit on my laptop, installed all the updates, and started using it for basic stuff prior to using it for media production.  Several issues have presented themselves, and I don't know what to do to proceed.  Additional note: some of the problems mentioned below also happened when I tried to install regular Ubuntu 12.04 64bit.

Sometimes when starting up, the boot hangs on the Ubuntu loading screen, never gets to the login screen.

While using the computer, I have had several instances in which the computer completely freezes up.  No keyboard or mouse input, including trying to switch to a TTY session (ctrl shift F1-6).  I haven't tried it recently, but I think one time it locked up, I tried to connect to it via SSH, and it wouldn't respond.

I cannot put the computer to sleep.  Or more accurately, I can put it to sleep, but upon trying to wake it up, the speakers pop and the system restarts.

When I try to restart the system, sometimes it will hang then, too.  For instance, after I installed the updates, Ubuntu requested I restart the computer.  I had to hard reboot it, because it got stuck.

I very much miss Ubuntu/Linux, and I suspect Lenovo is to blame for a lot of my problems in the past year or so, but until I can get things stable, I can't use it. :(

OK, wait, you can't just blame Lenovo for that.

I think maybe your installation is corrupted. Or maybe even your installation media IS corrupted. Don't forget to verify the MD5 checksum of the ISO image. Use unetbootin to burn the image to your USB. Then install it again and see if it still has these problems.

Also, you DID use the 12.04.1 images didn't you? Don't use the old 12.04 one.

If then there is still the problem maybe it then WILL be Lenovo to blame for the hardware.

Regards,
Howard Chan
Ubuntu Studio Team Member (Testing, documentation and support)

---

### Post by Ck.asdf on 2012-09-03
I appreciate the prompt response.

I checked the MD5 checksum of the ISO against the checksum listed online, and used LinuxLive to copy the image to my flash drive.

The problems happened with Ubuntu 12.04 standard as well as with Ubuntu Studio, and obviously they share a lot of the same core system stuff, so having many of the same issues seems to point to issues with Ubuntu 12.04 [all variants] correctly interfacing with my hardware.

As to which image I used, not quite sure, I grabbed it from the main site.  Reviewing my downloads folder, it appears neither the standard or studio versions include ".1" in the version.
By installing all the updates, should that take care of it, or should I re-install by using the updated iso?

---

### Post by jejeman on 2012-09-03
> **Ck.asdf said:**
> The problems happened with Ubuntu 12.04 standard as well as with Ubuntu Studio, and obviously they share a lot of the same core system stuffUbuntu studio is ubuntu. There are no differences on system level, only on software selection (including the DE).> **Ck.asdf said:**
> By installing all the updates, should that take care of it, I agree on that.

---

### Post by smartboyhw on 2012-09-03
> **jejeman said:**
> Ubuntu studio is ubuntu. There are no differences on system level, only on software selection (including the DE).I agree on that.
You're wrong there. Ubuntu Studio uses a different kernel from Ubuntu Desktop. Ubuntu Desktop uses a generic kernel, whilst Ubuntu Studio uses a lowlatency kernel to enable rt.

---

### Post by Ck.asdf on 2012-09-03
My purpose in mentioning both installs is:
*I used two different ISO images
*I installed Ubuntu twice
To have a corrupt ISO and/or install twice in a row seems unlikely.

By the way, for what it's worth, Ubuntu standard was installed with online access so it could grab updates, while uStudio was installed offline, with updates obtained after installation.

Smartboyhw, after downloading all updates available, would my install be considered 12.04.1, or do I need to reinstall with a newly obtained ISO?

---

### Post by smartboyhw on 2012-09-03
> **Ck.asdf said:**
> My purpose in mentioning both installs is:
*I used two different ISO images
*I installed Ubuntu twice
To have a corrupt ISO and/or install twice in a row seems unlikely.

By the way, for what it's worth, Ubuntu standard was installed with online access so it could grab updates, while uStudio was installed offline, with updates obtained after installation.

Smartboyhw, after downloading all updates available, would my install be considered 12.04.1, or do I need to reinstall with a newly obtained ISO?
NO. If you have the updates installed it is 12.04.1.

---

### Post by Ck.asdf on 2012-09-03
So what can I do from here to attempt to resolve these issues?  When the system seizes up like that, would there be any log files or something I could provide to give some kind of clue what's happening?

Thanks for all the help, by the way!

---

### Post by Windreaver on 2012-09-10
I have also experienced this same issue. Total system freeze up. This issue is not just in UStudio 64, but anything Ubuntu driven I have installed including Ubuntu 12.04 unity 64(even tried switching to gnome) and the new Linux Mint Maya 64. They all freeze within a 5 to 15 minute session. I have checked iso for errors, I have re-installed and re-downloaded the iso direct from either Ubuntu/UStudio/LMint sites. I've lost count how many attempts and I have been checking frequently for solutions. Very discouraging when I use UStudio for design work and have to use the release from two years ago since last years UStudio team split up gong show release was non existent.

**Equipment details...**
[COLOR="DarkRed"]MSI GT70 Intel Core i7 laptop 
Nvidia Geforce GTX 670M 3GBDDR5[/COLOR]

---

### Post by HomeOnThePlains on 2012-10-05
Ck.asdf, do you have any updates on this? Did you ever get things to work?

I'm just shooting in the dark bcuz I'm no guru here, but did you try a different distro? Maybe Debian or Fedora? Get any diff results? Did you try to disable the power manager?

---

### Post by Ck.asdf on 2012-10-05
Hello, I've not progressed any further, and it's been a while since I've booted to Linux. Tonight after work I'll do that and see where it stands.

To answer your question, I've used Linux Mint 12 on it before, and if I remember correctly, it ran pretty well, but I didn't like how it did a few things, so I came back to Ubuntu.

How would I go about disabling the power manager, and how would that affect things?

---

### Post by HomeOnThePlains on 2012-10-05
I mention the Power Manager because of this:> While using the computer, I have had several instances in which the computer completely freezes up.  No keyboard or mouse input, including trying to switch to a TTY session (ctrl shift F1-6).  I haven't tried it recently, but I think one time it locked up, I tried to connect to it via SSH, and it wouldn't respond.

I cannot put the computer to sleep.  Or more accurately, I can put it to sleep, but upon trying to wake it up, the speakers pop and the system restarts.

From what I've read/heard, laptops and the Power Manager have had issues. To see what the PM does go to:

AppMenu > Settings > Settings Manager > Power Manager 

If you want to disable it, from where you are in Settings go to the Applications Autostart tab and uncheck the box for Power Manager. Then to try it without rebooting at first, go to the Session tab and quit the PM there.

Because you're on a laptop, I'm guessing you'll want to be aware of your battery level, and that's what the PM will display for you, so obviously you'll lose that function while you try this.

Again, not being guru enlightened or anything, that's just what I would try ;)

---

