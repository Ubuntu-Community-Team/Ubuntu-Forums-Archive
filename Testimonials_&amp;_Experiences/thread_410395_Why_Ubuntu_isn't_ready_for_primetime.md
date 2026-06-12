---
title: "Why Ubuntu isn't ready for primetime"
date: 2007-04-15
forum: Testimonials &amp; Experiences
---

### Post by Geekkit on 2007-04-15
I figured I would share my experience in the hopes of improvement - not to start a flame war. Apologies if I come off as wanting to start a flame war. This isn't my intention. I truly like Linux and what it stands for and have been using it off and on since 95' back when I was a college student and would get a copy of Linux on three floppy disks from a friend who was patient enough to babysit a gopher session on a 24 baud modem. :) 

Every year I check out a couple of Linux distros in the hopes of getting rid of Windows (XP) for good. This year I started early because of the houpla around Ubuntu (houpla being a good thing :D ). I've listed problems in two categories (show stopper and annoyances) that I've come across to defend my position.

**Show Stoppers**

Freeze the kernel at boot menu:
By attempting to install, or even run the live CD of 6.10, the CD froze right after I chose a menu item. I found the solution which was to set the BIOS back to its defaults. This sounded suspiciously like something caused from what Windows might have done so maybe mentioning this here is not very fair - not really Ubuntu's fault in fact. However, it might be worth putting some sort of info in the setup operation to suggest that other operating systems do not play fair. This caused me a couple of hours of scratching my head.
**UPDATE:** This is caused by SATA issues. Bug reference here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269)

