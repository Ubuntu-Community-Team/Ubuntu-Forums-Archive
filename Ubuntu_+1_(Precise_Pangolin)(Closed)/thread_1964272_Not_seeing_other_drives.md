---
title: "Not seeing other drives"
date: 2012-04-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by swright007 on 2012-04-23
I tried installing 12.04B with updates (a FULL install) to a flash drive and when I booted off of it, in nautilus, I could not see the laptop's Hard Drive.  It could easily see the DVD drive and any other flashdrive.... 

I thought this was a fluke, so I booted off a live DVD copy and it, too, had the same failure.   In every other version of Ubuntu I have ever used, seeing the other drives on your system even booting live, was a major draw for me.

Is anyone else experiencing this?

---

### Post by swright007 on 2012-04-23
I tried again on a regular desktop and did not have that trouble.   The Laptop that I experienced that with was a Toshiba Satellite L355-S7915

---

### Post by arpanaut on 2012-04-23
Some possibilities, Is the drive a ntfs drive that was not unmounted properly or a Win install that has issues?
i.e. had a crash just prior to being booted to the flash drive or CD.

If it is a Win system that was suspended or hibernated, then Ubuntu will not detect the drive.

Something must be out of order with the drive because I have only seen drives not detected when something is wrong with the file system.

---

### Post by swright007 on 2012-04-24
Hahahaha... I have had some sleep now!   It seems that, since it was a portable laptop, I encrypted the hard drive to prevent data from being misused if I lost possession of the computer.   This accounts for why it doesn't readily show up in nautilus.

Thank you Arpanaut for your assistance.

---

