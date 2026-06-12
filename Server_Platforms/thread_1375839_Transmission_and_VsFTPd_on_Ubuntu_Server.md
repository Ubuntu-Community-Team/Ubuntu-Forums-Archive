---
title: "Transmission and VsFTPd on Ubuntu Server"
date: 2010-01-08
forum: Server Platforms
---

### Post by Yuu on 2010-01-08
Hi !

I am running an headless Ubuntu Server 9.10 which works great.

I am using Transmission as my torrent client (my favourite !) and VsFTPd as my FTP server.

Everything works great excepted that I want to get Transmission and VsFTPd to use the same directory. My easiest choice would be using my root directory (the one from my own account, of course), as I use my server only as a torrentbox, but maybe does it cause security problems ?

SInce I am quite new to this (learned Linux two days ago), I am somewhat confused about how to achieve that, especially since it's the only thing I haven't sorted out yet. And yes, I crawled into wiki, tutorials, and all, but that part remains obscure for me. ^^

Thank you in advance for your kind answers.

---

### Post by HighCommander540 on 2010-01-08
> **Yuu said:**
> Hi !

I am running an headless Ubuntu Server 9.10 which works great.

I am using Transmission as my torrent client (my favourite !) and VsFTPd as my FTP server.

Everything works great excepted that I want to get Transmission and VsFTPd to use the same directory. My easiest choice would be using my root directory (the one from my own account, of course), as I use my server only as a torrentbox, but maybe does it cause security problems ?

SInce I am quite new to this (learned Linux two days ago), I am somewhat confused about how to achieve that, especially since it's the only thing I haven't sorted out yet. And yes, I crawled into wiki, tutorials, and all, but that part remains obscure for me. ^^

Thank you in advance for your kind answers.

All you have to do is make Transmission user your /home/*user* holder as the default. Because when you login with vsftp, it will automatically go to your home directory. IDK, how transmission does that, but just find the config file for it and set that.

---

### Post by Yuu on 2010-01-08
Well, I feel quite stupid, since it worked !

I just had to do a "chmod 777 /home/*user*" for getting it to work.

Thank you very much for your fast answer ! :-)

---

