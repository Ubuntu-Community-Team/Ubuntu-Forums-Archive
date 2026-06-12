---
title: "Anyone recommend a good SSD?"
date: 2010-05-12
forum: The Cafe
---

### Post by beastrace91 on 2010-05-12
So I am looking to pickup an SSD to replace the standard platter hard drive in my netbook. I need at least 16gigs (prefer the 32gig range) and I would like at *least* a 200MB/sec read and 100MB/sec write speeds. Anyone have any recommend brands and/or drivers I should take a look at? I prefer to stay in the 160$ price range (although around 100$ would be best)

~Jeff

---

### Post by ubunterooster on 2010-05-12
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122)

---

### Post by McRat on 2010-05-12
...

---

### Post by beastrace91 on 2010-05-13
> **ubunterooster said:**
> [http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122](http://www.newegg.com/Product/Product.aspx?Item=N82E16820233122)

How does that compare to [this one](http://www.newegg.com/Product/Product.aspx?Item=N82E16820211419)? The one I am linking to has a higher read/write speed but the one you suggested has 64mb of cahce...

~Jeff

---

### Post by ubunterooster on 2010-05-13
Yours will be faster  except in random writes. I prefer to stay with name-brand components for relatively new technology, but that is a personal opinion.

---

### Post by 98cwitr on 2010-05-13
the one Im looking at: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227469](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227469)

---

### Post by julio_cortez on 2010-05-13
> **98cwitr said:**
> the one Im looking at: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227469](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227469)
Sounds interesting, apart from the price that is still a little too high..

I'm still thinking about adding one of them to my system (I would have bought it directly in January when I built the machine but I ran out of budget), maybe a 60 GB one to make a 40 GB partition for W7 (System + main programs like SonicStage) and a 20 GB space to mount / and /home plus some swap.

Might still wait till prices drop a little more, though. For the moment I'm happy with ny 1TB SATA2 drive which, though not being warp fast, has all the space I need.

---

### Post by 98cwitr on 2010-05-13
> **julio_cortez said:**
> Sounds interesting, apart from the price that is still a little too high..

I'm still thinking about adding one of them to my system (I would have bought it directly in January when I built the machine but I ran out of budget), maybe a 60 GB one to make a 40 GB partition for W7 (System + main programs like SonicStage) and a 20 GB space to mount / and /home plus some swap.

Might still wait till prices drop a little more, though. For the moment I'm happy with ny 1TB SATA2 drive which, though not being warp fast, has all the space I need.

price too high? youre...buying...an...SSD. The price is going to be high.

---

### Post by 98cwitr on 2010-05-13
gotta pay to play imho...just the best bang for the buck that I can find in MLC.

---

### Post by julio_cortez on 2010-05-13
> **98cwitr said:**
> price too high? youre...buying...an...SSD. The price is going to be high.
Even 10$ can be high when your budget is 5$.

At the very moment, the increase of performance a SSD would give me won't justify its cost. Of course I'll be buying it tomorrow if I know I'm going to run software requiring performing I/O..

---

### Post by psusi on 2010-05-13
> **98cwitr said:**
> the one Im looking at: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227469](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227469)

That's the one I picked up almost two months ago now and I've been loving it.  5 seconds to  boot.  Still waiting for the bloody $30 mail in rebate though, grrr.

Before I got it I had decided to start experimenting with LVM so when the SSD arrived, I was able to have lvm migrate my root partition over to the new drive on the fly while I was running from it.  Very nifty.

---

### Post by 98cwitr on 2010-05-13
> **psusi said:**
> That's the one I picked up almost two months ago now and I've been loving it.  5 seconds to  boot.  Still waiting for the bloody $30 mail in rebate though, grrr.

Before I got it I had decided to start experimenting with LVM so when the SSD arrived, I was able to have lvm migrate my root partition over to the new drive on the fly while I was running from it.  Very nifty.

you got TRIM working out the gate?

---

### Post by psusi on 2010-05-13
> **98cwitr said:**
> you got TRIM working out the gate?

