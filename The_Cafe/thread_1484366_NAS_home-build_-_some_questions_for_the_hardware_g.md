---
title: "NAS home-build - some questions for the hardware gurus..."
date: 2010-05-15
forum: The Cafe
---

### Post by bluelamp999 on 2010-05-15
Hello friends,

I've decided the time has come to add a NAS to my home network and would like to try to build my own based on open source components.

But not being a hardware maven, trying to decide on the nuts and bolts side of things is melting (what's left of) my brain...

What I'd ideally like is a small format FreeNAS box with either 3 x 2TB or 4 x 1.5TB disks in a RAID 5 array.

I really like this case - _[Fractal Design: Array Mini ITX NAS]("http://www.fractal-design.com/?view=product&category=3&prod=39")_ and would like to combine it with a low power consumption Atom motherboard and a FreeNAS compatible RAID 5 capable card.

I'm hoping some of you will have built similar setups and would be able to offer some hardware advice.

Is it sensible to want a separate RAID card? Is on-board RAID acceptable? Am I better off buying a dedicated NAS box (e.g. _[Synology DS-410]("http://www.synology.com/enu/products/DS410/index.php")_)?

Any advice appreciated...

Cheers

---

### Post by cariboo on 2010-05-15
Onboard raid is called FakeRaid for a reason, I found I was getting data corruption using it, so I would suggest using software raid, you won't notice the difference in performance.

---

### Post by Groodles on 2010-05-15
If you use a dedicated RAID card will FreeNAS use the RAID feature of the card?  As I was under the impression that FreeNAS used standard Linux (Software) Raid to create its arrays.

Assuming I'm right (I don't know if I am) then a specific RAID card isn't required.  You just need enough ports to plug in the number of HDDs that you want in your array.  I believe that Linux Software Raid can even mix disk types within the array.  (SATA/IDE).

An Atom CPU can certainly run a software raid array.  (Mine does 2 seperate RAID1 arrays of 2 disks/array.)  However, RAID5 requires a lot more computation and the Atom "may" struggle to keep up.  However, if it's a dedicated NAS box, perhaps this isn't an issue.

---

### Post by The Real Dave on 2010-05-15
Software RAID in FreeNAS is great. I've had FreeNAS on a 451Mhz Pentium III, running RAID1, albeit, only a 10GB RAID, but I never had any performance issues :)

---

### Post by seeker5528 on 2010-05-15
> **Groodles said:**
> If you use a dedicated RAID card will FreeNAS use the RAID feature of the card?  As I was under the impression that FreeNAS used standard Linux (Software) Raid to create its arrays.

If you have a dedicated RAID card that fully implements RAID in the hardware, you might have the options to set that up in FreeNAS. Personally I would probably rather use the functions provided by whatever RAID set up options the hardware gives you during the boot sequence.

When software RAID is used, I'm not all that sure the FreeNAS uses the same software RAID that Linux uses, seeing how it is built on Free BSD.

There doesn't seem to be a download yet, but the guy that started FreeNAS did decide he needed to use Linux to do everything he wanted to do.

