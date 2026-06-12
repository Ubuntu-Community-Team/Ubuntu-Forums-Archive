---
title: "How to have ubuntu host and Virtualbox windows guest on the same network"
date: 2013-11-16
forum: Virtualisation
---

### Post by regis.chingombe on 2013-11-16
I have Virtualbox 4.1.18_Ubuntu r78361 where I installed Windows 7 Professional. I want the virtual machine to be on the same network as the Ubuntu host. This is so that when I connect the Ubuntu machine on the corporate network, I can use the Windows virtual machine to access Windows applications on the network. In other words I need the virtual machine to join the Windows domain and have access to the Active Directory

---

### Post by coldraven on 2013-11-16
I don't have Vbox installed at the moment but here is something that I posted a while ago.
[I]For some good info about networking in Virtualbox  go here and click on the image of issue 61 to download it  (pdf)
[http://fullcirclemagazine.org/issue-61/](http://fullcirclemagazine.org/issue-61/)  
Then read from page 15 onwards.

I found this to be easy to understand, I hope it helps you.[/I]

---

### Post by Morbius1 on 2013-11-16
The default networking mechanism in a VBox guest is NAT so conceptually think of that as the host acting like a router. Just like in a real network someone behind a router can see out but no one from the outside can see in. That's why you can't ping my ip address: 192.168.0.100.

If you change networking to Bridge Adapter on the VBox guest you will be seen as another member of the local network on peer with the host itself. Whether or not you are allowed to have this new client on your corporate network is between you and your Network Administrator however.

---

### Post by regis.chingombe on 2013-11-20
I bridged the adaptor on Mac OS X and the VBox guest works as desired by not on Ubuntu. 

> **Morbius1 said:**
> The default networking mechanism in a VBox guest is NAT so conceptually think of that as the host acting like a router. Just like in a real network someone behind a router can see out but no one from the outside can see in. That's why you can't ping my ip address: 192.168.0.100.

If you change networking to Bridge Adapter on the VBox guest you will be seen as another member of the local network on peer with the host itself. Whether or not you are allowed to have this new client on your corporate network is between you and your Network Administrator however.

---

