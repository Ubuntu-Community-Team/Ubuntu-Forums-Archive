---
title: "Virtualbox network setup"
date: 2022-02-22
forum: Virtualisation
---

### Post by kengyel on 2022-02-22
Hi!
I want to "build" a basic vbox lab.(Practicing samba, dhcp, dns)
I need your help for proper network settings in vbox.
(2 vbox one of them has ubuntu server 20.04 other for example linux lite. I am using win10 as host :(

Thank in advance.

---

### Post by SeijiSensei on 2022-02-22
Use bridged networking if you require the VM to be visible to other machines on your network. The default NAT option hides the VM behind the host.

Have you read: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

Read it at least twice since this stuff can be complicated.

Sounds like you are trying to build a network of VMs on the host?. Then you definitely need to read that chapter.

---

### Post by TheFu on 2022-02-22
Read the virtualbox networking Chapter 6 in the online manual.
Normally, I would say to use bridged networking, but you have some specific needs.

---