Freeze the kernel attempting to access mobile phone via USB:
This problem happened several times and didn't appear to have anything to do with any one particular application. Wammu was the first one that I used. Later I didn't even fire up Wammu but when Ubuntu attempted to detect a device it still froze and I had to hit the reset switch on my tower. I found a couple of bug reports made late 2006 with no real time line or ETA on a solution.
**UPDATE:** reference at: [https://bugs.launchpad.net/ubuntu/+bug/102965](https://bugs.launchpad.net/ubuntu/+bug/102965)

Freeze the kernel while looking at OpenGL screen savers during Beryl being loaded:
Certain screen savers caused the kernel to freeze. I suppose this should be more of a complaint to Beryl but then again the kernel is ultimately responsible for such requests and issues no? This I'm sure will be fixed soon or at least that was the hopeful feeling of many posts in the forums for bugs like this.

Freeze the kernel while attempting to load a DVD:
This one caught be by surprise. MPlayer attempted to load the movie from DVD (the DVD was a store bought and in the right region DVD). MPlayer failed to load the movie, froze (I could hear the disc still spinning), I attempted to kill the process but Ubuntu wouldn't let me (reminded me of the "end process" game in XP). Then tried to shut down Ubuntu gracefully but couldn't. Had to hit the rest switch. At which point the X Server wouldn't work. After a half an hour and several command line options I got to a point where I could go into some sort of safe mode.



**Annoyances**

PDF support lacking:
If one is to the open source solution instead of closed source proprietary (i.e., not use Adobe's Acrobat reader), then the choices are pretty slim. The default PDF reader (Evince) actually renders the text *beautifully *but if one attempts to print more than one (1) copy of a document, then this fails. I specified 10 copies, 15 copies, three copies, but every time it only ever printed one copy. I know it's not CUPS because KPDF does manage to print multiple copies. Unfortunately KPDF's rendering of text is rather poor (especially compared to Evince) . So if a user has to stare at PDF documents for long periods of time, he/she must use Evince. If a user wants to print a document he/she must use KPDF. Kind of lame.

BlueFish edit crashes when attempting to save any document:
This was a disappointment because it appears to be a great editor. I read the bug report which had been made months ago with no posting of ETA on a fix. Had to abandon the idea of using this.

Synaptic Crashes:
Some combinations of add/remove programs (I apologize that I did not record the combination - but then again I wasn't expecting this) crash Synaptic.

Synaptic vs. Add/Remove Programs Confusion ... Which one?
I was never really sure which one I should use and I was not able to find appropriate documentation describing when I should use one over the other.

Adding Items to a Menu within Gnome: doesn't work:
I attempted to add several different icons to the menus (e.g., NetBeans). I went through finding icons and the executables but the icons (shortcuts if you will) never got added to the menus. I was never sure of why this did not work.

Certain software "add requests" fail:
I attempted to add GnomeSword (an online bible) but unfortunately did not work. Gave a message about needing to press the advanced button (which didn't exist), and remove other components. I found a forum post suggesting that I needed to go through Synaptic but the posting wasn't clear what I was supposed to remove via Synaptic. Either way, I couldn't load the software.

**EDIT: forgot to include ...**

Setting the volume in xmms to maximum makes the system volume peaks and therefore causes distortion, hiss, and crackling. Although the fix is to simply set the xmms media player volume lower, xmms should not be adjusting the overall system volume like that (at least not so as to cause distortion).

Clicking on media clips within Nautilus would cause duplicate instances of MPlayer to kick in and play the files (like two events were generated for each double click). Not sure why this was since I had it set to explicitly be double-click not single click.


**Summary**
All in all this distro of Linux is the closest that I've seen to a fully functional desktop solution. The things that did work flawlessly were:

- CD burning
- Audio streaming
- Office products
- Setting up printer drivers
- Setting up printers to share with Windows computers
- Setting up files/directories to share with Windows computers
- Installing JDK1.6 with Netbeans 5.5

In the end though (and most unfortunately) I've had to turn back to XP for the simple reason of ... stability. I really need an OS that doesn't freeze. I'm not saying that XP is perfect - far from it. I hate it's Orwellian approach to handling what I download/use, etc. But for what I try to do which is develop software, listen to streaming audio, play DVDs, sync my Nokia phone with my computer, view/print PDF files, Ubuntu is not really ready.

I am hopeful to see something in the future (maybe next year?) that addresses these problems. Until then, I'm still a Windows user.

---

### Post by fritz_monroe on 2007-04-15
Thanks for this thorough post.  I like to see people post things like this because it can really help the product improve.

My experiences are quite different from yours.  I've been using Ubuntu as my primary desktop environment for a year and a half.  I have been extremely happy.  I have had a couple minor annoyances, but nothing that is a show stopper.  As for the system freezing up, in the past year and a half, my system has frozen up about 3 times, far fewer times than XP has in that same length of time.

---

### Post by rok3 on 2007-04-15
What kind of hardware are you using?

---

### Post by finferflu on 2007-04-15
I suggest you to try the newly released Debian 4, it's been under development for 21 months, if I'm not mistaken, and it's called Stable, all the packages available have undergone heavy testing (therefore you'll not get the latest ones, but it's the price you pay for stability). Debian itself hasn't got all the bells and whistles of Ubuntu, but it's quick, stable and obviously fully customisable. 

Hope you consider this option :)

---

### Post by Geekkit on 2007-04-15
Thanks all for the positive feedback (esp. fritz_monroe). One thing that I failed to mention in my initial post was the absolutely positive support in the Ubuntu forums. I've seen some pretty basic questions - even some that seemed silly to ask in the said forum. The worst I ever saw however was no reply (not saying there aren't flames here, I'm sure if I dig long enough I'll find them. ;)   ) My point is that this online community seems incredibly supportive and I think that's what's going to make this particular distro popular.

@rok3: my hardware is as follows:

- P4, 3 GHz, 512 MB RAM
- Asus P4S800D-X with RAID BIOS Setting Utility v1.05_964
- 2 hard disk drives: WDC WD400BB-34DEA0 (80 GB), WDC WD800JB-00JJA0 (40 GB)
- NVIDIA GeForce4 Ti 4200 AGP 8x
- DVD Rewritable disks: HL-DT-ST DVDRAM GSA-41638 (LG), HP DVD Writer 200j (HP)

@finferflu:

Thanks for that. I was eyeballing Debian. You've strengthened my hunch to make this the next try. I have been tracking Feisty's list of things they want changed/improved. It looks promising. One thing I really was impressed with Edgy was it's ability to allow me to be brainless as I set up printer/file sharing. I remember a couple of years attempting the same thing in Fedora Core and having to mess with config files and such. The only thing to make it perfect would have been to allow a GUI choice instead of having to type at the command prompt to tell SAMBA about the account(s) allowed to print to the printer (from the network).

:)

---

### Post by 3rdalbum on 2007-04-17
You're using an x86 processor, so you should install Adobe Acrobat Reader (acroread in Synaptic). That's better than using Evince or Kpdf.

With your volume, try turning down the PCM channel in the Gnome mixer.

It's probably not the kernel that is crashing, it's more likely to be that Nvidia driver with Xorg. It happens a lot with me because I've got an ATI card (copy operations continue in the background and stuff), but I thought Nvidia drivers were supposed to be really good?

