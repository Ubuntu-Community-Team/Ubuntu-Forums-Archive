---
title: "How to get KVM switch to work at boot time"
date: 2011-11-13
forum: Server Platforms
---

### Post by nosmadar on 2011-11-13
I'm running Ubuntu 10.4.3 server. I would like to use a KVM switch for the Keyboard/Monitor.  But the System will only boot with a direct connection to the Monitor and a spare keyboards. So I wind up unplugging the monitor from the KVM to boot the thing and then re-doing the wires so the Monitor/keyboard input is from the KVM. (So the KVM Does work once the system is up and running.)
I finally just figured out that since X windows is not installed, there's no 'xorg.conf' file to create or use.

Any thoughts?

---

### Post by HermanAB on 2011-11-13
Depends on the KVM.  Some are crappy like that and some are not.

Also, modern Xorg doesn't use xorg.conf anymore.  It figures everything out on the fly.  You can create an xorg.conf though - read up on it at the project web site.

---

### Post by volkswagner on 2011-11-13
What happens when the kvm is connected?  Do you get a keyboard BIOS error?

What type of kvm is it (usb or ps2).  

If you can't boot with no monitor/keyboard, perhaps there is a BIOS setting for(halt "no error") when booting for things such as no keyboard attached.

---

### Post by nosmadar on 2011-11-13
It's a USB KVM (TrendnetTK-409).  Yes, it's a BIOS error.  I will check the BIOS settings, it never occurred to me there was a way to disable that error.

---

### Post by nosmadar on 2011-11-13
Checked the BIOS, nothing about suppressing boot errors from peripherals.  If X windows is not present, will creating an Xorg.conf file actually work?

---

### Post by volkswagner on 2011-11-13
If you are getting bios error, xorg. will not help.

I have run into this... Oddly I have a 1U unbranded intel server with no options to supress keyboard errors.  If you have an extra ps2 keyboard lying around you may be able to connect that to get past the error.

Also there may  be a BIOS setting for usb options allowing usb keyboard/mouse.

I have an ancient HP iPaq mini desktop that I setup headless.  I had the annoying f1 error and no setting in BIOS.  My solution was a "NoF1" bios modifier.   This is not freeware and had some odd license agreement.  If your machine happens to be an HP, you may fulfill the requirement.

I even had searched for a pseudo ps2 dongle to fake the bios....  Not much luck there either.

You may also try an ps2 to usb adapter for your kvm connection.

---