[http://sourceforge.net/projects/corenas/](http://sourceforge.net/projects/corenas/)

[http://blog.openmediavault.org/](http://blog.openmediavault.org/)

Later, Seeker

---

### Post by handy on 2010-05-15
**@bluelamp999:** Do you need RAID or just want to have it?

If you do require the extra speed, a problem you need to look at with external cards, (which I believe is the best way to go) is that if your card fails, you often require an identical card to be able to access your array. 

Most of us can't afford to buy 2 cards, so after a card failure you have to find another new or 2nd hand which may or may not be quickly achieved.

You also need to have a backup system so that in the event of a disaster that is beyond your RAID-5s redundancy you can actually recover your data & renew your setup.

I used to run a FreeNAS system which was used to backup specific data from my main machine. Recently I bought a Netgear ReadyNAS Duo, which runs a cut down version of Debian, uses a Sun CPU, has a 256MB SODIMM RAM which you can expand up to 1GB. It comes equipped with 2x hot swappable drive drawers, it is small, quiet, has a gigabit NIC built in, supports a variety of network protocols; I use NFS with Linux & AFP from OSX, it also has CIFS, FTP, HTTP, HTTPS, & Rsync.

It comes with Bittorrent built in, (which sucks) though fortunately someone has made a Transmission add-on which is both easily installed & accessible from the ReadyNAS web GUI administrative front end which add-ons make themselves a part of, so it is now an excellent .torrent slave that uses minimal electricity. 

It uses 4W at idle & apparently 35W with 2x 500GB drives working flat out.

The ability to set up sophisticated file access permissions is of course also available & more.

I bought mine drive-less & installed the 1TB WD Green HDD that I used to use in the FreeNAS box. 

There is RAID-1 built in, (which imho is the quickest way to spread corruption between drives known to man), you don't have to use it, you can also set up 2 drives as individual RAID-0s which in effect gives you JBOD. You can buy the ReadyNAS Duo quite cheaply if you shop around, they also make more expensive ones that hold more drives & have various other forms of RAID built in.

This one is all I need, though perhaps one day I'll get a 2nd one & use it as a backup of the first; multiple ReadyNAS devices can function together in various ways as well.

---

### Post by bluelamp999 on 2010-05-17
Firstly, thanks to all responders - it's certainly given me food for thought...

On reflection I feel I don't really need a NAS, what I need is a home server.

There seems to be too many potential drawbacks (and disasters waiting to happen) in adopting a RAID approach when I don't really need the performance/redundancy offered by RAID.

So now I'm thinking of a small form factor (mini-itx), low power draw Ubuntu server with a couple of HUGE hard disks where I can backup from one to the other (cron job or whatever.)

I really only need this to be on 24/7 to service my Squeezebox music player and feed my networked media player with video (and do a bit of BT on the side.)

It will also be cool to get up-to-speed with Ubuntu server and maybe set up my own FTP server etc.

I envisage administering my new server using Webmin.

Can anyone see any flaws in this plan?

Cheers!

---

### Post by jetsam on 2010-05-17
Only if you forget to let us know how it's going...

---

### Post by NCLI on 2010-05-17
> **bluelamp999 said:**
> Firstly, thanks to all responders - it's certainly given me food for thought...

On reflection I feel I don't really need a NAS, what I need is a home server.

There seems to be too many potential drawbacks (and disasters waiting to happen) in adopting a RAID approach when I don't really need the performance/redundancy offered by RAID.

So now I'm thinking of a small form factor (mini-itx), low power draw Ubuntu server with a couple of HUGE hard disks where I can backup from one to the other (cron job or whatever.)

I really only need this to be on 24/7 to service my Squeezebox music player and feed my networked media player with video (and do a bit of BT on the side.)

It will also be cool to get up-to-speed with Ubuntu server and maybe set up my own FTP server etc.

I envisage administering my new server using Webmin.

Can anyone see any flaws in this plan?

Cheers!

I have a home server, based on Ubuntu 10.04, which does everything you said, except that I've made it quite powerful(Hexa-core Athlon II) as I need it to transcode 1080p video on-the-fly. I built it myself, and use SSH to administer it. Also, I can recommend software RAID5 in Linux, as It's really easy to set up, and I'd be happy to assist you via IM or PM.

For what you need, I'd get an Intel Atom, you don't really need more than that, a 150W PSU, and at least three HDDs(Required for RAID5).

---

### Post by bluelamp999 on 2010-05-17
> **jetsam said:**
> Only if you forget to let us know how it's going...

Good idea! Hopefully, I'll put together a full HOWTO (in the fullness of time.)

---

### Post by jetsam on 2010-05-17
Awesome!:popcorn::popcorn:

---

### Post by bluelamp999 on 2010-05-17
> **NCLI said:**
> I have a home server, based on Ubuntu 10.04, which does everything you said, except that I've made it quite powerful(Hexa-core Athlon II) as I need it to transcode 1080p video on-the-fly. I built it myself, and use SSH to administer it. Also, I can recommend software RAID5 in Linux, as It's really easy to set up, and I'd be happy to assist you via IM or PM.

For what you need, I'd get an Intel Atom, you don't really need more than that, a 150W PSU, and at least three HDDs(Required for RAID5).

Thanks NCLI! That's really generous of you!

---

### Post by NCLI on 2010-05-17
> **bluelamp999 said:**
> Thanks NCLI! That's really generous of you!

A pleasure. Just contact me if you need help with any of it. It can be quite hard to get right the first time, I think I reinstalled 5 or 6 times because I was dissatisfied with what I'd set up and wanted to try something different, so I'd be glad to help you avoid that :-p

---

### Post by 98cwitr on 2010-05-17
hardware RAID > *

---

### Post by The Real Dave on 2010-05-17
> **NCLI said:**
> I have a home server, based on Ubuntu 10.04, which does everything you said, except that I've made it quite powerful(Hexa-core Athlon II) as I need it to transcode 1080p video on-the-fly. I built it myself, and use SSH to administer it. Also, I can recommend software RAID5 in Linux, as It's really easy to set up, and I'd be happy to assist you via IM or PM.

For what you need, I'd get an Intel Atom, you don't really need more than that, a 150W PSU, and at least three HDDs(Required for RAID5).

Two tri-cores?

---

### Post by 98cwitr on 2010-05-17
> **The Real Dave said:**
> Two tri-cores?

no

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343%2050001028%201302855196&name=Six-Core](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343%2050001028%201302855196&name=Six-Core)

they also have 12-core server proc. :guitar:


wtf, a NAS does NOT need that much processing power...any dual-core will be more than enough. My single core Sempron runs my NAS all day long to my PS3 @ 1080P with no hiccups

---

### Post by CharlesA on 2010-05-17
> **The Real Dave said:**
> Two tri-cores?

They have 6 core processors out, even if I don't know *why* you'd need 6 cores to do video recoding.

I've got Ubuntu Lucid running on a crappy home server running a hardware RAID5 using the card here: [http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115053)

It's not the best, but it's better then spending 300 to 500 for an insane HW RAID card. Plus they have linux drivers and a web/cli UI.

My home server has an E6500 Pentium Dual Core with 4GB of RAM and it has handled everything I've thrown at it. DHCP, DNS, NAS, VMs, etc.

---

### Post by The Real Dave on 2010-05-17
> **98cwitr said:**
> no

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343%2050001028%201302855196&name=Six-Core](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2010340343%2050001028%201302855196&name=Six-Core)

