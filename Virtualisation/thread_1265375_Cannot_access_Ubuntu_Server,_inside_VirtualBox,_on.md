---
title: "Cannot access Ubuntu Server, inside VirtualBox, on host machine"
date: 2009-09-13
forum: Virtualisation
---

### Post by Inifekt on 2009-09-13
I tried looking for a topic that would be related to this, but I haven't found any. So here goes...

I am a new Ubuntu (& Linux user) and I am trying to broaden my horizon. On Windows, I used to run an Apache server with PHP on it. So, I did some research and found out that I can use Ubuntu server (LAMP) to do this.

Well, I have followed several tutorials and cross-referenced a lot of sites to see what's wrong. I can install everything with with no errors, but I cannot access my server outside my VM on any machine on my LAN.

I'm not sure what I should output I should paste, so if any needs to be run let me know. Thanks in advance!

Edit: just some of the version numbers I am running.... Ubuntu 8.10, VirtualBox 3.0.6, and Ubuntu Server 9.04

Edit 2: Looked through this thread and it didn't work for me either. [http://ubuntuforums.org/showthread.php?t=1117517&highlight=virtualbox+ubuntu+server+access+host](http://ubuntuforums.org/showthread.php?t=1117517&highlight=virtualbox+ubuntu+server+access+host)

Edit 3: I kind of have it working now, but only on the host computer can I access the guest server. Still no access on computers on the LAN.

---

### Post by Inifekt on 2009-09-14
[SIZE=1]Bump...

I am still trying to get this fixed. At first, I couldn't access internet inside my server, but resolved that by installing a 2nd network card and changed the 1st one to "host only" mode and the 2nd one to "NAT." 

I tried testing that with Ping and doman names. It could ping IP addresses (servers IP, routers IP, and Googles IP), but not any domain name. I did some Google magic and found an article saying that if you clone your MAC address from your routers website it should fix it. Actually, I think it was about getting access from another computer on the network. Anyways, I cloned my MAC address (wrote down the previous one) and restarted my network. Now a new problem arises: when the server is running, I can access internet and it'll resolve domain names, but my machine (host) cannot get access to the internet. 

The only way I can get internet back is by clicking on the network icon and reconnecting (wired).

So, again, hope there's someone out there that can help me out. Thanks again.
 [/SIZE]

---

### Post by scrooge_74 on 2009-09-16
Go back the way you came and start anew.  Did you tried bridged mode? That is the way to get the guess OS to have its own IP given by the router or statically assign by you.

If not mistaken before doing that you need to install the guest additions


humm I never asked you if you are using VirtualBox :D

---

### Post by Zhwazi on 2009-09-18
Set the the network adapter to "bridged". See if the IP address of your guest is in the same range as the rest of the LAN (usually going to be 192.168.1.{100-150}, though some are 192.168.1.{2-50}, 192.168.1.{254-200} or 192.168.1.{64-100}, and some weird ones are 172.16.*.* If the interface is configured in NAT mode the default will be 10.*.*.*, which provides no access from outside, though company networks usually use this range as well). If it is, check your firewall or turn it off and try again.

If it's still not working, it would be helpful to have:

1. "ifconfig" from host
2. "ifconfig" from guest
3. network layout (where is the host in relation to any routers/modems/switches/hubs) and the DHCP range for any routers.

---

### Post by biprauk on 2009-09-18
Nice and informative post. Keep up the good work.

---

### Post by s_raghu20 on 2009-11-25
> **Zhwazi said:**
> Set the the network adapter to "bridged". See if the IP address of your guest is in the same range as the rest of the LAN (usually going to be 192.168.1.{100-150}, though some are 192.168.1.{2-50}, 192.168.1.{254-200} or 192.168.1.{64-100}, and some weird ones are 172.16.*.* If the interface is configured in NAT mode the default will be 10.*.*.*, which provides no access from outside, though company networks usually use this range as well). If it is, check your firewall or turn it off and try again.

If it's still not working, it would be helpful to have:

1. "ifconfig" from host
2. "ifconfig" from guest
3. network layout (where is the host in relation to any routers/modems/switches/hubs) and the DHCP range for any routers.

Helped me big time.
And by the way, just to add, if you do want to use bridged networking from a windows host, there are no tweaks required. It just works out of the box. Automatically.

cheers
raghav.. :)

---

