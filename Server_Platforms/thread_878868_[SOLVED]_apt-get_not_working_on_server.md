---
title: "[SOLVED] apt-get not working on server"
date: 2008-08-03
forum: Server Platforms
---

### Post by mickyd on 2008-08-03
Hi have an old desktop set up as a server with 2 nics the adsl modem goes to eth0 with dhcp and eth1 connects to the lan everything is connecting and i can surf the net from the lan but i am unable to update the server or install new packages. 

error message is "Err [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'ie.archive.ubuntu.com'"

to get the pc's on the lan to connect to the internet i used this command 
"iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE"
so there is a simple iptables rules set up.

I am assuming it is a problem with the dns on the server but unsure as to what it could be.

Ohh and am fairly new to linux and command line.

Anyone have any ideas??

---

### Post by windependence on 2008-08-03
Add this line to your /etc/resolv.conf:

```
193.1.193.69   ie.archive.ubuntu.com 
```

Then restart the network.

-Tim

---

### Post by mickyd on 2008-08-03
Thanks tim added that line to the /etc/resolv.conf:
but when i restart the network i lose the internet on the lan and it still doesn't do apt-get upate

---

### Post by windependence on 2008-08-03
Aye, crapola, I'm sorry, that line should go in your /etc/hosts file.

Take it out of your /etc/resolve.conf, and then add this to your resolve.conf:

nameserver 2.2.2.4

Apologize for the confusion, I have been working all night. :)

-Tim

---

### Post by mickyd on 2008-08-03
Thanks Tim that worked perfect, Is it a dns issue and by pasting there we are creating a small dns file?

Thanks again.

---

### Post by mickyd on 2008-08-03
Thanks

---

