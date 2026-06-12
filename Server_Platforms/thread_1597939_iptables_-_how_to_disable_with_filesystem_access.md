---
title: "iptables - how to disable with filesystem access"
date: 2010-10-15
forum: Server Platforms
---

### Post by shibbe on 2010-10-15
Hi,

so I followed [this guide](https://help.ubuntu.com/community/IptablesHowTo) in order to activate iptables. added 
iptables -A INPUT -p tcp --dport ssh -j ACCEPT
iptables -A INPUT -j DROP 
and drop was second in list when I entered iptables -l -v

so I did
sudo bash -c "iptables-save > /etc/iptables.rules"

and added this line to /etc/network/interface
pre-up iptables-restore < /etc/iptables.rules

I'd say everything was fine until there, because everything I wanted to be enabled was SSH.

Now I used this to activate iptables and lost my ssh connection after hitting return.
sudo ufw enable

How can I fix my server and disable iptables? I've got no physical access but I can use a recovery system to mount my sda2. So basically what I am looking for is a way to disable iptables without using any console commands.
I already removed the following from my /etc/network/interfaces and removed /etc/iptables.rules - didnt help :\
pre-up iptables-restore < /etc/iptables.rules

Thanks in advance, sry for my english and feel free to move this into absolute beginners if this is too easy for main support :)

---

### Post by shibbe on 2010-10-15
Solved it on my own, checked all ufw-related files and found /etc/ufw/ufw.conf - edited it from "ENABLE=yes" to "ENABLE=no" and now my system works like a charm.

:popcorn:

will try iptables again, but without using ufw too.

---

### Post by koenn on 2010-10-16
you should also check any other rules or default policies : allowing ssh in without allowing the remote system to reply (= output) won't work.

---

