---
title: "The fastest linux downlaod managers ever"
date: 2009-07-05
forum: The Cafe
---

### Post by mbz99 on 2009-07-05
Hi guys, I tested many linux downlaod managers to find any of it alternative to IDM for windows and I found it, they are Aria2c and Axel.

I made comparison of various tools and programs and I found the fastest ones did'nt have a good GUI :mad: like Axel and Aria2.



the programs that was used:
Axel
Aria2c
Wget
DownloadThemAll
Downloader for x (D4X)


Same versions in ubuntu jaunty res.




the ISP speed:
512 KBit/second

Actual speed:

[IMG]http://www.speedtest.net/result/510672647.png[/IMG]



the test URL link:
[http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.31-rc2.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.31-rc2.bz2)




Experiment:


 Axel


How to type command:


axel -n 20 URL
-n 20 = Parallel connections (like IDM)


I typed:
axel -n 4 [http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.31-rc2.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/patch-2.6.31-rc2.bz2)

Results:
[http://img14.imageshack.us/img14/2003/24437383.jpg](http://img14.imageshack.us/img14/2003/24437383.jpg)



 Aria2c

How to type command:


aria2c -s20 URL
-s20 = Parallel connections

Results:
[http://img21.imageshack.us/img21/9674/snapshot2nsz.jpg](http://img21.imageshack.us/img21/9674/snapshot2nsz.jpg)






 Wget


How to type command:


wget -t 40 URL
-t 40 = Set number of retries to number



Result:


[http://img21.imageshack.us/img21/8013/snapshot6a.jpg](http://img21.imageshack.us/img21/8013/snapshot6a.jpg)





firefox extension DownloadThemAll


Result:

[http://img111.imageshack.us/img111/102/snapshot9.jpg](http://img111.imageshack.us/img111/102/snapshot9.jpg)





 Download for x:

Result:

[http://img44.imageshack.us/img44/6773/snapshot12t.jpg](http://img44.imageshack.us/img44/6773/snapshot12t.jpg)



Axel the fastest and Aria2c, others are not close


We need GUI for Axel and Aria2c  ,



MBZ
Engineers do everything.

---

### Post by cb951303 on 2009-07-05
aria2 has a xml-rpc server built-in now that makes writing gui frontends easier. I would like to see a gui for aria2 since it supports bittorrent too.

---

### Post by mbz99 on 2009-07-05
I download the file with IDM in MS windows.

[IMG]http://www.linuxac.org/forum/images/smiley/hah.gif[/IMG] It takes 2:55 minutes 

Axel and Aria2c are the fastest [IMG]http://www.linuxac.org/forum/images/smiley/tooth.gif[/IMG]

---

### Post by bapoumba on 2009-07-05
Moved to Cafe.

---

### Post by artir on 2009-07-05
Those programs are sh*t when u compare them to Multiget (available on the repos). Trust me, IT'S DAMN FAST!

---

### Post by mbz99 on 2009-07-05
> **artir said:**
> Those programs are sh*t when u compare them to Multiget (available on the repos). Trust me, IT'S DAMN FAST!

[http://img12.imageshack.us/img12/714/aaaavtc.jpg](http://img12.imageshack.us/img12/714/aaaavtc.jpg)
Nice GUI but not the fastest

---

### Post by Arup on 2009-07-05
Please test multiget if you can, its the closest equivalent of Windows DM and is quite fast.

---

### Post by juancarlospaco on 2009-07-05
UDP or TCP ...?

---

### Post by Gizenshya on 2009-07-05
that is not a good benchmark file to download...

It only gets about 60-80 kbps, and it is not stable.  So you are running at or near peak for the server.  In other words, your connection might not be the bottleneck...

*searches around teh interwebz)

ok, here a couple files which should be big enough.  they are also on a pretty fast server (I get 400-600 kb/sec).  The 115 mb would be best... but I understand you might not want to wait that long to download a file that big each time.  So the 35 mb or 46 mb would suffice.

~35 mb file:

[http://www.gtlib.gatech.edu/pub/sunfreeware/intel/10/binutils-2.19-sol10-x86-local.gz](http://www.gtlib.gatech.edu/pub/sunfreeware/intel/10/binutils-2.19-sol10-x86-local.gz)


the ~46 mb file:

[http://www.gtlib.gatech.edu/pub/sunfreeware/intel/10/ethereal-0.10.7-sol10-intel-local.gz](http://www.gtlib.gatech.edu/pub/sunfreeware/intel/10/ethereal-0.10.7-sol10-intel-local.gz)


the 115 mb file:

[http://www.gtlib.gatech.edu/pub/sunfreeware/intel/10/boost-1.34.1-sol10-x86-local.gz](http://www.gtlib.gatech.edu/pub/sunfreeware/intel/10/boost-1.34.1-sol10-x86-local.gz)

don't worry about what they are.  I don't know :p  I just picked them because of their size and location (on a fast server).  Any data based on downloading anything smaller than that 35 mb file is worthless IMO... and it needs to be on a fast server.

If you're going to do it, do it right ;)

also, repeat the test at least 3 time per trial and get an average.

---

### Post by pt123 on 2009-07-05
have you tried multiget

---

### Post by Viva on 2009-07-06
Try any of the downloads from Java.com instead of the kernel.org

---

### Post by moster on 2009-07-06
I do not understand. I downloaded that file (kernel patch) in 66 seconds with DownThemAll. Speed was around 200kb/s and I have 375kb/s connection.

MY DownThemAll beats ALL :D

---

### Post by mbz99 on 2009-07-07
> **juancarlospaco said:**
> udp or tcp ...?
tcp

[[IMG]http://brainstorm.ubuntu.com/idea/3828/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/3828/)

---

### Post by ssam on 2009-07-07
what about gwget.

don't some of the programs work by opening many connections to the same server. so it may make your download slightly faster, but it will slow down everyone elses. if everyone used these than everyones downloads would be slower overall.

---

### Post by timjohn7 on 2009-07-07
> **artir said:**
> Those programs are sh*t when u compare them to Multiget (available on the repos). Trust me, IT'S DAMN FAST!

I cant find Multiget in the repos... Googled it successfully though.  An essential component for me is a timer to automatically start the download at a specific time (my ISP has hugely discounted rates between 01:00 and 07:59).  I believe wget is the only package which has this.

---

