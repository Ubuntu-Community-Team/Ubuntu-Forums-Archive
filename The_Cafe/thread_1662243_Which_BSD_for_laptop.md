---
title: "Which BSD for laptop?"
date: 2011-01-07
forum: The Cafe
---

### Post by Glenn Jones on 2011-01-07
Hey all,

I've been thinking of expanding my Unix knowledge by giving one of the BSD variants a go. I have had previous experience with OS X and PC-BSD (which is based on freeBSD). I have a new MSI CR620 laptop which works flawlessly under Ubuntu but I would like to install some variant of BSD on it with the main aim is to maximise battery life. I'll be mostly using the laptop to program, email, internet borwsing and some playing of mp3s.

Which flavour of BSD do you recommend for a laptop and to maximize battery life? My initial thoughts are NetBSD or FreeBSD? What do you think?

Cheers

---

### Post by dcstar on 2011-01-08
> **Glenn Jones said:**
> 
.........
Which flavour of BSD do you recommend for a laptop and to maximize battery life? My initial thoughts are NetBSD or FreeBSD? What do you think?

Cheers

I think that you should read what this forum is for:

**General Help**
*All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu.*

---

### Post by Sef on 2011-01-08
Moved to Community Cafe.

---

### Post by kaldor on 2011-01-08
FreeBSD is the most used, I believe. You'll have to do a lot of configuration by hand (similar to Gentoo in that aspect).

For the simple tasks you mentioned, it should work fine if you're willing to put effort into it. Please be aware that BSD is NOT as mature as Linux is when it comes to drivers and things like that.

---

### Post by ilovelinux33467 on 2011-01-08
I would say FreeBSD maybe because it is the one I am most used to out of the BSD's. And the ports system is awesome

---

### Post by veggen on 2011-01-08
I'd stick with PC-BSD. It's FreeBSD but with a little less hassle, and you already have some experience with it.

---

### Post by zigzag77 on 2011-01-08
[FONT=Arial][SIZE=2]Many years ago I was a NetBSD and FreeBSD user before I switched to Linux. It was the time, when you had to calculate hsync  + vsync frequency mode lines for X11 by hand on the command line... Today I appreciate the power and usability of Ubuntu out of the box.

I would check *BSD forums for laptop compatibility or problem reports.
Maybe there are *BSD Live CD's available for testing? A good starting point for your research might be:

[http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)

Distrowatch writes:
[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]Suggested FreeBSD-based alternatives: [PC-BSD]("http://distrowatch.com/pcbsd") (desktop), [DesktopBSD]("http://distrowatch.com/desktopbsd")[FreeSBIE]("http://distrowatch.com/freesbie") (live CD)
[/SIZE][/FONT][SIZE=2] (desktop), [/SIZE]
[*][FONT=Arial][SIZE=2]Other BSD alternatives: [OpenBSD]("http://distrowatch.com/openbsd"), [NetBSD]("http://distrowatch.com/netbsd"), [DragonFly BSD]("http://distrowatch.com/dragonflybsd"), [MidnightBSD]("http://distrowatch.com/midnightbsd")[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]I would expect that today Linux has the best laptop support. I use a Sony Vaio with Intel Core i5. With the gnome panel applets in Ubuntu I can manually control CPU speed and display brightness. Also power management - suspend to RAM and wake up - works, which is important to extend lifetime when running on battery.

I would try a live *BSD distribution to check compatibilty with my laptop:
[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]display driver: resolution, brightness, performance (check VLC + youtube flash video fullscreen performance)
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]lan[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]wlan (wpa2 supprted?)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]keyboard: special FN keys[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]touch pad[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]sound card: output, volume
[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]...etc...
[/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2]
I am a friend of dual boot systems: Use Ubuntu with grub2 as master OS + FreeBSD as second OS - and then compare the battery life time with each operating system. My Sony Vaio E series has a very short battery lifetime of less than one hour...

I enabled CPU virtualization in the BIOS of my Vaio, so it is really fun to play around with [COLOR=Black]other OS installations in qemu with Ubuntu as host:
[/COLOR][/SIZE][/FONT]
[LIST=1]
[*][FONT=Arial][SIZE=2][COLOR=Black][COLOR=#666666][FONT=Arial]Create an empty hard disk image file:
$ [/FONT][/COLOR][COLOR=#666666][FONT=Arial][B]dd if=/dev/zero of=harddisk1.img bs=1M count=8192

[/B][/FONT][/COLOR][COLOR=#666666][FONT=Arial][/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][COLOR=Black][COLOR=#666666][FONT=Arial]Boot virtual machine:
$ qemu-system-x86_64
       -m 1024
       -boot order=dc 
       -hda      harddisk1.img 
       -cdrom  linux-or-bsd-ISO-image.iso[/FONT][/COLOR][/COLOR][/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2][COLOR=Black] [/COLOR][/SIZE][/FONT]

---

### Post by kevdog on 2011-01-08
Why don't you just move to Arch?

---

### Post by kaldor on 2011-01-08
> **kevdog said:**
> Why don't you just move to Arch?

[_USE ARCH_]("http://linsux.org/forum/index.php?/topic/6618-opensuse/")


:)

---

### Post by wojox on 2011-01-08
PC-BSD is nice and geared more for desktop use. Free-BSD is more server-side.

---

