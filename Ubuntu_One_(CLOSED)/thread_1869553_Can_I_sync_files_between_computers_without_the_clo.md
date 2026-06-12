---
title: "Can I sync files between computers without the cloud storage?"
date: 2011-10-25
forum: Ubuntu One (CLOSED)
---

### Post by NJC_EE on 2011-10-25
I am looking to drop Windows Live Mesh and have been playing around with Ubuntu One. So far I love it, but I can't seem to find a way to sync folders between my computers and bypass the online (5GB) storage. I have about 150GB I need to sync between 5 computers, only about 4GB worth of it needs to be on the cloud.

Is this possible? I remember reading somewhere that in 11.10, this might be possible. If this feature is not implemented yet, does anyone have any idea when we can expect to see this?

---

### Post by papibe on 2011-10-25
Hi NJC_EE. Welcome to the forums!

You can sync your computers directly either from one to another, or all from and to a LAN server. There are several alternatives depending on your needs:

- rsync for mirroring would be my first suggestion. Work best over OpenSSH.
- Unison it is more sophisticated if you need perfect two-way synchronization instead of mirroring.

Hope that helps,
Regards.

---

### Post by docbop on 2011-10-25
That looks like a very cool tool.

Does it transfer delta's like rsync or the whole file.

---

### Post by papibe on 2011-10-25
Indeed, Unison does intelligent transfers. Here's from their [web]("http://www.cis.upenn.edu/~bcpierce/unison/") page:
> Unison works between any pair of machines connected to the internet, communicating over either a direct socket link or tunneling over an encrypted ssh connection. It is careful with network bandwidth, and runs well over slow links such as PPP connections. Transfers of small updates to large files are optimized using a compression protocol similar to rsync. 
BTW, it is in the Software Center ;)

Regards.

---

