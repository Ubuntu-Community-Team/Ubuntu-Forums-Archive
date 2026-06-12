---
title: "Advice on External Drives"
date: 2008-03-17
forum: The Cafe
---

### Post by the beak on 2008-03-17
Hi,

I'm looking to add an external hardrive to my laptop. I'm using a fairly old machine, and as I have Xubuntu working fine on it I can't be bothered setting it up on another one, so I would like add an external hardrive.

Which ones are the easiest/best for using with xubuntu/ubuntu?

---

### Post by mips on 2008-03-17
Western Digital or Seagate are good brands to look for.

I'm not sure if you want to install ubuntu on the external drive or just use it as a data drive but keep the following in mind:

1. Depending on how old your machine is it might only support the older USB v1.1 at 12Mb/s which is slow.
2. It's also not always possible to boot off external hard drives on older computers.

I would advise you to check the specs on you pc with regards to the above two issues.

---

### Post by insane_alien on 2008-03-17
any should work, just don't expect blinding performance out of a drive on USB.  especially ifit is USB1.1 should still be good to watch videos off though.

---

### Post by billgoldberg on 2008-03-17
I have a 500gb Western Digital elements hdd and have had no problems with it on ubuntu (so xubuntu shouldn't have any problems).

I however don't like the hard drive that much because it needs to be jacked into the electricity jack. So that might be something to look out for (ensure that it only needs a usb cable plugged in).

A friend of mine has a Lacie external harddrive and it also works well under ubuntu.

---

### Post by mips on 2008-03-17
> **billgoldberg said:**
> 
I however don't like the hard drive that much because it needs to be jacked into the electricity jack. So that might be something to look out for (ensure that it only needs a usb cable plugged in).


I might be wrong but I don't know of any external 3.5" that does not need external power. The 2.5" drives can usually just get their power off the USB port though.

---

### Post by prshah on 2008-03-17
> **mips said:**
> I might be wrong but I don't know of any external 3.5" that does not need external power. The 2.5" drives can usually just get their power off the USB port though.

Nope, not wrong; 3.5" disk boxes need an external power source.

2.5" drives on the other hand will run off USB power, but in a laptop, you may have to use 2 USB ports (the drive casing will come with a "Y" cable) since one port may not provide enough power. 

Note that the "Y" cable does NOT double your transfer speed as advertised by many people. It just supplies more power to the drive if one port cannot supply enough. Most laptops and unpowered hubs cannot supply enough.

---

### Post by billgoldberg on 2008-03-17
> **mips said:**
> I might be wrong but I don't know of any external 3.5" that does not need external power. The 2.5" drives can usually just get their power off the USB port though.

I didn't know that, you learn something new everyday.

---

### Post by kiko72 on 2008-03-17
I boot into Ubuntu from a 3.5" external (yup, needs power) and everything works great. Actually, I'm shocked at how well everything has been going with my new OS over the past three weeks!
 
But here's my noob question on this topic: I just got a LaCie 120g external 2.5" so I can run off USB power alone. My XP can see it just fine, but how do I get Ubuntu to recognize it? I really do want to use it for both OSs, and since it's FAT32 - I should be able to, right?

I'm using 7.04, by the way.

My little USB pendrive pops right onto the desktop whenever I plug it in (much to my amazement!), but I'm really not sure what to do about an actual external HD.

Please excuse the noobness if this is really some kind of easy mount question or something. I guess I don't really know much about mount either - since I'm really crawling out from under the Windows rock for the fist time.

---

### Post by mips on 2008-03-17
> **kiko72 said:**
> 
But here's my noob question on this topic: I just got a LaCie 120g external 2.5" so I can run off USB power alone. My XP can see it just fine, but how do I get Ubuntu to recognize it? I really do want to use it for both OSs, and since it's FAT32 - I should be able to, right?

I'm using 7.04, by the way.

My little USB pendrive pops right onto the desktop whenever I plug it in (much to my amazement!), but I'm really not sure what to do about an actual external HD.

I should 'just work' like your pendrive does.

---

### Post by kiko72 on 2008-03-18
> **mips said:**
> I should 'just work' like your pendrive does.

Well, not so far. I'm asking around. Everyone seems to be talking about gparted, which I strangely don't have. Maybe that will help.

---

### Post by dca on 2008-03-18
I spend the extra money and get a 3.5" ext HDD enclosure.  Looks just like a regular external but it allows you to remove screws and replace HDD w/ different IDE as needed...

---

### Post by lespaul_rentals on 2008-03-18
My Seagate FreeAgent 250GB external hard drive works great with Ubuntu.

---

### Post by ksennin on 2008-03-18
I have plugged into my ubuntu box both a single-drive USB external enclosure (with removable 40gb hd) and a Venus T4U 4-drive usb enclosure containing a 500gb drive and two 250gb ones.  All were recognized inmediately without need for any tinkering.  All executed copy/transfer operations much faster than when plugged into my office XP Pro pc.

Maybe the external you are using uses some propietary software interface, designed for backup purposes, like I think the WD MyBook ones use, which automatically looks for windows filesystems.  In that case, you may need to do a full format and make it a "bare" drive.

Jorge

---

### Post by kman14 on 2008-04-24
> Maybe the external you are using uses some propietary software interface, designed for backup purposes, like I think the WD MyBook ones use, which automatically looks for windows filesystems. In that case, you may need to do a full format and make it a "bare" drive.


i have just bought a WD mybook 320gig and seem to be having that same problem. i was wondering if you could point me in the right direction in regards to  re-formatting the hard drive.
it would only be used for linux.

thanks.

---

### Post by mips on 2008-04-24
> **kman14 said:**
> i have just bought a WD mybook 320gig and seem to be having that same problem. i was wondering if you could point me in the right direction in regards to  re-formatting the hard drive.
it would only be used for linux.

thanks.

Plug the drive in, open GParted, format it or erase existing partitions. I would recommend using Ext3 file system on an external drive, this way you could also access the data from a windows pc (with the help of a driver) which is cool if you want to use it on someone else computer at times.

---

### Post by kman14 on 2008-04-24
thanks for your reply Mips.
that seems to have done the trick.....except now the disk has a "lost and found" folder when i open it, (i can't open the folder it says i don't have permission) and i can't copy anything onto the disk.
is this something with me needing to be "root"?

thanks.

---

### Post by timo1023 on 2008-04-24
Do not buy a Seagate External. They do not provide Linux support, and their power saving features do not work under Linux.

[http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/](http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/)

I've read about some workarounds; however, I would simply not buy from this company out of general principle.

EDIT: Looks like you have already bought an HD. I guess I'll just leave this post here for future reference.

---

