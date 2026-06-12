---
title: "shared folders help"
date: 2010-05-27
forum: Server Platforms
---

### Post by whitetimer on 2010-05-27
Hi All

I have ubuntu server as a guest in virtualbox and xubuntu as my host os.  I have a shared folder on my host that can be accessed by my network.  I'm trying to use my server without the need to install a desktop, so how would i transfer a file (in this case Coldfusion.bin ) from my host machine to my ubuntu server guest ?

Many Thanks

:popcorn:

---

### Post by mstjohn1974 on 2010-05-27
Hi there,

I would use scp

example:
scp Coldfusion.bin 192.168.1.100:/home/username/directory

This will work if the user accounts are the same on both boxes 
if that is not the case you have to specify a user account for the remote machine

scp Coldfusion.bin user@192.168.1.100:/home/username/directory

I hope that helps
[]("http://ubuntuvideocast.blogspot.com")

---

### Post by whitetimer on 2010-05-27
> **mstjohn1974 said:**
> Hi there,

I would use scp

example:
scp Coldfusion.bin 192.168.1.100:/home/username/directory

This will work if the user accounts are the same on both boxes 
if that is not the case you have to specify a user account for the remote machine

scp Coldfusion.bin user@192.168.1.100:/home/username/directory

I hope that helps


Hi ... Ok i just tried and i got this message

> The authenticity of host '192.168.1.65 (192.168.1.65)' can't be established.
RSA key fingerprint is 86:ea:fb:24:b8:49:bb:ca:9d:e6:bf:f3:e3:00:21:cd.Any suggestions ?

Sorted ... I tried to use sudo infront ... duh ... haha

Thanks for your advice, it works great !!!

---

### Post by mstjohn1974 on 2010-05-27
you do it from the machine where the file is located

---

### Post by mstjohn1974 on 2010-05-27
you can get information for the usage of scp by typing

man scp

or on this [webpage]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/04eaff076bce249dca256fb6007f53e5?OpenDocument")

---

### Post by whitetimer on 2010-05-27
> **mstjohn1974 said:**
> you can get information for the usage of scp by typing

man scp

or on this [webpage]("http://www.lesbell.com.au/Home.nsf/b8ec57204f60dfcb4a2568c60014ed0f/04eaff076bce249dca256fb6007f53e5?OpenDocument")


Thanks for the link, i have it sorted now 

Cheers :popcorn:

---