they also have 12-core server proc. :guitar:


wtf, a NAS does NOT need that much processing power...any dual-core will be more than enough. My single core Sempron runs my NAS all day long to my PS3 @ 1080P with no hiccups

Wow, offtopic I know, but I did not know you could get that many cores in one CPU :) Madness. My "encoding" server is a 2.6Ghz Celeron (128K L2) with 100GB of SoftRAID0. Takes about 8 hours to encode a standard DVD, but it's what I had spare, and it means that my main machine isn't always occupied :)

---

### Post by 98cwitr on 2010-05-17
ah well that could be the reason to have a more powerful processor...encoding vs transcoding

---

### Post by handy on 2010-05-18
Still off topic:

I've been putting some of my DVD collection onto my main machine & the little ReadyNAS Duo, using Handbrake to make compressed .mp4 files out of them.

I'm using two machines to do this, one is a 24" iMac, Core2Duo @ 2.4Ghz & 1GB RAM, the other is an old home built job running an Athlon64 3500+ single core CPU, with 2GB RAM. Both are running Arch64.

I would consider the Athlon to be a superior chip to the Intel when it comes to a job requiring just one core. Though Handbrake uses both cores of the Intel & boy it shows in the time it takes to process a DVD.

The Core2Duo takes on average 1.5 hours, the Athlon takes 3.5 hours.

I'll have to have a read up on it, but if Handbrake would use all cores in a quad core, or all 6 or 12 in those fancy processors mentioned above, you would certainly be able to make fast work of transcoding videos.

---

### Post by Sporkman on 2010-05-18
> **The Real Dave said:**
> Madness.

Sparta. :)

BTW Tilera makes a 64-core processor. :D

---

### Post by HankB on 2010-06-29
Apologies for an attempt to drag this back to the original topic. :lolflag:

I'd like to build a small NAS box to colocate at my son's place for off site backups. I'm thinking about a small Atom based box that will hold at least two drives. I thought I'd use two 1.5 TB drives and mirror them. This should cover my backup needs for a long time and by mirroring two different manufacturer's drives I should gain some reliability. I'll choose 5300/5900 RPM drives to reduce energy requirements and maybe even improve reliability. Since access is limited by Cable Internet upload speeds, I don't need much performance to keep up.

At present I'm considering a Foxconn R20-D1 Barebone system. Add a couple drives, 1GB RAM and I should be ready to go. I've priced all of this out at a bit more than $300US which seems reasonable.

Once I get Ubuntu Server installed, I'll disconnect the keyboard, monitor and mouse and run it blind, sshing in to administer it as necessary.

I can't imagine a cheaper solution that will provide 1.5TB mirrored storage, but I'm open to suggestions. 

Is there anything I'm overlooking? 

Do you have any other thoughts on this setup?

Hmmm... For about $20US I can fill the empty PCI slot with a SATA card and put both drives on their own controller. That would be a further reliability benefit.

Then there's 
> **handy said:**
> There is RAID-1 built in, (which imho is the quickest way to spread corruption between drives known to man), ...
I'd like to understand better what handy meant by that. Are they deprecating Raid-1 in general or just the built in Raid-1 in the ReadyNAS Duo.


thanks,
hank

---

### Post by CharlesA on 2010-06-29
I looked up that barebones package and it's only got 1 3.5" internal drive bay. How were you planning on having 2 or 3 drives in that case?

I know you can boot Ubuntu from USB, but maybe something like FreeNAS would work better?

---

### Post by HankB on 2010-06-29
> **CharlesA said:**
> I looked up that barebones package and it's only got 1 3.5" internal drive bay. How were you planning on having 2 or 3 drives in that case?

I know you can boot Ubuntu from USB, but maybe something like FreeNAS would work better?
I don't plan for optical storage so I can use the 5.25 external bay for the second drive. Any further expansion would require an external enclosure. But I should add a 5.25 -> 3.5 adapter to my order.


I'll have to look at FreeNAS, though I do have the advantage that I'm more familiar with Ubuntu Linux. I need the capability to boot from the RAID and install from a USB thumb drive, both of which Ubuntu can do.

thanks,
hank

Edit: FreeNAS limitations that leave it less than desirable for me:
# FreeNAS' boot drive partition cannot be used as part of any RAID array. Only whole disks can be used to form a RAID array.

That's the one that counts. I plan to boot from the RAID and don't intend to have another boot device.

---

