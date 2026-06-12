---
title: "Problem starting VirtualBox"
date: 2013-05-07
forum: Virtualisation
---

### Post by Deucalion29710 on 2013-05-07
Since I upgraded to 13.04 I cannot start my Windows 7 virtual box.  All I use this for is to program a remote.  Anyway the error messages in which I receive are as follows:

 Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

...and then...

 
Failed to open a session for the virtual machine Windows 7.
 The virtual machine 'Windows 7' has terminated unexpectedly during startup with exit code 1.

 
[TABLE]
 [TR]
 [TD] Result Code: 
[/TD]
 [TD] NS_ERROR_FAILURE (0x80004005)
[/TD]
[/TR]
 [TR]
 [TD] Component: 
[/TD]
 [TD] Machine
[/TD]
[/TR]
 [TR]
 [TD] Interface: 
[/TD]
 [TD] IMachine {22781af3-1c96-4126-9edf-67a020e0e858}
[/TD]
[/TR]
[/TABLE]




What I have tried so far:

Reinstalled Ubuntu DKMS via Synaptic and installed virtualbox-dkms and virtualbox-guest-dkms also via Synaptic.  I get the exact same error message as I did before I made any changes.  Any ideas?  Anyone?

---

### Post by MoebusNet on 2013-05-08
Have you tried opening Terminal and typing: ```
 sudo /etc/init.d/vboxdrv setup 
``` It wasn't clear whether or not you did.

---

### Post by Deucalion29710 on 2013-05-08
> **MoebusNet said:**
> Have you tried opening Terminal and typing: ```
 sudo /etc/init.d/vboxdrv setup 
``` It wasn't clear whether or not you did.

So I have to install the old kernel?  The output I get is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-18-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-18-generic'


Would kernel 3.5.4 work?  I have it in my little collection of kernels already downloaded.

---

### Post by MoebusNet on 2013-05-08
I think VBox is looking for kernel 3.5.0-18-generic according to the error message; whether or not VBox is compatible with newer kernels is beyond me. I suppose you could always run VBox on the older kernel when needed occasionally, then switch back to the newer kernel for other work. I'm not very adventurous when it comes to kernels, as you can see by the Ubuntu version I run (12.04). Perhaps someone else with more expertise will have some advice.

---

### Post by QIII on 2013-05-08
Moved to [B]Virtualisation
[/B]
My experience with VBox in 13.04 leads me to believe that it is not compatible with the kernel yet. While I was able to get installed, the tainted kernel crashed or panicked frequently.  I uninstalled VBox and blacklisted the module, but still had problems and ultimately just reinstalled Raring and didn't install VBox.  I have another machine running Win 7 Pro, so I just RDP into that one.

You might cruise the VBox forum to see what others have encountered.

---

### Post by ibjsb4 on 2013-05-08
The site install has the appearance of being solid.  Or just got lucky.

[http://ubuntuforums.org/showthread.php?t=2143224&p=12638864#post12638864](http://ubuntuforums.org/showthread.php?t=2143224&p=12638864#post12638864)

---

### Post by Deucalion29710 on 2013-05-08
I performed a purge and fresh install of the one from the Oracle site that says it's for 13.04.  Same error.  I installed the kernel image mentioned above and same error.  I'm beginning to regret doing the Raring Ringtail upgrade because it broke a lot of things.  Really I'm seeing no real advantage of having 13.04 over 12.10.

---

### Post by QIII on 2013-05-08
In reality, Raring didn't break it.  That's a third party application that Canonical has no control over.  If it has not been updated, it won't work.  It takes developers some time to update things.

But it is certainly frustrating and I don't blame you for being frustrated!

---

### Post by Deucalion29710 on 2013-05-08
Yeah I can understand that.  According to Oracle there is an appropriate version for RR, but I still can't seem to get it going for love or for money.  I just posted to their community forum.  Maybe somebody knows the magic action to get me back going.  If Logitech had official Linux support for the Harmony One then I wouldn't need a Windoze VM anyway.  I did have it going on 12.10 Gnome Remix, but when I did my upgrade it removed "obsolete packages" and I believe this is where the specific problem originates.  Anyway, thanks to everybody who tried to shed some insight on this issue.

---

### Post by MoebusNet on 2013-05-12
> **Deucalion29710 said:**
> ...If Logitech had official Linux support for the Harmony One then I wouldn't need a Windoze VM anyway.

Have you tried WINE in 13.04 to program your remote? Then you wouldn't need the Win VM :)

---

### Post by Deucalion29710 on 2013-05-12
> **MoebusNet said:**
> Have you tried WINE in 13.04 to program your remote? Then you wouldn't need the Win VM :)


OK now I have Wine and I installed Q4wine to open the program exe files easily.  I got my Harmony Remote control program to install, but it does not seem that I have USB support.  I am able to set the desired parameters for the remote but when I apply the changes it is stuck trying to communicate with the remote as if it is waiting for me to plug it in.  What am I missing to get USB support in Wine?

---

### Post by MoebusNet on 2013-05-13
I haven't been using WINE, just VBox. I thought WINE would have USB support out-of-the-box by now; apparently not. Here is a way WINE is working on USB support:

[http://wiki.winehq.org/USB](http://wiki.winehq.org/USB)

---

### Post by Deucalion29710 on 2013-05-13
Either one would be great if I could get my smart remote programmed properly.  I just spent thousands on a new home theater and can't program the remote for it because this "upgrade" broke my VirtualBox.  Now I'm trying to do this by using Wine and it has no USB support seemingly.  Oracle refuses to support their own product and the problem seems to be a known issue to many.  The USB problem with Wine seems to be known to many also but I can't seem to find a positive resolution.  I know that what I am seeking can be done in Ubuntu as I did it in version 12.10 Gnome Remix using VirtualBox.  I would really hate to ask a friend to borrow their Windows 7 machine especially being that I have sang many praises for Linux.  Let's try this...could anybody give me an official step by step on how to completely purge VirtualBox and all of it's components and install fresh from repository?  Or could somebody advise me of how to get USB support in Wine?

---

### Post by MoebusNet on 2013-05-13
This will work, but you won't like it. Dual-boot 12.10 for your WinVM just like your old setup, boot 13.04 the rest of the time. This should get you by until VBox catches up with Ubuntu.

---

### Post by Deucalion29710 on 2013-05-13
Well it never worked on Ubuntu.  That's why I needed a Win7 virtual machine to begin with.  If only it were that easy.  :)

---

### Post by Deucalion29710 on 2013-05-13
Wine is what's intriguing to me though.  I guess my question has now changed to "How do I get USB support in Wine?"  This way at least I can get rid of Virtual Box.

---

### Post by Deucalion29710 on 2013-05-13
OK new question, and back to VBox.  I got it installed again with a Working Win7.  Installed Guest Additions.  I can't see any of my USB devices in the settings.  I forget how I fixed that before.  USB is enabled but nothing is showing although I have 7 or 8 USB devices attacked to my desktop.  I also cannot remember how I accessed a file in my Ubuntu downloads folder using my Windows 7 VirtualBox.

---

### Post by Deucalion29710 on 2013-05-13
By the way, the fix for VirtualBox was an easy one:


sudo apt-get install  linux-headers-3.8.0-19-generic

---

### Post by Deucalion29710 on 2013-05-13
OK problem solved.  I am a ditz sometimes.  I forgot about the functions that appear in the non-scale mode to turn on USB devices.  Thanks to all who helped.  I still <3 my Ubuntu.

---

### Post by MoebusNet on 2013-05-13
Doh! Should have suggested installing header first; got sidetracked by newer kernel issue. Glad you got it working!

---

