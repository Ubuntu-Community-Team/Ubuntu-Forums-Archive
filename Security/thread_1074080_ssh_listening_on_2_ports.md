---
title: "ssh listening on 2 ports?"
date: 2009-02-18
forum: Security
---

### Post by rhcm123 on 2009-02-18
I would like to start ssh listening on port 10000 along with the usual port 22. 

long and over complicated explanation of why here:

Right now when i ssh in from the outside world (which i do quite often, and i also use sshfs) i go through the standard port. 22. I know, not the smartest idea. So i wanna change that. Right now, i leave port 10000 open for webmin access (which may not seem smart either, but when the only user capable of using webmin dosen't have sudo priviliges it's fairly safe) I wanna get ssh listening on that port so i can close port 22 to the world. However, i want to leave the ssh daemon listening on 22 because when i'm at home on my protected network i don't wanna have to type ssh ussr@192.168.2.193 -p 10000, i just want to use the standard port.

---

### Post by yoyoned on 2009-02-18
use ip tables to redirect port 10000 to 22

---

### Post by rhcm123 on 2009-02-19
> **yoyoned said:**
> use ip tables to redirect port 10000 to 22

cant as webmin listens for https traffic on 10000

---

### Post by yoyoned on 2009-02-19
I not sure if I understand what you want.  You want to SSh from home on 22 and use webmin from home on 10000, but use ssh from the net on 10000. ?

---

### Post by cdenley on 2009-02-19
You can't have 2 servers listening on the same port.

---

### Post by HermanAB on 2009-02-19
SSH can listen on multiple ports, but you cannot have multiple servers listen on the same port.

In /etc/ssh/sshd_config simply add a second port command underneath the default one, then restart sshd. (and update your firewall to allow the new port in).

Cheers,

Herman

---

### Post by rhcm123 on 2009-02-19
> **HermanAB said:**
> SSH can listen on multiple ports, but you cannot have multiple servers listen on the same port.

In /etc/ssh/sshd_config simply add a second port command underneath the default one, then restart sshd. (and update your firewall to allow the new port in).

Cheers,

Herman

Exactly what i wanted. Thank you!

---

