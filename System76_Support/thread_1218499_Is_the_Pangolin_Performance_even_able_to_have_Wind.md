---
title: "Is the Pangolin Performance even able to have Windows XP installed?"
date: 2009-07-20
forum: System76 Support
---

### Post by Cadeyrn on 2009-07-20
I'm trying to dual-boot Ubuntu with Windows XP. I've followed all of the guides, the hard way (Ubuntu installed before Windows), and it should be working. My Windows XP partition is /dev/sda2, or (hd0,1) and my menu.lst entry for Windows is:

title Microsuck Windoze XP
root (hd0,1)
makeactive
chainloader +1

I'm well aware of the "map (hdA) (hdA)" lines, which give me error 22 instead of fixing error 22. Because of this, we can rule out the 1024 cylinder issue as a cause.

Without those two lines, Windoze boots into a blank black screen and hangs there forever. I've looked at Microsoft's support and Googled the issue, and it seems the only Linux-using people who get this error have at least one IDE hard drive as well as at least one SATA hard drive, and their SATA drive is causing the problem--I have just one IDE drive and no others. Plus their problems have not been solved.

Here is my fdisk output:
"Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00052287

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    11631059     5815498+   5  Extended
/dev/sda2   *   415424835   625137344   104856255    7  HPFS/NTFS
/dev/sda3        11631060   415424834   201896887+  83  Linux
/dev/sda5             126    11631059     5815467   82  Linux swap / Solaris

Partition table entries are not in disk order"

On a side note, I've tried making sda3 and sda2 the boot partitions and then booting into Windows, in fact I want sda3 to be the boot partition, but no matter which one the computer boots into, it goes straight to sda3's grub menu. Also, it might be a help to know:
/dev/sda1 is (hd0,0)
/dev/sda2 is (hd0,1)
/dev/sda3 is (hd0,2)
/dev/sda5 is inside of sda1 and therefore not a physical parition.

GParted's parition list for /dev/sda looks like this:
/dev/sda1
->/dev/sda5
/dev/sda3
/dev/sda2

EDIT: Aha! I just found out the problem: sda2's physical location is (hd0,3) while its digital location is (hd0,1). Since 1 and 3 are not the same number, grub gives me either a blank screen or error 22: no partition there. A simple fix is to remake the NTFS partition to the left of sda3 instead of the right. Although that will take hours to finish from a LiveCD...

---

### Post by thomasaaron on 2009-07-20
There ya go! :)

---

### Post by Lee_Machine on 2009-07-20
The Pangolin works great with Windows XP, Vista, and 7. But depending on your reasons for having it installed, running it virtually is the way to go. Of course for running games dual booting would be the way to go.

---

### Post by steveneddy on 2009-07-20
> **Lee_Machine said:**
> The Pangolin works great with Windows XP, Vista, and 7. But depending on your reasons for having it installed, running it virtually is the way to go. Of course for running games dual booting would be the way to go.

I agree that virtualization is the answer for most.

VirtualBox is a great product.

---

### Post by 3Miro on 2009-07-21
My recommendation:

1. Try Virtual Box
2. Try Wine
3. Set up Dual-Boot

(depending on the situation you can interchange 1 and 2)

Dual-Boot is so much pain, that you should leave it as last resort. I used to triple-boot on my machine before Ubuntu 8.10 and I am do not wish to back to that situation.

---

### Post by Cadeyrn on 2009-08-16
Yes, I LOVE VBox and WINE, but neither of them work for me because of simple reasons.

VBox isn't good for me because it's pretty horrible as far as playing games. Its graphics are good enough for everything except games, but games will just act like I have no graphics card and not launch. Plus the virtual DVD-ROM drive that VBox uses to access my own DVD drive is one of the many DVD-RW drives that SecuROM hates. My normal DVD-RW drive, however, is in the minority of DVD-RW drives that actually works with SecuROM.

