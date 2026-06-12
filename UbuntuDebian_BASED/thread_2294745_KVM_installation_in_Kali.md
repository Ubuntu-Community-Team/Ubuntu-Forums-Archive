---
title: "KVM installation in Kali"
date: 2015-09-13
forum: Ubuntu/Debian BASED
---

### Post by zmask37 on 2015-09-13
Hi Guys,

I tried installing kvm in ubuntu and it worked whereas when i tried to install kvm in Kali it shows package not available. your suggestions please.

# apt-get install qemu-kvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package qemu-kvm
#

---

### Post by QIII on 2015-09-13
*Moved to **Ubuntu/Debian BASED***

Kali is not Ubuntu or even based on Ubuntu.

It is based on Debian Testing.

This is likely a better place to find folks with experience with Kali.

---

### Post by zmask37 on 2015-09-13
Thanks for your response Qlll. I knew it is Debian based testing os. But a doubt that pops is wont kali supports kvm. :roll:

---

### Post by QIII on 2015-09-13
You could always ask at the [Kali Forums]("https://forums.kali.org/") as well.

---

### Post by zmask37 on 2015-09-13
Done that already. Waiting for someone to sort it out.

---

### Post by zmask37 on 2015-09-13
By the way just figured it out. Looks like the sources.list file doesnot point out to the correct debain mirror link. Just changed the required one for kvm in kali and did a update and there it is qemu-kvm. :D

---

