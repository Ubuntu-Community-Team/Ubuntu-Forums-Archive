---
title: "New AMD 7750 (Kuma) vs. Old Phenom 9550"
date: 2009-01-14
forum: The Cafe
---

### Post by cubeist on 2009-01-14
Hey, This is a brief benchmark of the new AMD 7750 (codename Kuma) which is sold as a dual-core Athlon CPU, but is actually a Phenom with two cores and lots of cache.

The tests compare the Athlon 7750 running at stock 2.7GHz speed as well as OC to 3.2GHz to my old Phenom 9550 at stock 2.2GHz and OC at 2.4GHz.

I picked tests from the Phoronix Test Suite that show real-world day to day applications, as well as a couple custom benchmarks.

Sorry, some tests don't have data for all speeds, I was tired and lazy!

From Phoronix-test-suite:

_build-apache_
Stock Phenom 9550 2.2: 47.79s
OC Phenom 9550 2.4: [COLOR="Lime"]36.88s[/COLOR]

Stock Athlon 7750 2.7: [COLOR="Red"]54.17s[/COLOR]
OC Athlon 7750 3.2: 44.50
This is a multi-threaded test, so four cores helps!


_encode-mp3_
Stock Phenom 9550 2.2: [COLOR="Red"]45.74s[/COLOR]
OC Phenom 9550 2.4: 40.59s

Stock Athlon 7750 2.7: 37.14s
OC Athlon 7750 3.2: [COLOR="Lime"]31.20s[/COLOR]
**46% improvement over stock Phenom**


_compress-Gzip_
Stock Phenom 9550 2.2: [COLOR="Red"]117.92s[/COLOR]

OC Athlon 7750 3.2: [COLOR="Lime"]81.85s[/COLOR]
**44% improvement!**


_ffmpeg_
Stock Phenom 9550 2.2: [COLOR="Red"]31.40s[/COLOR]
OC Phenom 9550 2.4: 27.39s

Stock Athlon 7750 2.7: 24.35s
OC Athlon 7750 3.2: [COLOR="Lime"]20.66s[/COLOR]
**55% improvement over stock Phenom**


_tandem-xml_
Stock Phenom 9550 2.2: [COLOR="Red"]32.91s[/COLOR]
OC Phenom 9550 2.4: NA

Stock Athlon 7750 2.7: 26.57s
OC Athlon 7750 3.2: [COLOR="Lime"]22.45s[/COLOR]
**45% improvement over stock Phenom**


_super-pi (1M)_
Stock Phenom 9550 2.2: [COLOR="Red"]27.67s[/COLOR]
OC Phenom 9550 2.4: 24.68s

Stock Athlon 7750 2.7: 22.88s
OC Athlon 7750 3.2: [COLOR="Lime"]19.79s[/COLOR]
**40% improvement over stock Phenom**
Remember: Try not to compare super-pi results between AMD and Intel, as Intel chips have better math execution built into super-pi, IE, Intel always wins at super-pi!

**Custom Test A**
I use enblend a lot, so I tested a 10 image 74 Megapixel blend

_enblend -l 29_
Stock Phenom 9550 2.2: [COLOR="Red"]3m47s[/COLOR]
OC Phenom 9550 2.4: NA

Stock Athlon 7750 2.7: 3min45s (This blew me away because enblend is fully multi-threaded!)
OC Athlon 7750 3.2: [COLOR="Lime"]3m26s[/COLOR]
**11% improvement over stock Phenom**

**Custom Test B**
I use various gimp filters like GreyCStoration daily.  I tested this on a 100MB 25 MegaPixel image.
_GreyCStoration (stock plugin settings)_
Stock Phenom 9550 2.2: [COLOR="Red"]3m20s[/COLOR]

OC Athlon 7750 3.2: [COLOR="Lime"]2m31s[/COLOR]
**32% improvement over stock Phenom**


Notes: The 7750 is a black edition and overclock's to 3.2GHz on air with no problem (just multiplier, no extra voltage).  It runs at 35C idle and a max of 47C under load (30min stresstest), temps may drop a couple degrees when the arctic silver breaks in.  Later I will try to OC to 3.4 or 3.5 and check temps and stability.

The new phenom 2 940 3GHz runs super-pi (1M) SLOWER than the 7750 (OC) at 22.964s and OC'd to 3.5GHz at 19.76s.  See Link. Overall, I think I made a good purchase and this is a real stinker for 80USD.
[http://www.legitreviews.com/article/860/6/]("http://www.legitreviews.com/article/860/6/")

Conclusion: For $107 CDN, this is a fantastic CPU...who needs four cores anyway!

---

### Post by Changturkey on 2009-01-14
AMD's Prices are always a bonus, and I don't think their performance lags way too much behind Intel.

---

### Post by cubeist on 2009-01-15
After some more tweaking I was able to max out at 3400Mhz on air.  It seemed stable at this speed and the idle/load temps were about the same as 3200Mhz (35C Idle/ 47C Load).  I was able to run the phoronix encode-mp3 test again and it scored a very decent 25.20s.  This is **23%** better than being overclocked at 3.2Ghz, and a whopping **82%** better than my old phenom!
Unfortunately, when I tried to load up a game, or run the cpustress test, the X server would crash and I would have to reboot.  So I have backed it down to 3.2GHz where it will remain.

Again, I am very pleased (blown away really) with the performance of a $100 chip...

---

### Post by redonwhite on 2009-02-18
Thanks for this thread.  I just got one off newegg today.  I cant wait for it to come in!  Only thing is I need to upgrade my Mobo to an AM2+.  What motherboard are you using with your 7750?

---

### Post by wolfen69 on 2009-02-18
my AMD Phenom 9950 Agena 2.6GHz Socket AM2+ 125W Quad-Core Black Edition comes in tomorrow. paid $148 for it. it got 5 eggs from 379 reviews. can't wait. with that much speed, i probably won't overclock though.

---

### Post by wolfen69 on 2009-02-18
> **redonwhite said:**
> I just got one off newegg today.
newegg is the bomb. i buy almost everything from them.

---

### Post by BuffaloX on 2009-02-18
Wow that's incredible value! And a very nice OC capacity.

I just don't understand how the Phenom is so much faster in the Apache compile test.
Looks to me like it might be a hard-drive issue?

Fast cores rulez for single threaded apps. :p

---

### Post by darrenn on 2009-02-19
Yeah im going to buy one of these. I was going to buy a phenom II but my motherboard doesn't support them and won't in the future.

---

### Post by cubeist on 2009-02-20
After a month of continuous usage on my graphics workstation, this chip is still blazing fast.  I am still running it OC'd at 3.2GHz with no hiccups... ~ 300+ hours! Everything from blender to gimp runs great.  I don't have a single complaint.  It really renders great... 

Also, I should have mentioned in an earlier post, when I installed it I used a dab of arctic silver paste and a new scythe shuriken cooler... which probably accounts for the relatively low temps (35C to 45C)

For the person that asked, I am using a gigabyte GA-MAS2H mobo...works aok in linux, but the northbridge runs way too hot...you could cook eggs on it! and the usb controller is affected by the infamous USB pendrive problem; where pen drives will only run on USB 1.1

I see they are currently about $66 on Newegg which is pretty good price, but if anyone in Canada is looking for this chip, NCIX has them for 85 CDN this week.

---

