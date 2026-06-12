---
title: "1TB SSD, R/W @ 500MB/s &amp; 600MB/s !!!"
date: 2009-03-09
forum: The Cafe
---

### Post by mips on 2009-03-09
Holy cow, I would love to have one...

[http://www.tomshardware.com/news/ocz-ssd-soild-state-terabyte-madshrimps,7200.html](http://www.tomshardware.com/news/ocz-ssd-soild-state-terabyte-madshrimps,7200.html)
[http://www.madshrimps.be/?action=getarticle&number=2&artpage=3980&articID=911](http://www.madshrimps.be/?action=getarticle&number=2&artpage=3980&articID=911)

What are the current fastest SSDs in the 8-16GB size range (non raid)?
Links to reviews/comparisons would be nice. I might be interested :)

---

### Post by Muffinabus on 2009-03-09
If only I had $1500 to throw away...

---

### Post by miegiel on 2009-03-09
600MB/s :D I can beat that```
sudo hdparm -T /dev/sda1

/dev/sda1:
 Timing cached reads:   1712 MB in  2.00 seconds = 856.32 MB/sec

```

---

### Post by mihai.ile on 2009-03-09
> **miegiel said:**
> 600MB/s :D I can beat that
you mean you can beat 600MB/**2**s

because

> **miegiel said:**
> 1712 MB in  **2.00** seconds = 856.32 MB/sec

---

### Post by Muffinabus on 2009-03-09
> **mihai007 said:**
> you mean you can beat 600MB/**2**s

because

What?  1712/2 = 856

---

### Post by Eisenwinter on 2009-03-09
```
Timing cached reads:   1746 MB in  2.00 seconds = 873.41 MB/sec
```

---

### Post by Grant A. on 2009-03-09
My 1TB HDD gets 3GB/s. However, this is quite an achievement for the SSD's storage capacity. I just hope that the write limitation problem gets fixed, though.

---

### Post by zmjjmz on 2009-03-09
Do want.

---

### Post by kevin11951 on 2009-03-09
```
/dev/sda:
 Timing cached reads:   5766 MB in  2.00 seconds = 2889.60 MB/sec

```

I can see where this thread is going ;)

---

### Post by mips on 2009-03-10
> **Grant A. said:**
> My 1TB HDD gets 3GB/s. 

rotflmao. And my name is Santa Clause.

As for all you other smart alec's here, real world performance is not what you are posting.

[IMG]http://www.madshrimps.be/articles/OCZ-Z-Drive-1000GB-SSD-Performance-Preview-at-Cebit-jmke-25854.jpg[/IMG]

---

### Post by .Maleficus. on 2009-03-10
> **mips said:**
> Holy cow, I would love to have one...

[http://www.tomshardware.com/news/ocz-ssd-soild-state-terabyte-madshrimps,7200.html](http://www.tomshardware.com/news/ocz-ssd-soild-state-terabyte-madshrimps,7200.html)
[http://www.madshrimps.be/?action=getarticle&number=2&artpage=3980&articID=911](http://www.madshrimps.be/?action=getarticle&number=2&artpage=3980&articID=911)

What are the current fastest SSDs in the 8-16GB size range (non raid)?
Links to reviews/comparisons would be nice. I might be interested :)
Intel had some of the fastest a few months ago at 250MB/s read and 70MB/s write speed so that's very impressive.

Intel X25-M 80GB
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820167005](http://www.newegg.com/Product/Product.aspx?Item=N82E16820167005)
For $400 it isn't too bad...

---

### Post by miegiel on 2009-03-10
> **mips said:**
> rotflmao. And my name is Santa Clause.

As for all you other smart alec's here, real world performance is not what you are posting.

We're just cheating with cached reads :twisted: small T big t

```
:~$ sudo hdparm -t /dev/sda1

/dev/sda1:
 Timing buffered disk reads:  244 MB in  3.02 seconds =  80.76 MB/sec

:~$ sudo hdparm -T /dev/sda1

/dev/sda1:
 Timing cached reads:   1618 MB in  2.00 seconds = 809.34 MB/sec

```

---

### Post by mips on 2009-03-10
> **.Maleficus. said:**
> Intel had some of the fastest a few months ago at 250MB/s read and 70MB/s write speed so that's very impressive.


I would love to have a FAST 8-16GB SSD, just for the OS.

Anyone have experience with the new Sandisk G3 SSD?
[http://www.sandisk.com/OEM/ProductCatalog(1436)-SanDiskG3_SSD_Family.aspx]("http://www.sandisk.com/OEM/ProductCatalog%281436%29-SanDiskG3_SSD_Family.aspx")

Not the size I'm looking for but they seem relatively cheap ($150 60GB) and they claim big performance.
Wonder if there are any reviews out yet.

---

### Post by tom66 on 2009-03-10
```

thomas@pluto:~$ sudo hdparm -T /dev/sda1
[sudo] password for thomas: 

/dev/sda1:
 Timing cached reads:   1340 MB in  2.00 seconds = 670.02 MB/sec
thomas@pluto:~$ 

```

An old laptop HDD.

```

thomas@pluto:~$ sudo hdparm -T /dev/sdb1

/dev/sdb1:
 Timing cached reads:   1368 MB in  2.00 seconds = 683.64 MB/sec

```

An external USB disk drive. Seems a bit too much...

---

### Post by mips on 2009-03-10
WTF are people posting their cached read times here? 

[COLOR=Red]It's off-topic so please** STOP**![/COLOR]

---

### Post by miegiel on 2009-03-10
sorry :oops:

I just tested my 16GB sd card out of curiosity, 16 and 19 MB/sec in different card readers.

If it's for a laptop fast SSDs are the best option, but for a pc I'd still prefer western digital's raptors. Take a look a look as sandisk's competitors too. Sandisk is often a bit more expensive, but a good brand as far as I know.

---

### Post by .Maleficus. on 2009-03-10
> **mips said:**
> I would love to have a FAST 8-16GB SSD, just for the OS.

Anyone have experience with the new Sandisk G3 SSD?
[http://www.sandisk.com/OEM/ProductCatalog(1436)-SanDiskG3_SSD_Family.aspx]("http://www.sandisk.com/OEM/ProductCatalog%281436%29-SanDiskG3_SSD_Family.aspx")

Not the size I'm looking for but they seem relatively cheap ($150 60GB) and they claim big performance.
Wonder if there are any reviews out yet.
I would love to have even a Raptor for my OS (and like everyone else, for a few games).  I had a chance to pick up one of those Intel SSDs with their Retail Edge program for relatively cheap (<$200 I think it was) and should have jumped on it but I didn't :(.

If you're looking for a cheap, fast SSD, [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227393") OCZ Vertex looks pretty good.  $115 for 30GB with 200MB/s read and 160MB/s write.


Edit:  ...Didn't notice you were in South Africa.  I'm sure you could still find it relatively cheap.

---

### Post by tuxsheadache on 2009-03-13
I think you guys need to meet this PC:
[http://www.youtube.com/watch?v=96dWOEa4Djs&fmt=22](http://www.youtube.com/watch?v=96dWOEa4Djs&fmt=22)
He wins on all levels in comparison.

---

### Post by MikeTheC on 2009-03-13
I guess we're moving to solid-state storage. I hope it proves to have the longevity everyone seems to think it will.

In the meantime, I'll be happy to "get by with" a regular, spinning disk.

---

