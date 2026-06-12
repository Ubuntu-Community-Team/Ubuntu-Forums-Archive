---
title: "host/network not found"
date: 2010-06-18
forum: Security
---

### Post by jmore9 on 2010-06-18
For weeks now i keep getting this one fellow pinging my machine.  I am running a desktop not a server.  As far as i am aware of no server stuff is installed or tunning that does not come with the standard ubuntu 10.04 install.

I tried using sudo iptables -A INPUT -s xx.xx.xx.xx -j DROP , it works sometines , then sometimes it does not.  Some that it seems to block just come back in about 15 to 20 minutes.

On this one in particular i get the following error :

sudo iptables -A INPUT -s 222-208-183-218 -j DROP
iptables v1.4.4: host/network `222-208-183-218' not found
Try `iptables -h' or 'iptables --help' for more information.

Anyone have any idea why i get this error ?

Thanks in advance for any help.

---

### Post by bodhi.zazen on 2010-06-18
use . not -

```
sudo iptables -A INPUT -s 222.208.183.218/32 -j DROP
```

You do not need the /32 at the end, but it looks geeky.

---

### Post by Ryan Dwyer on 2010-06-19
How do you know someone is pinging you? If you're on a desktop, shouldn't you be behind a router? Why is your router forwarding ping requests?

---

