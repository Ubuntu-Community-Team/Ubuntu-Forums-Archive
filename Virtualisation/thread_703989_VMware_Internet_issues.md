---
title: "VMware Internet issues"
date: 2008-02-21
forum: Virtualisation
---

### Post by yao_man on 2008-02-21
I am using VMware workstation 6 on Windows XP and running ubuntu 7.10 through a virtual disk. At first, I connected to the internet using NAT connection and it worked fine, I installed vmware tools and restarted and it still worked. Then I downloaded the updates it recommended (about 185 of them I believe), installed them, and restarted. Before I started it back up I tried to make the connection a bridged connection directly through my NETGEAR wg311T wireless card to my wireless network but it didn't work. Since then I have been completely unable to connect to the internet inside that virtual disk. I cannot make a bridged connection (I can't see wireless network options, only ethernet or modem) or connect through the NAT virtual connection. Any help would be appreciated.

Also, I took a snapshot right after I installed the vmtools, but I am not sure how, why, or what to do with it. I'm not sure if that can possibly help me though. Again, thank you for any help.

---

### Post by yao_man on 2008-02-22
I had other issues involving that virtual disk so I deleted it and created a new virtual disk and reloaded ubuntu onto it. If anyone could still, however, help me create a bridged connection directly to the internet I would greatly appreciate it.

---

### Post by kaginken on 2008-02-22
What is the status of your virtual network interface?

Check your guest OS settings --> ethernet1 --> device status

Is it connected?  Does it have the box checked, "connect at power on"?

do you get an IP?  what does ifconfig command give you?  It may be you have a valid network address, but just can't get to the internet.  You can test this by pinging your gateway/router/other local network device...

can you ping yourself?  ie ping localhost

---

### Post by yao_man on 2008-02-22
I am able to ping the localhost and the IP address that my host computer is on, but I am unable to connect via NAT connection or bridged connection.

---

### Post by kaginken on 2008-02-22
Try another type of connection, not bridged.  Bridged should work, but if it's not, I'd try some of the other ways VM offers.

---

### Post by yao_man on 2008-02-23
I had to work with it a little bit after installing the recommended Ubuntu updates, but I have NAT connection working, I was just hoping to be able to use bridged and connect directly, oh well, thanks anyway.

---

