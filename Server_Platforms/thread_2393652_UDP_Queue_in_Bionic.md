---
title: "UDP Queue in Bionic"
date: 2018-06-06
forum: Server Platforms
---

### Post by trevor-francis on 2018-06-06
We have noticed that since upgrading a few hundred servers to Bionic, the rx_queue in /proc/net/udp is now reporting a queue, regardless of system load and regardless of what applications are running on it. The tx_queue is always 0, but rx_queue has seemingly random spikes of udp queueing. This is observed across hundreds of servers with either varying or no workload. Is this a kernel bug or a different way that the kernel now counts udp metrics?

netstat -nl|grep ^udp
udp     4352      0 0.0.0.0:68              0.0.0.0:*

[COLOR=#000000][FONT=Helvetica]  sl  local_address rem_address   st tx_queue rx_queue tr tm->when retrnsmt   uid  timeout inode ref pointer drops[/FONT][/COLOR]
[COLOR=#000000][FONT=Helvetica]14645: 3500007F:0035 00000000:0000 07 00000000:0000C900 00:00000000 00000000   101        0 3367 2 ffff8da177fdcc00 0


This behavior did not show up in Xenial and it is giving us cause for concern, although this doesnt appear to have a meaningful impact on performance. It does, however, impact our monitoring of udp-intensive applications.[/FONT][/COLOR]

---

### Post by slickymaster on 2018-06-06
Thread moved to **Server Platforms** for a better fit

---

### Post by Doug S on 2018-06-06
> **trevor-francis said:**
> We have noticed that since upgrading a few hundred servers to Bionic, the rx_queue in /proc/net/udp is now reporting a queue, regardless of system load and regardless of what applications are running on it. The tx_queue is always 0, but rx_queue has seemingly random spikes of udp queueing. This is observed across hundreds of servers with either varying or no workload. Is this a kernel bug or a different way that the kernel now counts udp metrics?I confirm your findings on my 16.04 test server with any kernel >= 4.15, including 4.17
kernels <= 4.14 are O.K.

I do not know if this is a kernel bug or a change in how it counts stuff. I'll search for a bug report and/or bisect the kernel to isolate the actual commit.

---

### Post by trevor-francis on 2018-06-07
FWIW, we tested with Fedora...and it is doing the same thing. This appears to be kernel related.

---

### Post by Doug S on 2018-06-07
> **trevor-francis said:**
> FWIW, we tested with Fedora...and it is doing the same thing. This appears to be kernel related.It is for certain in the kernel. I am about 1/2 way through a kernel bisection.

---

### Post by trevor-francis on 2018-06-07
Filed Kernel Bug:

[https://bugzilla.kernel.org/show_bug.cgi?id=199963](https://bugzilla.kernel.org/show_bug.cgi?id=199963)

---

### Post by Doug S on 2018-06-07
> **trevor-francis said:**
> Filed Kernel Bug:

[https://bugzilla.kernel.org/show_bug.cgi?id=199963](https://bugzilla.kernel.org/show_bug.cgi?id=199963)Hmmm... I am just getting to commit 0d4a6608f68c7532dcbfec2ea1150c9761767d03, but I also see [here]("https://www.mail-archive.com/netdev@vger.kernel.org/msg239743.html") That someone has already figured it out.

---

### Post by trevor-francis on 2018-06-07
Updating response here, as a good netizen.:

[https://www.mail-archive.com/netdev@vger.kernel.org/msg239743.html](https://www.mail-archive.com/netdev@vger.kernel.org/msg239743.html)

---

