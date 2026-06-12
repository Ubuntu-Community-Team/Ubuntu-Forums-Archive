---
title: "Ubuntu 20.1 new install as a vmware machine cant access from LAN"
date: 2021-02-12
forum: Server Platforms
---

### Post by deepakdeshp on 2021-02-12
Hello,
I installed Ubuntu server 20.1 but I am not able to ssh , ping to it from LAN or open it in a browser with [http://ip](http://ip) of machine

It can ping google.com though. I am trying to ssh from my host machine with ip 192.168.1.107/24 and the server ip is 192.168.1.160/24
ufw is off for the server. From the Ubuntu 20 virtual server I can ping my host and ssh to it. Please advise.

---

### Post by guiverc on 2021-02-12
Firstly you might want to check & update your release details.
 
Ubuntu's main releases are *year.month* in format, so 20.1 as you put it means the 2020-January release, except none came out in January?

Ubuntu does also have a different product group which uses the *year* only format, eg. Ubuntu Core 20 meaning the 2020 release, but that's a more limited product (smaller means lighter which is huge plus on devices, appliances or even for cloud use), use *snaps* only, and have a longer supported life (10 years).

You mention Ubuntu 20 - do you mean Ubuntu Core 20? It'll mean a different product to the the non-existent 20.1 (2020-January) release, so check what you have and please correct.

---

### Post by deepakdeshp on 2021-02-12
Sorry for reporting the version incorrectly. It is 20.10 server version.

---

### Post by darkod on 2021-02-13
First of all, is this VM only for some short specific test?

Because if you want to keep it for longer, use only LTS releases and the latest LTS is 20.04 LTS. If you are new to linux servers and ubuntu in particular, you have to get used not to simply get the latest version and rush to install it. 20.10 has only 9 months of support since it was released, which means it ends around July-2021. By the time you set up and configure everything on your 20.10 server it will run out of support.

20.04 has 5 years of support, until April-2025. So if you need this server for longer, destroy this 20.10 VM while it is still new and install 20.04.

That is why, unless you need something very specific from 20.10, you don't install it.

Related to your problem, it can be related to vmware settings. But that area is quite large to discuss here and now.

Do you have any other VMs in the same virtual network / virtual switch? Can you ping your server VM from them?

You could try to trace route from another computer on the same LAN and see where the traffic stops. That could give you some pointers.

---

### Post by deepakdeshp on 2021-02-13
> **darkod said:**
> First of all, is this VM only for some short specific test?

Because if you want to keep it for longer, use only LTS releases and the latest LTS is 20.04 LTS. If you are new to linux servers and ubuntu in particular, you have to get used not to simply get the latest version and rush to install it. 20.10 has only 9 months of support since it was released, which means it ends around July-2021. By the time you set up and configure everything on your 20.10 server it will run out of support.

20.04 has 5 years of support, until April-2025. So if you need this server for longer, destroy this 20.10 VM while it is still new and install 20.04.

That is why, unless you need something very specific from 20.10, you don't install it.

Related to your problem, it can be related to vmware settings. But that area is quite large to discuss here and now.

Do you have any other VMs in the same virtual network / virtual switch? Can you ping your server VM from them?

You could try to trace route from another computer on the same LAN and see where the traffic stops. That could give you some pointers.

Thank you for pointing out that 20.10 isnt LTS. I thought all the 20.x versions are LTS and 21.x will have short term support. Accordingly I installed server 20.04.
About the network problem, I had made an entry```
 92.168.1.160 server1 ubuntu 

``` in /etc/hosts . It should have been 192 instead of 92 above. Everything is working fine and I have installed LTS 20.04. I will install the php applications like phpmyadmin, moodle etc.

---

### Post by LHammonds on 2021-02-14
Hehehe, I love and hate how computers do what they are told.  Congrats on finding it.

---

### Post by deepakdeshp on 2021-02-21
> **LHammonds said:**
> Hehehe, I love and hate how computers do what they are told.  Congrats on finding it.
That was easy to laugh . I spent many hours for the problem One thing I should have done was to ssh with ip address instead of the name. A learning no doubt.:)
And more important I installed 20.04, LTS rather than 20.10 because of this thread.

---

