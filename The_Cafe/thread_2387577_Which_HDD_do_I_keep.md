---
title: "Which HDD do I keep???"
date: 2018-03-20
forum: The Cafe
---

### Post by mr.travo on 2018-03-20
I have been thinking about this and it's kind of funny. I have an older Dell Precision T3500 that I got at a really good price. So far I have maxed out the ram (24gb) and that's about it. The ram is maxed out with two different brands of memory (that I had on hand) and it's working, but I will upgrade it "correctly" after I upgrade the HDD. 

What I have in here is a 500gb 7200rpm WD BLue (WD5000AAKX) and I also have a spare 2.5" WD Blue 1TB 5400rpm (WD10JPVT) on my shelf collecting dust. The 500gb has a 16mb buffer and the 1tb has a 8mb buffer. I am wondering which one I should go with as a secondary. Will there be much of a speed difference between the two? I am replacing the 500gb (current main drive) with an Intel 256gb SSD drive. I know the question is kind of apples and oranges but I am looking at using the secondary drive as a work area to compile and test android builds out on. 

Thanks!!!

T

---

### Post by oldfred on 2018-03-20
Test them and see.

these tests are from two totally different systems:

 Newer hard drive:
sudo lshw -C Disk -short
1TB WDC WD10EZEX-00B
sudo hdparm -t /dev/sdb4
 Timing buffered disk reads: 514 MB in  3.00 seconds = 171.16 MB/sec 

      
 Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec

---

### Post by mr.travo on 2018-03-21
Awesome! I am writing that down in my notes as a great way to test! I tested the current main drive and got 
```

/dev/sda:
 Timing buffered disk reads: 192 MB in  3.02 seconds =  63.62 MB/sec

```

The 1tb sare drive is in a usb 3.0 external case right now. I think it would give a false reading that way, correct?

Thank you for that bit of info OldFred, much appreciated!!

T

---

### Post by oldfred on 2018-03-21
USB is slower than SATA.
Also whether USB2 or USB3.

 [http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2)
The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller
[http://en.wikipedia.org/wiki/USB3#USB_3.0](http://en.wikipedia.org/wiki/USB3#USB_3.0)
SuperSpeed (USB 3.0) rate of 4800 Mbit/s (~572 MB/s). Renamed USB 3.1 Gen 1
But speeds are more limited by devices at each end.

---

### Post by iscollin on 2018-04-07
True, true I'm new here but I'm really getting into ubuntu SATA is faster definitely but It depends on your needs it would definitely bottleneck and create a slight variable in your testing

---

### Post by kurt18947 on 2018-04-07
There is also a speed test utility in Disks (gnome-disks)found in Ubuntu-gnome 16.04 and I assume in 17.10/18.04.

---

### Post by sp40140 on 2018-04-08
You can try the utilities mentioned above. In my experience though, the higher RPM drive is usually better (provided all other things are same like port specs).
If you are going with 256 Gig SSD, I suggest you partition that SSD and use one of the partitions on the SSD for compiling.
The performance difference is night and day from platter drive to even the slowest SSD.
you can just add / keep the other two in there for misc data / backups and such.

---

