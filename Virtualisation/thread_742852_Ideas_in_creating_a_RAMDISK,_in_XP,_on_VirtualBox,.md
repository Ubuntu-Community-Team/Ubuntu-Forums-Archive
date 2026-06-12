---
title: "Ideas in creating a RAMDISK, in XP, on VirtualBox, on Ubuntu"
date: 2008-04-02
forum: Virtualisation
---

### Post by drhiii on 2008-04-02
I have some approaches, but wanted to ask of this group: 

Anyone have a recommendation for creating a RAMdrive under XP, under... well, as the subject states. I have a need to utilize a small Ram drive instead of hard drive, for a demo of sorts. 

Anyone have experience in this scenario and can make recommendations? 

tx a mil

---

### Post by jms1989 on 2009-04-03
I heard there is a driver from MS that can create a ram disk but I didn't have any success with making it work on windows. I do know you can create one under linux by mounting one with tmpfs to a directory on your hdd.

Something like (sudo mount -t tmpfs -o size=256MB /ramdisk) will create a 256MB ram disk at /ramdisk on your hdd. The fstab equivalent, (none /ramdisk tmpfs nodev,nosuid,noexec,nodiratime,size=256M,rw 0 0) to create one at bootup. Note the lack of the letter B in the fstab line. I don't know why its missing but if you add a B to it, you will experience a error while booting.

I'm looking for ideas for using a ramdisk. I've got a 512MB ramdisk setup but no uses pop into mind. :(

EDIT: Opps, I didn't realise that this post was over a year old till after I posted. Heh.

---

