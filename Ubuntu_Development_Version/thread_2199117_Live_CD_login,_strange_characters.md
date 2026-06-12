---
title: "Live CD login, strange characters"
date: 2014-01-12
forum: Ubuntu Development Version
---

### Post by The Cog on 2014-01-12
I thought I would give a live CD of Xubuntu 14.04 a try. dd the daily .iso to a usb stick and boot that. Two problems immediately:

Boots OK but when I click to try xubuntu, I get a login screen with a username and password prompt. I tried a blank username, then "ubuntu", then blank again. At this point the GUI seemed to crash although I was able to Ctrl-Alt-F1 then Ctrl-Alt-Del to reboot. However, after rebooting I couldn't boot from the stick any more - it just beeped and jumped to hard disk boot. Unplugging the stick completely from the PC seemed to clear that problem.

I was able to log in using username "xubuntu" and got a working desktop - of sorts. Most of the menus seem to be in a strange characterset. I used the defaults when logging in, which seem to be US english. I attach a screenshot showing the strange characters.

I wondered if anyone else has seen this.

EDIT
Well, that's helpful - not. The forum has shrunk the image so it's not really readable any more. I'll try to find somewhere public to post it. In the meantime, am attaching a cropped portion - hopefully that won't get ruined.
Yup, forum mangled that one too.

---

### Post by Elfy on 2014-01-12
Hi The Cog, it's a known bug, we've not got it pushed through yet.

[https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1259525](https://bugs.launchpad.net/ubuntu-manual-tests/+bug/1259525)

Reboot, if brave enough ... 

Set language to English - top right Flag icon

Username is xubuntu

Set session to Xubuntu - top right Gear Icon

then login.

---

### Post by The Cog on 2014-01-12
Ah yes. Thanks, Elfy. I hadn't even noticed the language selection widget top right before. Doh! 

Looks good. When I get time, I'll install that and try to give it some real use. I'm sure I'll be pestering here again.

---

### Post by The Cog on 2014-01-12
And another thanks to Elfy: That wrong lightdm.conf greeter-session and user-session caught me as well. 
For some reason, not until I installed the nvidia-331-updates driver, but then even after removing the driver (with aptitude) I couldn't get a GUI until I edited lightdm.conf.

Now it's looking quite sweet.

---

### Post by Elfy on 2014-01-12
Don't know if you get affected by this type of thing with nouveau - but we think we have that cracked as well

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1267742](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/1267742)

[IMG]https://launchpadlibrarian.net/162094730/CAM00034.jpg[/IMG]

---

### Post by Elfy on 2014-01-12
> **The Cog said:**
> ... Now it's looking quite sweet.

I've got 2 permanent installs here - one with nouveau and one with nvidia - both are looking better slowly.

Though atm I've still got the unity-greeter in use, must remember to change back now it's proved.

The transparent panel's return and the GTK3 indicator panel are a nice return. Still got issues with the indicator-applications not working properly.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=249431&d=1389558760[/IMG]

---

### Post by The Cog on 2014-01-12
The login prompt background? Oh yes, that got me going. At one stage, it showed a collage of my desktop wallpaper, a copy of a web browser session I had been using earlier and a couple of other bits a can't remember. And that was immediately after a reboot! I nearly had to change my underwear. They must have been left lying around in the video card memory. You could argue that showing these post-logout and post-reboot screenshots on the login prompt background represents something of a security problem, so it's good that it's being addressed. The screenshot you post looks like a power-on from cold, just noise rather than old images. I guess it's just waiting for a login prompt background to be chosen and configured. 

P.S. Glad to see the sound control is working this time round. Out of interest, has it been rewritten for gtk3, or has gtk2 support been resurrected? I think it was a gtk2/3 issue wasn't it?

I will stick with the nvidia drivers for now because I sometimes play games. Can't wait until nouveau performs well enough. I don't really understand why nvidia are so obstructive, but that's another topic.

---

### Post by Elfy on 2014-01-12
> The screenshot you post looks like a power-on from cold, just noise rather than old images.It is.

You can see the other type of it in the other image I uploaded to the bug report. Which I marked as a security issue :p

I'm using a GTK3 indicator for sound in the GTK2 panel - [https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators](https://wiki.ubuntu.com/Xubuntu/Roadmap/Specifications/Trusty/Gtk3Indicators) if you're interested :)

The sacuy issue was different - but that's been released now to -updates.

---

