---
title: "clone / migrate ubuntu headless server"
date: 2015-09-06
forum: Server Platforms
---

### Post by jmb3 on 2015-09-06
Dear ubuntu community,


Unfortunately, i couldn't find any thread on the internet helping me about the problem. Or i probably missed something so here is my post.


I got one dedicated server running ubuntu server 14.04 LTS x64 hired at online.net.
Online.net updated their prices to cheaper so i ordered a new one hoping to clone the first server to the second.
The hardware is exactly the same, only the price was updated.


To do this, i booted both servers in rescue mode (ubuntu 12.04 live cd) and did a dd command with a ssh pipe of the whole hard disk (500 gb, byte-per-byte copy, all partitions).


The copy was successful but now it seems the second / new server won't boot as i get no sign of connectivity.


Then i booted back to rescue mode, chrooted the ubuntu partition to reinstall grub. Everything went fine.
Checked UUID between grub and fstab, they're identical as expected.
Did a fsck, all good.
But still no log so probably no boot.


I'm being short on ideas...


Anyone could help me on this issue ?


Regards

---

### Post by TheFu on 2015-09-06
Are you certain these are dedicated physical servers and not dedicated VPS?
There are some storage tricks done for VPSs with copy-on-write so all of them need to be running the same base OS on the same hardware to make things work.  By shoveling 12.04 into a 14.04 box, well that might not fix the VPS plan - hence it doesn't work.

But, what do I know. Don't use that provider. I'd call their support line.

---

### Post by jmb3 on 2015-09-07
I'm pretty sure they are physical servers, waiting for support confirmation though.
Link to the actual servers we are talking about : [http://www.online.net/en/dedicated-server/dedibox-scg2](http://www.online.net/en/dedicated-server/dedibox-scg2)

> By shoveling 12.04 into a 14.04 box, well that might not fix the VPS plan

I think there is a misunderstanding here : both systems are 14.04 but i used a 12.04 live cd to run dd.

I'm calling their support line and keep this thread updated.
Never had an issue with this provider before.

---

### Post by TheFu on 2015-09-07
Yep - I missed that. Re-reading, i see it now.

Any chance the BIOS switched from legacy to UEFI? I reaching.  

I've mirrored entire installs with dd just like you - at the whole-disk level before - and it worked fine. Moved between systems.  After, the only thing that needed clean up was the udev network rules so eth0 wouldn't be locked-out by the NIC from the old machine.

I'd never heard of dedicated HW that cheap before - most are $300+/month.  A friend is paying $650+/month here, but he's running about 20 VMs on that hardware.  The VIA Nano is interesting for certain workloads - about as fast as an Atom from 2009.  

Thanks for the education!

---

### Post by jmb3 on 2015-09-07
I have no clue about the BIOS switching by itself. It would make no sense if it did actually.

You're right about the network persistent udev file. Totally missed the point. I changed the MAC addresses right now after figuring out a suspicious line on dmesg log file:
> systemd-udevd[331]: renamed network interface eth0 to eth3

Hope it fixes the issue

About the servers, they're worth every cents so far.
Running 2 lamp websites + 1 owncloud instance + mumble server
Rock solid

---

### Post by TheFu on 2015-09-07
It was a reach.

Are you sure the server hardware is identical and didn't move to UEFI booting?  The pre-installed OS that you replaced ... was there an EFI boot partition?

BTW - I've been looking for HW like this to purchase and can't find it. Any leads?

---

### Post by jmb3 on 2015-09-07
yes both hardware are identical and in legacy mode.

still no networking on this new server ! it's driving me mad ^^

> BTW - I've been looking for HW like this to purchase and can't find it. Any leads?
No clue about purchasing the HW. I guess it's only B2B deals.
However, if you want to rent some low end servers, there is some good deals on the french market : online.net & kimsufi.com
The only drawback is the lack of available servers

---

### Post by jmb3 on 2015-09-08
Ok, here is some good news.

After checking the timestamps of log files. I noticed that the new server only booted once when udev checked that network interfaces' NIC were in conflict.
Probably related with the grub reinstall.

So i redid the whole copy from server 1 to server 2 and made all the modifications before booting the first time.
And everything is up & running now ! :)

Thanks TheFu for your insights.
I'll switch this thread to fixed

---

