---
title: "Buidling a NAS (preferably low-power, mini ITX)"
date: 2013-05-25
forum: The Cafe
---

### Post by Kdar on 2013-05-25
I am planning to build a NAS device for off loading all audio and video collection for my XBMC (since my drive in HTPC is almost full). I plan to keep it somewhere in garage and just use it to stream audio or video files to my main HTPC computer over wired Ethernet network (additionally it could be nice to be able to download torrents and use mkvmerge to remove extra audio and subtitle tracks from mkv's). 
I also want to have large number of drives in my NAS (6 or more), which I hope to eventually fill up as I need the extra space. 

I done some research on parts I will need and want to have some suggestion and opinions.

**1. Case (I do like design of Fractal more, probably will pick one of those two):**
Fractal Design Node 304 (upto 6 HDDs)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811352027](http://www.newegg.com/Product/Product.aspx?Item=N82E16811352027)
Fractal Design Define R4 (upto 8 HDDs)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811352020](http://www.newegg.com/Product/Product.aspx?Item=N82E16811352020)
LIAN LI PC-Q25B (upto 7 HDDs)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811112339](http://www.newegg.com/Product/Product.aspx?Item=N82E16811112339)

**2. Motherboard (need the most help here):**
**Motherboard/CPU/VGA Combo (most likely mini ITX formfactor)**
ASUS C60M1-I AMD (really like that it is mini ITX and has 6 x SATA 6.0Gb/s... but it's sold out)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131843](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131843)
JetWay JNF99FL-525-LF Intel Atom D525 (also 6 SATAs but at 3.0Gb/s and more expensive ~$200)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153212](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153212)
BIOSTAR NM70I-847 Intel Celeron 847 (4 SATAs, 3 at 3.0Gb/s and 1 at 6.0Gb/s) + free 8GB Crucial memory w/ purchase
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813138368](http://www.newegg.com/Product/Product.aspx?Item=N82E16813138368)
**or..... Motherboard and CPU separately**
ASUS P8H77-I LGA 1155 Intel H77 (6 SATAs, 4 at 3.0Gb/s and 2 at 6.0Gb/s)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131841](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131841)
ASRock FM2A85X-ITX FM2 AMD A85X (7 x SATA 6Gb/s)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157357](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157357)

and then compatible CPU... and some RAM
.......
Another question/consideration.......I guess even if I will get motherboard with only 4 SATAs, I could use PCI slot to expand number of ports to 8 or 6 with PCI SATA card.
What do you all think? Which motherboard would it be best for me to get? and any other thoughts?

---

### Post by CharlesA on 2013-05-25
The ASRock FM2A85X-ITX FM2 AMD A85X (7 x SATA 6Gb/s) sounds pretty sweet for a low power NAS, especially with the 7 x SATA3 ports.

I also like that LIAN LI case, but I might be biased cuz my server is sitting in a LIAN LI case...

---

### Post by Kdar on 2013-05-25
yes. I would really love to have at least 6 SATAs, especially if possible at 6 Gb/s.
But what do you think would be energy efficient CPU that I can use with that motherboard? I haven't used AMD CPUs in a while.

---

### Post by sandyd on 2013-05-25
> **Kdar said:**
> yes. I would really love to have at least 6 SATAs, especially if possible at 6 Gb/s.
But what do you think would be energy efficient CPU that I can use with that motherboard? I haven't used AMD CPUs in a while.

Get an Atom.

Few things if you are serious about performance:
If you want faster read speeds, get 5 HDDs, put them in RAID6, and find a raid controller that supports having a SSD cache :D
If you want faster access speeds get a 10000RPM Drive like a Velociraptor.
If you want faster read speeds, get a RAID controller that supports RAID6/10. Make sure you have a spare RAID controller if your using HW RAID unless you are sure that you can get an identical controller if this one ever fails. Its one of the things that makes people use sw RAID over HW RAID. However, SW RAID has a bit of a CPU usage.
If your accessing the NAS from one computer, think about using iSCSI
There is no difference between SAS and SATA unless your ready to spend time tuning SAS. Then there is a difference.
Dont get WD Green Drives. Their slow, and have performance issues documented throughout the forums. Having owned one personally, I can confirm those problems.
There are some HDDs that include a onboard SSD cache. If your strapped for cache, you might want to look into getting one

