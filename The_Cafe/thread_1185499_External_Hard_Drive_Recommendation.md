---
title: "External Hard Drive Recommendation"
date: 2009-06-12
forum: The Cafe
---

### Post by Ubuntist on 2009-06-12
I'm moving from one continent to another and will be leaving my old computer behind.  It dual-boots to Ubuntu 9.04 (usually) and XP (when I have to).  The machine that I will have access to in my new location initially runs XP only.

 Essentially all of my files are on my Linux file system (ext3 with ntfs-3g installed).  The size of the (internal) hard disk is 160 GB.

So... I was thinking of buying an external hard drive so that I can bring all of my files with me.  Questions:

[LIST=1]
[*]Any recommendations on a drive to buy?  Are there any particular gotchas I need to look out for?
[*]Given that my files are mostly under Linux/ext3 now, is there a way that I will be able to access them when the external drive is plugged into an Windows-only computer?
[/LIST]
Thanks much....

---

### Post by 4th guy on 2009-06-12
> **Ubuntist said:**
> Any recommendations on a drive to buy?  Are there any particular gotchas I need to look out for?Remember: hard disks (well, any storage device actually) give you only 93% of the advertised storage space.

---

### Post by jomacintosh on 2009-06-12
Since you are switching continents, you may have a power supply issue.  I would recommend buying a USB powered external hard drive.  External Drives are available at any computer store, electronics shop, hardware store, gas station....well you get the idea.

If you are somewhat handy, you can purchase a SATA hard drive for a laptop and an external SATA 2.5" enclosure.  A 250Gig hard drive will cost around $100 and the enclosure around $40.  It takes maybe 10 minutes to build and format, and voila!  A drive that will work in any USB equipped machine.

Jo

Forgot to mention...I don't think you shoud format the drive in ext3, but FAT 16/32 because XP does not like ext3 at all

---

### Post by Vostrocity on 2009-06-12
> **jomacintosh said:**
> Since you are switching continents, you may have a power supply issue.  I would recommend buying a USB powered external hard drive.  External Drives are available at any computer store, electronics shop, hardware store, gas station....well you get the idea.

If you are somewhat handy, you can purchase a SATA hard drive for a laptop and an external SATA 2.5" enclosure.  A 250Gig hard drive will cost around $100 and the enclosure around $40.  It takes maybe 10 minutes to build and format, and voila!  A drive that will work in any USB equipped machine.

Jo

Forgot to mention...I don't think you shoud format the drive in ext3, but FAT 16/32 because XP does not like ext3 at all

Heck no, I've seen 320GB 7200RPM 2.5" drives for $50 and cases for $10. :o

---

### Post by jomacintosh on 2009-06-12
> **Vostrocity said:**
> Heck no, I've seen 320GB 7200RPM 2.5" drives for $50 and cases for $10. :o

That is true, but where I live things are more expensive than, say, the US.  Just bought a new SATA drive for my laptop 500GB = $145.00 and that is a good deal!

---

### Post by ukripper on 2009-06-12
> **Ubuntist said:**
> 
[*]Given that my files are mostly under Linux/ext3 now, is there a way that I will be able to access them when the external drive is plugged into an Windows-only computer?
[/LIST]
Thanks much....

This should work fine for you on windows machine- [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by Ubuntist on 2009-06-12
Thanks, everybody!  Looks like this is going to be easier and cheaper than I had expected.

---

### Post by HavocXphere on 2009-06-12
Remember that the USB powered drives will cost a lot more per gigabyte than the others that use a power brick & are 3"5 format.

FAT32 -> 4gb limit on individual files. I'd go with ntfs.

I would avoid the buying enclosure and then adding a hdd yourself. In my experience they don't last like those complete factory built ones. Some of the enclosures are poorly designed and trap heat. I'd go with a seagate FreeAgent...One that has both usb and firewire.

And finally: If the drive is spinning then don't touch/move it. If its not spinning then the drive head is "parked" and it can take hectic knocks...not so if its in use.

NTFS-> Always unmount/safely remove. Always.

> **ukripper said:**
> This should work fine for you on windows machine- [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
Does not work with 8.10 and after. They change the inode size and all the Win apps can't handle the new size.

---

### Post by ukripper on 2009-06-12
> **HavocXphere said:**
> 


Does not work with 8.10 and after. They change the inode size and all the Win apps can't handle the new size.

Such a shame I liked the project though.

---

### Post by Vostrocity on 2009-06-12
Here are some good deals if you're in the US.

1. [$64 free shipping 320GB 5400RPM 2.5" USB/eSATA]("http://www.newegg.com/product/product.aspx?nm_mc=AFC-TechBargains&cm_mmc=AFC-TechBargains-_-NA-_-NA-_-NA&Item=N82E16822216050")

2. If you want 7200RPM. [$9 free shipping 2.5" aluminum USB enclosure]("http://www.techsunny.com/3231620%2Ftechsunny-aluminum-usb-2.0-2.5.html")
[$70 free shipping coupon code EMCLTMN35 320GB 7200RPM 2.5" internal]("http://www.newegg.com/product/product.aspx?nm_mc=AFC-TechBargains&cm_mmc=AFC-TechBargains-_-NA-_-NA-_-NA&Item=N82E16822136280")

---

