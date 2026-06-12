---
title: "Mounting Issues in Virtual Box with FreeNas"
date: 2014-06-20
forum: Virtualisation
---

### Post by Robert_lemm on 2014-06-20
Hello, first post so apologies if im in the wrong place etc.

Currently setting up a FreeNas file server and been suprsingly successful with getting it to work on Ubuntu but cant get it to work with the Virtual machine we're using.

On ubuntu i managed to get it to work using the nfs-common and then using a Sudo mount -t freeNasIp:/mnt/diskvol/foler /home/username/folder and it connects and shows the folders on the NAS. However when i try do this on the Xubuntu we use for developing it works fine installing the nfs-common but when running the command to mount the Nas it says permissions denied [mount.nfs: access denied by server while mounting 192.168.1.84:/mnt/Volume1/UnixPFS], i used the same command but changed the folder structure to match the virtual machine which in my head makes sense.

Does anyone know how to get it to work? 

Should mention im not super savy when it comes to linux and commands

Any help is appriciated guys thanks

---

### Post by TheFu on 2014-06-20
Does the server have an export that allows the new client machine?
An example:
Server "istar" /etc/exports:```

/D      lubuntu(rw,async,root_squash) romulus(rw,root_squash,async) hadar(rw,roo
t_squash,async) c720(rw,async,root_squash) c720w(rw,async,root_squash) 
```

Then from the clients, I use autofs. Here's lubuntu's setup:
/etc/auto.master:
```
/-      /etc/auto.nfs

```
/etc/auto.nfs:
```
/D -fstype=nfs,hard,intr,rw,async    istar:/D

```
Simple.

---

