---
title: "If you can't beat them, join them"
date: 2008-10-08
forum: Testimonials &amp; Experiences
---

### Post by SabreWolfy on 2008-10-08
See follow-up further down [here]("http://ubuntuforums.org/showpost.php?p=5939985&postcount=8").

For the last six or seven months I've been using Ubuntu exclusively -- I removed W*ndows from my laptop because I just didn't need it. I even tried (unsuccessfully) to entice friends and family to try Ubuntu. Friends jeered at me because I used "Linux" which just "didn't work". I defended GNU/Linux/Ubuntu/OSS and happily continued using it. My Acer TravelMate 4602LCi "just worked" with Ubuntu. I loved having comprehensive package repositories and access to cool things like SSH and RSYNC and a powerful bash shell. I even spent almost a week getting extended desktop functionality to work. All that changed when my four-year old laptop died. The motherboard died and the cost of a replacement one was the same as the cost of a brand new machine. In retrospect, I should have had the motherboard replaced.

I spent over a week researching hardware in order to decide what to buy. I decided I wanted a powerful desktop machine and a small, more portable laptop. A friend advised me to select a machine with NVidia, as support for these cards in Ubuntu was good. I was told to avoid ATI / Radeon, a comment which was supported by the comments on the relevant Wikiepedia page. After ages of comparing and searching, I selected an Acer Aspire M5640 desktop machine (Quad Core, Nvidia 7100 onboard) and an Acer Aspire 4710 laptop machine (Core Duo, Intel Graphics). All Acer machines ship with a hidden recovery partition and  the remainder of the drive partitioned into two equal parts. The MBR contains special Acer code which responds to Alt+F10 at boot time. This triggers the recovery process via the recovery partition which reinstalls W*ndows into the second partition, which has to exist.

I booted the desktop off an Ubuntu Hardy Heron 8.04.1 Live CD. It booted without problems, but went into 800x600 resolution. I noticed there was a restricted driver available (nvidia-glx-new) which I installed, but I still could not increase the resolution. I could choose between 640x480 and 800x600.

I then restarted in W*ndows and burnt the two Acer recovery DVDs, which effectively just copy the recovery partition onto DVD. They failed. I returned the machine the next day for a swap-out and tried again. The DVDs burnt successfully.

Ideally, I wanted three partitions for Ubuntu: root, home and swap. As there were already three partitions on the disk, this meant I would have to remove W*ndows in order to create three partitions (leaving the recovery partition in place). I ran the LiveCD Ubuntu installer and removed the second and third parition and installed Ubuntu (all at 800x600). After a restart and installing the restricted driver, I could only access a maximum resolution of 800x600. I tried other nvidia drivers in the repository. I downloaded four different versions of NVidia drivers from their website (about 70MB in total). None of these worked. I "Googled" up a storm. I "Googled" some more. I downloaded another 30MB of Envy. No luck. Eventually I had to admit defeat. The onboard 7100 is not compatible with Hardy Heron. After retracing my previous research, I came across a site which mentioned the "7100 GS" as being compatible. Guess that was my mistake. Someone may post a reply to this explaining how to get the onboard 7100 to work. Hack this file. Edit xorg.conf. Stand on your head. Whistle through you eyebrows. See this post number 17 in thread 123532 on yetanotherubuntuforum.org. Or someone will post about how this hardware is NOT compatible, see this link here at wishihadknownbefore.com. Too bad. I didn't find any of those during my searching.

During my attempts to restore W*ndows to the machine and reinstate the MBR, I succeeded in trashing the partition table (with "dd if=acermbr of=/dev/sda" instead of "sda1" I think). This meant that the recovery partition was gone. No matter. I had the recovery DVDs right. These, I was told by Acer, would restore the machine even "after a hard drive crash or a virus". I tried them and got a "Type Mismatch" error, after being told that the partitioning process would take some time. I returned to the LiveCD and made two equally-sized NTFS partitions and tried again. W*ndows was restored successfully. I returned to the LiveCD to mark partition 1 as bootable and booted into W*ndows. I then attempted to return the machine to the retailer. They refused to accept it as it was no in the "original condition". Acer kindly agreed to restore the recovery partition for me if I was prepared to take the machine to their offices. The retailer agreed to accept the return in this case. My other option was to purchase an off-board Nvidia card in the hopes that it would work with Ubuntu.

Before doing any of that, I thought I would look at the laptop machine. I booted off the LiveCD and Ubuntu correctly selected 1280x800 resolution. A restricted driver icon mentioned that I needed drivers for the wireless card. I installed them (off the LiveCD I presume), but a restart was required, which is clearly pointless from a LiveCD. I was very hesitant to install Ubuntu on this machine for fear of repeating the disaster of the desktop machine -- what if I installed it and then discovered that the restricted drivers did not work, as was the case with the desktop machine. I installed Ubuntu from a LiveCD onto an external HDD to test-drive it first. I instructed the installer to install GRUB onto the USB HDD. After rebooting off the USB HDD, GRUB appeared! I selected the first entry (Ubuntu) and GRUB returned "Error 17". I gave up. 

I decided it was not worth the risk -- I decided to simply use W*ndows Vista on both machines. I had no choice. Yes, there is bloat, and sometimes lots of it. Yes, I need anti-virus, anti-spyware, anti-malware, anti-antiware. Yes, it can be clunky. Yes, it's not free, as in freedom. But hey, it just works!

