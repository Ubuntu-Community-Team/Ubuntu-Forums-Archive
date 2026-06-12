---
title: "Blocking unwanted websites and domains"
date: 2018-12-02
forum: Security
---

### Post by dannyk2 on 2018-12-02
Could someone tell me if it's possible to block a web site such as Facebook from my desktop computer using the hosts file?
Would it also be possible to block the likes of Facebook using their domain?

---

### Post by TheFu on 2018-12-02
Yes.  If you want to do it for all devices on the network, setup a pi-hole system.

I don't understand the 2nd line.  Do you mean the "like" buttons spread all over the place?  You can certainly block lots of them, but getting all the domains is non-trivial.

[https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279) is an article about this from 2011.  I've been blocking social networks a long time. ;)

---

### Post by gone.sovereign on 2018-12-03
yes you can use a hosts file for a single computer or install pi-hole.  I have pi-hole setup and it works quite well.  if you are using a hosts file you need to point to local host for URLS you dont want passed.  you can also use your firewall to trap ip's and drop incoming or outgoing packets.

---

