---
title: "VirtualBox - Higher Resolution &amp; Full Screen"
date: 2007-12-07
forum: Virtualisation
---

### Post by poorbadger on 2007-12-07
So, I've got VMWare Server installed but I've read a bunch of favorable comments about VirtualBox so I thought I'd give it a shot since I don't have much invested in any particular Virtualizer.

You can see the details below but essentially I'm unable to run beyond 800x600 and fullscreen mode gives me that same 800x600 display with a big black border surrounding it.  I need to crank things up to proper full screen display for whatever I use.

Thanks!

***************************************

Host: Ubuntu 7.10 Desktop i386 on Thinkpad T61P w/ 4GB RAM (3GB visible)
Video Card: Nvidia 570M (256MB + 256MB stolen from System RAM)
Video Drivers: Nvidia Restricted from Package Manager
Resolution: 1920x1200

Virtual: VirtualBox 1.5.2 OSE
Memory: All the way up to 1024MB (Started at 512 then went 1024MB)
Video Memory: All the way up to 128MB (Started at 8, went to 32, then to 128MB )

Guest: Linux Mint 4.0 Desktop i386 - VirtualBox 1.5.2 Extensions Installed

Symptoms/Issues: Default resolution is 800x600 which looks good but is way too small for my use (had to move the dock toolbar vertical on the left side to even be able to access "Next" buttons during Mint installation).  

1024x768 is an option but after selecting through Preferences>Screen Resolution the virtual's display is garbled (multicolored bands).  This occurred under both the Nvidia restricted drivers and after disabling that driver, stepping back to the VESA drivers, and rebooting.

I've seen posts on how to get additional display resolution options under VBox but since I wasn't able to get anything intelligible out of 1024x768, I didn't see the point in going down that path.

Running @ 800x600 and flipping into fullscreen mode just gave me a huge black border with the same small 800x600 display in the center.

I intend to give Ubuntu a shot this weekend and maybe XP to see if I get any different results.

Anyone already gone through this and have any solutions or pointers?

---

### Post by ThrashJazzAssassin on 2007-12-07
You need to install the guest additions

---

### Post by poorbadger on 2007-12-07
The extensions are installed.

> **ThrashJazzAssassin said:**
> You need to install the guest additions

---

### Post by fjf on 2007-12-07
Maybe go to the configuration and give the graphic card more memory?.

---

### Post by poorbadger on 2007-12-07
I've given it the max system memory and video memory it'll take through the VBox Control Console.  Played around inside Mint w/ the video drivers and it doesn't seem to like that.

Default w/in Mint is...

Administration>Screen and Graphics Preferences
[Graphics Card]
Driver: vboxvideo
Video Memory: Automatic (greyed out - unable to change)

I'll try another OS over this weekend and report back.

> **fjf said:**
> Maybe go to the configuration and give the graphic card more memory?.

---

### Post by poorbadger on 2007-12-07
Allright, just installed XP w/ SP2 and that works fine.  There must be a difference in the "Linux 2.6" machine or the Linux Guest Additions.

BTW, "Seamless Mode" is disabled under the Linux 2.6 Guest Machine.  Fullscreen & AutoResize are available but they seem to work (or not work) differently than the XP machine.

I'm going to check out the VBox forums and see if I can turn anything up over there.

---

### Post by Ubeaut on 2008-06-09
There's a new, simple solution to this problem since VirtualBox 1.6.2.

Check out my post at:

[http://ubuntuforums.org/showthread.php?p=5145028#post5145028](http://ubuntuforums.org/showthread.php?p=5145028#post5145028)

.

---