No.  The lucid kernel does not support auto trim, and manual trim requires a newer version of hdparm as well, and isn't supported on LVM anyhow.  I'm not worried about it though since if it ever does slow down, I can just have lvm migrate the volume off the drive and do a full disk erase, then migrate back.  So far I have not seen any evidence of a slow down and I don't expect to either since I don't have the entire disk allocated to logical volumes yet, so there is no way that every block could be written to.  As long as there are still plenty of blocks that have never been written to, the firmware should have plenty of empty erase blocks to play with.

---

### Post by 98cwitr on 2010-05-13
id really like to see TRIM in the new kernel update...im amazed this hasnt been addressed in production releases [/preachingToTheChoir]

---

### Post by ubunterooster on 2010-05-13
Mine is super fast w/o trim

---

### Post by Penguin Guy on 2010-05-13
I was thinking of getting an SSD, but wanted to save money by getting an 8GB one and having only my root partition on it. Only problem was, I couldn't find any good 8GB SSDs. [Thread here]("http://ubuntuforums.org/showthread.php?t=1458818").

---

### Post by 98cwitr on 2010-05-13
apparently TRIM support on the kernel level was released in Feb :?

[http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb](http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb)

What kernel as you using

---

### Post by Penguin Guy on 2010-05-13
> **98cwitr said:**
> apparently TRIM support on the kernel level was released in Feb :?

[http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb](http://kernelnewbies.org/Linux_2_6_33#head-b9b8a40358aaef60a61fcf12e9055900709a1cfb)

What kernel as you using
I believe TRIM support was added to kernel 2.6.3.33, Ubuntu 10.04 currently uses kernel 2.6.32. Launchpad bug report [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/571476").

---

### Post by 98cwitr on 2010-05-13
guess i'll be waiting...I want trim or no SSD (it's not even really that important...I just want an SSD and to blow some cash) ;)

---

### Post by ubunterooster on 2010-05-13
Will we need to reinstall to use TRIM, Penguinguy?

---

### Post by cariboo on 2010-05-13
From the looks of it MM is skipping the .33 kernel and going with .34, which should be in the repositories within the next couple of days. Unfortunately unless there is a very good reason for it, I don't think it will be back-ported to lucid.

---

### Post by beastrace91 on 2010-05-13
> **cariboo907 said:**
> From the looks of it MM is skipping the .33 kernel and going with .34

