---
title: "Sidux on a tablet PC, was this my fault?"
date: 2009-07-31
forum: The Cafe
---

### Post by AllRadioisDead on 2009-07-31
Hi guys, so the other day I went out and bought a factory refurbished HP TC4400. It comes with windows xp tablet edition and all the crap on it. My first thought was to install linux, naturally. I booted my sidux DVD, and began installing. I completely formatted the drive including the recovery partition. After that, it told me I needed the madwifi drivers for the onboard wireless, since I didn't have an internet connection, I couldn't install it and shut down. Right before grabbing my kubuntu live cd, I had to go out. I came home booted the pc and the display wouldn't come on. No bios screen, nothing. The computer booted, no screen. Tried just about everything, but the screen wouldn't turn on. I suppose it was defective. I called the store back and told them that the screen was defective and he told me to bring it back and he'd exchange it. He asked if it was dropped, etc and I replied no. He asked if I installed software, I said installed Debian. He was surprised that I used linux, but told me that it would probably cost him money since the company would know I removed the original O/S. Reluctantly, he exchanged it for me.

Now was this my fault? I don't see how formatting the hard drive could cause the display to fail completely...
I have a new one, but I am reluctant to install linux or any other operating system for that matter. He told me if I chose to do it again and something went wrong, I was SOL. I don't see how this was possibly my fault, but I figure getting a second oppinion from you guys couldn't hurt. Thanks!

---

### Post by sydbat on 2009-07-31
This time do not format the recovery partition. If you get the same result, you can reinstall XP and see if it works again. Then you will know if it is the tablet or the Linux install. 

If it is defective, you can bring it back with XP on it and claim absolute innocence.

---

### Post by AllRadioisDead on 2009-07-31
> **sydbat said:**
> This time do not format the recovery partition. If you get the same result, you can reinstall XP and see if it works again. Then you will know if it is the tablet or the Linux install. 

If it is defective, you can bring it back with XP on it and claim absolute innocence.
Good idea. Since the screen failed, theorecically it would work if I plugged it into an external monitor? I just don't understand what happened, I've seen plenty of people on the forums using arch/debian/ubuntu on this model.

---

### Post by lisati on 2009-07-31
It's a good idea (but not written in stone) to make backups of recovery partitions, even if you don't think you're likely to need them again. Some computers even come preloaded with software that can help with the task.

---

### Post by AllRadioisDead on 2009-07-31
> **lisati said:**
> It's a good idea (but not written in stone) to make backups of recovery partitions, even if you don't think you're likely to need them again. Some computers even come preloaded with software that can help with the task.
Alright, thank you. After I install kubuntu, will I be able to get rid of the recovery partition?
I still don't understand what happened, or if my install had anything to do with it.

---

### Post by sydbat on 2009-07-31
As lisati states, make a copy of the recovery partition (usually an icon on the XP desktop that shows you the way), then install whatever you want. 

You shouldn't need the recovery partition after making a recovery CD through XP.

And it likely wasn't your install that did anything. It sounds like it was a defective screen.

---

### Post by AllRadioisDead on 2009-07-31
> **sydbat said:**
> As lisati states, make a copy of the recovery partition (usually an icon on the XP desktop that shows you the way), then install whatever you want. 

You shouldn't need the recovery partition after making a recovery CD through XP.

And it likely wasn't your install that did anything. It sounds like it was a defective screen.
I tried running HP's recovery tool to create a set of discs but a CD has already been created for this system so it won't let me.

---

### Post by MaxIBoy on 2009-07-31
It's possible that some bad firmware was loaded by a Linux driver, but I don't think that's it. Probably the screen was simply broken.

---

### Post by lisati on 2009-07-31
> **ihermit said:**
> I tried running HP's recovery tool to create a set of discs but a CD has already been created for this system so it won't let me.

There is a way round this, but I'm not sure if the forum rules will let me post it here, and there are a couple of traps for the unwary (and I'd have to do some searching to remind myself of the link).

---

### Post by AllRadioisDead on 2009-07-31
> **MaxIBoy said:**
> It's possible that some bad firmware was loaded by a Linux driver, but I don't think that's it. Probably the screen was simply broken.
I don't think so...
There are many cases of people running linux on tc4400's.
I don't understand how anything on the hard drive would affect the screen. Technically, linux was never loaded. I used the livecd and repartitioned the drive, I never installed. 
> **lisati said:**
> There is a way round this, but I'm not sure if the forum rules will let me post it here, and there are a couple of traps for the unwary (and I'd have to do some searching to remind myself of the link).Pm please, I'm open to it..

---

### Post by AllRadioisDead on 2009-07-31
Bleh, sorry for the bump, but I want to install kubuntu, but I'm scared Tux will eat my display.

---

### Post by lisati on 2009-07-31
> **lisati said:**
> There is a way round this, but I'm not sure if the forum rules will let me post it here, and there are a couple of traps for the unwary (and I'd have to do some searching to remind myself of the link).

> **ihermit said:**
> Pm please, I'm open to it..

[Done!]("http://h30434.www3.hp.com/psg/board/message?board.id=OSandSW&message.id=7267")

---

### Post by AllRadioisDead on 2009-07-31
> **lisati said:**
> [Done!]("http://h30434.www3.hp.com/psg/board/message?board.id=OSandSW&message.id=7267")
Very much appreciated!
Works like a charm... however since it didn't come with a DVD burner I'm going to need 11 DVD's o_0

---

### Post by AllRadioisDead on 2009-07-31
Guys, I don't have 11 CD's.
Should I just go for the kubuntu install? I seriously doubt it will happen again...
I know I'm not allowed to discuss this, but I found a copy of the manufactures operating system on the internet that I can download, will that be a good fall-back plan?

---

### Post by Antman on 2009-07-31
> **ihermit said:**
> Guys, I don't have 11 CD's.
Should I just go for the kubuntu install? I seriously doubt it will happen again...

If WindowsXP is on the tablet and WORKS... just use it and be happy. If however you want the masochistic pleasure of getting Linux to work on it, then you inherit all the risks involved.

Good Luck.:popcorn:

---

### Post by lisati on 2009-07-31
> **ihermit said:**
> Very much appreciated!
Works like a charm... however since it didn't come with a DVD burner I'm going to need 11 DVD's o_0

I think I used something like 11 CDs when I first went through this exercise on my Compaq desktop (xp). It took something like 2 hours to restore from CD one time I wanted XP back after I'd deleted the recovery partition, a regular "restore to factory settings" direct from the recovery partition usually takes about 15 minutes  or so (not counting the installation of drivers for a couple a video card I've put in along with some software)

I'd hate to think how many I'd need for my laptop (either 2xDVD or 1xDL DVD, Vista home premium)

Good luck.

---

### Post by Dullstar on 2009-07-31
What a stupid reseller.

I guess this won't work for you, but I already have a battle plan for next time I get a computer, which will be a MacBook.

1.  Save money.
2.  Get MacBook
3.  If it comes with recovery disks, great.  If not, look into making them manually.
4.  Install Ubuntu Linux on 30-50 Gigabyte partition (unlike some people I actually want the Mac because of Mac OS X).
5.  Begin using the computer.

---

