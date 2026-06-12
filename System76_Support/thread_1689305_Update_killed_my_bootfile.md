---
title: "Update killed my bootfile"
date: 2011-02-16
forum: System76 Support
---

### Post by eadwacer on 2011-02-16
Just now (11AM PST 16Nov) ran an update that required a restart. Machine beeped once, flashed the Sys76 logo, and went blank. Required a power-cycle restart. When I booted with F12 I got:

DHCP ...with spinner, for a while, then

PXE-E53 No boot filename recieved
PXE-M0F: Exiting Intel Boot Agent

I don't have a recovery disk, but my live install disk is around...somewhere.

Any ideas?

---

### Post by isantop on 2011-02-16
After the System76 Logo disappears, do you see a flashing, white underscore in the upper left-hand corner of the screen?

---

### Post by eadwacer on 2011-02-16
> **isantop said:**
> After the System76 Logo disappears, do you see a flashing, white underscore in the upper left-hand corner of the screen?

I see a non-flashing white underscore briefly _before_ the logo pops up, then nothing. Goes away when logo appears, doesnt' come back when the Intel Boot Agent message shows up.

Thanks for the superfast response.

---

### Post by eadwacer on 2011-02-16
> **eadwacer said:**
> I see a non-flashing white underscore briefly _before_ the logo pops up, then nothing. Goes away when logo appears, doesnt' come back when the Intel Boot Agent message shows up.

Thanks for the superfast response.

CORRECTION: If I don't hit F12 I see a bright white underscore that fades until the logo appears, then turns to a faded, rapidly flashing underscore that continues even as I type.

BTW, I hit F-keys in the blind on startup ('cause I don't remember which one to use on this machine), and got it to open up the boot config system. It knows that the WD drive is there. I didn't change any settings. It has the boot from CD option as the second option after HD, but I put in a U8.04 DVD and it didn't boot from it. I guess it failed before it got that far.

So, I don't know if the HD failed-without-warning (the system is only nine months old or so) or if the update overwrote something. If it was the latter, I'd expect a lot more people would be noticing it.

---

### Post by isantop on 2011-02-17
This is almost certainly a Grub update problem. What version is your liveCD? If it's the same as what you have on your hard drive, then you can follow these instructions to restore the bootloader:

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

---

### Post by eadwacer on 2011-02-17
> **isantop said:**
> This is almost certainly a Grub update problem. What version is your liveCD? If it's the same as what you have on your hard drive, then you can follow these instructions to restore the bootloader:

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

Unfortunately, the CD is  8.04, and the version on the drive is.....upgraded recently.  I can check. If necessary, I can download and reburn.

Also unfortunately, I'll be tied up the rest of the day and night, so I won't get back on this till tomorrow.

Thanks for your help.
Steve

---

### Post by eadwacer on 2011-02-18
> **isantop said:**
> This is almost certainly a Grub update problem. What version is your liveCD? If it's the same as what you have on your hard drive, then you can follow these instructions to restore the bootloader:

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

OK, I am back, and I am following the instructions for updating GRUB. Problem now is, I am not sure what version of U I am running - this is a Sys76 machine from June 2010. So I downloaded 10.10 [the old live CD was 8.04 , and turned out to be for my netbook, and simply wanted to install over everything], but I get a "Exec format" error (once I used sudo), which means I am using the wrong version of Ubuntu.

I tried uname -a and got roughly (I am on a different machine, so I can't copypaste):
linux ubuntu 2.6.35-22-generic #33*ubuntu smp sun sep 19 ...2010 i686 gnu/linux

The problem is, I can't tell if some of this is the terminal talking about the CD, and I am not sure how to get to something on the HD to tell me what's there. I've been using Ubuntu for some years now, but not at the sysadmin level. Googling for help just gets me advice for when I am acutally logged into the system on the HD.

---

### Post by isantop on 2011-02-18
Actually, it's not so much the version of Ubuntu in that case. Instead it sounds like you're trying to use a 32-bit CD on a 64-bit installation. Make sure you have Ubuntu 10.10 64-bit.

---

### Post by eadwacer on 2011-02-18
> **isantop said:**
> Actually, it's not so much the version of Ubuntu in that case. Instead it sounds like you're trying to use a 32-bit CD on a 64-bit installation. Make sure you have Ubuntu 10.10 64-bit.

And I had _just_ finished downloading 32bit Jaunty! OK, back to the pipes. At this rate I'll have to upgrade my Internet service.

I doubt I finish before y'all go off for the three day weekend, so thanks, and I'll update here as I go along.

---

### Post by eadwacer on 2011-02-18
> **eadwacer said:**
> And I had _just_ finished downloading 32bit Jaunty! OK, back to the pipes. At this rate I'll have to upgrade my Internet service.

I doubt I finish before y'all go off for the three day weekend, so thanks, and I'll update here as I go along.

Well, you were right all along. It was GRUB, in the update, with a 64bit system. Everything is back to normal.

I cannot say how much I appreciate the level of support I've gotten from these forums over the years. Thanks again.

---

### Post by eadwacer on 2012-02-28
A year after my last episode, a power failure trashed my bootloader again. I fired up my backup machine and came back here, followed the link to go here

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

to fix it. And it worked like a charm. Again.

No reason you shouldn't get thanked twice.

---

