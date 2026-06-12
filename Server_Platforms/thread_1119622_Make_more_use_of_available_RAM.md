---
title: "Make more use of available RAM"
date: 2009-04-08
forum: Server Platforms
---

### Post by Deschutes on 2009-04-08
Hi,

I currently use a Pentium 2 350 MHz with 512 Mb SDRAM as a media- and fileserver. 
Having 512 Mb RAM is nice but my server never uses it. Idle, it uses 40 Mb (LAMP, SAMBA, FTP, ...). Playing a HD movie, stored on the server, on a remote PC while backing up another PC on the server it goes up to 140 Mb of RAM use.

But, I have a severe bottleneck in writing speeds on my server.
I get like 4 MegaBYTE/s write speeds. Which is caused by the high CPU use of samba and the ntfs-3g driver. CPU stays steady at 100% load while writing.

Isn't there an option to use this RAM as a buffer in file transfers? For files copied that are smaller then the available amount of free RAM, it could  cache them. This way I could maybe saturate my 100 Mbit connection...

(Other tips to cache more in RAM are allso welcome)

Thanks in advance

---

### Post by BkkBonanza on 2009-04-08
The linux kernel already uses any free memory for disk caching. This is automatic without user intervention. Anything read from disk is kept in memory until that memory is needed for something else. If you read and send the same file over and over then after the first time it will come from RAM. Nothing you can do about the first read though. If you want more control over what stays in cache and what doesn't then you can add various other types of caching but what and how depends on what exactly you're doing. For servers people often use Memcached, but whether that will help depends on the situation.

---

