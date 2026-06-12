---
title: "Home Server, Is This Hardware Fit For Purpose"
date: 2012-07-26
forum: Server Platforms
---

### Post by fungus1487 on 2012-07-26
Hi Everyone,

New around here so please be easy on me.

I am looking to re-use/piece together a home server. It's purpose, to replace the synology ds112j which currently functions as such.

I need to support:

[LIST]
[*]SSH
[*]MySQL
[*]WebMin
[*]OpenVPN
[*]Tvheadend
[*]SABnzbd
[*]Transmission
[*]A few SAMBA shares
[*]Backup of Shares (Preferably snapshot based every 24 hours)
[/LIST]

I have the following hardware:

[LIST]
[*]ASUS AT5NM10T-I [http://www.asus.com/Motherboards/Intel_CPU_on_Board/AT5NM10TI/](http://www.asus.com/Motherboards/Intel_CPU_on_Board/AT5NM10TI/)
[*]8GB RAM
[*]2 x 1TB Drives
[*]DVB-T2 Tuner PCIe card
[/LIST]

Main usage patterns would be:

[LIST]
[*]2 Users Accessing SAMBA Shares
[*]XBMC Accessing MySQL
[*]Torrent + Usenet Downloading, Verifying, Unpacking
[*]Live TV Streaming/Recording
[/LIST]

*The above is quite possibly the worst case for usage at any given time.*

I am looking for someone who has had experience with some or all of these services and whether the hardware I have available is capable of running it all decently within ubuntu server. By decently I mean no major bottlenecks for 95% of use cases.

Any suggestions if there is room for improvement in the above without breaking the bank are welcomed, thanks.

---

### Post by Grenage on 2012-07-26
I imagine that the weak point here will be the processor and graphics card.

---

### Post by fungus1487 on 2012-07-26
> **Grenage said:**
> I imagine that the weak point here will be the processor and graphics card.

I forgot to mention the server would be headless, other than offloading live tv onto the GPU where do you see the graphics card being a weak point? I'm just curious as I never considered it to be. I thought as much about CPU but to give it credit the ATOM D525 is quite a little workhorse [http://ark.intel.com/products/49490/](http://ark.intel.com/products/49490/) .

Another point would be I want this to be relatively low power, being an always on device, thanks for the help.

---

### Post by Grenage on 2012-07-26
Ahh, if it's merely a back-end for services such as XBMC, it should be fine!

---

### Post by rg4w on 2012-07-26
The ATOM D525 is a great processor for always-on systems, but I recently built one with the D2700 and was quite impressed with the performance, and with a bit lower power consumption:

D525  - Passmark: 714  TDP: 13W
D2700  - Passmark: 834  TDP: 10W

Either one will probably suffice for that light workload, but you may check out mobos with the D2700 to see if you can get the extra performance and power savings at the same price.  I suspect you can, since Intel tends not to drop prices on EOL'd chips when new ones come out.

---

### Post by d4m1r on 2012-07-26
I'd say 2TB is not enough (depending on how many torrent/usenet stuff you have) but other than that, should be good to go with that hardware....

---

### Post by fungus1487 on 2012-07-27
> **d4m1r said:**
> I'd say 2TB is not enough (depending on how many torrent/usenet stuff you have)

This is just a staging server which does the grunt work of downloading, verifying, unpacking etc. I have an 18TB file server where everything ends up. Thanks for the heads up though.

---

### Post by andrew.46 on 2012-07-30
Leafnode or leafnode 2 would be handy for usenet...

---

### Post by fungus1487 on 2012-07-30
> **andrew.46 said:**
> Leafnode or leafnode 2 would be handy for usenet...

I don't have any restrictions from my ISP and we have a 50Mb cable line. Leafnode is some form of proxy caching server I believe, very useful for slower/capped/unstable broadband/dial-up packages but what benefit would I get from using this?

Sorry if I'm missing the point :)

---

### Post by continuous on 2012-07-30
> **fungus1487 said:**
> 

[LIST]
[*]ASUS AT5NM10T-I [http://www.asus.com/Motherboards/Intel_CPU_on_Board/AT5NM10TI/](http://www.asus.com/Motherboards/Intel_CPU_on_Board/AT5NM10TI/)
[*]8GB RAM
[/LIST]
I read Asus RAM spec "2 x SO-DIMM, Max. 4GB, DDR3 800 Hz Non-ECC, Un-buffered Memory" as supporting a max of 4GB RAM - i could be wrong!


The other consideration is the throughput on the disks - let's see now, a backup happening, a couple of TV shows being recorded, a couple of people saving/reading from the disks....sure an extreme scenario, and perhaps not overly important? 

Also hope the disks are 24/7 variety, or at least run a good size fan over them. 



Just considerations...

---

### Post by fungus1487 on 2012-07-30
> **continuous said:**
> 
I read Asus RAM spec "2 x SO-DIMM, Max. 4GB, DDR3 800 Hz Non-ECC, Un-buffered Memory" as supporting a max of 4GB RAM - i could be wrong!


It does indeed state 4GB max, but I was using the mobo as my old FreeNAS board. The FreeNAS forums advised that the board was capable of 8GB, so I bought more RAM, tried it and voilà! The OS reported 8GB usable back to me. Lucky eh :)

> **continuous said:**
> The other consideration is the throughput on the disks - let's see now, a backup happening, a couple of TV shows being recorded, a couple of people saving/reading from the disks....sure an extreme scenario, and perhaps not overly important? 

Also hope the disks are 24/7 variety, or at least run a good size fan over them. 

Just considerations...

Backups will be incremental and nightly, hopefully taking less than a few hours.

I plan to only schedule downloading during the evening -> morning hours.

I agree TV recording and user access at the same time is a worst case scenario but even if I possibly could saturate our gigabit network over SAMBA accessing the drives it should leave a pretty large overhead for TV recording on a SATA II drive. It then comes down to disc performance.

Perhaps I would be better maintaining a public and private drive? One accessible to SAMBA clients and the other local to the OS and only used for downloading/TV recording. Am I being overly paranoid though? :)

---

### Post by andrew.46 on 2012-07-30
> **fungus1487 said:**
> I don't have any restrictions from my ISP and we have a 50Mb cable line. Leafnode is some form of proxy caching server I believe, very useful for slower/capped/unstable broadband/dial-up packages but what benefit would I get from using this?

Do you wish to share your usenet feed with the rest of your network?

---

### Post by fungus1487 on 2012-07-30
> **andrew.46 said:**
> Do you wish to share your usenet feed with the rest of your network?

No :)

But I now understand why you suggested Leafnode, thanks.

---

### Post by andrew.46 on 2012-07-30
> **fungus1487 said:**
> But I now understand why you suggested Leafnode, thanks.

No probs, and I envy your internet connection :).

---

### Post by fungus1487 on 2012-07-30
> **andrew.46 said:**
> No probs, and I envy your internet connection :).

I tried to get 100Mb but it wouldn't wash with the missus ;)

---

