---
title: "pptp vpn very slow"
date: 2013-05-10
forum: Server Platforms
---

### Post by icu12345 on 2013-05-10
I am having trouble with my vpn connection (had also some other connectivity issues [here]("http://ubuntuforums.org/showthread.php?t=2141623&page=2")). It's a real simple setup: one dd-wrt router acting as a pptp vpn server. When I connect to the server via my ubuntu 13.04 laptop and try to copy some files from the remote network I get extremely low speed (100-200 KB/s). If I use a very similar laptop which is running windows (in the same LAN as the ubuntu laptop) and try to copy the same data from the same remote location via the same vpn connection, the copy speed I get is about 1 MB/s.

What could be wrong?

The settings at the moment are like this:

[IMG]http://img90.imageshack.us/img90/7405/screenshotfrom201305101.png[/IMG]

Use Point-to-Point encryption must be checked, because the server is set up to reject not encrypted connections. Tried playing with the other options (stateful encryption, BSD data compression, Deflate data compression and TCP header compression) but there was no difference... Also tried send PPP echo packets but it didn't bring anything..

now here's the dd-wrt setup...

[IMG]http://img7.imageshack.us/img7/92/selection002ax.png[/IMG]

Please keep in mind that I'm very new to linux so I'd ask you to please bear with me and give me detailed explanation what to try... Thank you!

---

### Post by stmiller on 2013-05-12
You might experiment with MTU settings inside dd-wrt and bump it up to say, 1500. Then see if the VPN works any better.

---

### Post by icu12345 on 2013-05-13
It's currently set to 1500....

---

### Post by d4m1r on 2013-05-13
What kind of router is it? Make + model. Also, what kind of partition is the data stored on? If you are transferring stuff from an NTFS partition under Ubuntu, it is indeed unfortunately much slower than under Windows.

---

### Post by icu12345 on 2013-05-14
Dlink DIR-615.
Yes, I am indeed transferring files from a windows machine (NTFS) to a linux laptop (ext4)... Would be really unfortunate if this was the reason...

---

### Post by icu12345 on 2013-05-15
> **d4m1r said:**
> What kind of router is it? Make + model. Also, what kind of partition is the data stored on? If you are transferring stuff from an NTFS partition under Ubuntu, it is indeed unfortunately much slower than under Windows.

> **icu12345 said:**
> Dlink DIR-615.
Yes, I am indeed transferring files from a windows machine (NTFS) to a linux laptop (ext4)... Would be really unfortunate if this was the reason...

What could I possibly do? I doubt that this is all due to the different file systems because when I copy files from ntfs to ext4 across a local network I get 1 GB/s and even more..

Could I achieve something through samba?

---

### Post by icu12345 on 2013-05-19
> **stmiller said:**
> You might experiment with MTU settings inside dd-wrt and bump it up to say, 1500. Then see if the VPN works any better.

I need to correct my statement.. turned out it was set to 1400, NOT to 1500. However, I tried various mtu sizes - 1460, 1492, 1500, etc. but none of this led to any improvement. The windows machines also have mtu size set to 1400 and get 8-10 times better speed..

What else can I try? I'm getting really desperate..

---

