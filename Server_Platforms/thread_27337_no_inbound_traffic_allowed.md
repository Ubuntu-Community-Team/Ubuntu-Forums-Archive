---
title: "no inbound traffic allowed?"
date: 2005-04-15
forum: Server Platforms
---

### Post by thevampir on 2005-04-15
well, after searching the forums for about 2+ hrs, i have come to the conclusion that i am one of the only simi-newbs that has had this prob. After installing the server option for Hoary, the computer boots up fine. i am able to download whatever i need, this includes apt-get. but whenever i try to access it via Apache, ssh, or webmin, the connection as always refused. i have used various linux distros and this is the only one i have found to do this. it is getting really annoying.  i have removed iptable w/o any changes.   any help would be greatly apreciated



as a side note, i am using smoothwall as a gateway..but all relevent ports are forwarded/open

---

### Post by philipacamaniac on 2005-04-15
From another machine, can you ping it? Better yet, from another machine, run 

nmap -vv the_machine's_ip_address -P0

and see what services are up. If all ports are filtered, then possibly iptables is still having an effect on outbound traffic. Rather than uninstalling iptables, maybe try installing iptables and a GUI frontend, like firestarter, and config it to open up ports 22, 80, etc.

On my hoary installation I have been succesfully using a SAMBA server.

---

### Post by alastair on 2005-04-15
If things are getting blocked via iptables, I think you would see log messages i.e. check :

/var/log/syslog

For things like Apache, SSH etc. 

1) Make sure they are running - listening to the right port (use : ps ax, netstat --inet -nlp etc.)
2) Check log files : auth.log and /apache/access.log, /apache/error.log

---

