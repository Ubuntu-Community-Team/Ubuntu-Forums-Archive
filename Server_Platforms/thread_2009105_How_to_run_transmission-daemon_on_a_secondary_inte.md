---
title: "How to run transmission-daemon on a secondary interface"
date: 2012-06-24
forum: Server Platforms
---

### Post by sona1111 on 2012-06-24
I have been in the irc support chat for many weeks trying to figure this one out, but finally i decided to give the forum a go. 

Anyway i have a web/file/halo/etc server going with a main fast connection, and i also have a slower connection that i want to make use of. (two separate modems) So basically i want every single thing on the server to use one interface EXCEPT transmission-daemon, which i want to use the other. i also want remote connections to go through the main interface, only the traffic itself goes through the secondary. (both already have static ips)

Transmission looks like it has this all good to go in its settings.json file, where you can set a bind ip for both the remote and regular connections. However, changing it to the ip of the other connection does nothing, it just uses the main connection. (even after restarting the daemon, yes)

I have heard you need to mess with iptables or something to get this to work, but i could not find a tutorial applying to transmission. can anyone tell me how to do this?

thanks for reading.

---

### Post by sona1111 on 2012-06-24
bump

---

