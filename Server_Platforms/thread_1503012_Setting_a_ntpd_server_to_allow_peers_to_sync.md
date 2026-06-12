---
title: "Setting a ntpd server to allow peers to sync"
date: 2010-06-06
forum: Server Platforms
---

### Post by tr333 on 2010-06-06
What configuration options in /etc/ntp.conf do I have to set to allow other computers to receive time from a ntpd server?  I've tried removing "nopeers" and "noquery" from the restrict lines, but I can't see anything on port 123.

---

### Post by swizman on 2010-06-06
I added this to the end of /etc/ntp.conf

# define the networks from which this server will accept NTP synchronization requests
# You do so with a modified restrict statement removing the noquery keyword to allow the network to query your NTP server. 
restrict 192.168.2.0 mask 255.255.255.0 nomodify notrap       # you need to enter your correct subnet here

You need to restart ntpd:
sudo /etc/init.d/ntp restart

---

### Post by tr333 on 2010-06-06
Thanks for that.

---

