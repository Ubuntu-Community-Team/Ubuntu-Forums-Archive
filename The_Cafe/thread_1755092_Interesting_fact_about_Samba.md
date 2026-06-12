---
title: "Interesting fact about Samba"
date: 2011-05-10
forum: The Cafe
---

### Post by timZZ on 2011-05-10
I have been using samba for my windows share with the assumption this was faster than sftp.

Interesting fact: on my systems at least sftp is faster than samba shares.

---

### Post by jerenept on 2011-05-10
wat? i sense something is missing here.

Are you transferring a large file, or a lot of small files?

---

### Post by timZZ on 2011-05-10
I would be interested in someone elses results.

I expected the encryption to be the bottle neck.

---

### Post by jerenept on 2011-05-10
Not that, FTP is incredibly inefficient at beginning and ending transfers. I doubt the encryption has a large effect.. (also, afaik, samba is encrypted too)

---

### Post by 3Miro on 2011-05-10
Samba (and the whole windows thins) runs a lot of overhead. And Encryption is not a problem so long as you have a fast CPU.

The type of the transfer would make a bigger difference, do you do one large file or many small ones.

---

### Post by PhillyPhil on 2011-05-11
I have a disk plugged into my router, mounted as a samba share, and am very disappointed with the transfer speeds.  
Usually less than 6 MB/sec for large files...

---

### Post by Grenage on 2011-05-11
> **PhillyPhil said:**
> I have a disk plugged into my router, mounted as a samba share, and am very disappointed with the transfer speeds.  
Usually less than 6 MB/sec for large files...

On a home router, that's not uncommon; a decent switch connected to the router will give far greater performance.  It it's a GB switch, then far and above.

> **timZZ said:**
> I would be interested in someone elses results

Samba is marginally slower than a direct SCP, on my machines.

---

### Post by PhillyPhil on 2011-05-11
> **Grenage said:**
> On a home router, that's not uncommon; a decent switch connected to the router will give far greater performance.  It it's a GB switch, then far and above.

My "router" is a switch/broadband router combined in a single unit, from my ISP. The disk and the computer that has root access to the disk are both connected to the router with an ethernet cable.

So my router/switch is what's causing the slow transfer speeds? (It can't possibly be the disks or cables at either end.)
I'm amazed that it can't do much, much better than that...

---

### Post by Grenage on 2011-05-11
> **PhillyPhil said:**
> My "router" is a switch/broadband router combined in a single unit, from my ISP. The disk and the computer that has root access to the disk are both connected to the router with an ethernet cable.

So my router/switch is what's causing the slow transfer speeds? (It can't possibly be the disks or cables at either end.)
I'm amazed that it can't do much, much better than that...

Many home gateways can't; the ISPs are more interested in reliable internet connections than local transfers.  I had an old 10/100 netgear router that wouldn't top 5.5MB/s; I would have just bought a switch to connect to it, but it was so unreliable I ended up replacing it.

---

### Post by Icehuck on 2011-05-11
> **PhillyPhil said:**
> My "router" is a switch/broadband router combined in a single unit, from my ISP. The disk and the computer that has root access to the disk are both connected to the router with an ethernet cable.

So my router/switch is what's causing the slow transfer speeds? (It can't possibly be the disks or cables at either end.)
I'm amazed that it can't do much, much better than that...

Slow router speeds are generally only towards the WAN. Your LAN speeds should be just fine. There are a few issues with samaba and file transfer speeds. You'll most likely need to tweak samba to get better results.

You can look into adding

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

to the global section of your smb.conf file. You might need to tweak the buffer setting to improve performance.

---

### Post by sostentado on 2011-05-11
Depends upon your connection. Imagine a fiber optic connected lan to regular one. :)

---