I am typing this on the laptop machine. I plugged in my external 22" LCD. Vista asked if I wanted to (1) extend the desktop on the LCD, (2) clone the display or (3) move the display to the LCD. I selected "Extend". Done. Success. Achieving extended desktop functionality on my old laptop with Ubuntu required an entire week of Internet searches and xorg.conf editing. And then clone mode did not work. I know some manufacturers are providing Ubuntu preinstalled on new machines. None are available in this country though, except for Linpus Linus on the Acer Aspire One. What choice did I have? Risk "breaking" the laptop machine to find out? I'm sad to go. I enjoyed my Ubuntu days.

---

### Post by elmer_42 on 2008-10-08
This isn't the best place for this to be posted, it should be moved [here]("http://ubuntuforums.org/forumdisplay.php?f=103").

With that said, I'm very sorry that the computer you purchased does not work as intended with Ubuntu. I can't really identify with that, building a computer myself allows me to pick and choose which components I want.

---

### Post by SabreWolfy on 2008-10-08
> **elmer_42 said:**
> I can't really identify with that, building a computer myself allows me to pick and choose which components I want.

I considered building a machine from scratch, but found it very difficult to find consensus on which hardware components did and did not work with Ubuntu. Again, it felt too risky to spend money on something which might not work, based on reviews read on the Internet.

---

### Post by taladan on 2008-10-08
Put me in with the crowd that's sorry you had a bad experience.  I've had some doozy's myself.  I had an issue with an nvidia 5200 fx card similar where I had to cycle through graphics drivers to find the right one.  Driver detection could be a /lot/ better in (k)ubuntu.  That said, I'm also a computer tech/network tech and I work a lot with all the windows operating systems, so I see the down sides to them as well.  

Today for example, I had to work on a brand new emachines system running vista with an HP f4280 (i think that was the model) deskjet printer.  Vista, all of a sudden, just had a problem printing to it.  Not that it didn't see the printer, just that any time you want to print whatever program you were printing from shut completely down - IE, Word, Windows Explorer.  Come to find out - and not through any forum posting or help article - it was the fact that Vista was trying to spool the document.  I told it to print directly to the HP and let it worry about spooling them and it started working right.

I guess all of that is said to say this - there is no OS where /everything/ 'just works'.  Each OS has issues.  The good thing about the Linux distros is, you can complain about it and people will either try to help you figure out a workaround, or they'll point you to the devs who can patch the problem up for you almost immediately.  Windows will have printing problems in Vista for the next...well, however long it takes them to decide they really want to fix it.  I guess when they feel like it's affecting their bottom line, I dunno what drives them to patch problems.  

Please don't give up on it because of one bad experience.  It's not a static program with no one working on it.  You came to the right place to vent your frustrations with it, but please, let that be the first step in getting a pleasurable experience out of the OS, not the last.

If I can help out in any way, I'd be more than happy to, though I don't program, am not a dev, and am no guru with linux, just a wanna-be guru.  

Just let me know,

Tal

---

### Post by lisati on 2008-10-08
You've got company here, with people who have had their share of challenges to meet - last week I had my share of hassles with partition tables and MBRs getting scrambled, with several hours bumbling through various options, frustrated at my own ignorance, trying to get things working again - it ended with a degree of success, thanks in part to ideas in these forums.

Feel free to stick around and toss ideas around and asking questions.

---

### Post by ukripper on 2008-10-09
Envy was your answer and is in repos for nvidia and ati cards. and i am surprised envy didn't work on that card as my cousin got the same and he is running hardy with no problem using envy.

---

### Post by armandh on 2008-10-09
any desktop or laptop with built in recovery partitions is suspect IMHO. the manufacturer expecting you to reinstall often has made it easy [but not standard]

---

### Post by SabreWolfy on 2008-10-10
Thanks for all the positive and supportive replies! After trying V*sta for a short while, I decided that I could not use it on a permanent basis! For the record, the Acer Aspire 4710 notebook works fine with Ubuntu Hardy Heron (so far!). The restricted wireless driver installed and worked perfectly without a restart. The camera (cheese) and microphone work. The card-reader works. Some of the Acer shortcut buttons work (internet and email). Haven't had success with Bluetooth yet though (although I'm not quite sure how it works).

I have returned the Aspire M5640 and have had a desktop machine custom built to run Ubuntu. I booted off the Live CD with the desktop connected to my 22" LCD. The Ubuntu desktop appeared at the correct 1680x1050 resolution! No entry appeared in the restricted hardware drivers, even after updating packages however. No *compiz* effects could be enabled. After installing Ubuntu to the hard drive and updating the packages, I was given the option to install the restricted *nvidia-glx-new* drivers. One restart later and I had full *compiz* effects at the correct resolution for the 22" LCD. For reference, the relevant hardware I have is:

Gigabyte EG31M-S2 Motherboard
Intel Core 2 Quad 2.4GHz Q6600
Forsa nVidia GeForce 8400GS 512MB PCI-Express

---

### Post by Geek In The Pink on 2008-10-16
@SabreWolfy:
My laptop is the same model as yours and I'm glad you were able to run Hardy from it without any glitches.
I've been toying with the idea of wiping out everything from the hard drive and doing a fresh install. I'll be doing it soon as a birthday present for myself. :)
Knowing your story and armed with the support from this community I'm looking forward to making the big switch.
Thanks!

---

### Post by SabreWolfy on 2008-10-16
@Geek In The Pink:
Good luck with the the installation - let us know how it goes! :eek:

---

