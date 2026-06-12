---
title: "cant access samba share"
date: 2008-04-18
forum: Server Platforms
---

### Post by nefx on 2008-04-18
im having some issues sharing a directory.  I installed a new hard drive on the ubuntu server runing fiesty fawn.  I have samba configured and have webmin.  hdb1 and hdc2 have a couple of network shares on there that are accessbible from my other computers and my xbox.  I created a folder in hdd1 and tried to share it using webmin.  When I try to access it from my windows computers, it freezes the computer to the point where I have to do a cold restart.  When I try to access it using my xbox, it says workgroup not found.  I'm able to access other network shares on the server but when I try to access the one on hdd1, it wont let me.  I have iptables running but all my computers ip address are whitelisted.  Plus, im able to access the other shares on the server with no problem.  Anyone have any recommendations?


victor:confused:

---

### Post by HermanAB on 2008-04-18
See this: [http://aeronetworks.ca/samba-debug-howto.html](http://aeronetworks.ca/samba-debug-howto.html)

---

### Post by nefx on 2008-04-20
Herman AB, thanks for your reply.  I tried everything in the line you provided and nothing helped.  I unmounted the disk, re-formatted it with gparted to ext3 (it had already been formated to that), and tried again and it worked.  Hopefully it stays working.

:guitar::KS

---

