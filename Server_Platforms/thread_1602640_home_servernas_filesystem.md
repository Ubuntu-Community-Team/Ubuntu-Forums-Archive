---
title: "home server/nas filesystem"
date: 2010-10-21
forum: Server Platforms
---

### Post by TheVillain9 on 2010-10-21
What is the recommended filesystem to use when creating a home server/nas?

I'd be sharing files using SAMBA, DLNA Server or some sort of streaming. I'll have two win7 laptops, 2 ubuntu desktops and ps3 accessing the files.  Most of the time the server will just 75% read from 25% writing.

Would ext4 be an ideal?

---

### Post by CharlesA on 2010-10-21
I use ext4 on my file server. It really doesn't matter since you are using Samba.

---

### Post by redmk2 on 2010-10-21
> **TheVillain9 said:**
> What is the recommended filesystem to use when creating a home server/nas?

I'd be sharing files using SAMBA, DLNA Server or some sort of streaming. I'll have two win7 laptops, 2 ubuntu desktops and ps3 accessing the files.  Most of the time the server will just 75% read from 25% writing.

Would ext4 be an ideal?

EXT4 will work, but XFS is better for video and audion files.  See [**_here_**]("http://en.wikipedia.org/wiki/XFS").

---

### Post by TheVillain9 on 2010-10-21
why does it not matter what filesystem i use when using samba? (sorry for the newb question)

---

### Post by CharlesA on 2010-10-21
> **TheVillain9 said:**
> why does it not matter what filesystem i use when using samba? (sorry for the newb question)

The host deals with the file system, not the clients. The clients will only see what shares you have defined.

---

