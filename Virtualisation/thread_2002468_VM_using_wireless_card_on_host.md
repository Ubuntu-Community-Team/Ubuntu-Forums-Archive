---
title: "VM using wireless card on host"
date: 2012-06-12
forum: Virtualisation
---

### Post by BradleyAtkins on 2012-06-12
Hi All

I'm not sure if it is possible to do this or not but I want to set up my ubuntu VM to be a wireless access point as described here: -

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/?utm_source=newsletter&utm_medium=email&utm_campaign=120612](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/?utm_source=newsletter&utm_medium=email&utm_campaign=120612)

What I have is my work laptop running Windows 7. On it I have installed virtualbox and created an ubuntu VM.

I want to connect the vm to the laptop wireless card.

I seem to be able to do this by adding another network card  in VBox and associating it with the wireless card, but it shows up in my network settings in Ubuntu as a wired connection.

So I can't setit up as a wireless access point.

Any ideas on a way forward?

Thanks in advance

Brad


Here is the ifconfig from my attempts to do this at home with the same setup: -

eth0      Link encap:Ethernet  HWaddr 08:00:27:52:62:0a  
          inet addr:192.168.1.89  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe52:620a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14510352 (14.5 MB)  TX bytes:398288 (398.2 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:0f:48:a6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe0f:48a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:615 errors:0 dropped:0 overruns:0 frame:0
          TX packets:126 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62712 (62.7 KB)  TX bytes:15948 (15.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11753 (11.7 KB)  TX bytes:11753 (11.7 KB)

---

### Post by wildmanne39 on 2012-06-15
Hi, I do not know the particulars for setting up an access point, I can tell you that in a vm the guest can only see a wired connection unless you use an usb adapter.
Thanks

---

### Post by dcstar on 2012-06-16
> **BradleyAtkins said:**
> Hi All

I'm not sure if it is possible to do this or not but I want to set up my ubuntu VM to be a wireless access point as described here: -

[http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/?utm_source=newsletter&utm_medium=email&utm_campaign=120612](http://www.howtogeek.com/116409/how-to-turn-your-ubuntu-laptop-into-a-wireless-access-point/?utm_source=newsletter&utm_medium=email&utm_campaign=120612)

What I have is my work laptop running Windows 7. On it I have installed virtualbox and created an ubuntu VM.
.........

Just set up the native OS to be a "Wireless Access Point". The seem to be many options available on-line.

---

