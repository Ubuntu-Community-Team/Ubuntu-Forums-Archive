---
title: "My Feisty expereince"
date: 2007-04-26
forum: The Cafe
---

### Post by Aranel on 2007-04-26
Hey there. The day it was released, I downloaded Feisty - Kubuntu for the desktop PC and Xubuntu for my laptop - and installed it. The laptop dual-boots Linux and Windows XP, while the desktop is straight Linux. During the installation, some things "just worked"; with others, I had difficulty. So I thought I'd share my experience.

Laptop (Xubuntu):

Good:
[list][*]My wireless card, which uses a BCM4306 chipset (notorious for not working in Linux), worked almost out-of-the-box. I hooked up a wired connection and apt-got the package *bcm43xx-fwcutter*, and that was that. Support seems to have improved since Edgy; I didn't have to track down a file from the CD to install the firmware, and the connection no longer drops every five hours or so, like it did in Edgy.
[*]The installer asked whether I wanted to import stuff from my Windows XP installation. I declined, since all my important files are on a FAT32 partition for shared storage, but this was awesome.
[*]Unlike Edgy, Feisty detected and auto-mounted the other two partitions on my hard disk.
[*]Universe, Multiverse, and Restricted repositories were set up by default. Yay!
[*]Thunderbird had the proper icons instead of that annoying envelope thing.
[*]Suspend and Hibernate work *perfectly*![/list]

Bad:
[list][*]When I installed Opera, Thunderbird decided it was going to open every link in Opera, despite the fact that I had set the default browser as Firefox. I had to Google around to figure out how to change this, and I found on a Linspire forum that I needed to use *update-alternatives* to set *x-www-browser* back to Firefox. Needless to say, this isn't very user-friendly. If I set the default browser, the applications should obey - period.
[*]AbiWord is *crap*. It doesn't support the ODT format very well, and it's not very customizable at all.
[*]When I installed OpenOffice.org Writer to replace AbiWord, the line spacing was screwed up; when it said it was double-spacing, it was really doing 2.5. I'm not sure whether this is a problem with OpenOffice.org 2.2 or with Ubuntu's package of it, but it got me very frustrated until I figured out how to fix it. (In case you were wondering, I ended up setting the spacing to 175% and creating a template from that.)[/list]
Ugly:
[list][*]After I installed Feisty, Windows XP was not on the GRUB menu. I had to go in and manually edit my /boot/grub/menu.lst file, where there were (thankfully) commented-out instructions for adding a Windows entry. I can boot into Windows just fine now, but this is very... shall we say... newbie-deterrent.[/list]

Desktop (Kubuntu):

Good:
[list][*]Uhh... nice-looking splash screen? This was about the only thing that was good because...[/list]
Bad:
[list][*]On the LiveCD, KNetworkManager could not make the wireless card, which has a RT2500 chipset (notorious for working *well* with Linux!) to connect. I had to quit NetworkManager and configure it through the command line.[/list]
Ugly:
[list][*]Once I'd installed, all heck broke loose after the initial boot. Suddenly, the wireless card wasn't detected anymore ("ra0: no such interface"), the sound no longer worked, and the *mouse* also stopped working. Even when I went and got a USB-to-miniDIN converter, the mouse's light came on, but the cursor wouldn't move. I reinstalled, but it did the same thing. And no, the CD was not corrupted; the ISO's md5sum was correct, and I burned it at 4x (on a 52x-capable burner and CD, mind you).[/list]

I finally ended up installing Xubuntu (and then the *kde-core* package) on the latter computer. The sound works, the mouse works, and now that the accursed NetworkManager is gone, wireless works too. It's very ironic that the wireless card most famous for having Linux problems worked fine, while the one with about the best Linux support available failed to work at all with NetworkManager.

But I digress. Overall, Feisty is one step back and two steps forward, but in my experience, it's a bit over-hyped. Still, Ubuntu and its derivatives are awesome (with the possible exception of Kubuntu...?).

Anyway, thanks for reading my little review/vent. :)

---

### Post by Aranel on 2007-04-26
Um, please disregard this. I apparently double-posted the thread - the real one has been moved to the Testimonials board. Oops.

---

