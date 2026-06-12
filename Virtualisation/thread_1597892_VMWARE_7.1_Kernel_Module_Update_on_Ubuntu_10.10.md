---
title: "VMWARE 7.1 Kernel Module Update on Ubuntu 10.10"
date: 2010-10-15
forum: Virtualisation
---

### Post by 11cerealkiller26 on 2010-10-15
Guys, i install ubuntu 10.10, then my vmware 7.1..installation was fine..the only problem i noticed is when i run vware, it gives me an error for kernel module updater.. so what i did is to click install, then it shows stopping /starting the services.. so now vware starts..but when i close the program and run it again, always and always prompts me to install that thing.. anyone can help here? thanks in advance...

---

### Post by yuppy on 2010-10-16
i got same problem too, can anyone help ?

---

### Post by mising on 2010-10-17
This worked for me...
[http://communities.vmware.com/message/1627018#1627018](http://communities.vmware.com/message/1627018#1627018)
follow mirla's instructions in the third post

---

### Post by tejdig on 2010-10-28
Hi There,

if you are using 2.6.35-22-generic-pae kernel than following link will help

[http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10](http://www.debuntu.org/how-wmware-workstation-7.1-ubuntu-maverick-meerkat-10.10)

TJ

---

### Post by Nevill.Burn on 2010-10-30
The third link is to one somewhere in the middle, I've linked to the  comments page so you can make your own choice based on if anything there  affects you.

---

### Post by alomari on 2010-11-22
try this
wget [http://communities.vmware.com/servlet/JiveServlet/download/1553530-39784/patch-modules.sh](http://communities.vmware.com/servlet/JiveServlet/download/1553530-39784/patch-modules.sh)
wget [http://communities.vmware.com/servlet/JiveServlet/download/1553530-39785/vmware-7.1-2.6.35-3-generic.patch](http://communities.vmware.com/servlet/JiveServlet/download/1553530-39785/vmware-7.1-2.6.35-3-generic.patch)
sudo sh patch-modules.sh

works with me

---

### Post by TJet1.8 on 2010-11-24
VMware just release Workstation and Player 7.1.3  and 3.1.3 respectively which fixed the issue with installing on the 2.6.35-x Linux kernel.

Fixes installing on almost all distro's using that kernel version.

:popcorn:

---