WINE will not run any game. Period. Every game I want to play has a rating of silver to platinum on the same WINE version, but they simply don't work on my computer through WINE. At first I didn't know what was going on, until STALKER Beer Sky in the Terminal told me it couldn't load the x32 architecture properly and so it crashed on purpose. So, basically, WINE isn't made to run on x64 Linux, and I'd rather not do a reinstall, so I'll just use x32 the next time I buy a computer.

---

### Post by thinman1189 on 2009-08-16
I have Serp4 with 64bit 8.10 and I can use wine fine for every game I've tried (WoW, COD4, Starcraft). Never got AOE2 working but it's apparently possible through the use of a winescript that I haven't tried yet (but that's not a graphics or install issue, but due to m$ drm).

If you need help with wine, feel free to join us in #winehq on the ubuntu or freenode irc servers.

---

### Post by betrunkenaffe on 2009-08-16
fyi, anyone having issues with installing xp, double check that bios is set to either XP or has AHCI off.. that caused me lots of blue screens :)

and  yes, it works fine.

---

### Post by jdb on 2009-08-17
> **Cadeyrn said:**
> Yes, I LOVE VBox and WINE, but neither of them work for me because of simple reasons.

VBox isn't good for me because it's pretty horrible as far as playing games. Its graphics are good enough for everything except games, but games will just act like I have no graphics card and not launch. Plus the virtual DVD-ROM drive that VBox uses to access my own DVD drive is one of the many DVD-RW drives that SecuROM hates. My normal DVD-RW drive, however, is in the minority of DVD-RW drives that actually works with SecuROM.

WINE will not run any game. Period. Every game I want to play has a rating of silver to platinum on the same WINE version, but they simply don't work on my computer through WINE. At first I didn't know what was going on, until STALKER Beer Sky in the Terminal told me it couldn't load the x32 architecture properly and so it crashed on purpose. So, basically, WINE isn't made to run on x64 Linux, and I'd rather not do a reinstall, so I'll just use x32 the next time I buy a computer.

It looks like there might be better graphics on the way for VBox.

[http://virtualization-spotlight.com/sun-virtualbox-3-introduces-support-for-3d-graphics-and-smp/]("http://virtualization-spotlight.com/sun-virtualbox-3-introduces-support-for-3d-graphics-and-smp/")

jdb

---

### Post by samalex on 2009-08-17
Though I'm not much of a gamer, I've found Win XP runs very well through VirtualBox 3.  I do lots of streaming video using codecs that aren't Linux friendly (AppDev Training), plus I've setup a few applications that just won't work in Linux, or not well anyway, namely some of the Microsoft server applications (SSMS, VS, etc) plus iTunes.

But I can see where hard core gamers would want to run Win XP natively for the video card.  But honestly I've found some great games under Linux, so I might get back into gaming... but only running Linux native games :)

Sam

---

### Post by Cadeyrn on 2009-08-17
> **betrunkenaffe said:**
> fyi, anyone having issues with installing xp, double check that bios is set to either XP or has AHCI off.. that caused me lots of blue screens :)

and  yes, it works fine.

Been there, done that. Lol, it took me two days to realize my BIOS was doing it.

> **jdb said:**
> It looks like there might be better graphics on the way for VBox.

