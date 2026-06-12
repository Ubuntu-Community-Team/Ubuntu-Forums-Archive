---
title: "macchanger on boot"
date: 2011-01-05
forum: Security
---

### Post by raffen on 2011-01-05
I want to change MAC address on boot on a stock Dell laptop running Ubuntu 10.10.

I have adapted the */etc/init/macchanger* script found towards the end of [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336736](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/336736) as follows:

```
$ cat /etc/init/macchanger 
# macchanger - set MAC addresses
#
# Set the MAC addresses for the network interfaces.

description "change mac addresses"

start on starting network-manager

pre-start script
        /usr/bin/logger wlan0 pre  `/usr/bin/macchanger -s wlan0`
        /usr/bin/macchanger -A wlan0
        /usr/bin/logger wlan0 post `/usr/bin/macchanger -s wlan0`
end script

```

The MAC address does not change nor is there anything matching lines in /var/log/messages (i.e. no output from `sudo grep 'wlan0 pre' /var/log/*`).

If I run *sudo /usr/bin/macchanger -A wlan0* the MAC address is changed (provided wireless networking is disabled).  

How to I automate the same thing on boot?

---

### Post by HermanAB on 2011-01-06
Hmm, you can change the MAC with ifconfig.

---