---

### Post by kazuya on 2007-04-17
I sort of agree with the original poster on one issue. Pdf editor. I was trying to fill out tax 1040 pdf form last night and guess what? I have installed acroread, xpdf, evince, etc. None of these would let me modify the 1040 pdf document.. I had to reluctantly borrow the wife's laptop which had windows XP so as to be able to use adobe acrobat reader to do this.

I was very perplexed. I followed the howto for installing acroread, but do not know how to launch it as it did not show up on my menu.

Does adobe acroread solve this issue. On the good side, the online tax softwares worked easily on my Ubuntu via firefox with no issues at all. I was impressed.. But minor things like that turn some users off. Trust me, I was back to my Ubuntu PC as soon as that one thing was done.

I am frightened to use XP for too long. Paranoia... Just too unsafe for me as I have not installed any antivirus, firewall, etc on her laptop and I already saw waves of spyware...

I agree but would also add that it is closer to prime time than say Windows XP, Vista,.. I cannot speak for OSX here. But for my use, it beats out any of the others. There are features it offers me that I need that the others cannot yield me and many others once they have discovered them...

No OS existent thus far is really ready for prime time. If any, I'd say linux. The pdf problems have workarounds as well. I shall investigate and see how workable this is..

---

### Post by Ti_Uhl on 2007-04-17
> **kazuya said:**
> 
...
 
I was very perplexed. I followed the howto for installing acroread, but do not know how to launch it as it did not show up on my menu.
 
...

 
open up a terminal and enter 'acroread' then press enter. 
 
If you want to add it to your start menu, right-click on your menu to add launchers.

---

### Post by Geekkit on 2007-04-17
> **kazuya said:**
> The pdf problems have workarounds as well. I shall investigate and see how workable this is..

For me the PDF problem is a minor annoyance. That I can deal with. It's the crashes with USB, mounting DVDs and crashing the X Server when it cannot shut down properly that keep me from pursuing Linux.

Those are all things that work in XP and so as a user I expect them to work in Linux as well.

---

### Post by Geekkit on 2007-04-17
> **motin said:**
> Wow, you should really give your opinion on what the market-shaping features of either Ubuntu, Windows and/or OS X are if you can ...[/URL]


Thanks for that Motin, I'll submit one now.

---

### Post by stchman on 2007-04-18
> **Geekkit said:**
> I figured I would share my experience in the hopes of improvement - not to start a flame war. Apologies if I come off as wanting to start a flame war. This isn't my intention. I truly like Linux and what it stands for and have been using it off and on since 95' back when I was a college student and would get a copy of Linux on three floppy disks from a friend who was patient enough to babysit a gopher session on a 24 baud modem. :) 

Every year I check out a couple of Linux distros in the hopes of getting rid of Windows (XP) for good. This year I started early because of the houpla around Ubuntu (houpla being a good thing :D ). I've listed problems in two categories (show stopper and annoyances) that I've come across to defend my position.

**Show Stoppers**

Freeze the kernel at boot menu:
By attempting to install, or even run the live CD of 6.10, the CD froze right after I chose a menu item. I found the solution which was to set the BIOS back to its defaults. This sounded suspiciously like something caused from what Windows might have done so maybe mentioning this here is not very fair - not really Ubuntu's fault in fact. However, it might be worth putting some sort of info in the setup operation to suggest that other operating systems do not play fair. This caused me a couple of hours of scratching my head.
**UPDATE:** This is caused by SATA issues. Bug reference here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33269)

