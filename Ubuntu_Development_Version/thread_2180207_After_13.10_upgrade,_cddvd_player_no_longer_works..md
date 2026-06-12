---
title: "After 13.10 upgrade, cd/dvd player no longer works..."
date: 2013-10-12
forum: Ubuntu Development Version
---

### Post by Baldrick_NZ on 2013-10-12
Hi all,

Any tips to get this going again please?

It spins breifly, but then nothing. It does it with CD's, DVD's and iso's.

Any help much appreciated!

---

### Post by varunendra on 2013-10-13
> **Baldrick_NZ said:**
> It spins breifly, but then nothing. It does it with CD's, DVD's and iso's.

Please explain the problem in detail. By "player", do you mean the software player? Like VLC or "Movie Player"?

And what kind of CD/DVDs? Just the video ones or even the data CD/DVDs?

As much details as possible, it is hard to make assumptions with what you have provided.

---

### Post by Baldrick_NZ on 2013-10-13
Thanks for the reply..

Nothing works. You put in a CD or DVD or data disc, home-made or bought, it makes no difference.

The CD drive whirrs for a few seconds, settles down and nothing further happens.

A quick check in nautilus, and the drive doesn't show up. Under Settings/Disk, the drive is listed.

I'm using GS3.8.

---

### Post by varunendra on 2013-10-13
That sounds like the physical drive and physical disc problem. You also mentioned "iso's" - that's what confused me. Could you please also explain what you mean by ISOs ?

As for the drive issue, the first thing to check would be the drive's physical status. Do you have a bootable CD/DVD? Can you boot from it?

---

### Post by Baldrick_NZ on 2013-10-13
> **varunendra said:**
> That sounds like the physical drive and physical disc problem. You also mentioned "iso's" - that's what confused me. Could you please also explain what you mean by ISOs ?

As for the drive issue, the first thing to check would be the drive's physical status. Do you have a bootable CD/DVD? Can you boot from it?

Not a Linux one, but I have a XP one somewhere. Will that help?

What alerted me to this issue was when I tried to burn a copy of Fedora to DVD using the DVD drive.

---

### Post by varunendra on 2013-10-13
Yes, any bootable cd would do. We only need to make sure the drive itself is able to read the disks. If the system boots with the xp cd, then the drive is fine and we need to look into the OS for the problem.

And I don't know what a GS3.8 is. Is it a laptop, desktop or something else?

---

### Post by cariboo on 2013-10-13
When checking dmseg, do you get indication that the CD/DVD is detected? The output on my system on a DVD I had just ripped looks like this:

```
dmesg | tail -n5
[   44.413902] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.418788] skge 0000:01:09.0 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   47.418828] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   85.010541] UDF-fs: INFO Mounting volume 'AFTER_EARTH', timestamp 2013/08/16 23:00 (1e5c)
[ 1983.965911] UDF-fs: INFO Mounting volume 'AFTER_EARTH', timestamp 2013/08/16 23:00 (1e5c)

```

---

### Post by Baldrick_NZ on 2013-10-13
> **cariboo907 said:**
> When checking dmseg, do you get indication that the CD/DVD is detected? The output on my system on a DVD I had just ripped looks like this:

```
dmesg | tail -n5
[   44.413902] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.418788] skge 0000:01:09.0 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   47.418828] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   85.010541] UDF-fs: INFO Mounting volume 'AFTER_EARTH', timestamp 2013/08/16 23:00 (1e5c)
[ 1983.965911] UDF-fs: INFO Mounting volume 'AFTER_EARTH', timestamp 2013/08/16 23:00 (1e5c)

```

Thanks Cariboo907,

This it what I get...
```
baldrick@baldrick:~$ dmesg | tail -n5
[33245.892208] wlan0: associate with a4:b1:e9:9d:c5:ee (try 1/3)
[33245.895977] wlan0: RX AssocResp from a4:b1:e9:9d:c5:ee (capab=0x411 status=0 aid=2)
[33245.900484] wlan0: associated
[33349.517458] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:9d:c5:ed:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=6214 DF PROTO=2 
[33474.627688] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:b1:e9:9d:c5:ed:08:00 SRC=192.168.1.254 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=6215 DF PROTO=2 
baldrick@baldrick:~$ 

```

---

### Post by Baldrick_NZ on 2013-10-16
Solved by wiping drive and installing fresh version of Ubuntu Gnome 13.10. Working happily now. :-) Thanks for all your help though, very much appreciated!

---

