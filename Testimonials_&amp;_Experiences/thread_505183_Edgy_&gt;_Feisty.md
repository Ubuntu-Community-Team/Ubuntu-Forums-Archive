---
title: "Edgy &gt; Feisty?"
date: 2007-07-20
forum: Testimonials &amp; Experiences
---

### Post by bmartin on 2007-07-20
I'm glad I wasn't one of the people that got **really worked up** about Feisty when it came out. I've tried it out on several PCs and laptops. I've burned a copy and I ordered a copy through ship-it. Here are my observations:
[LIST]
[*]A lot of people have problems getting their hardware working in Feisty after success in Edgy. According to a poll, people tend to have better luck in Edgy. This is a big drawback of Feisty. I encountered a problem today when I upgraded my parents' PC from Edgy to Feisty; their Belkin F5D7050 (RT73 driver) no longer worked (rt73 kernel module from Serialmonkey). When I blacklisted the rt73usb kernel module, Feisty locked up during boot if the USB WiFi device was plugged in. This seems to be a problem with the kernel (or perhaps the module), so I had to manually edit my GRUB menu.lst file so that the old kernel loads up by default.
[*]Another hardware problem I experienced was with my parents' computer was getting the HP6100 all-in-one printer/scanner/fax to work in Feisty. The Administration > Printing did the trick in Edgy. In Feisty, this caused problems. I tried redoing the printer setup, but that didn't do the trick. I had to use the hp-setup program to get the printer and scanner to work (after removing them from the Printing window).
[*]More than once, when trying to install Feisty from either my CD or the ship-it one, the Live CD failed to load; I didn't bother to check where.
[*]More than once, when trying to install Feisty from either CD, the Live CD's setup failed at the "Setting up USB devices stage. When I say more than once, I mean it happened on different computers. We have 7 computers in my house, including three laptops (one which is very old) and four PCs (all of which are relatively new). I've never had a problem with Edgy's installation.
[*]I use Gentoo 95% of the time; I prefer my PC to my laptop. When I try to compile things on my PC, the compilation goes off without a hitch. When I want to compile something on Ubuntu (my laptop), I almost always have problems. The configure step always works fine; the compilation yields errors, which vary from program to program.
[*]Ubuntu needs a program to help people get their wireless internet connections up-and-running. I understand that there are licensing issues, but there must be something that could be done to simplify the process. Too many users get frustrated; I had nothing but problems with my device and it's a very common chipset. Also, I read somewhere that another WiFi device I had was compatible with Mad WiFi, but when I checked the restricted drivers manager, it said I didn't need the driver.
[/LIST]
Despite all this, Feisty Fawn is great. The codec support, NTFS support, restricted drivers, migration assistant, and WPA support were all great achievements. Feisty has been a much more difficult than Edgy for me (and many others, I'm sure) to install and set up. I hope Gutsy to see some improvements in many of the aforementioned areas; I think many people would benefit from them.

---

### Post by Geekkit on 2007-07-20
For me it's been the complete opposite. Feisty has been the stable version for me where USB support doesn't actually crash the kernel. When I would plug in my USB memory stick or camera or mobile phone into my computer with 6.10 it would literally lock up the system. In 6.10 I also still had to do some config file diddling for SAMBA. I use Totem for video/DVD and Rhythmbox for mp3/shoutcast and compact discs. Absolutely no problems.

Feisty for me has been a rock. I have been using it since the end of May for both my home as well as office computer and developing software on both boxes (two completely different pieces of hardware) and I have been having the time of my life with it.

The one thing that I have seen come up many times is the wireless support. However for me I don't do wireless so it's not an issue.

Sorry to hear that it's not working for you.

:(

---

### Post by bmartin on 2007-07-20
I've gotten everything to work; it's just that it's not simple. I'm glad that you've had a good experience. I don't know why my problems have been so varied. The installation was the most annoying part of all; I had to upgrade several computers to Feisty by downloading the packages.

No where in the Gutsy Gibbon plans is anything related to wireless support enhancement mentioned. Video cards work with restricted drivers and most printers work (esp. HP), but wireless is still an issue in most distros.

I've written a script that detects Broadcom chipsets and installs the firmware or ndiswrapper as appropriate, depending on whether the firmware will work or not. I learned some Python and made a GUI program to detect and install the appropriate drivers. It seems like such a program could be scaled to handle many more chipsets, perhaps using a text file to store the location of the files on the net and the location of their licenses... you know, so users would be required to agree to whatever terms were necessary to download the drivers.

---

### Post by soapytheclown on 2007-07-21
> **bmartin said:**
> I've gotten everything to work; it's just that it's not simple. I'm glad that you've had a good experience. I don't know why my problems have been so varied. The installation was the most annoying part of all; I had to upgrade several computers to Feisty by downloading the packages.

No where in the Gutsy Gibbon plans is anything related to wireless support enhancement mentioned. Video cards work with restricted drivers and most printers work (esp. HP), but wireless is still an issue in most distros.

I've written a script that detects Broadcom chipsets and installs the firmware or ndiswrapper as appropriate, depending on whether the firmware will work or not. I learned some Python and made a GUI program to detect and install the appropriate drivers. It seems like such a program could be scaled to handle many more chipsets, perhaps using a text file to store the location of the files on the net and the location of their licenses... you know, so users would be required to agree to whatever terms were necessary to download the drivers.

In gutsy, the new restircted modules sections detects and downloads then installs your broadcom firmware and gets wireless working for you provided you're wired-in at the time, of course. tried and tested on 2 chipsets no complaints so far using gutsy tribe 3 :D

---

### Post by bmartin on 2007-07-21
> **soapytheclown said:**
> In gutsy, the new restircted modules sections detects and downloads then installs your broadcom firmware and gets wireless working for you provided you're wired-in at the time, of course. tried and tested on 2 chipsets no complaints so far using gutsy tribe 3 :D
Sadly, this is part of the problem. Many chipsets don't work with the Broadcom firmware. I have to use ndiswrapper. There are power problems with many of the chipsets, and until they're worked out, many people will be using ndiswrapper.

Also, the firmware limits people to 11Mbps. I never need more than that, but I could see why some users might not like that limit.

---

### Post by popch on 2007-07-21
I have used both edgy and feisty on several laptops and some desktops. On the whole, feisty works much better for me than did edgy.

However, one area took some fiddling until I got it to work: the wireless LAN support. The culprit seems to be the automatic network setup thingie in the top panel. Using manual setup worked without a hitch, until the automatic setup thingie messed it up again.  So I do not touch the automatic setup again and can use my WLAN all day without any problem.

One other thing does not work at all: ripping CDs and encoding to MP3. Yes, I know that I have to  install some software which uses other licensing schemes. However,  sound juicer appeared to be broken even when just out of the box; no number of re-installations of the package makes any difference.

One of these days I probably will re-install the os; after all, that takes only about 40 minutes. Once you have saved all your data, that is.

---

### Post by punkybouy on 2007-08-13
The real issue here is taking Mom and Dad's PC from a working production PC and making them beta testers.  Put Mom and Dad on 6.06 LTS, keep them happy, then get a PC for you to test with.

---

