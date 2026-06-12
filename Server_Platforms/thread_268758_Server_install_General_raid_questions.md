---
title: "Server install General raid questions"
date: 2006-09-30
forum: Server Platforms
---

### Post by Astro6312 on 2006-09-30
Hi all,

First post, some experience with ubuntu on laptop, desktop and one try on a vmware pc...

I am setting up a new server for a small office.  My hardware is the following:
- Dual core 3.2Ghz
- 2 Gig ram
- 3x 160Gig SATA2 HD

I want to setup Samba, HTTP, SSH, PHP and Mysql

My question is related to HD setup.  I was thinking of going for 2 drive in raid 1 (mirror) for my boot drive and the other drive for backup purposes.  My second option is going raid 5 on the 3 HD and boot from it and do my data backup on the same disk at night and the tgz files copied to DVD during the day.

So... What is the easy way of doing option1 raid 1 boot and is there a easy way of doing a raid 5 at boot time.

I have read this : [http://tinyurl.com/l35yh](http://tinyurl.com/l35yh) but not sure if I can apply it directly.  Not much experience with LVM, MD stuff the manual way.  I installed a lot of server on 3ware controllers, but wanted to try something else this time.

Any comments, help, pointers would be appreciated

Regards,

---

