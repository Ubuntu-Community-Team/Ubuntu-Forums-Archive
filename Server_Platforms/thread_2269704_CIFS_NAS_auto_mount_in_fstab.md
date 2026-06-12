---
title: "CIFS NAS auto mount in fstab"
date: 2015-03-17
forum: Server Platforms
---

### Post by scott.bouch on 2015-03-17
Hi, having trouble auto re-mounting my NAS to my server when I reboot...

Running this command in terminal works to mount it after a reboot:
```
mount -t cifs //My.NAS.I.P/Volume_1 /mnt/nas
```

I've tried configuring fstab a few failed ways, the current failed method is:
```
//My.NAS.I.P/Volume_1 /mnt/nas cifs guest,uid=1000,iocharset=utf8 0 0
```
(All the failed methods are just from what google results I've found..)

Any hints as to how I can improve things?

Cheers, Scott.

---

### Post by darkod on 2015-03-17
I'm not sure if the options guest and uid are compatible because they might not match on the system. Also since network share depends on the network service running first you need to add the _netdev option. That tells it to wait for network before it tries mounting.

So try dropping the uid and adding the _netdev. If that works try adding the uid and test again.

---

### Post by nerdtron on 2015-03-18
add _netdev on mount options on fstab so that it will wait for the network to initialize before mounting the shares.

---

### Post by samsonluk on 2015-03-18
Try using  guest,uid=nobody,iocharset=utf8,file_mode=0777,dir_mode=0777,noperm

---

### Post by scott.bouch on 2015-03-20
Here 's an interesting thing: last night I tried re mounting the NAS using the following line in terminal, and it failed... which is odd as it normally works.

mount -t cifs //My.NAS.I.P/Volume_1 /mnt/nas

I then tried it again, but added "-o guest" and it worked. Something has changed, and I don't know what.

This may help with the fstab issue.

---

