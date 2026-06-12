---
title: "can't automount nfs @ boot"
date: 2007-10-27
forum: Server Platforms
---

### Post by Girya on 2007-10-27
I can manually mount my nfs with this command: 

sudo mount 192.168.1.100:/home /mnt/home

but when I edit my fstab file to mount at boot the nfs doesn't mount. here is the line in mt fstab file.

192.168.1.100:/home    /mnt/home nfs  auto rw,hard.intr	0	0

 if anyone  could look it over and give me any ideas that would be great, thanks

---

### Post by Girya on 2007-10-27
Answered my own question. the options for nfs are different than other file types. Here is the link that  explains everything

[http://linux.die.net/man/5/nfs](http://linux.die.net/man/5/nfs)

---