### Post by nosmadar on 2011-11-13
So I retested the entire problem. To be honest, I'm not sure if it's a BIOS error or not.  If I reboot with the KVM attached, I hear two single beeps a few seconds apart (not the double beep I'd expect if the BIOS was unhappy) and eventually the monitor's status light goes from Green to orange (no activity) and no amount of pressing keys will bring it back.  Also, if I then disconnect the KVM and connect a usb keyboard and connect the monitor directly to the box, I get no activity, so I can't really tell what state the server software is in.  But, if I then reboot with the monitor/kbd/mouse directly connected, it comes up just find.  When I look at the syslog, I can see that Ubuntu recognizes the KVM eventually, but it just doesn't do it soon enough. (Or is that the Clue that it's a BIOS issue?).  This is an Intel motherboard for a i5 processor. (I can dig up the actual model if needed).  All I want it to is boot happily with the KVM attached. :-)

So...I guess it's worth trying the xorg.conf file? 

And I'll let this be the end of it. 
Thanks for your time!

---

### Post by volkswagner on 2011-11-13
Try booting the pc with no keyboard attached but have the monitor directly attached so you can see what is going on.  Take notice of the beeps.

Does the MOBO have PS2 ports?

---

### Post by nosmadar on 2011-11-14
So I rebooted it with just a directly connected monitor, no keyboard.  The BIOS issued a warning about the missing keyboard but it continued to boot and Lucid Server did start. 


Also, it looks like there is a single PS2 port. But 'weird' looking it's half green and half purple - so there's a combo mouse/keybd connection???

---

### Post by nosmadar on 2011-11-14
So the sequence is:
BIOS screen appears 
Function Key choices appear (F2 for BIOS ...)
Warning about missing Keyboard appears.
Single Beep
Screen changes from lo-res to normal (much-higher res) 
Normal Ubuntu start up messages appear.

---

### Post by volkswagner on 2011-11-14
Well since it passes the keyboard error, I think you have pinned down the issue is with video.

Perhaps you can try "nomodeset" boot option in Grub2.  I'm not sure what screen resolution it will leave you with, but it may get you past video connected to KVM.

To be methodical, you may want to have the monitor directly connected and run the keyboard through KVM.  If that works, then try the nomodeset approach.

Check out this[ link]("http://ubuntuforums.org/showthread.php?t=1613132") for the grub2 help.  Make sure you try it at the grub boot menu first to test it out then move on to the "How to permanently set kernel boot options on an installed OS" section. 

It also looks like that how to was for a GUI, so don't try gksudo.  :)

---

### Post by nosmadar on 2011-11-15
I've been all thru the GRUB2 manual and there's no reference to 'nomodeset'.  The closest things I found are: ‘GRUB_GFXPAYLOAD_LINUX’ which references a /boot/grub/video.lst file and 
"13.1.8 gfxmode

If this variable is set, it sets the resolution used on the ‘gfxterm’ graphical terminal. Note that you can only use modes which your graphics card supports via VESA BIOS Extensions (VBE), so for example native LCD panel resolutions may not be available. The default is ‘auto’, which selects a platform-specific default that should look reasonable.

The resolution may be specified as a sequence of one or more modes, separated by commas (‘,’) or semicolons (‘;’); each will be tried in turn until one is found. Each mode should be either ‘auto’, ‘widthxheight’, or ‘widthxheightxdepth’. "

Currently the /boot/grub/video.lst contains 
'vbe'
Is this what you were thinking of ?

[source]http://www.gnu.org/software/grub/manual/grub.html#GNU_002fLinux

---

### Post by Jonathan L on 2011-11-15
> Is this what you were thinking of ?


Hi Nosmadar

... monitoring this thread as (I think) I have the same problem with a rack I can't get to at the moment!

I believe Volkswagner was thinking of the descriptions here
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Kind regards
Jonathan

---

### Post by volkswagner on 2011-11-15
The link I provided is for a grub entry.  Grub can pass kernel boot options.  Kernel parameters are vast, and are not necessarily inherent to Grub so you may not find info in the Man pages.  

I have had to use the nomodeset many times booting live CD's and even after installing CLI systems.  It seems on or around Ubuntu Version 9 or 10, the Devs assumed everyone would have a monitor with resolutions greater than 1024x768.  To boot Ubuntu 10.04 live cd, with a 1024x768 monitor,  nomodeset is required.

I'm not saying this is certain to fix your issue, but it is a viable starting point.

---

### Post by nosmadar on 2011-11-15
Well, for the most part it worked.  Once I added the nomodeset option, the system will boot with a Monitor connection from the KVM.  Only bad news is that it defaults to 600 x 480 resolution.  
Would the best way to fix that be with another GRUB setting or would this be where the Xorg.conf file might be of use.

but Thanks! I think the worst part of this is over.  And this issue was a *pain* because my ssh connection from my laptop was also busted - got that fixed (with Forum Help) today as well.

---

### Post by volkswagner on 2011-11-15
Yes, after the nomodeset you can add vga=xxx

Check this page for proper code for resolution you want.

[https://help.ubuntu.com/community/BootText](https://help.ubuntu.com/community/BootText)

EDIT: Please realize the above link is for grub1, so the menu.lst and such don't apply.  It was just an easy link for the vga codes.

---

### Post by nosmadar on 2011-11-19
So it's not looking good. Looking a GRUB2 options from a couple of sources including the v1.99 doc page turned something like this:
Adding

set gfxmode=1920x1440     
set gfxpayload=keep       
insmod gfxterm            
insmod vbe                

to the GRUB config file. (or at least testing them in the GRUB boot menu - which is what I've been doing. 

So far it has not worked when used either above the boot command or at the end of the boot command. I've tried removing the 'nomodeset' that is now at the end of the boot command adding the 4 lines above - no joy. And then one could just try the two 'set' commands, I may do that next.

So now I'm trying to figure out if this is best addressed with the commands that manage the Kernal modules.  One thing that's odd is that 'vbe' and 'gfxterm' aren't recognized by the modinfo command.

So if they are really GRUB modules, do they stick around when the Kernel is loaded?  And how could the gfxmode env. variable be passed to the Kernel?

---

### Post by nosmadar on 2011-11-26
After fixing an issue with uvesa loading ( a v86d module was missing) this still does not work.  It all comes down to this:
If, either in Grub or as a KMS option, nomodeset is enabled, I get video but it's the lowest resolution. If 'modeset' is enabled, which should allow the Kernal video drivers to be used, the monitor acts like it can't find a valid connection. 

All of the remedies that I have found rely on X, but this is a server and I was trying to avoid installed X. I may take another look at this later in December, but can at least see well enough to shut it down quickly if needed and I've got other problems to solve.

---

### Post by sudodus on 2011-11-26
I have the KVM switch 'ATEN Petite CS-62A 2P PS/2' and it works to boot without 'looking at' the particular computer, but it defaults to a low resolution (maybe 1024x768 ) because it does not feel any monitor. This can be avoided by quickly switching to the booting computer until the graphics is selected and switching away to another computer again. I think it is possible set the final resolution in some x-configuration file so that you get good graphics without 'looking at' it. But I have not bothered to do that.

I think this problem of the final resolution is not related to your primary problem, that it refused to boot.

---

### Post by nosmadar on 2012-03-24
I agree.
I just wanted to add a closing note that I never did figure out the answer, I just gave up and dropped $$ on a small (19") monitor that can stay directly attached.  There are just too many other things that I need to focus on first.

But thanks to everyone who commented and tried to help.

---

