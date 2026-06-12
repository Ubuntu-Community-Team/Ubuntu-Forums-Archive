---
title: "Was i hacked via ssh with denyhosts, keybased logins and firewall configured?"
date: 2008-02-06
forum: Server Platforms
---

### Post by DigitalDuality on 2008-02-06
I have passwordless (key based) ssh open (the only open port) on a machine of mine i use to tunnel through at home.

I have a router with the port forwarded and it works beautifully. I also have denyhosts installed and configured.

Today when i attempted to tunnel, i couldn't connect. I come home and do an ifconfig...and there a 3rd entry. One for eht0, one for eth0:avah, and one for lo.

The eth0 no longer had an ip address,and ifconfig eth0 up wouldn't work. I tried eth0 down and back up and still nothing. I rebooted the machine and all of a sudden that eth0:avah was gone.

 the eth0:avah had some ip, which i did a whois on and it's somewhere in cali. I have never typed this ip for anything. The last thing i installed on this machine was icecast and i abandoned that last night and just unisntalled it.

My /var/logs look like their ok. The times that users have logged in is consistant with when i logged in. Any ideas what the **** just happened?

Let me add, someone attempted a dictionary based attack on this machine about 3 days ago. As far as i know they didn't succeed.

---

### Post by koenn on 2008-02-06
avah refers to, I think, a network autoconfiguration mechanism - ZeroConf Networking. You probably have some avahi-enabled packages installed

---

