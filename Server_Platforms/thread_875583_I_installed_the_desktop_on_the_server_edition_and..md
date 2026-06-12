---
title: "I installed the desktop on the server edition and.."
date: 2008-07-31
forum: Server Platforms
---

### Post by KSI xXCazzXx on 2008-07-31
I installed the desktop using apt-get and when I tried removing it, nothing happened.

Any ideas?

**I uninstalled it now but now I need to know how I can put it on the internet again.

I used the network thing where the clock/date is to connect last time but it no longer connects I think.
I use linksys card and the network name is linksys.

Is there some package or something I can use to automatically connect?

---

### Post by pdwerryhouse on 2008-07-31
What did you do to try to remove it? If it was just ```
apt-get remove ubuntu-desktop
```, then that's not going to remove it all - it's a virtual package, and it pulls in all the others via dependencies.

---

### Post by KSI xXCazzXx on 2008-07-31
I removed it with some command I found on another website and everything works except I need internet, read the first post (Edited)

---

### Post by cariboo on 2008-07-31
There a couple of things you can do in at the console type:

```
ifconfig
```

This should echo back something like this:

```
eth0      Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe9c:84b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31970607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18458019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47341978500 (47.3 GB)  TX bytes:1389067195 (1.3 GB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:51462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2744033 (2.7 MB)  TX bytes:2744033 (2.7 MB)

```

If eth0 doesn't have an ip address try:

```
sudo dhclient eth0
```

IF that doesn't work or you get no output from ifconfig, type:

```
sudo /etc/init.d/networking start
```

then try the above commands again.

---

### Post by KSI xXCazzXx on 2008-07-31
nono..

I can hook an ethernet coord up thats connected to my laptop and get internet but I need my linksys card to do what it's supposed to do and connect to 'linksys' our router.

---

### Post by ChumleyEX on 2008-07-31
First of all you need to be a bit more clear in your problem. Based from what is written it seems like you

1. Installed the desktop
2. then uninstalled it
3. and now there is nothing near the clock to connect your linksys with. (oh wait but you don't have the desktop installed [read your post])

So this is why the command line info was given to you. Not that you said it (which you should have if you wanted proper help) but I'm guessing this linksys (linksys makes wired and wireless devices) is a wireless card. Does this sound right?

So you have reinstalled the desktop and now you don't have the wireless manager? 

or 

You need to know how to connect the wireless card via the command line?

---

### Post by KSI xXCazzXx on 2008-07-31
My friend told me to install ubuntu-desktop on the computer and then connect to the wireless internet named 'linksys' using my linksys card which worked fine, he then told me to uninstall it so I did and from there the wireless internet was no longer connected or working.

I'd like it so when I start my computer or when I type some sort of command it connects automatically to the internet network 'linksys' with my linksys wireless card.

So, I no longer have the desktop installed, it's now back at ubuntu server.

After saying that...

> You need to know how to connect the wireless card via the command line? 

Exactly. I don't know and I need to know. So if you or someone could tell me how or find a guide for it, that would be great.

Thanks.

---

### Post by KSI xXCazzXx on 2008-07-31
Aye, never mind.

My friend stepped in and told me about 'man iwconfig'.

---

