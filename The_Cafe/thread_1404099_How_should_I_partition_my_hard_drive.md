---
title: "How should I partition my hard drive?"
date: 2010-02-11
forum: The Cafe
---

### Post by gymophett on 2010-02-11
I have a 250 GB HD. I am going to dual-boot Win7 and Ubuntu 9.10
However, I want to share files between the two. Should I give Win7 20GB, Ubuntu 9.10 20GB then have 210 GB partition for all of my files, games, music, videos, etc?
Or should I go another way about this?
Thanks.

---

### Post by bleeding±the±dead on 2010-02-11
> **gymophett said:**
> I have a 250 GB HD. I am going to dual-boot Win7 and Ubuntu 9.10
However, I want to share files between the two. Should I give Win7 20GB, Ubuntu 9.10 20GB then have 210 GB partition for all of my files, games, music, videos, etc?
Or should I go another way about this?
Thanks.

get a 2nd hdd.

---

### Post by gymophett on 2010-02-11
> **bleeding±the±dead said:**
> get a 2nd hdd.

I have an external HD, but I now use it on a media center rig. 
This is a laptop, so no second HD.

---

### Post by bleeding±the±dead on 2010-02-11
> **gymophett said:**
> I have an external HD, but I now use it on a media center rig. 
This is a laptop, so no second HD.

my bad, sorry.

---

### Post by gymophett on 2010-02-11
> **bleeding±the±dead said:**
> my bad, sorry.

No problem. You were only trying to help :D

---

### Post by bleeding±the±dead on 2010-02-11
> **gymophett said:**
> No problem. You were only trying to help :D

(y)

install windows 7 first ;]

---

### Post by megamania on 2010-02-11
> **gymophett said:**
> I have a 250 GB HD. I am going to dual-boot Win7 and Ubuntu 9.10
However, I want to share files between the two. Should I give Win7 20GB, Ubuntu 9.10 20GB then have 210 GB partition for all of my files, games, music, videos, etc?

There are several options. The easiest one is to have two partitions: one for Ubuntu (20gb should be enough) and the other one for win 7 and all your data.

However, a third partition for data would be useful in case you want to reinstall. So, I'd say 20gb ntfs + 20gb ext3 + 210gb ntfs, as you said.

Keep in mind that you can move windows' "my documents" folder to another partition, so it could directly point to the 210gb partition (don't ask me the steps to do this though, since I don't use windows - I just know it is pretty simple in win 7).

---

### Post by Gallahhad on 2010-02-11
> **gymophett said:**
> I have a 250 GB HD. I am going to dual-boot Win7 and Ubuntu 9.10
However, I want to share files between the two. Should I give Win7 20GB, Ubuntu 9.10 20GB then have 210 GB partition for all of my files, games, music, videos, etc?
Or should I go another way about this?
Thanks.
Half and half is pretty realistic. On Windows half, just one big NTFS partition. On Ubuntu's half give / about 20gb, Swap >=RAM, and the rest to /home.

If your going to use and enjoy Win7, don't cripple it with a too small partition. Games, movies, and other media tend to be hard disk hogs.

Gallahhad

---

### Post by megamania on 2010-02-11
> **Gallahhad said:**
> Half and half is pretty realistic. On Windows half, just one big NTFS partition. On Ubuntu's half give / about 20gb, Swap >=RAM, and the rest to /home.

Since he said he wants to share files, there's no real need to partition the drive 50% win and 50% ubuntu. Also, no particular need to have a separate /home in this situation (he can just "tar" it and back it up to the shared partition when reinstalling).

Windows doesn't get along particularly well with ext3 - there are solutions, but I'd suggest using NTFS as a shared partition.

---

