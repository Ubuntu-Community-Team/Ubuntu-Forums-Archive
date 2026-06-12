---
title: "us.archive.ubuntu.com down?"
date: 2005-04-09
forum: Repositories &amp; Backports
---

### Post by Dustin Wyatt on 2005-04-09
In the middle of upgrading to hoary it appears that us.archive.ubuntu.com has lost connectivity.

```
Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out

```

and (from my Windows box obviously...)

```
C:\WINDOWS>ping us.archive.ubuntu.com

Pinging us.archive.ubuntu.com [216.165.129.138] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 216.165.129.138:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

```


Is this just me or is it really down?  If it's down can I just issue sudo apt-get dist-upgrade again later without fear or breaking anything?

---

### Post by gw90se on 2005-04-09
I went to download the iso last night and it was down, so I went to a mirror site to get it. Guesss the new release is generating a whole lot of traffic. 

You should be able to complete it later, but I'm not 100% positive. Maybe someone else will know for sure.

---

### Post by jdong on 2005-04-09
All the Ubuntu sites have been under heavy load due to the recent release. :)

---