What OS are you planning to use on the NAS btw

---

### Post by CharlesA on 2013-05-25
> **sandyd said:**
> Get an Atom.
If you want faster write speeds, get 5 HDDs, put them in RAID6, and find a raid controller that supports having a SSD cache :D

Otherwise - just make sure you have plenty of RAM - Linux does caching there anyways

+1. It looks like that ASRock board takes some pretty high powered CPUs
[http://www.asrock.com/mb/AMD/FM2A85X-ITX/?cat=CPU](http://www.asrock.com/mb/AMD/FM2A85X-ITX/?cat=CPU)

---

### Post by mips on 2013-05-26
Over here the HP Proliant Micro Servers are very popular for NAS or Media Servers. And they are cheap.

---

### Post by cprofitt on 2013-05-26
> **mips said:**
> Over here the HP Proliant Micro Servers are very popular for NAS or Media Servers. And they are cheap.

Yeah, the HP servers are pretty solid for the cost. Check it out [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16859107921").

The only issue with it would be that it only has Integrated 4 port SATA RAID so you would be limited to only 4 drives.

---

### Post by Kdar on 2013-05-26
Yes.. I guess now I am trying to decide between Atom and AMD C-60 motherboards.. plus I decided to just use Motherboard/CPU Combos as well.

ASUS C60M1-I AMD (really like that it is mini ITX and has 6 x SATA 6.0Gb/s... I did found it on tigerdirect for $93)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131843](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131843)
~$93
ZOTAC NM10-B-E-ION Intel Atom D510 (1.66GHz, dual-core) BGA559 Intel NM10 Mini DTX Motherboard/CPU/VGA Combo
(with 6 x SATA @ 3.0Gb/s)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500055](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500055)
~$100
**or**
JetWay JNF99FL-525-LF Intel Atom D525 (also 6 SATAs but at 3.0Gb/s and more expensive ~$200)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153212](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153212)
~$200

All three have 6 SATA connectors, which would be perfect for me.... question is just the price and the processor differences.
---

Speaking about RAIDs.. I am not sure if I will use one. I might just physically do routine backups.. since really.. the content I plan to store on my NAS will not be moving around much. I will just save it there and keep there to access it with my HTPC for streaming. And backups I can do on the raw drives.

And all the content from my NAS I will just want to stream to my HTPC over wired Ethernet.

---

### Post by CharlesA on 2013-05-26
Too bad that ASUS board is discontiuned on both newegg and Amazon. I found a similar board with 5 SATA3 ports instead of 6 for a little bit more:[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131875](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131875)

The AMD E-450 is 1.7Ghz.

The only other board I found was the JetWay out you already listed.

---

### Post by Kdar on 2013-05-26
> **CharlesA said:**
> Too bad that ASUS board is discontiuned on both newegg and Amazon. I found a similar board with 5 SATA3 ports instead of 6 for a little bit more:[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131875](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131875)

The AMD E-450 is 1.7Ghz.

The only other board I found was the JetWay out you already listed.

I found it just a moment ago on TigerDirect.

---

### Post by CharlesA on 2013-05-26
> **Kdar said:**
> I found it just a moment ago on TigerDirect.

Awesome. Should be a solid build.

---

### Post by Kdar on 2013-05-26
> **CharlesA said:**
> Awesome. Should be a solid build.

Do you think AMD C-60 will be ok for running mkvmerge to remove extra audio tracks?

---

### Post by CharlesA on 2013-05-26
Uh... It's a dual core, but only runs at 1Ghz, so it might take a while to process each file, but it should be "OK" I think.

I've been running a 3.4Ghz i7 on my "file server" which doubles as my VM host, so I've got plenty of horsepower for those.

---

### Post by Kdar on 2013-05-27
OK, I started ordering my stuff. Got the LIAN LI case, Corsair XMS3 8 GB RAM, and will order that ASUS C60M1-I motherboard (I might wait for it to show up on amazon)... But I am wondering what PSU I should get and also which hard drive.

For PSU I am curious what Watt level should be an efficient choice for this build. I was looking at Corsair Builder Series CX 430 W and Thermaltake TR2 W0070 430W, but I am curious if I can get be okay getting some PSU with lower Watt. What Watt level should I need if, eventually, I will have 6 HDDs in this NAS (3TB to 4TB each).

