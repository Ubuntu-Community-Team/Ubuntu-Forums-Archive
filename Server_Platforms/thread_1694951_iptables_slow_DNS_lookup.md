---
title: "iptables slow DNS lookup"
date: 2011-02-25
forum: Server Platforms
---

### Post by bjh6 on 2011-02-25
My server's response to uname -a is:

2.6.32-28-server #55-Ubuntu SMP Mon Jan 10 23:57:16 UTC 2011 x86_64 GNU/Linux

On this machine,

iptables -L -n 

works fine, but 

iptables -L 

seems to try a DNS lookup on ranges (e.g. 131.111.0.0/16) and on private ip addresses such as 192.168.248.1 and as a result is very slow! This does not happen on SLES 10. Is there some setting that can solve this problem?

Thanks

---

### Post by elico on 2011-02-25
it's not a problem.
it a feature in almost any ip command such as ping traceroute and route.

also its not a problem and you can add an alias for the command like:
> alias iptables='iptables -n'

or to setup the correct dns settings to look-up using a local dns server that will respond fast.

i think  you better the alias.

also to make it default on system wide scale add it to the buttom to the file:
> /etc/bash.bashrc

---