[http://virtualization-spotlight.com/sun-virtualbox-3-introduces-support-for-3d-graphics-and-smp/]("http://virtualization-spotlight.com/sun-virtualbox-3-introduces-support-for-3d-graphics-and-smp/")

jdb

Yup, my second try of Windows through VBox was on VBox 3, and I noticed those features right away, except it still isn't good for gaming because it can't have over 128MB of video RAM, and the one thing I don't like about VBox, is instead of letting the guest OS access the computer's hardware directly, it simply tells the computer that there is a generic DVD drive called VBOX DVD DRIVE, and a generic video card. The DVD drive thing causes SecuROM to freak out, rendering all games unplayable without a fixed exe, and the fake video card that VBox tells Windows about has none of the basic graphical capabilities that my card has, such as pixel shading 2.0. When a video game from the 21st century notices the computer is running a 128MB video card with zero capabilities besides just basic 3D acceleration, it WILL NOT LAUNCH, no matter what you do. And I've tried [3DAnalyzer](http://www.google.com/url?sa=t&source=web&ct=res&cd=5&url=http%3A%2F%2Frdhacker.blogspot.com%2F2009%2F03%2Fusing-3d-analyzer-to-play-games-without.html&ei=g4qJSvGVM42csgOupr3mAg&usg=AFQjCNFjTu0lAObpXlXrhTAiyTATwdmSDg&sig2=wTsvtZlj4PrFTlzeqL3GMg)'s emulation.

Samalex, I see what you're getting at. I like a few Linux games a lot, too, like Warsaw and OpenArena and SuperTux (2/Kart). But there are a few games I only own the Windows version of that I can't be without. It's not about just playing any game for me; some of those games have many things I've never seen in a Linux game. Such as an Unreal Tournament clone that actually has vehicles. I won't be buying any new Windows games because PC gaming is dead, but a few that I bought before it died are still great.

---

### Post by Jozza The Wick on 2009-08-25
> **betrunkenaffe said:**
> fyi, anyone having issues with installing xp, double check that bios is set to either XP or has AHCI off.. that caused me lots of blue screens :)

and  yes, it works fine.

Are these recommendations for VirtualBox or the actual BIOS settings in Pangolin?

I'm trying to dual-boot in order to play some games that don't work either in Wine or VB (by the way, I love VB - it's very impressive). But, when I try to book the XP install disk, it bluescreens. I've tried this with two disks (just to confirm that my disk wasn't faulty). One was Home, the other was Pro. Neither work.

Has anyone got XP dual-booting on a Pangolin?

Thanks.

---

### Post by Cadeyrn on 2009-08-25
Yeah, you have to go into the BIOS and set the OS from Vista to XP. That's why you're getting blue screens.

---

### Post by Jozza The Wick on 2009-08-26
oooooooooh I saw that setting in the BIOS but didn't know if that's what people were referring to - thanks!

---

### Post by thomasaaron on 2009-08-26
Also, depending on the SP level of your XP disk, you may need to disable AHCI in the BIOS.

---

### Post by betrunkenaffe on 2009-08-26
There's a SP level that doesn't require AHCI disabled? I was installing SP3...

Which reminds me, might want to update your Win XP guide in your support documents to reflect this, seems it might be a fairly common problem for users with a very simple resolution.

---

### Post by thomasaaron on 2009-08-26
I *thought* that SP2 and above supported SATA hard drives. However, we depend on customer feedback on this sort of thing, as we do no testing with Windows.

---

### Post by betrunkenaffe on 2009-08-28
> **thomasaaron said:**
> I *thought* that SP2 and above supported SATA hard drives. However, we depend on customer feedback on this sort of thing, as we do no testing with Windows.

I figured as much :)

Dunno, apparently SP3 didn't have support for it (or at least enough that I could leave AHCI on). Maybe just a note indicating if you get blue screen, possible step to resolve.

---

### Post by Cadeyrn on 2009-08-28
And a note to ALL future dual-booters: First and foremost, don't make the mistake I made, which is not knowing System76 provides a step-to-step guide in their Wiki on installing Windows on a System76 computer. Because I made the mistake of not knowing that, I spent a week trying to get Windows working, two days of which Linux did not work because of my own negligence.

Also, remember to reinstall GRUB from a LiveCD and configure it to boot Windows, and also, I experienced a freak bug where instead of moving on to the GUI part of the Windows installation, it gave me a missing/corrupt hal.dll error and restarted. No matter how many times I replace the hal.dll file with the one from the Windows disk, it kept re-corrupting itself upon startup. So I fixed it by deleting and remaking the NTFS partition and trying again at installing Windows.

---

