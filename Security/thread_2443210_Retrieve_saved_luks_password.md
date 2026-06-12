---
title: "Retrieve saved luks password?"
date: 2020-05-12
forum: Security
---

### Post by jonsson on 2020-05-12
This feels like a strange problem but I have a luks encrypted USB-disk and I *know* that one of my computers has the password saved, presumably in Kwallet. It used to be that whenever I plugged it in there would be a popup with the password already entered and all I had to do was press enter to mount it. This made me lazy and I forgot the password... Now, I *know* I have it written down *somewhere*, but that note is probably in some box that hasn't been unpacked in the 5 years since I last moved. Now what has happened is that the enclosure that the disk was in has died. It just doesn't work. The disk, however, seems fine if I put it in another enclosure. The problem with that is that now the computer doesn't recognize it and suggest the password anymore. I've had a look around in Kwallet but I can't find it. I find other saved passwords but not this one.The computer in question is running Kubuntu 16.04, but it must have been running an older version when the password was originally saved (2010-ish), if that might make a difference.

TLDR: Where might KDE have saved a luks password for a removable drive if it doesn't show up in Kwallet?

---

### Post by jonsson on 2020-05-12
Never mind, I guessed the password! It would still be interesting to know where the save one might be, though.

---

### Post by EuclideanCoffee on 2020-05-12
I believe you can find it via this command.

blkid -t TYPE=crypto_LUKS -o device

Then you can learn how to find the exact key from Red Hat.

[https://access.redhat.com/solutions/1543373](https://access.redhat.com/solutions/1543373)

---