Thats really sad :( If 10.10 isn't going to get .35 it means we have to wait till 11.04 to get multi-touch support in Ubuntu OOTB

~Jeff

---

### Post by cariboo on 2010-05-13
Not necessarily, the Ubuntu devs create customized kernels, we'll just have to wait for .34 to be see, once it finishes compiling.

---

### Post by Penguin Guy on 2010-05-13
> **ubunterooster said:**
> Will we need to reinstall to use TRIM, Penguinguy?
No, it's just like any other kernel update; it automatically adds a new option in your grub list, you select it, and you're back in your normal system, but with a new kernel.

---

### Post by ubunterooster on 2010-05-13
> **Penguin Guy said:**
> No, it's just like any other kernel update; it automatically adds a new option in your grub list, you select it, and you're back in your normal system, but with a new kernel.
Good; thanks.

---

### Post by 98cwitr on 2010-05-13
...and a new contender emerges: [http://www.newegg.com/Product/Product.aspx?Item=N82E16820226136](http://www.newegg.com/Product/Product.aspx?Item=N82E16820226136)

---

### Post by McRat on 2010-05-13
The hotrod is the C300 made by Micron, but sold under Crucial logo.

375-355mbps in independent testing.  Needs a SATA III motherboard or controller to get full speed, but even with SATA II, it is faster than any other mass storage device.

Not cheap.  $700'ish.

---

### Post by andrewabc on 2010-05-13
Recommend OCZ Agility or Vertex. They will be going on sale now that they've been superceded by agility/vertex 2 which use sandforce controllers.

[60gb vertex $160](http://ncix.com/products/index.php?sku=36022&vpn=OCZSSD2-1VTX60G&manufacture=OCZ%20Technology&promoid=1114) - canada

I have 60gb vertex. works good. I still have old firmware on it though. $180 free shipping at newegg. I got mine for $200 free shipping in October on big sale. Shows how slow it has taken for prices to drop.

When buying wait for good sales. Compare prices to other places to make sure good prices.
Use [diskcompare](http://diskcompare.com/disk/664/?v=1) website to check on prices.

---

### Post by beastrace91 on 2010-05-14
> **andrewabc said:**
> [60gb vertex $160](http://ncix.com/products/index.php?sku=36022&vpn=OCZSSD2-1VTX60G&manufacture=OCZ%20Technology&promoid=1114) - canada

That is an amazing deal! I think I have a winner... Thanks :D

~Jeff

---

### Post by psusi on 2010-05-14
> **98cwitr said:**
> guess i'll be waiting...I want trim or no SSD (it's not even really that important...I just want an SSD and to blow some cash) ;)

That's like cutting off your nose to spite your face.  If you want an SSD, go get one; it is well worth it.  In practice TRIM really doesn't matter.  It is a theoretical problem that has been way overblown in the media.  As long as the drive supports it you can always upgrade your kernel down the road if you need to.

You can also get the latest hdparm and manually trim every once in a while.

---

### Post by 98cwitr on 2010-05-14
just ordered mine...got paid today :)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820226136](http://www.newegg.com/Product/Product.aspx?Item=N82E16820226136)

---

### Post by andrewabc on 2010-05-14
> **beastrace91 said:**
> That is an amazing deal! I think I have a winner... Thanks :D

~Jeff

Should note that the drives I linked to are the ones that 'ruled' from April 2009->April 2010 (my guesstimate, and I'm talking about all Indilinx controllers). They have stable drivers (went through like 10 versions in a year).

The new Sandforce based SSD are supposed to be faster, but they have only been out a couple months and only went mainstream in past month.

So basically it comes down to:
1. Indilinx based controller: been out for a year. Some good prices (per gb) if you're patient for a sale. 'Garbage collection' is good for drives in RAID (since TRIM not possible in RAID).

2. New Sandforce controller: looks like it will be replacing Indilinx for now, faster, but new so no idea on firmware or reliable. Benchmarks are great though.

3. Intel drives. Fast read and random 4k. But slow sequential write speed (if you know you'll e writing lots of larger files). I think Sandforce might even be faster or close enough. Ok prices. Intel will be releasing new versions in 4th quarter.

Definitely use the diskcompare website to check on prices and compare at different retailers.

If you don't know anything about SSD then you MUST read
[http://www.anandtech.com/show/2614](http://www.anandtech.com/show/2614)
[http://www.anandtech.com/show/2738](http://www.anandtech.com/show/2738)
[http://www.anandtech.com/show/2829](http://www.anandtech.com/show/2829)
[http://www.anandtech.com/show/2944](http://www.anandtech.com/show/2944)
[http://www.anandtech.com/show/3661](http://www.anandtech.com/show/3661)
[http://www.anandtech.com/show/3681](http://www.anandtech.com/show/3681)

to understand what has happened over time in SSD market. They went from crap stuttering slower than HDD, to now where they are awesome. :)

EDIT:
I'm sure non OCZ indilinx or sandforce SSD are fine (make sure same controller though!! not some real old slow crap), it all depends on prices and what brands you like. I've really only followed OCZ SSD products, so I'm biased towards them. As long as other brands that you look into have same controller, they should be similar to OCZ stuff. There are some 'slow'/budget/value SSD out there that everyone sells (including OCZ), which aren't really worth time purchasing.

---

### Post by RaZe42 on 2010-05-14
I'd say the safest bet is to go for the new, cheaper Intel X25-V 40GB. Not as fast write speeds as the X25-M, but same read speed and random access times. Personally I think Intel makes the most dependable SSDs on the market.

Edit: as andrew said anandtech is a great source for information on SSDs. I'd recommend sticking to Intel because of the whole drive controller mess out there.

---

