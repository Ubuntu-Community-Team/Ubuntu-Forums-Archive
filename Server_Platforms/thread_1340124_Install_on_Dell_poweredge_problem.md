---
title: "Install on Dell poweredge problem"
date: 2009-11-28
forum: Server Platforms
---

### Post by kaspar_silas on 2009-11-28
I am planning on switching a small cluster of Dell poweredge 2900 servers to 64bit ubuntu 9.10 from opensuse 10.2. I done a test on one server on friday. It did not go well.

I did the install and it seemed to go went. However on restart Grub gave Error 22. Unfortunately the server edition didn't have a live option (or I did not see it). So I tried using a 8.10 live CD I had on me to fix the grub. Unfortunately this can't mount the ext4 file-system.

So I am going to fix this early on monday morning. However I won't have so long to do this so I thought I would see if anyone can point me in the right direction. Firstly has anyone had this problem before with 9.10 server? Secondly if anyone sees anything wrong or has any better ideas than the following plan please let me know.

So my Current plan:
-Download and burn a 9.10 liveCD.
-Boot up live version
-hopefully mount the hard-drive (a 80Gb Sata) on which I installed the OS
-chroot the mounted drive as /bin/bash
-restore grub in the normal root(), setup() way
-restart with fingers crossed.

All help or pointers are greatly appreciated.

---

### Post by kaspar_silas on 2009-11-29
Just a thought but has anyone even had this grub error 22 on a clean install of 9.10 server version before. I did reinstall a few times and always ended up with this message.

EDIT: O plus if the above recipe has worked for anyone previously let me know. I'd like to know the odds of success.

---

### Post by kaspar_silas on 2009-11-29
Hhhm, just discovered this link:

[http://webapps.ubuntu.com/certification/list/?category=Server](http://webapps.ubuntu.com/certification/list/?category=Server)

apparently Dell's Power Edge 2900 only supports 9.04 and 8.04LTS. Bit annoying this, why was support removed in a succeeding version. Surely what ever is unsupported should fall back to the old supported version.

Sod it I am going to go to 8.04-LTS.

---

### Post by kaspar_silas on 2009-11-30
Humble pie time. 

Ubuntu 9.10 64bit server works perfectly on a dell power edge. Perfect that is if you boot from the hard drive you actually installed it on.

O the shame!

---

