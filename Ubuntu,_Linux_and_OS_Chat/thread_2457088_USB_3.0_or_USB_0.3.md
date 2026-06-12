---
title: "USB 3.0 or USB 0.3?"
date: 2021-01-25
forum: Ubuntu, Linux and OS Chat
---

### Post by xinuzi on 2021-01-25
Question: "Why does usb 3.0 and beyond often not render what it promises?"

Just an example:

2 FAT32 usb-sticks, both so-called usb 3.0, results from /etc/mtab compared to Ubuntu (20.04) Disks Benchmark :

Emtec 3.0 stick:
/dev/sdb/media/me/Emtec62GB vfat rw,nosuid,nodev,relatime,uid=mybr,gid=mygrnr,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0

Disks -> Benchmark -> readspeed: 25.8 Mb/s

Lexar 3.0 stick:
/dev/sdb/media/me/Lexar128GB vfat rw,nosuid,nodev,relatime,uid=mynr,gid=mygrnr,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro 0 0

Disks -> Benchmark -> readspeed: 122.6 Mb/s

Of course both of the disks blue and on the same blue usb-port.
Same result on whichever other blue usb-port.
Any other formatting (NTFS, EXT4), same result.

Emtec = turtle
Lexar = batman (but still not superman).

Anyone in Outer (Linux) Space?

('remou nt' = 'remount')

---

### Post by crip720 on 2021-01-25
Would try and google what speeds are expected out of each stick, they might just have slow speeds.  Then you can probably test/google what speed your USB port is capable of.  After these two, then you will have an idea where or if you have a problem.  Imagine neither stick is their top of line(expensive) models.

---

### Post by TheFu on 2021-01-25
USB is a bus. It provides a theoretical max throughput only.  It is usually shared by multiple devices.
Storage devices could be faster than usb2, but few were faster than usb3 until NVMe SSDs.

put a bicycle on a super highway and it will still be limited to the speed of the bicycle, not the 200 kph that the highway supports.

Storage performance has always been impacted by the file system used.  Fat32 is slow for multi-gigabyte.  Flash storage comes in many types, different speeds, for different prices. We have lots of choices. Spend less and usually get poor performing flash storage, with cheaper flash controllers.  There are many fakes on the market too.

---

### Post by Autodave on 2021-01-25
I have a 1 TB USB stick that will only format to a max of 8 gig.  After that, this "USB 3.0" stick takes about 15 minutes to write a 1 gig file.  Made in China might have something to do with it.

---

### Post by TheFu on 2021-01-25
> **Autodave said:**
> I have a 1 TB USB stick that will only format to a max of 8 gig.  After that, this "USB 3.0" stick takes about 15 minutes to write a 1 gig file.  Made in China might have something to do with it.

Likely a fake - with modified firmware to appear as 1TB, but probably really only 8GB.

I stopped buying from online retail due to the fakes.  Walking into a box store and buying usually ensures someone cares about the supply chain. There have been sub-$10 usb3 storage devices here at the big-blue-box store for a few years if spectacular performance isn't important. If performance matters, I expect to pay 2-3x more.

---

### Post by Irihapeti on 2021-01-25
*Thread moved to **Ubuntu, Linux and OS Chat**, as it's not really a request for support.*

---

### Post by mastablasta on 2021-01-26
> **TheFu said:**
> There have been sub-$10 usb3 storage devices here at the big-blue-box store for a few years if spectaclar performance isn't important. If performance matters, I expect to pay 2-3x more.

here they have a sale every year of USB and SD. when they have it, they would normally cost less than 10 EUR and they can go run out fast. i buy a few each time and keep some small stock. i only bought branded ones like Sony and Sandisk. They proved themselves well, come with a 2 or 3 year warranty and i had no issues with them so far. they are the bulky ones and not meant as USB for key chain. those are a bit more expensive as they are more resistant to scratches and such. so i have only one of those for a couple of years now.

---

