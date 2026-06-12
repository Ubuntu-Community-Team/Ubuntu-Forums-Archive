---
title: "USB 128 GB Stick"
date: 2011-02-22
forum: Server Platforms
---

### Post by Vegan on 2011-02-22
I see USB sticks on eBay are cheaper than ever. Not very fast but 20 MB a second is not that bad.

My current web server is a tad oldish but if I was to boot from the USB stick which the BIOS supports, would one of those be of any help to my server?

Lots of room with 128 GB

---

### Post by James78 on 2011-02-22
Beware of those 128GB flash drives on eBay. A lot of them are faked and counterfeit. A few 128GB flash drives really do exist, but that doesn't change the fact that it's really bad on eBay.

[http://www.brighthub.com/computing/hardware/articles/33110.aspx?p=2](http://www.brighthub.com/computing/hardware/articles/33110.aspx?p=2)
[http://sosfakeflash.wordpress.com/](http://sosfakeflash.wordpress.com/)

---

### Post by Vegan on 2011-02-22
I have noticed, but eBay does insure the transaction.

I can make a program to verify a USB stick capacity easily.

Write 128 GB of data, if it fits, pass else fake USB IDENT table.

---

### Post by James78 on 2011-02-22
> **Vegan said:**
> I have noticed, but eBay does insure the transaction.

I can make a program to verify a USB stick capacity easily.

Write 128 GB of data, if it fits, pass else fake USB IDENT table.
1. So far as I have read, eBay is actually trying to cover most of that up, and they wouldn't do anything to take down this one counterfeiting ring leader for 2 years. The people had to be extremely persistent.
2 & 3. That'd definitely verify it, but you'd have to buy the device first, and the (likely) fake manufacturer would refuse to refund (and eBay would at least 75% likely do nothing I think).

Anyways, not trying to start a flame war here, I just wanted you to know about that. :)

To answer your question.. When you say boot from the USB stick, you mean like a liveCD, e.g. have the OS on the stick? If that's what you mean, in my experience, booting up from that has actually been slower, although don't be completely fooled; running your entire OS in RAM really does speed things up.

Note: Running it in RAM does increase the time for the system to startup, just fyi.

(Hint: To run your OS in RAM. [http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694))

---

### Post by elico on 2011-02-23
well the only benefit for any USB drive is the constant speed of 20MBs or what so ever.
means that on HD you have a jitter of finding and serving splitted data on the drive surface.
if you do want to speed up your system it very simple to do so using RAID and\or RAM DRIVE.

---

### Post by Vegan on 2011-03-05
I am watching the trade in USB sticks.

The low capacity ones seem to be dirt cheap now and they seem to be relatively free of problems.

Sadly fakes and rip-offs are a growing part of life.

---

### Post by HermanAB on 2011-03-05
Hmm, the trouble is that 64 GB and 128 GB USB memory sticks do not exist yet.  So if you see one for sale, it most probably isn't...

---

### Post by windependence on 2011-03-06
I don't see what all the fuss is over boot time since my servers rarely, if ever get booted unless I need to make a kernel level change. Once you are booted, if you have enough RAM, you are not accessing the stick anyway. My NAS and VMware boxes all run off Compact flash memory and the performance is as goos as if not better than hard disks. Why use a hard disk when a 4GB flash card is all you need to load the OS and run the machine?
 
-Tim

---

### Post by BkkBonanza on 2011-03-06
I've run a Ubuntu server as a router for almost a year booting from USB 4 GB flash. It works fine and I haven't had any issues. Good ones can get about 30MB/s (mine) and poor ones < 9MB/s. It doesn't really matter much for your typical server since the disk caching built into Linux is very good and most disk accesses get cached well enough. If you really want speed then pick up a Samsung SSD drive. I got a 30GB one for about $55 on ebay and it's been working great (SATA, faster than USB, though not as fast as my Vertex in my notebook, much cheaper).

The problem with buying fake flash memory on ebay is that your best case scenario if it is fake is filing a paypal dispute and paying to return the item with tracking to the supplier. After weeks and weeks you *may* get a refund but it will cost you a lot of hassle and some money for a trackable return shipment. Depending on the cost for the item often times the seller counts on you not wanting to bother returning the item due to postage fees. Don't send it back without tracking or they'll just claim it wasn't received and you won't get the refund (and have already given back the product). If you are suspicious of the validity of what's offered then DO NOT buy it. I say this as an ebay user for more than 10 years and over 1800 feedback. Do waste your time on items that appear to be too good to be true.

---

### Post by Vegan on 2011-03-06
I was looking at a USB stick for security repairs on unbootable machines.

I agree a smaller stick is fine, but I wanted to use security software in addition to the desktop

The advantage is it can be updated but the disadvantage is the device is not easily protected.

---

### Post by James78 on 2011-03-09
> **HermanAB said:**
> Hmm, the trouble is that 64 GB and 128 GB USB memory sticks do not exist yet.  So if you see one for sale, it most probably isn't...
Actually, they do exist.
[http://www.tomshardware.com/news/kingston-usb-drive-128gb-stick,8083.html](http://www.tomshardware.com/news/kingston-usb-drive-128gb-stick,8083.html)

---

### Post by Grenage on 2011-03-09
> **James78 said:**
> Actually, they do exist.
[http://www.tomshardware.com/news/kingston-usb-drive-128gb-stick,8083.html](http://www.tomshardware.com/news/kingston-usb-drive-128gb-stick,8083.html)

Indeed; as do [256GB]("http://www.saverstore.com/product/20069747/7725665/Kingston-DataTraveler-310-256GB-USB-Flash-Memory-Drive") sticks.

---

### Post by James78 on 2011-03-09
> **Grenage said:**
> Indeed; as do [256GB]("http://www.saverstore.com/product/20069747/7725665/Kingston-DataTraveler-310-256GB-USB-Flash-Memory-Drive") sticks.
Insane! I thought it was only up to 128GB.. That's so awesome lol. And to think a 256GB SSD costs more... (Although to be fair, they're made to have faster read/write than USB sticks too, plus other things)

Tried to search for some 512GB USB sticks. Something I noticed.. They all seemed to be from Hong Kong and China lol. Not something I'd trust haha. Next thing there's going to be "2TB USB sticks", but take a look at where they were made... China right? (Pun intended)

---

### Post by Grenage on 2011-03-09
> **James78 said:**
> Insane! I thought it was only up to 128GB.. That's so awesome lol. And to think a 256GB SSD costs more... (Although to be fair, they're made to have faster read/write than USB sticks too, plus other things)

Yup, I've got a few 16GB drives, but can't quite justify the cost of anything that large. ;)

---

### Post by KegHead on 2011-03-09
Hi!

64 & 126 gb sticks?

I've used 8gb for years and can't fill them w/data!

KegHead

---

### Post by Vegan on 2011-03-12
I have searched around and the Kingston brand is the one I have seen.

At present I have 2 USB hard disks that I am using for backup for want of an application.

The old one is 160 GB and the new one is 320 GB.

I recently bought a used netbook, works fine. Has a 160 GB disk but I was considering using the 320 on it or maybe a bigger disk.

---

### Post by KegHead on 2011-03-12
Hi!

Disks or sticks?

KegHead

---

### Post by Vegan on 2011-03-12
they are hard disks, repurposed notebook disks

---

### Post by KegHead on 2011-03-13
Hi!

I see.

KegHead

---

