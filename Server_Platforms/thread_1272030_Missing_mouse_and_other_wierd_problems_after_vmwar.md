---
title: "Missing mouse and other wierd problems after vmware tools install and removal"
date: 2009-09-21
forum: Server Platforms
---

### Post by kanaida on 2009-09-21
I created a virtual server in vmware 1.09 (server 2003 host), the guest is my ubuntu 8.04 LTS server.
 
I installed everything and it was fine for a while, I installed vmware tools but noticed that the vmxnet driver didn't compile ok, and I need the network acceleration...
 
I deided to try open-vm-tools from their ftp, it compiled some stuff, and also installed an older kernel for some reason.
 
after playing with kernel packages for a little while at an attempt to simply have 2.6.24-24, the latest kernel available - things got weird.
 
now I can't use the mouse inside of x, 
I can't mouse samba shares (gives me a cif's error), 
 
when i try to do a "sudo mount /media/cdrom" 
I get : mount: unknown filesystem type 'iso9660' 
This one is what gives away that some sort of missing package or driver problem has occured.
 
It's not an option to re-install this server from scratch, I need some suggestions...
how can i make sure all the packages that came with ubuntu are there, as well as the latest server kernel with all the drivers etc... ?
 
another thing i noticed after comparing a fresh install (with all updates) to my existing server was the /dev/input only has:
mice
 
the fresh install has:
by-path event0 event1 event2 event3 event4 event5 mice mouse0 mouse1
 
please help i'm pulling my hair out on a deadline :confused:

---

### Post by kanaida on 2009-09-21
I forgot to mention, I can no longer mount smb shares in fstab (even though they were working previously, and smbmout can browse them)

---

