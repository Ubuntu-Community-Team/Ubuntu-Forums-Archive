---
title: "Looking to buy a new laptop hard drive, wanting opinions"
date: 2011-05-29
forum: The Cafe
---

### Post by Brushstroke on 2011-05-29
I have a Toshiba Satellite laptop that I've been wanting to do a few upgrades to. Number one is the hard drive. It has a 250GB SATA drive in it running at 5400 RPM. I want to get something with double the capacity and at 7200 RPM, 16 MB cache. Pretty basic specs, something that I could get for between $70 and $100. But I'm also looking for the most energy efficient piece of hardware. 

So, opinions on the most energy efficient laptop hard drive with these specifications? What brand should I go with? Seagate, Western Digital, Samsung, Hitachi, something else entirely...?

Thanks!

---

### Post by wizard10000 on 2011-05-29
> **Brushstroke said:**
> I have a Toshiba Satellite laptop that I've been wanting to do a few upgrades to. Number one is the hard drive. It has a 250GB SATA drive in it running at 5400 RPM. I want to get something with double the capacity and at 7200 RPM, 16 MB cache. Pretty basic specs, something that I could get for between $70 and $100. But I'm also looking for the most energy efficient piece of hardware. 

So, opinions on the most energy efficient laptop hard drive with these specifications? What brand should I go with? Seagate, Western Digital, Samsung, Hitachi, something else entirely...?

Thanks!

I put this one in my netbook and have been very happy with it.  Dense platters, large cache, fast spindle speed.  Reads and writes consistently ~100mb/s

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822152236](http://www.newegg.com/Product/Product.aspx?Item=N82E16822152236)

Real world benchmarks -

```
wizard@wizard-netbook:~$ sudo -i
[sudo] password for wizard:
root@wizard-netbook:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1226 MB in  2.00 seconds = 613.03 MB/sec
 Timing buffered disk reads: 312 MB in  3.01 seconds = 103.78 MB/sec

root@wizard-netbook:~# dd bs=1M count=2560 if=/dev/zero of=/tmp/test conv=fdatasync && rm -rf /tmp/test
2560+0 records in
2560+0 records out
2684354560 bytes (2.7 GB) copied, 27.2035 s, 98.7 MB/s

root@wizard-netbook:~# ./seeker /dev/sda1
Seeker v2.0, 2007-01-15, http://www.linuxinsight.com/how_fast_is_your_disk.html
Benchmarking /dev/sda1 [29297MB], wait 30 seconds..............................
Results: 105 seeks/second, 9.44 ms random access time

```

---

