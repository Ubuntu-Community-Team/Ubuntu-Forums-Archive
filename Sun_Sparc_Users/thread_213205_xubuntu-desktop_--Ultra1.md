---
title: "xubuntu-desktop --Ultra1"
date: 2006-07-11
forum: Sun Sparc Users
---

### Post by gevans on 2006-07-11
Alright, and for my next question... (I **know** I don't **need** a GUI, but I want to check it out anyway)...

Since now that I have followed the instructions for the Ultra 2 boot problem and added an alias in /etc/modprobe.d for the ethernet, installed apache, mysql and php :) I decided that I need to check out xubuntu-desktop.

Unfortunately the X server fails to start. :/ with the following error:

gevans@ultra1:/var/log$ tail Xorg.0.log
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.2
(==) Depth 24 pixmap format is 32 bpp
(EE) FBDEV(0): mmap fbmem: Invalid argument
(EE) FBDEV(0): mapping of video memory failed

Fatal server error:
AddScreen/ScreenInit failed for driver 0

gevans@ultra1:/var/log$ 


Any ideas?

Thanks,

Greg

---

### Post by gevans on 2006-07-11
Changed the device section from fbdev to suncg6 (as shown):

Section "Device"
        Identifier      "Generic Video Card" 
        Driver          "suncg6" #was fbdev
        Option          "UseFBDev"              "true"
EndSection

 and think I may have came closer with the following error:

(II) SUNCG6: driver for CGsix (GX and Turbo GX)
(--) Assigning device section with no busID to SBUS:/sbus@1f,0/cgsix@2,0
(II) resource ranges after probing:
(EE) SUNCG6(0): Driver can't support depth 24
(II) UnloadModule: "suncg6"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

so now I will make teh default color depth 16 and see if that works.

---

### Post by gevans on 2006-07-11
switching it to 16 didn't work. switching it to 8 however allows X to start but the screen is just black...hmm..closer anyway

---

### Post by gevans on 2006-07-12
AFter doing some ridiculously long searching, it appears (I could be wrong here) that it is a kernel(?) >2.6.x issue that doesn't do something correctly with the suncg6 driver and therefore the best that can be achieved is a black screen with a blue underline at the top left.

Anyone know who I might need to talk to about this? I am assuming the Linux Kernel Dev team? Though that seems not quite right.

-Greg

P.S. Webmin installed flawlessly which was nice...funny thing about it is that this old sparc is faster than most of the servers at my job and they are definitely way newer...ha!

Maybe I will try Ubuntu on my Ultra 10 next hee he

---

### Post by bazz on 2006-07-26
I know when I had some kernel problems my video wouldn’t come in. Now this could be totally different, but on my Deb machine I did a apt-get install hotplug and it worked.

---

### Post by CobyR on 2006-08-09
I am having issues very similar to what you described, but on my Ultra 5.  When I installed Debian I used the ati video driver and things worked fine.  Using the ATI driver with ubuntu gives me results very similar to what you described above.

Currently installing xubuntu-desktop and trying it with the suncg6 setting to see if I get anything different.

I've been told there are other threads here that discuss configuration of X-Windows for an Ultra 5, but I have been unable to find them using advanced search, searching in the sparc user forums.  Am I missing something?

---

