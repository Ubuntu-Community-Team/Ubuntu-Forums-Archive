---
title: "connection times out when contecting to remote SSH server"
date: 2011-01-24
forum: Server Platforms
---

### Post by Red Raven on 2011-01-24
When ever i run ssh -p <port> <user>@<remote IP>, i get a connection has timed out error. (i use the -p <port> part because i'm using a custom port). does anyone know what could be causing this? i know of a few *possible* problems, but i don't know how to test them all.

- I am on the same network as the server (I'm trying to test using remote IP to make sure it works before i go out an try it somewhere else)

-The router could be blocking it (i'm using linksys)

-IPtables may not be set up right (i think it is though. the only thing i've run is "sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT". I have changed the port for the server since then. maybe i have to restart it or something for it to recognise the change? I know very little about IPtables though).

-maybe i have to change something in my client or server config files? (the only config file i've changed is the sshd_config file on the seerver, and that was to change the port to my custom port).

thats all i can think of for now. It may be none of those. I do have the sshd_config and port forwarding in my router set to the same port, so thats good. Thanks!

---

### Post by Red Raven on 2011-01-24
ok i think i have narrowed it down to the router settings. but in linksys there are so many, i don't know which one to change.

---

