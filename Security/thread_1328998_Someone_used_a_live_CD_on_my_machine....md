---
title: "Someone used a live CD on my machine..."
date: 2009-11-17
forum: Security
---

### Post by bilekbp on 2009-11-17
Hi, I brought my PC in to a repair shop to have some BIOS issues looked at. It turns out I have to replace some hardware in the PC.

However, my problem is that I was triple-booting the machine with Vista, XP, and Jaunty, and I gave the technician access to Vista (where I keep no personal data) to run some Windows utilities (BIOS, overclocking, etc.)...except when I got the machine back, I found a Karmic live CD in the drive.

I didn't lock the BIOS down because I wanted the techs to work with it, so they could boot from CD without a problem. So now I'm not quite sure what to do with the PC - how can I tell if something has happened to my Jaunty installation? I don't know the first thing about security on Ubuntu, since it is usually locked down tight for me I never thought about forensics before now.

Are there any newbie guides out there to help determine if I have a problem?

I don't really have an issue with wiping / and installing Karmic myself, I intended to do that anyway, and I keep /home on a separate partition, but I would like to determine if this tech abused the trust I gave before I make accusations.

It is possible that the CD was left in my drive as a kind of "geek gift," but I sort of doubt it...

Thanks!

---

### Post by QLee on 2009-11-17
[QUOTE=bilekbp]Hi, I brought my PC in to a repair shop to have some BIOS issues looked at. It turns out I have to replace some hardware in the PC.

However, my problem is that I was triple-booting the machine with Vista, XP, and Jaunty, and I gave the technician access to Vista (where I keep no personal data) to run some Windows utilities (BIOS, overclocking, etc.)...except when I got the machine back, I found a Karmic live CD in the drive.[/QUOTE]


Odd, BIOS and overclocking aren't done in Windows, but nice bonus getting a free cd.

[QUOTE=bilekbp]I didn't lock the BIOS down because I wanted the techs to work with it, so they could boot from CD without a problem. So now I'm not quite sure what to do with the PC - how can I tell if something has happened to my Jaunty installation? I don't know the first thing about security on Ubuntu, since it is usually locked down tight for me I never thought about forensics before now.[/QUOTE]


You couldn't have locked down the BIOS anyway, not to a tech who had physical access to the system and who was going to open the case for hardware repairs anyway.



[QUOTE=bilekbp]I don't really have an issue with wiping / and installing Karmic myself, I intended to do that anyway, and I keep /home on a separate partition, but I would like to determine if this tech abused the trust I gave before I make accusations.[/QUOTE]

If your system isn't encrypted and someone had physical access while you weren't watching, it's going to be extremely difficult to find anything as "proof" of what was (or might have been) done if they wanted to do something malicious and were any good at it. If I were you, I would ask them about what was the reason for the CD left in the drive and decide if I was going to use that shop next time by the answer, I wouldn't make any accusations.

As a general overview of Ubuntu security, this page has some good info:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

You might be especially interested in the last part of the page.

---

### Post by magneze on 2009-11-17
I would just phone them up and ask. Just say you found the CD in the drawer and wondered why it was there.

---

### Post by cdenley on 2009-11-17
Whenever I am asked to repair a computer with what sounds like a hardware problem, often the first thing I do is boot an ubuntu livecd. It has memtest86 on it, and you can also use it to dump the hard drive to test for bad sectors. It helps eliminate the possibility of software being the cause of any problem, and lets you work with the computer without risking filesystem corruption.

---

### Post by tubbygweilo on 2009-11-17
If you have the slightest worry about the integrity of your operating system or that of your data then you must for your own peace of mind consider a clean install and the rebuilding of data from backed up data storage if at all possible. I tend to have sensitive data encrypted by Truecrypt and held in several partitions thus a reinstall of the operating system and the creation of a few symlinks and I am back in business with the minimum of fuss.

---

