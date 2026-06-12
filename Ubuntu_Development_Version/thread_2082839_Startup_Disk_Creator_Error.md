---
title: "Startup Disk Creator Error"
date: 2012-11-10
forum: Ubuntu Development Version
---

### Post by sparker256 on 2012-11-10
I am getting this error when trying to use Startup Disk Creator.

An error occurred while talking to the udisks service

Anyone have this working correctly?

Bill

---

### Post by jppr on 2012-11-10
I have same error and issue :popcorn:

---

### Post by mc4man on 2012-11-10
It's a crash of usb-creator-helper, you'd likely see the .crash in /var/crash (root owned

If trying to file on, the report may be uploaded somewhere but at least here there will be no typical pop up, launchpad, ect.
(thanks alot, see you later ??

---

### Post by jerrylamos on 2012-11-11
Which startup disk creator?  Raring?  Quantal?  Precise?  Lucid?

---

### Post by jppr on 2012-11-12
> **jerrylamos said:**
> Which startup disk creator?  Raring?  Quantal?  Precise?  Lucid?
What you think... Is that a thing now difficult to determine which version of ubuntu, this forum might that be?

---

### Post by cariboo on 2012-11-12
> **jppr said:**
> What you think... Is that a thing now difficult to determine which version of ubuntu, this forum might that be?

Historically, this sub-forum hasn't been opened until a week or so after UDS-X, it's only since I became an Admin that it's been opened earlier. Usually there isn't much happening the first week after UDS, but for many of the devs it was fairly close to home this time, so they didn't need a week to recover from their UDS hangover. :).

On top of that, for many of us, Startup Disk Creator was broken in Quantal too, so jerrylamos' question isn't out of line at all.

---

### Post by sparker256 on 2012-11-12
Then I will make it clear I am asking about Startup Disk Creator for Raring.

Bill

---

### Post by cecilpierce on 2012-11-12
It has not worked for me in a long time and cant't write other distros. Unetbootin has its ups and downs to .
Ive had problems with Brasero to so I use k3b when all else fails.

---

### Post by jerrylamos on 2012-11-12
> **jppr said:**
> What you think... Is that a thing now difficult to determine which version of ubuntu, this forum might that be?

When making a raring.iso usb to test the raring.iso I use whatever works.  

I'd really expect someone starting to try raring would be running either precise LTS or quantal to make their first raring.iso.

Testing the raring.iso startup disk creator is a different test.

Personally I find it easier and faster just to boot the .iso from the hard disk.  Zsync, reboot, try the .iso, if it works, install.  Faster for me than creating USB's or DVD's.  I've had poor luck with R/W DVD's and with the .iso's changing fast I don't want a pile of DVD's on the floor.  I will use a USB to take the test .iso to a different pc, or just copy the .iso over the local network.

---

### Post by ventrical on 2012-11-12
> **sparker256 said:**
> Then I will make it clear I am asking about Startup Disk Creator for Raring.

Bill

  I have had intermittent errors on all my boxes (all the way from Lucid) with SDC. As it stands now on one of my main machines , sometimes it works, sometimes it crashes. In otherwords, it's useless. What I do is I use this old version of Oneric Ocelot on an old Dell Opti and it  has yet to fail.

---

### Post by ventrical on 2012-11-12
It's worse now since the update...

---

### Post by nm_geo on 2012-11-14
I filed a bug on this a few days back. Join if you want.

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1077766](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1077766)

---

### Post by mc4man on 2012-11-14
Finally filed a bug on this based on the crash
(got apport to actually use LP on crashes , not sure if this is desired anymore vs just having it uploaded to some whoopsie db.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1078810](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1078810)

Maybe I'll start a thread on apport, possibly someone knows...
(hesitant to post how to get apport to file/open LP reports if it's not wanted anymore

---

### Post by dentaku65 on 2012-11-23
The only way that I'm able to use usb-creator is to format the usb-key in FAT32 then:
```
sudo usb-creator-gtk --iso=/path/to/iso
```
Then select Erase Disk button (wait a moment that the disk will be available again), choose the desired extra space and finaly click on Make Startup Disk button
Done!

In this way I'm able to put the distro isos on usb-key since Lucid; tried everything else without luck.

by

---

