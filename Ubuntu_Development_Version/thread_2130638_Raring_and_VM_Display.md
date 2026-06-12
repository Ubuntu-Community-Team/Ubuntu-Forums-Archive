---
title: "Raring and VM Display"
date: 2013-03-30
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2013-03-30
I now have Raring bedded down and have started bringing in things that I had set up in Precise, such as Virtualbox and a Windows 7 VM.

This is the bottom right hand corner of my display in Precise with the VM full screen and viewed in seamless mode.   The Win 7 bottom panel is permanent (not auto-hide) and everything is as it should be:
[IMG]https://lh6.googleusercontent.com/fENWpx6V0W9lSezzPPyTTJJkIEef2Wq91z82UJFolBBpf08MCpBRn8Z7ofO9Ks7gSSI1taCUINFRbPfUvJRiBniLN4tdhlNOSijGaWLYd50B8I_J6pOIvxKSIA[/IMG]

And this is what I get when running Raring, again with the VM full screen and seamless mode:
[img]https://lh6.googleusercontent.com/glkdx3HT3pCWSEMQeD5LOP243HAwYSN_h-vJvGMxJvfDHJdnMO2LneL7Ygx3B5eWL-c5KnQFXs6-Qop93AJxebZAyB651DHNqduLGBMpOJequdCmJQtKHjWA_Q[/img]

I've tried setting the Windows panel to auto-hide and then back to fixed... no change.
I've tried increasing the height of the panel but the bottom part (about 24 pixels worth) is still chopped off.
On both systems the monitor is running 1920 x 1080 (under unity) and both Win 7's report a screen size of 1920 x 1056 which I'm guessing is correct to allow for the compulsory top panel in unity; about 24 pixels.

It 'appears' that Raring unity is 'placeholding' a bottom panel that is cropping the Windows panel.   Graphics is an nVidia GTX650 with nvidia-310.   I did a test by reverting to nvidia-304 but it made no difference.

Am I missing something obvious here?   Anyone else come across this raring/seamless VM issue.

---

### Post by MarcusPereira on 2013-04-30
Happens the same with me but only in Seamless mode.
Guest is a Windows XP. After the upgrade to Raring I reinstall the Guest additions at the guest to try to fix it but it did not help.
Guest additions is now version 4.2.12r84980.

At Host:
# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)

# dpkg -l | grep virtualbox
ii  virtualbox-4.2                            4.2.12-84980~Ubuntu~raring             amd64        Oracle VM VirtualBox

---

### Post by Aenima99x on 2013-04-30
Just adding another "me too". Using an XP VM in Seamless Mode.
VirtualBox 4.2.12 r84980

---

### Post by cariboo on 2013-04-30
Raring has been released, and is no longer a development version. If you are having problems with vbox, I'd suggest you start a new thread in [Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308"). Thread closed.

---