Freeze the kernel attempting to access mobile phone via USB:
This problem happened several times and didn't appear to have anything to do with any one particular application. Wammu was the first one that I used. Later I didn't even fire up Wammu but when Ubuntu attempted to detect a device it still froze and I had to hit the reset switch on my tower. I found a couple of bug reports made late 2006 with no real time line or ETA on a solution.
**UPDATE:** reference at: [https://bugs.launchpad.net/ubuntu/+bug/102965](https://bugs.launchpad.net/ubuntu/+bug/102965)

Freeze the kernel while looking at OpenGL screen savers during Beryl being loaded:
Certain screen savers caused the kernel to freeze. I suppose this should be more of a complaint to Beryl but then again the kernel is ultimately responsible for such requests and issues no? This I'm sure will be fixed soon or at least that was the hopeful feeling of many posts in the forums for bugs like this.

Freeze the kernel while attempting to load a DVD:
This one caught be by surprise. MPlayer attempted to load the movie from DVD (the DVD was a store bought and in the right region DVD). MPlayer failed to load the movie, froze (I could hear the disc still spinning), I attempted to kill the process but Ubuntu wouldn't let me (reminded me of the "end process" game in XP). Then tried to shut down Ubuntu gracefully but couldn't. Had to hit the rest switch. At which point the X Server wouldn't work. After a half an hour and several command line options I got to a point where I could go into some sort of safe mode.



**Annoyances**

PDF support lacking:
If one is to the open source solution instead of closed source proprietary (i.e., not use Adobe's Acrobat reader), then the choices are pretty slim. The default PDF reader (Evince) actually renders the text *beautifully *but if one attempts to print more than one (1) copy of a document, then this fails. I specified 10 copies, 15 copies, three copies, but every time it only ever printed one copy. I know it's not CUPS because KPDF does manage to print multiple copies. Unfortunately KPDF's rendering of text is rather poor (especially compared to Evince) . So if a user has to stare at PDF documents for long periods of time, he/she must use Evince. If a user wants to print a document he/she must use KPDF. Kind of lame.

BlueFish edit crashes when attempting to save any document:
This was a disappointment because it appears to be a great editor. I read the bug report which had been made months ago with no posting of ETA on a fix. Had to abandon the idea of using this.

Synaptic Crashes:
Some combinations of add/remove programs (I apologize that I did not record the combination - but then again I wasn't expecting this) crash Synaptic.

Synaptic vs. Add/Remove Programs Confusion ... Which one?
I was never really sure which one I should use and I was not able to find appropriate documentation describing when I should use one over the other.

Adding Items to a Menu within Gnome: doesn't work:
I attempted to add several different icons to the menus (e.g., NetBeans). I went through finding icons and the executables but the icons (shortcuts if you will) never got added to the menus. I was never sure of why this did not work.

Certain software "add requests" fail:
I attempted to add GnomeSword (an online bible) but unfortunately did not work. Gave a message about needing to press the advanced button (which didn't exist), and remove other components. I found a forum post suggesting that I needed to go through Synaptic but the posting wasn't clear what I was supposed to remove via Synaptic. Either way, I couldn't load the software.

**EDIT: forgot to include ...**

Setting the volume in xmms to maximum makes the system volume peaks and therefore causes distortion, hiss, and crackling. Although the fix is to simply set the xmms media player volume lower, xmms should not be adjusting the overall system volume like that (at least not so as to cause distortion).

Clicking on media clips within Nautilus would cause duplicate instances of MPlayer to kick in and play the files (like two events were generated for each double click). Not sure why this was since I had it set to explicitly be double-click not single click.


**Summary**
All in all this distro of Linux is the closest that I've seen to a fully functional desktop solution. The things that did work flawlessly were:

- CD burning
- Audio streaming
- Office products
- Setting up printer drivers
- Setting up printers to share with Windows computers
- Setting up files/directories to share with Windows computers
- Installing JDK1.6 with Netbeans 5.5

In the end though (and most unfortunately) I've had to turn back to XP for the simple reason of ... stability. I really need an OS that doesn't freeze. I'm not saying that XP is perfect - far from it. I hate it's Orwellian approach to handling what I download/use, etc. But for what I try to do which is develop software, listen to streaming audio, play DVDs, sync my Nokia phone with my computer, view/print PDF files, Ubuntu is not really ready.

I am hopeful to see something in the future (maybe next year?) that addresses these problems. Until then, I'm still a Windows user.

You are condemning Ubuntu for its difficulties with (1) PC.  I have Ubuntu installed on (3) PCs and they all work great.

My PCs don't freeze when I add or remove software.  As a matter of fact I  find Ubuntu more stable than XP.

---

### Post by justin whitaker on 2007-04-18
Geekkit, nice post. Thoughtful, well laid out. 

I had a terrible time with 6.10...it seemed to be really unstable, and some of the bugs you listed I had trouble with as well: synaptic fails, usb fails, add/remove fails, etc. 

What I would suggest is trying out 7.04 before condemning Ubuntu outright, but that's just me.

Submit bug reports for all, and hope you give Ubuntu another look.

---

### Post by Geekkit on 2007-04-18
> **stchman said:**
> You are condemning Ubuntu for its difficulties with (1) PC.  I have Ubuntu installed on (3) PCs and they all work great.

My PCs don't freeze when I add or remove software.  As a matter of fact I  find Ubuntu more stable than XP.

Stchman,

I'm glad for you that your PC works. I wish I could say the same. I'm not condemning Ubuntu or Linux. I've simply said I'm awaiting bug fixes before I attempt again. All showstoppers that I've listed are already listed/posted as bugs (visit the links) - whether or not you've experienced them, they are bugs that others have experienced too (not just me). If you haven't experienced these bugs, then consider yourself fortunate.

This particular forum is for Ubuntu testimonials and experiences. Thus, my post, which is a testimonial/experience, has been posted in the hopes that Ubuntu maintainers are listening and will consider resolutions to these bugs. At present, both the ones I referenced in my original post seem to be not a consideration (SATA from 2006, they are undecided), and the recent Nokia issue from just this month is undecided too.

> **justin whitaker said:**
> Geekkit, nice post. Thoughtful, well laid out. 

I had a terrible time with 6.10...it seemed to be really unstable, and some of the bugs you listed I had trouble with as well: synaptic fails, usb fails, add/remove fails, etc. 

What I would suggest is trying out 7.04 before condemning Ubuntu outright, but that's just me.

Submit bug reports for all, and hope you give Ubuntu another look.

Justin, thanks. I was trying to be as tactful as possible. I will definitely look into 7 (after the smoke/steam clears) and later on in the summer when I have a moment. I really would like it to work. My whole intent had been to do a total wipe (i.e., no dual boot crap and no looking back, Ubuntu on one drive and my data on the other drive). I also really got used to Beryl and how absolutely funky things looked. I also liked how quick applications popped up on my desktop like PDF viewers and development tools, and how my JDK1.6 installation took about 1/5 the time to install due to not having to diddle the registry.

---

### Post by stchman on 2007-04-19
> **Geekkit said:**
> Stchman,

I'm glad for you that your PC works. I wish I could say the same. I'm not condemning Ubuntu or Linux. I've simply said I'm awaiting bug fixes before I attempt again. All showstoppers that I've listed are already listed/posted as bugs (visit the links) - whether or not you've experienced them, they are bugs that others have experienced too (not just me). If you haven't experienced these bugs, then consider yourself fortunate.

This particular forum is for Ubuntu testimonials and experiences. Thus, my post, which is a testimonial/experience, has been posted in the hopes that Ubuntu maintainers are listening and will consider resolutions to these bugs. At present, both the ones I referenced in my original post seem to be not a consideration (SATA from 2006, they are undecided), and the recent Nokia issue from just this month is undecided too.



Justin, thanks. I was trying to be as tactful as possible. I will definitely look into 7 (after the smoke/steam clears) and later on in the summer when I have a moment. I really would like it to work. My whole intent had been to do a total wipe (i.e., no dual boot crap and no looking back, Ubuntu on one drive and my data on the other drive). I also really got used to Beryl and how absolutely funky things looked. I also liked how quick applications popped up on my desktop like PDF viewers and development tools, and how my JDK1.6 installation took about 1/5 the time to install due to not having to diddle the registry.

Update:  I checked out your bugs links and the SATA thing refers to 64bit Ubuntu.  I tried the 64bit Ubuntu and found it to be too cumbersome so I went back to the 32bit version.  You want buggy flaky OS, try Windows XP 64 bit.

BTW, my laptop has a SATA drive and it works well using Ubuntu.

As far as the Nokia phone thing I cannot comment as I don't own a Nokia phone.

You do know that Beryl is still beta?  Beta software can freeze on you.  Beryl is just eye candy, it adds nothing to the functionality of the OS.  My advice, uninstall Beryl until it is ready.

As far as PDF support, Ubuntu comes with Evince (pdf reader) and you can get Acrobat 7 from the package manager.  Acrobat is not open source, but it is a free install and it works great.  how many PDF readers does XP come with?   ZERO.  As a matter of fact XP comes with very little software at all.  You have to either buy or download a bunch of software to get XP to be useful.

Is Ubuntu perfect?  No.  Does it have bugs?  Yes.  All OSs have bugs.  That is why Ubuntu and Microsoft have updates.  I challenge anyone to find a piece of code over 20MB that does not have any bugs.

I do consider Ubuntu superior to XP in every aspect besides gaming.  I do consider Excel and Powerpoint to be superior to Openoffice Calc and Impress.

I like having a glut of software at my disposal in a one stop shopping area for zero cost.

---

