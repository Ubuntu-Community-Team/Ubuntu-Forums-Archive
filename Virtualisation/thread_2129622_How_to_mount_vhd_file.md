---
title: "How to mount vhd file"
date: 2013-03-26
forum: Virtualisation
---

### Post by MaxLinuxLover on 2013-03-26
I have files on a vhd that I want to put in a flash drive, but VirtualBox will not recognize the flash drive so I must mount the vhd.

here is the info of my vhd
My vhd contains Windows XP
it is 32GB
It is .VHD file type

If I can access the files safely, then please tell me how to do it.
thanks in advance

 my os is ubuntu 12.10

---

### Post by Ceiber Boy on 2013-03-30
You could copy them to network storage with your vm. Then download them to anotyer machine.
Vurtual box has a shared folders option. Allowing you to copy files straight from guest to host.
I also thought a saw once a program in the ubuntu repository that allowed virtual hard disk files to be mounted as real hard disks (although not sure as ive never used it)
f

---

### Post by MaxLinuxLover on 2013-03-31
Thanks Ceiber Boy, it worked. You need VirtualBox Guest Additions, which I already have.

---

