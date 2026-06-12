---
title: "Raid 5 read speed very slow via Samba"
date: 2009-01-30
forum: Server Platforms
---

### Post by deadball on 2009-01-30
Hey guys.

I've got a problem with my new Home-Fileserver.

The reading speed of my encrypted Software Raid 5 is very low when i access it with my Vista PC.

When i test with hdparm or dd, the speed is good (hdparm: reading about 70 Mb/s; dd writing from /dev/zero: about 40-50Mb/s).

Via Samba i reach about 32 Mb/s writing. But reading is slow - ~10 Mb/s.

My Specs:
- Asrock k10n78 with geforce 8200 chipset
- AMD 4850e (2.5ghz, dualcore)
- 2gb ram
- 3x 400 GB SataII HDD (Storage)
- 1x 300 GB IDE HDD (System)
- Gbit LAN

The three Sata HDDs are combined through a Software Raid 5 via mdadm.
This Raid is encrypted by cryptsetup LUKS and this device is a PV for the LVM.

I thought the CPU was the bottleneck, but actually the cpu-load goes only up to max 70% and falls down to ~ 12%. This repeats periodically..

Iowait is at ~5% (<- is that good or bad?:D)

Its clear, that it needs some power to write data to the Raid. But why is reading so slow?

Im using an updated Ubuntu 8.10.

I think it's a problem of Samba.. Maybe i can tweak it a bit?

Hopefully my english is not too bad and you can understand it :)

Best regards, thanks,
db

---

### Post by handy on 2009-01-30
I can't really offer you much assistance, but you may find some of this thread quite interesting, I know I did:

*_[http://ubuntuforums.org/archive/index.php/t-643138.html](http://ubuntuforums.org/archive/index.php/t-643138.html)_*

---

### Post by deadball on 2009-01-30
Nice thread. Thank you

I'll try. Does anybody else have an idea?

Best regards

---

### Post by deadball on 2009-02-02
Am I allowed to push my post after 2 days? : / ;)

---

### Post by HermanAB on 2009-02-02
Samba *is* slow.

There is nothing much you can do about it, beyond writing a complaint letter to Bill Gates.

If you want something faster, easier and less problematic, use NFS.

Cheers,

Herman

---

### Post by deadball on 2009-03-09
I need to push this thread again.

I installed a ftp Server (vsftpd). 

Uploading works with 30 MiB/sec. Fine so far, 100% CPU utilization @ 2500 Mhz.

But re-downloading is not fast enough. It only reaches ~ 13 MiB/sec. What the ****? Cpu @ medium utilization, only 1000 Mhz. If i stop powernowd, it has 2500 Mhz again, but no change in reading speed.

What could THAT be? Were is the bottleneck? :  /


Thanks guys

---

### Post by cariboo on 2009-03-09
You didn't mention which server version you are using, I found that with Hardy (8.04) samba was so slow that I was considering changing back to Debian. I decided to give Intrepid (8.10) a try before switching, I was happy to find that I now average 70-80Mbps both uploading and downloading using samba.

Jim

---

### Post by deadball on 2009-03-10
Well thanks.

But i did mention it in first post. Ubuntu 8.10.

And as i wrote, it's not only a problem of samba : /

---

### Post by fjgaude on 2009-03-10
Say, what does **hdparm** show for the array:

```
sudo hdparm -tT /dev/md[n]
```

That might tell something.

---

### Post by deadball on 2009-03-10
Crypted partition @ 1 ghz

```

/dev/vgStorage/share:
 Timing cached reads:   1152 MB in  2.00 seconds = 575.82 MB/sec
 Timing buffered disk reads:  100 MB in  3.01 seconds =  33.17 MB/sec

```

crypted partition @ 2.5 ghz ; 1st run

```

/dev/vgStorage/share:
 Timing cached reads:   1532 MB in  2.00 seconds = 765.91 MB/sec
 Timing buffered disk reads:  136 MB in  3.04 seconds =  44.74 MB/sec

```

crypted partition @ 2.5 ghz; 2nd run..

```

/dev/vgStorage/share:
 Timing cached reads:   1914 MB in  2.00 seconds = 957.54 MB/sec
 Timing buffered disk reads:  162 MB in  3.00 seconds =  53.99 MB/sec

```

Md0 @ 2.5 ghz
```

/dev/md0:
 Timing cached reads:   1914 MB in  2.00 seconds = 956.83 MB/sec
 Timing buffered disk reads:  326 MB in  3.01 seconds = 108.40 MB/sec

```

always full cpu %%

edit:

System drive (1 single Pata Hdd...)
```

/dev/vgSystem/root:
 Timing cached reads:   1910 MB in  2.00 seconds = 955.07 MB/sec
 Timing buffered disk reads:  176 MB in  3.03 seconds =  58.12 MB/sec

```

the LV home is in the vgStorage, too:
```

/dev/vgStorage/home:
 Timing cached reads:   1900 MB in  2.00 seconds = 950.50 MB/sec
 Timing buffered disk reads:  166 MB in  3.00 seconds =  55.26 MB/sec

```

```

sudo dd if=/dev/zero of=.null bs=1M count=2000
2000+0 records in
2000+0 records out
2097152000 bytes (2,1 GB) copied, 32,1893 s, 65,2 MB/s

```

```

dd if=.null of=/dev/null
4096000+0 records in
4096000+0 records out
2097152000 bytes (2,1 GB) copied, 38,5497 s, 54,4 MB/s

```

is something cached there?

BUT still faster writing to home than reading from home? Why :D

---

### Post by deadball on 2009-03-13
No idea, guys? :)

---

### Post by HermanAB on 2009-03-13
Howdy,

Upgrade Samba to the latest version to get rid of the worst slowness bugs.  If necessary, download it from the Samba web site and compile it yourself.

However, Samba is slow by design.  The only real solution is to avoid using it.

Cheers,

Herman

---

### Post by deadball on 2009-03-13
Thank you.. 

but did you read post #10? It's not Samba I think. Its the file system or raid or lvm.

Look @ the hdparm values..

---

