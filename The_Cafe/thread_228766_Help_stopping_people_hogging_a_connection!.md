---
title: "Help stopping people hogging a connection!"
date: 2006-08-03
forum: The Cafe
---

### Post by xerxesv5 on 2006-08-03
Hi all,

I run a small network and I have a friend who shares my connection. This friend insists on using peer-to-peer software and downloading torrents during peak times (evenings and weekends), and the connection slows to unusable speeds for every other machine.

1) Social engineering has not worked, he pays for a small portion of the connection cost and I need that help as telecoms in South Africa have horrendous costs associated, especially for a student.

2) My IPCop router's "Traffic Shaping" doesn't do a thing (if anything it slows the whole lot down).

3) I tried implimenting shaping using tc ([http://lartc.org](http://lartc.org)) on the router, that also seems to make no difference to me.

4) He's running a Mac, says he's looked for limiting apps and hasn't found anything decent.

I'm so sick of not being able to do anything short of unplugging him. Any ideas, ANYTHING is welcome at this point. A distro, a package, a script, a way to slow the outbound adapter down. ](*,)  100B/s sucks for ubuntu updates. =)

Thanks for the read!
- xerxesv5

---

### Post by eXisor on 2006-08-03
What router are you using?

---

### Post by mips on 2006-08-04
[http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html)

---

### Post by peabody on 2006-08-06
I'm curios...if the only p2p he's using is bittorrent, he's lying if he says he's found no bandwidth limiting.  Even the default client has bandwidth limiting.  And to my knowledge, there definitely is bandwidth limiting for Mac OS in general.

In my opinion, you should work on that instead of dealing with bandwidth limiting on a router.  It's a pain in the *** and error prone and likely to mess with his non-p2p networking stuff.

---

### Post by Ocxic on 2006-08-06
if he uses bittorrent you can login to the router, and block his listen port that will severly limit his connections to peers. then set a password on the router, and see if he will come to an agreement then.

---

### Post by huygens on 2006-08-14
Hi,

Instead of blocking the port, which could be your last solution. You could ask him to use [Azureus]("http://azureus.sourceforge.net/"), it is also available on Mac OS X (it is Java based), quite neat and allow the user to control upload and download speed. So he could limit itself to some small speed when there is a rush hour.
I think (but as I am not a deep user of these things, I'm not sure) that there is a kind of scheduling (or native or by plug-in) to change automatically the download/upload speed at certain time. Thus, that would be a good solution for your mate and yourself :)

Huygens

---

### Post by mips on 2006-08-14
He might have lost interest...

---

