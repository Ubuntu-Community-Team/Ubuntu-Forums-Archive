---
title: "Port Usage"
date: 2008-07-14
forum: Server Platforms
---

### Post by prem1er on 2008-07-14
Can't find much on this topic.  I have a server at home running a specific process on a specific port that allows contact to the server from outside my network.  I'm running through a router which allows connections to this port.  Is there another way (besides setting up wireshark) on my machine to give me an approximate number of times the port is being used?  Could it be done with the router firmware?  Or is there some sort of log I could set up that I could read over showing me ports connected to?

---

### Post by ilrudie on 2008-07-15
You can use tcpdump from the command line.  You can specify to only show packets on a specific port and protocol.  You must be root to use this command so you will need to prefix it with sudo like:
```
sudo tcpdump -A -v tcp port 22
```

---

### Post by prem1er on 2008-07-15
> **ilrudie said:**
> You can use tcpdump from the command line.  You can specify to only show packets on a specific port and protocol.  You must be root to use this command so you will need to prefix it with sudo like:
```
sudo tcpdump -A -v tcp port 22
```

Thanks.  Will try this out when I get back from work (seeing as I can't ssh out of this prison lol).  Any other suggestions are welcomed!

---

### Post by windependence on 2008-07-16
TIP: Try setting up your ssh on port 443. That traffic is encrypted and the port is usually open so many companies simply can't block it because they can't tell what traffis is going through it. You would need to start an ssh daemon on 443, real easy. sudo /usr/bin/sshd -p 443.

-Tim

---

### Post by prem1er on 2008-07-17
> **ilrudie said:**
> You can use tcpdump from the command line.  You can specify to only show packets on a specific port and protocol.  You must be root to use this command so you will need to prefix it with sudo like:
```
sudo tcpdump -A -v tcp port 22
```

This works for me, but is there any way to just see and IP address of systems that tried to connect on that particular port.  tcpdump just gives me too much data with all the connections being made.  I just want to see how many users are connecting to this port per day/week.

---

### Post by ilrudie on 2008-07-17
try ```

sudo tcpdump -n tcp port 22 | sed -n 's/.*\b\([0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\b\).*/\1/p'

```You can man sed but essentially its searching for ip addresses and removing everything that is not an ip address in lines that have ip's.  eg in lines with just text you get the text and in lines with ips you just get the ips.  As a side note this does not perfectly match ips because 999.999.999.999 is not an ip but is matched by my regular expression.  In your case tcp dump should not be printing any invalid ips so its not a problem.  There is probably a better solution but I can't think of it and this will work.

---

