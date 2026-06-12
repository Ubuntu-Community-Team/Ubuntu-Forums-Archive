---
title: "Firewall Config"
date: 2006-09-16
forum: Server Platforms
---

### Post by skali on 2006-09-16
Hi!

I need to configure a proxy server and a firewall on  ubuntu 6.06
I have suceesfully configure the squid server; however, i'm stuck with firewall. I also check the help.ubuntu... but i didn't get it?
The firewall is suppose to stop user from downloading .exe, .rar .zip etc during the office working hours. Moreover, it should provide content filtering for specific site(cracks, keygens, sex, nudity, etc...)

The problem is i'm coming from windows and on linux side my knowledge is not sufficient. Kindly mention some comprehensive tutorials/web-site so that the firewall is started soon.

Thanks

---

### Post by bluefrog on 2006-09-25
content filtering comes from proxy.

install firestarter for a firewall gui (look in synaptic). from there you should find your way.

James

---

### Post by skymt on 2006-09-25
For a good content-filtering proxy, look at [DansGuardian](http://dansguardian.org/). The final chain for your setup would look something like Internet > Firewall > DansGuardian > Squid > user. Firewall (take your pick of firewalls) for port blocking, DansGuardian for content and Squid for caching.

---

### Post by Macchi on 2006-09-25
I would recommend FireHoL as a good firewall for a server instead of firestarter. FireHOL is easy to configure through a simple text file, 
thus you will be able to administrate your server headless through ssh, without the potential security risk and computational burden of having a graphic user interface. FireHOL is actually a nice "syntactic sugar"
for iptables.

Maybe this is overkill to mention but: 
1) Allow the universe repositories on /etc/apt/sources.list 
2) Issue the command: sudo apt-get update && sudo apt-get install firehol. 
3) Edit the configuration in /etc/firehol/firehol.conf
5) Restart the firewall with sudo /etc/init.d/firehol restart
Your firewall is running!

Here is an example of /etc/firehol/firehol.conf configuration
file for a system with two interfaces,  eth0 towards LAN, and
ppp+ towards the internet: 
-------------------------------------------------------------
# Example configuration file for FireHOL
# This maybe optimized later
#  
interface eth0 home 
  server dns ftp samba http squid dhcp ssh smtp icmp accept 
  client samba icmp accept 

interface ppp+ internet
  server smtp http ftp accept 
  client all accept

router home2internet inface eth0 outface ppp+ 
 route all accept 

router internet2home inface ppp+ outface eth0 
-------------------------------------------------------------

More information on:
[http://firehol.sourceforge.net/](http://firehol.sourceforge.net/)

---