I also trying to decide what hard drives to get (at least the first one for now.. I plan to get one now.. and then buy them as I need to expand my storage). 

Looking at 4TB drives, there is WD Black - which costs ~$282 (~$70/TB) and Seagate - which costs ~$173.37 ($43.34/TB). Seagate 4TB drive does have more negative reviews (with DOAs) and also has a shorted warranty (1 years instead of 5 with WD Black).

There is also a WD Red (which however is only offered in 3TB size, but I heard 4TB might come out later this year). It costs $150.99 ($50.33/TB). It is supposedly designed specifically for NAS use, instead of WD Black which is a desktop HDD. And it also has low power consumption and temperature from some reviews I been reading.

---

### Post by mips on 2013-05-27
> **cprofitt said:**
> 
The only issue with it would be that it only has Integrated 4 port SATA RAID so you would be limited to only 4 drives.

Not really. You can fit 6x 1TB 2.5" drives into the 5.25" bay area in addition to 4x 4TB 3.5" drives with an additional SATA controller.

---

### Post by Kdar on 2013-05-28
Does anyone think if this PSU could handle this build?
SeaSonic SS-300ET Bronze 300W ATX12V V2.3 80 PLUS 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817151086](http://www.newegg.com/Product/Product.aspx?Item=N82E16817151086)
I never owned SeaSonic and I am also wondering if 300W would be enough for  ASUS C60M1-I, 8GB of RAM and 6 HDDs.

---

### Post by mips on 2013-05-28
Seasonic is one of good PSU brands ;)

---

### Post by CharlesA on 2013-05-28
> **Kdar said:**
> Does anyone think if this PSU could handle this build?
SeaSonic SS-300ET Bronze 300W ATX12V V2.3 80 PLUS 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817151086](http://www.newegg.com/Product/Product.aspx?Item=N82E16817151086)
I never owned SeaSonic and I am also wondering if 300W would be enough for  ASUS C60M1-I, 8GB of RAM and 6 HDDs.

Use this:
[http://www.extreme.outervision.com/psucalculatorlite.jsp](http://www.extreme.outervision.com/psucalculatorlite.jsp)

:)

> **mips said:**
> Seasonic is one of good PSU brands ;)

Agreed. It is up there will PC Power and Cooling and Corsair.

---

### Post by Kdar on 2013-05-29
Thanks...

What HDD do you think I should get?
ST4000DM000 (Seagate @ 5900RPM - 4tb), WD30EFRX (WD Red @ 5900RPM - 3tb) or WD4001FAEX (WD Black @ 7200RPM - 4tb).

WD seem to have the longest warranty on their drives (WD Red 3 years, WD Black 5).
Seagate is the cheapest ($43/TB), then comes WD Red ($50/TB) and WD Red ($75/TB).

I am a bit put off from Seagate drives due to Seagate lying about RPM speed in ST4000DM000.

However, I am wondering if anyone used any of those three, and which do you think would be perfect for NAS.

---

### Post by CharlesA on 2013-05-29
Get the one with the 5 year warranty - preferably a 7200 drive as you are doing a NAS.

Why do you think Seagate is lying about the speed of the ST4000DM000?

---

### Post by Kdar on 2013-05-29
I am not sure why... But at first, when I was looking at this drive for the first time, I got impression that is it regular 7200 drive (since same drive with 3TB is 7200RPM). RPM or warranty information are not clear presented on newegg or amazon. But then I started to look up more information on this and found that is it 5900RPM disk and that Seagate is trying to cover this information up.

