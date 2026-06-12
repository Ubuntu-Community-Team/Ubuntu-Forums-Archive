---
title: "VPN for school"
date: 2006-08-22
forum: Server Platforms
---

### Post by ramasdf123 on 2006-08-22
I use Cisco VPN Client 4.6 and it uses a .pcf as a the configuration file.  Is there a program I could use that uses those file types? I have to keep my school username and password to login the next work.  Or is it possible to wine the client to get to work on ubunut?

I go to University of Houston.....

---

### Post by meng on 2006-08-22
I recommend
sudo apt-get install vpnc
and if you google vpnc you can easily find how to set up a cleartext configuration file to login.
vpnc is much easier to install and use than Cisco VPN, IMHO
There may be a way to convert the .pcf file, but it's been a while since I looked into this.

---

### Post by NetworkGuy on 2006-08-22
Try this link

[HTML]
http://ubuntuforums.org/showthread.php?t=21054&page=6[/HTML]

It should help you with vpnc and the .pcf file

---

