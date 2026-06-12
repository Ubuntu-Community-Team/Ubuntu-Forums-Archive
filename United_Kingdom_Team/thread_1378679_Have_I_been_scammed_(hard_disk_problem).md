---
title: "Have I been scammed? (hard disk problem)"
date: 2010-01-11
forum: United Kingdom Team
---

### Post by Pernig on 2010-01-11
Hi guys, firstly I will introduce myself. My name is James, I am 21 and from Lincolnshire. After dabbling about with Linux distributions for a few years I took the leap and am now using Karmic exclusively :D.

Secondly, apologies if this is off-topic, but didn't want to post in the main Support categories.

My problem is that I bought a hard drive from a third party seller on Amazon a couple of weeks ago so I could add it to my system and make a RAID setup. I have done this and am now up and running. Anyway, I casually went on Palimpsest Disk Utility today and noticed that not only were there 35 bad sectors, but the hard drive apparently has been turned on for 95 days!

Do you think Palimpsest could be reading wrong due to the Nvidia RAID wrapper, or have I been sold a second hand drive? The drive came in OEM packaging (ie a shiny bag) but I can't find it to see if it has been sealed or not.

Is it worth complaining and sending the disk back to the place I got it from, or should I tell Hitachi about it? Unsure on what to do on this one, as part of me can't be arsed to format and set up another RAID0, but also I don't want to risk losing all my data after being sold a drive that seems to me as if it has been sent back due to having bad sectors so early in its life.

Any advice would be appreciated, and thank you in advance. ;)

---

### Post by mocoloco on 2010-01-12
I'm not in the UK but found your thread and though I'd reply.  There's a [know issue with Palimpsest]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136"), I personally have these types of warnings come up on two different installs, so at this point I don't trust the utility.
If you are concerned about the drive I would suggest getting the manufacturer's tool and testing it, for example Seagate offers their own bootable iso that will check a drive.  Not sure if there's an easier way to check it while on a RAID.

---

### Post by Pernig on 2010-01-12
> **mocoloco said:**
> I'm not in the UK but found your thread and though I'd reply.  There's a [know issue with Palimpsest]("https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136"), I personally have these types of warnings come up on two different installs, so at this point I don't trust the utility.
If you are concerned about the drive I would suggest getting the manufacturer's tool and testing it, for example Seagate offers their own bootable iso that will check a drive.  Not sure if there's an easier way to check it while on a RAID.

Thanks for pointing this out, mocoloco. As of booting up today, I now only have 19 bad sectors according to Palimpsest. I think I will double check with the manufacturer's tool as you said.

---