Even on Amazon it has wrong information:
> 4TB storage capacity with SATA 6Gb/s NCQ Interface
Double your capacity and drive down costs with up to 1TB-per-disk hard drive technology
Seagate AcuTrac servo technology delivers dependable performance, even with hard drive track widths of only 75 nanometers
Free Seagate DiskWizard software allows you to install 3TB and 4TB hard drives in Windows, including XP, without UEFI BIOS
7200rpm Spindle Speed
[http://www.amazon.com/Seagate-Desktop-3-5-Inch-Internal-ST4000DM000/dp/B00B99JU4S/ref=sr_1_3?ie=UTF8&qid=1369833498&sr=8-3&keywords=seagate+4tb](http://www.amazon.com/Seagate-Desktop-3-5-Inch-Internal-ST4000DM000/dp/B00B99JU4S/ref=sr_1_3?ie=UTF8&qid=1369833498&sr=8-3&keywords=seagate+4tb)

There is whole topic on this on Xbit forum. [http://forum.xbitlabs.com/viewtopic.php?t=20232](http://forum.xbitlabs.com/viewtopic.php?t=20232)

---

### Post by CharlesA on 2013-05-29
Ew. That sounds really shady.

I usually stick with WD or Hitachi drives, but I do have a few Seagate external drives. So far none have died.

---

### Post by Grenage on 2013-05-29
All of my storage drives are Seagate, mainly because of the price-point.  If a drive dies, I don't really care about the drive itself - I can get a new drive with twice the capacity.  The price difference is often not worth the warranty, especially when you factor postage.  Over the course of 13 years, I'd say that at work I've seen roughly equal failure rates across the main suppliers.  My Father had a WD external unit, and it died twice within two months; it's luck, especially when it comes to archive drives.

Lets face it, your average home NAS user is just looking to store terabytes of illicitly obtained movies, and doesn't give a toss about drive speed.

---

### Post by CharlesA on 2013-05-29
> **Grenage said:**
> 
Lets face it, your average home NAS user is just looking to store terabytes of illicitly obtained movies, and doesn't give a toss about drive speed.

Pretty much, capacity > speed in those cases. I still like my 7200 drives, but I am still running a 4TB RAID5 array using 2TB drives. Thinking about throwing another drive at it because I've got like 300GB left and my Steam library keeps growing. >.>

---

### Post by Grenage on 2013-05-30
> **CharlesA said:**
> Thinking about throwing another drive at it because I've got like 300GB left and my Steam library keeps growing. >.>

Aye, Steam storage does have a habit of creeping up on one. :)

---

### Post by codingman on 2013-05-30
I prefer Seagate for low capacity, 250GB-500GB. WD for higher. As it is an NAS, I'd go for WD.

---

### Post by CharlesA on 2013-05-30
> **Grenage said:**
> Aye, Steam storage does have a habit of creeping up on one. :)

Especially with those humble bundle sales... D'oh!

---

### Post by Kdar on 2013-05-31
Well.. sadly I had a bad luck trying to order ASUS C60M1-I from TigerDirect or MacMall (which listed them as available). All they did is made me order it and then in two days changed my order statues to back order... So I am kind of tired of wasting my time like this.

Does anyone know if this board is really discontinued by ASUS or why is it out of stock everywhere?

What can be miniITX alternative to this? (that can be use with that Seasonic 300W PSU) and something that also have 6 SATA posts (I guess now I would not really care if it is 6GBps or 3GBps.. however with C60M1-I it was nice to have a 6GBps SATA speed).

From those I listed before.. the ones with 6 SATA posts are just....

