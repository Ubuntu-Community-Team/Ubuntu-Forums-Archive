---
title: "Encrypted Partition and SAMBA - Problem?"
date: 2011-07-09
forum: Security
---

### Post by H4rm0ny on 2011-07-09
I set up an encrypted partition on my home server using LUKS with AES. Mounts okay, all seems okay locally and over SSH.

When I come to try and share the mounted partition via SAMBA, the share is visible to my other Linux box and my Windows box, but permission is denied to access it. I've created other locations with the same permissions which I can access from the same boxes and with the same accounts. The only thing I've been able to narrow it down to as different, is that it is a mounted encrypted system. Does anyone know if there is a reason why this wouldn't be possible? And if it should be, can anyone suggest the next thing to check as I'm at a loss from here on.

I'm not an expert on either SAMBA or encrypted partions, so stupid errors are a possibility. I have checked that I can read and write from the mounted directory as that user however.

It might seem odd that I go to the bother of encrypting a partition and then turn it into a SAMBA share, but it's really just intended as good practice security in case my home server got nicked (hopefully not).

I'm also open to suggestions of better ways to do this, but I need to access it from both Windows 7 and Linux boxes.

Thanks a lot for all help. I'm asking in this forum because I figured this was a question about security software. Apologies if it's the wrong place.

H.

---

