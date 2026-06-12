---
title: "The Cloud and Sync"
date: 2021-05-18
forum: Ubuntu, Linux and OS Chat
---

### Post by dddman on 2021-05-18
I would like to know what others use for cloud storage and sync.

I have not yet hit on a good Linux solution.  My first try was Megasync, which I think is an excellent product and linux compatible.  However after the install I found out Virtualbox is not supported.  And that's a deal breaker.

Currently I'm backing up my Ubuntu Home directory to my windows cloud (Google Drive) but this is not 100% compatible with linux either and I really don't want linux combined with my windows storage.  It gets confusing.

I want to have separate cloud storage and sync just for Ubuntu.  Seeking a free service of course :)  I can do with 10/15G of storage, but more is better.

Thanks

---

### Post by dddman on 2021-05-19
Degoo offers 100G of free storage, but has a lot of bad reviews.

There are others offering 10G of storage (like pCloud, icedrive, sync) with good reviews.  Megasync being one of them with good reviews and 15G of storage.

Really not seeing much of a difference in any of these storage options.  I originally thought I just upload the entire virtual folder (9.4G+overhead), but it looks like that is not going to be a feasible plan.  So it's looking like plan B will be just reverting things back to plan A (Megasync).  Wish I didn't nuke that password ](*,)

---

### Post by deadflowr on 2021-05-19
*Thread moved to **Ubuntu Linux and OS Chat***

---

### Post by scorp123 on 2021-05-19
> **dddman said:**
> I would like to know what others use for cloud storage and sync. 

**Dropbox.** Some time in the distant past (2008) I bought a 8 GB plan from them. Over time I got upgraded to 64 GB for free (... there were various ways in the past by which you could earn lots of extra-storage space ...) and now over the years I have upgraded to 2 TB. I find it convenient, it just works across all my computer platforms (Windows, Linux, Mac), smartphones and tablets (Android) and even for my Qnap NAS.

---

### Post by dddman on 2021-05-19
Hi scorp123

Yes that is convenient and I had a look at Dropbox, these days I think it was 2G free.

Megasync actually starts you out at 50G free, but after 30 days that drops down to 15 unless terms are met.  And like Dropbox, it hooks up to Nautilus.  Without spending some money I think that's going to be as good as it gets.

Thanks for the input.

---

### Post by TheFu on 2021-05-19
Live by the cloud, die by the cloud.

If I wanted to share all my data with the world, I'd use a cloudy storage provider.

---

### Post by dddman on 2021-05-19
Hello TheFu

There is encryption.  

Besides anyone plugged into the internet is subject to hack.  Governments get hacked, I'm not going to stop it.  Just got to do what I can and move on.

Hey, and on a side note:

[ATTACH=CONFIG]288515[/ATTACH]

Xman is really Microman :)

---

### Post by scorp123 on 2021-05-19
> **dddman said:**
>  Without spending some money I think that's going to be as good as it gets. 

What about your phone / mobile phone / Internet / cable / fiber / TV provider? Do they offer something? Where I live I could get cloud storage space included with my mobile phone/ Internet / digital TV plan if I wanted...

Example:
[https://sub.mycloud.swisscom.ch/#/subscribe?lang=en]("https://sub.mycloud.swisscom.ch/#/subscribe?lang=en")

So, it's not really "free" but the fees are already included with whatever mobile phone or Internet plan you buy from these guys. Did you check in your area / your country? Maybe the mobile phone and Internet providers in your corner of the world offer something similar?

**_Last but not least:_**

There's always the option to build something yourself. Small server with 4 or 5 drive bays, maybe use ZFS or some other RAID mechanism, and then something such as **"OwnCloud"** or **"NextCloud"** ... Why not? Might not even cost that much. If you calculate the costs of building your own small server vs. the costs of paying for a cloud service (e.g. costs after 2 years) you might find that running your own server and your own little "cloud service" isn't so expensive after all and might be worth doing.

[https://doc.owncloud.com/server/admin_manual/installation/quick_guides/ubuntu_20_04.html]("https://doc.owncloud.com/server/admin_manual/installation/quick_guides/ubuntu_20_04.html")
[https://www.linuxbabe.com/ubuntu/install-nextcloud-ubuntu-20-04-apache-lamp-stack]("https://www.linuxbabe.com/ubuntu/install-nextcloud-ubuntu-20-04-apache-lamp-stack")

---

### Post by TheFu on 2021-05-19
Storage, directories, files.  The original "database."  Ignore that at your peril.

NextCloud runs well on a Raspberry Pi.  A r-pi v4 with some external storage should work fine. That's a $50-ish, 10W computer with USB3 and GigE networking. Older models have I/O contention issues. The NIC and USB bus is shared, so only about 220Mbps is possible. The v4 Pi addressed that.

I have a nextcloud server running in a VM on a Pentium system here and use it for mostly static data. Much of the data that can be accessed via nextcloud is through read-only NFS mounts. I keep unimportant things like shopping lists in read-write nextcloud areas.  Hardly critical if lost.
I've been burned too many times, lost access to data that was put into "apps". At some point, the data needs to be in directories and files.

I think of all the people using "photo management" programs that fill them up with metadata ... only to discover that metadata is trapped inside the specific tool, never to be released. Adobe does this all the time.

---

### Post by dddman on 2021-05-19
Quote
"What about your phone / mobile phone / Internet / cable / fiber / TV provider? Do they offer something? Where I live I could get cloud storage space included with my mobile phone/ Internet / digital TV plan if I wanted..."

All I have is a mobile phone set up as a hot spot.  You may be right AT&T just may have cloud service bundled in with my phone, have to check into that.  My desktop/laptop work well off of this.  No cable, no fiber and TV is provided via the internet.  $50 a month and I got it all (dddman breaks arm patting himself on the back).

I use the cloud just in case the house gets hit by a meteor and I loose it all.  I feel off site storage is important.

As for NextCloud/OwnCloud I  just soon let those nerdy people in the cloud figure this stuff out.  I have enough going on.  But thanks for the suggestion.

Thanks for the input and hey, fix Microman :)

---

