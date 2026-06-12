---
title: "iptables, close/open ports... tutorial for newbie"
date: 2005-05-22
forum: Server Platforms
---

### Post by CrustyDOD on 2005-05-22
Is there any tutorial/explanation page for newbie about iptables? I would really want to block all connections from outside/internet to my server except for ports 80 and 21/20... My server is behind router (router forwards only 80 and 21 ports)... and allow ssh, webmin access from lan connection..

Anyone knows for really good site about iptables?

---

### Post by matej on 2005-05-22
[QUOTE=CrustyDOD]Is there any tutorial/explanation page for newbie about iptables? [/QUOTE]
google - howto iptables: [http://www.linuxguruz.com/iptables/howto/]("http://www.linuxguruz.com/iptables/howto/") [:)]("http://www.linuxguruz.com/iptables/howto/")

[QUOTE=CrustyDOD] I would really want to block all connections from outside/internet to my server except for ports 80 and 21/20... My server is behind router (router forwards only 80 and 21 ports)... and allow ssh, webmin access from lan connection..[/QUOTE]
You can use also Firestarter - gui firewall configurator and tool for observing firewall.
 ```
apt-get install firestarter
```

---

### Post by CrustyDOD on 2005-05-22
erm using FireStarter on server without GUI? Hardly  :) 

Thx for the link, did a search on these forums but forgot about uncle Google  ](*,)

---

