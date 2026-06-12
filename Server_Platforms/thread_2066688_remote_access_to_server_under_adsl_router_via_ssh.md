---
title: "remote access to server under adsl router via ssh"
date: 2012-10-05
forum: Server Platforms
---

### Post by hawaiiman on 2012-10-05
Set up a 12.04 server under an adsl router running pppoa. I have no experience with ssh, but want to be able to access server from home win7 64 manchine. Opensshd on server, port 22 checks open with Nmap, port22 forwarded to 192.168.1.10 (server). Have Bitvise client on home machine. Can't figure out how to set a destination as there isn't a static ip. Possible?

---

### Post by albandy on 2012-10-05
register in [http://www.no-ip.com/](http://www.no-ip.com/) and install the noip2 package

sudo apt-get install noip2

---

### Post by Lars Noodén on 2012-10-05
There are a number of dynamic DNS services available, in addition to no-ip above:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

Once you have picked one, you can use the package ddclient to make the connection and update your IP address.

---

### Post by markbl on 2012-10-05
You could also have your pc email you on boot/periodicially. The mail header should contain your WAN side IP address, mine does.

Not saying I would do it like this btw. I use dyndns for my home ssh servers. Just putting the comment here as food for thought.

---

### Post by hawaiiman on 2012-10-20
Thanks to all. I went with the free basic account with no-ip for now. The school will hopefully spring for a registered domain eventually, but for now this will be fine.

---

