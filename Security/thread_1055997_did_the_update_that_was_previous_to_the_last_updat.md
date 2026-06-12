---
title: "did the update that was previous to the last update (from now) require restart?"
date: 2009-01-31
forum: Security
---

### Post by q.dinar on 2009-01-31
did the update that was previous to the last update (from now) require restart?
can update packages be replaced by replacing update server to hack my system?
can i check from a web-site the last updates? what packages they was?

---

### Post by SnakeHips on 2009-01-31
> **q.dinar said:**
> did the update that was previous to the last update (from now) require restart?
Generally speaking Ubuntu will suggest a restart if its essential that you do. In my case I always restart after updates.
> **q.dinar said:**
> 
can update packages be replaced by replacing update server to hack my system.
Not sure I fully understand the question
> **q.dinar said:**
> 
can i check from a web-site the last updates? what packages they was?
Should be no need if you know what you are updating ??

---

### Post by Nepherte on 2009-01-31
It pretty much comes to this: to use the updated software, you need to restart that piece of software. So if firefox is updated, you restart firefox (not the computer). If something like the kernel is updated, you need to reboot as it's the only way to restart the kernel.

---

### Post by jerome1232 on 2009-01-31
> **q.dinar said:**
> 
can update packages be replaced by replacing update server to hack my system?


No, the packages are signed by a private key, you have the public key, the public key can be used to determine if those packages have been signed by the private key or not. If packages are found to not be signed by the private key you will be warned about the packages not being authenticated.

---

### Post by q.dinar on 2009-02-01
i had suspected that my linux is hacked and have reinstalled it. now i have compared two directories: now just /boot and that of the old. and i have seen different binary files with equal names here! these files are different except menu.lst : initrd.img-2.6.27-7-generic and initrd.img-2.6.27-11-generic . i have not yet seen their content difference. their sizes are also different, and the new installation's are bigger.
initrd.img-2.6.27-7-generic :
new: 8206478, old: 8186116.
initrd.img-2.6.27-11-generic :
new: 8207213, old: 8191776. (bytes).
md5 sums:
initrd.img-2.6.27-7-generic :
new: 2d8170dd8e651d9e5b6562c870931b66, old: 217d13398ee4edf5bc36759f0fb3e9e5.
initrd.img-2.6.27-11-generic :
new: 491d4a95b11abaeabbf4c1fa6ebd861b, old: 82444291e15c83aa10de6fd33a336c1e.

---

### Post by q.dinar on 2009-02-01
and files in /lib/modules/2.6.27-7-generic and /lib/modules/2.6.27-11-generic are different.

---

### Post by teddks on 2009-02-01
If you're keeping current with intrepid, there was a kernel update not too long ago, which means you would have to reboot (otherwise the new kernel wouldn't load) and obviously a new kernel would be added to the system.

If you didn't get any warnings about authentication, you're fine.

---

### Post by q.dinar on 2009-02-02
now i install some programs again. would not it be unsecure if i copy some needed files from /var/cache/apt/archives of the old installation? (instead of downloading it again) (and is it possible?). for example a 25 mb java package has just been downloaded though i probably have it in the old installation's cache. yes, it is there.
but i think it works. i am going to try this way next time i install something like that.

---

### Post by Nepherte on 2009-02-02
Yup that should work. Apt first looks in the cache directory to see if it has downloaded the file already, if not it will attempt to download it from the repositories. If you copy the deb file of the old install to the cache directory of the new install it will detect it as "already downloaded".

---

