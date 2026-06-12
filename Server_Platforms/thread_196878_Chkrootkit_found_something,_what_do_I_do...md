---
title: "Chkrootkit found something, what do I do..?"
date: 2006-06-14
forum: Server Platforms
---

### Post by Raavea on 2006-06-14
> Checking `lkm'... chkproc: nothing detected
Checking `rexedcs'... not found
Checking `sniffer'... lo: not promisc and no packet sniffer sockets
eth0: PACKET SNIFFER(/sbin/dhclient3[3176])
Checking `w55808'... not infected

Above you will see a few items around the thing it said that alarmed me. If this information will endanger my system security by being here, please tell me as soon as possible.

As you can see, it says something about eth0, which you may or may not know to be my ethernet cable and connection.

What do I do or will chkrootkit have fixed this?

---

### Post by David_T on 2006-06-14
dhclient3 is fine, that's just the DHCP client so that you can get an IP address
from your ISP to connect to the internet.
There's a linspire forum post that talks about chkrootkit -- it may not always give the most helpful results.
[http://forum.linspire.com/viewtopic.php?t=395040&sid=c9e03c66c432f7e87cff673588aea132](http://forum.linspire.com/viewtopic.php?t=395040&sid=c9e03c66c432f7e87cff673588aea132)

---

### Post by Raavea on 2006-06-14
Thanks a lot, David.

 I get panicy. Its not that I have any sensitive info on here (though I do run several websites, I shouldn't like the passwords to them nicked...) but... I guess I just don't like the idea of someone doing something with my PC that I don't even know how to do...

---

### Post by escape on 2006-06-15
Might also want to try [http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html)

---

