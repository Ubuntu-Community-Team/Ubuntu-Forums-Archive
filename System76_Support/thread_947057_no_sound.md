---
title: "no sound"
date: 2008-10-13
forum: System76 Support
---

### Post by johnmata on 2008-10-13
Hi,

I have recently installed the latest Ubuntu on my System76 machine:

1 x  	Ratel Value
Options
*Operating System : Ubuntu 7.10 (Gutsy Gibbon) Linux
+ $0.00
*Processor : Celeron D 331 2.66 Ghz FSB 533 M
+ $0.00
*Memory : 2 GB - 2 x 1 GB DDR2 667 MHZ


Everything is working great except there is no sound.  Here are a couple of things I did in the terminal to gather more information:

john@Ace:~$ aplay -l
aplay: device_list:205: no soundcards found...

john@Ace:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
	Subsystem: ASUSTeK Computer Inc. P5VD2-VM mothervoard
	Flags: medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=128M]
	Capabilities: <access denied>

Any ideas on what I can do to get my sound up and running would be greatly appreciated.

Cheers,
John

---

### Post by thomasaaron on 2008-10-14
Hi, John. Have you downloaded and ran the latest System76 driver?

If not, go to [http://planet76.com/repositories](http://planet76.com/repositories)
Download the latest driver (second file from the bottom).
Double-click to install it.

Then run it: System > Administration > System76 Driver > Restore (tab) > Restore (button)

When it finishes, reboot your computer.

---

### Post by johnmata on 2008-10-14
Hi,

Actually I had already tried that.  I yesterday I found instructions at the System76 website.  It didn't solve the issue.  Just now when I went to install it again I received confirmation that it's already installed.

What else could it be?

Thanks,
John

---

### Post by thomasaaron on 2008-10-15
Double-click on the speaker icon in the upper right corner of your screen. In the resulting sound control panel, go to Edit > Preferences and make sure all of the available checkboxes have been selected.

Make sure the PCM, Master and Front sliders are not muted. There may be other things that need to be unmuted.

Let me know if this doesn't help, and I'll try to get some screenshots of the settings on our shop Ratel.

Also (and I hate to ask; I really do) are your speakers connected to the right jacks? Are they turned on? Is the volume knob on the speakers turned up?

One last question: Did you *install* 8.04 on your machine, or did you *upgrade* from 7.10?

---

### Post by johnmata on 2008-10-15
Hi,

It seems that the new kernel update last night, 10/14, has fixed the issue.  Before what I had was a, i am gong off of memory now, a red slash through the speaker.  When I would click on it I would get an error message of some sort.  Anyway, all good now.

Thanks for getting back.

Regards,
John

---

### Post by steveneddy on 2008-10-16
I believe there is an issue with the -21 kernel

I use a Serval Performance Type 1 and I will wait for the kernel to be fixed.

If using the -19 kernel, everything works great.

With the -21 kernel I have no sound and the Nvidia graphics are hosed.

After installation of Hardy, it wasn't necessary to install the System76 drivers, either.

Lots of folks are having issues with the -21 kernel.

---

