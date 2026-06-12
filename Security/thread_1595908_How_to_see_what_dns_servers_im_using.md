---
title: "How to see what dns servers im using?"
date: 2010-10-13
forum: Security
---

### Post by dogdo on 2010-10-13
I have my standard internet connection with opendns. But i then connect to a vpn-what dns servers does the vpn use then?

---

### Post by anomie on 2010-10-13
Many VPN clients will replace your resolvers for the duration of your VPN connection. Check **/etc/resolv.conf** to see what's currently being used. 

For a real time look, you could always observe UDP 53 packets using tcpdump.

---

### Post by spikoley on 2010-10-14
You can run Etherape for a GUI view of your connections.  It will show you the DNS server and everything else you are connecting to.

```
sudo apt-get install etherape
```

---

### Post by wacky_sung on 2010-10-14
See below link for the thread in which i posted which may be used for you.

[http://ubuntuforums.org/showthread.php?t=1551267](http://ubuntuforums.org/showthread.php?t=1551267)

---

### Post by HermanAB on 2010-10-15
Howdy,

Your machine will still use whatever is listed in /etc/resolv.conf:
$ cat /etc/resolv.conf

---

### Post by MechaMechanism on 2010-10-15
Another way is to use the GRC DNS Nameserver Spoofability Test.  Scroll to very bottom to iniate test and it will tell you the servers your using.

[https://www.grc.com/dns/dns.htm](https://www.grc.com/dns/dns.htm)

---