[COLOR="#FF0000"]ZOTAC NM10-B-E-ION Intel Atom D510 (1.66GHz, dual-core) BGA559 Intel NM10 Mini DTX Motherboard/CPU/VGA Combo
(with 6 x SATA @ 3.0Gb/s)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500055](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500055)
~$100[/COLOR]
**or**
JetWay JNF99FL-525-LF Intel Atom D525 (with 6 x SATA @ 3.0Gb/s)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813153212](http://www.newegg.com/Product/Product.aspx?Item=N82E16813153212)
~$200

.... actually.. the $100 one is Mini DTX. I guess it's not compatible.

---

### Post by CharlesA on 2013-05-31
Are you wanting to stick with an ITX board or could you use a micro ATX one?

I'd probably go with the ZOTAC one, but please keep in mind that it will likely only be able to address 3.5GB of RAM, even with a 64-bit OS.

I ran into that problem when I tried using an atom box for my HTPC... after a lot of searching, it turned out to be a chipset limitation on the Atom.
[http://www.zotacusa.com/forum/topic/1467-ionitx-a-4gb-ram-issue/](http://www.zotacusa.com/forum/topic/1467-ionitx-a-4gb-ram-issue/)

---

### Post by Kdar on 2013-05-31
Well.. I already ordered everything.. except motherboard.. and I have LIAN LI PC-Q25B case, which only supports mini ITX... but that ZOTAC is also Mini DTX.. I am not sure what that means.. Can it fit in mini ITX case?

ah.. that really suck.. yes.. I guess it is the same for JetWay as well. I just saw it.... then I guess atom will be out of consideration.

Maybe I can just stick with Celeron (even if it only has 4 SATA ports).. and later expand it with IBM Serveraid M1015 Sas/sata Controller.... once I get to the limit with 4 drives.

or.. maybe I can get this (also only 4 SATA ports)
ASRock E350M1 AMD E-350 APU (1.6GHz, Dual-Core) AMD A50M Hudson M1 Mini ITX Motherboard/CPU Combo
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228)

---

### Post by CharlesA on 2013-05-31
It should fit, but I dunno if the standoffs will be in the right places.

mini DTX is smaller than ITX, but bigger than mini ITX. :(
[http://www.10stripe.com/featured/form/dtx.php](http://www.10stripe.com/featured/form/dtx.php)
[http://www.10stripe.com/featured/form/itx.php](http://www.10stripe.com/featured/form/itx.php)

EDIT: With that being said, the manufature's site says it can take 
mini ITX or mini DTX mobos. :)
[http://www.lian-li.com/v2/en/product/product06.php?pr_index=584&cl_index=1&sc_index=25&ss_index=64&g=spec](http://www.lian-li.com/v2/en/product/product06.php?pr_index=584&cl_index=1&sc_index=25&ss_index=64&g=spec)

---

### Post by Kdar on 2013-05-31
ah nice.. Thanks for info.. I should have checked there too... But I guess the problem is that it's Atom anyways... and only limited to 4GB (I bought 8GB - 2 x 4GB sticks, it would be a pity to let other go to waste, unused )...... or should I just "sacrifice" that other 4GB for 6 SATA posts for now?

ASRock E350M1 AMD E-350 APU (1.6GHz, Dual-Core) AMD A50M Hudson M1 Mini ITX Motherboard/CPU Combo
Maybe I should buy this instead?

---

### Post by Kdar on 2013-05-31
What if I order this motherboard and CPU instead?

ASUS P8H77-I LGA 1155 Intel H77 HDMI SATA 6Gb/s USB 3.0 Mini ITX Intel Motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131841](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131841)

Intel Core i3-2120T (TDP 35 Watts [http://pcpartpicker.com/part/intel-cpu-bx80623i32120t](http://pcpartpicker.com/part/intel-cpu-bx80623i32120t))... is it most power efficient Intel chip?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115094](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115094)

Can I still hope for power efficient NAS with this CPU and motherboard?

---

### Post by CharlesA on 2013-05-31
That should work fine.

---

### Post by Kdar on 2013-05-31
I actually decides to get ASUS P8H77-I with Intel Celeron G1610 instead.
Hopefully I will get those tomorrow and can try to put this NAS together.

Now just thinking if I should use FreeNAS or just Ubuntu server.

---

### Post by CharlesA on 2013-05-31
> **Kdar said:**
> I actually decides to get ASUS P8H77-I with Intel Celeron G1610 instead.
Hopefully I will get those tomorrow and can try to put this NAS together.

Now just thinking if I should use FreeNAS or just Ubuntu server.

I've heard FreeNAS is good (based on FreeBSD from what I remember).

Depending on what you are going to do with it, that might work too.

---

### Post by mips on 2013-06-01
Just go FreeNAS.

---

### Post by Kdar on 2013-06-01
I will give it a try...

I just saw a 4tb Seagate drive ST4000DM000 for like $150 on sale.. wondering if I should get it at this price. That's like $37.5 per TB...

---

### Post by Kdar on 2013-06-02
OK.. the problem that I have now with FreeNAS is that it can't mount my external ext4 drives... What do you think I can do about this?

---

### Post by CharlesA on 2013-06-02
Is it saying "invalid argument" or something? What is the error you are getting?

---

### Post by Kdar on 2013-06-02
yes.. Or unknown type, argument or something like that... After that I was reading up on this and apparently ext4 can't be mounted in FreeBSD (which FreeNAS is based off).

I will try to mount a reiserfs filesystem.. and check if it will work (I did read somewhere that FreeBSD supports reiserfs).... but I am not sure if it will be optimal solution.. since it might only support reads, not writes to reiserfs.

---

