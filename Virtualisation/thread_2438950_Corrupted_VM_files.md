---
title: "Corrupted VM files"
date: 2020-03-20
forum: Virtualisation
---

### Post by shdekap on 2020-03-20
After i changed the file name of    /home/user/VirtualBox VMs/SecCon/_New Folder_/Kalivirtual/Kalivirtual.vbox' for /New Folder then all my virtual devices had turned inaccesible then i changed the name again to precedent, nothing fixed so I wanted to create new machine from old ones .vdi but i forgot to mention Debian and created wit kali.iso disk so i deleted this machine completely.  There is new file appeared as kalivirtual.vbox-prev in the folder where kalivirtual.vbox are. So i copied .vbox-prev and pasted inside orginal .vbox. Now i get this error below for all my machines. 

   Runtime error opening '/home/user/VirtualBox VMs/SecCon/Yeni grup/Kalivirtual/Kalivirtual.vbox' for reading: -102 (File not found.).
 /build/virtualbox-p8NxA3/virtualbox-5.2.34-dfsg/src/VBox/Main/src-server/MachineImpl.cpp[745] (nsresult Machine::i_registeredInit())

---

### Post by deadflowr on 2020-03-20
*Thread moved to **Virtualization***

---

