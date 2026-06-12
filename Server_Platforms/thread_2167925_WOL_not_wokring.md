---
title: "WOL not wokring"
date: 2013-08-15
forum: Server Platforms
---

### Post by ads2996 on 2013-08-15
Hi,

I recently set up my home server for the second time but this time i have run into a probelm and that is that WOL will only work a few minutes after powering down the pc. It worked with my old router but i now have the BT HomeHub 4 which i think may be the porbelm. The server side of things is set up like it was the last time i had the server running.

Any help greatly appreicated.

---

### Post by ads2996 on 2013-08-16
I have done some research and it seems that it is because of the router deleting arp data whatever that is

---

### Post by papibe on 2013-08-16
> **ads2996 said:**
> ... because of the router deleting arp data
That is a very common situation.

arp data is actually a table that matches IP address with a MAC address. You can see what is in the arp table of any Linux machine by running:
```
arp
```

Within a LAN, the proper way to wake up a machine is to use its MAC address, that way the system doesn't need to look at the arp table. That  works because the WOL protocol is a broadcast package, so it does not need any info or function from the router.

If you want to wake your server up from outside your LAN or the Internet (then it is mandatory to pass through the router), it is a another task completely. It doesn't mean you can't do it, but it will depend on the router's capabilities and how do you configure it.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by ads2996 on 2013-08-16
I have an app on my android phone to send magic packets to the server, but it requires an ip for the server. Is there a way to send the magic packet without the ip address? and any ideas on how to do this from outside my network

---

### Post by ads2996 on 2013-08-16
i think i just sorted out the part for waking from my internal lan but from the internet is proving more of a probelm.

---

### Post by papibe on 2013-08-16
To get your MAC address or your server, connect to it and run:
```
ifconfig
```
It would be the field named as HWaddr.

Then from your desktop you can install a command line tool:
```
sudo apt-get install wakeonlan
```
or, install a GUI WOL client:
```
sudo apt-get install gwakeonlan
```
Both tools will require the MAC address you got from your server.

BTW, I would tinker a little bit with you app, since in my assessment, it should have an option for MAC addresses. If it doesn't allow it, there are several other apps that allow MACs.

Let us know how it goes.
Regards.

---

### Post by ads2996 on 2013-08-16
i did have the app set up with the mac address but my probelm was for the ip i had set it to the server rather than the broadcast ip of my router, i believe it is now working but over the internet may prove more difficult

---

