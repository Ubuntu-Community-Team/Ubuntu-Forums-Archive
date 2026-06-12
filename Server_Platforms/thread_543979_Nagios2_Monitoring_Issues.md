---
title: "Nagios2 Monitoring Issues"
date: 2007-09-05
forum: Server Platforms
---

### Post by johng4 on 2007-09-05
I've been configuring Nagios2 from the repos with little issue.  I have a few hurdles I need to cross yet, and thats where I need a fresh set of eyes to look at the problem... been troubleshooting this so long its all blurred to me at this point...


1. MySQL/PostGRE SQL Monitoring...
On all my checks, no matter what settings, I get a permission error on accessing the database.. even the localhost database for the machine that nagios is on.  I'm figuring this is an issue with MySQL being configured not to allow external connections to it.

2. Jabber Monitoring...
I get a bad return about not being able to make a SSL connection.  I use ejabberd, and the return value from the check_jabber plugin returns a value that indicates that it sees Jabber, but it can't connect to it.  I don't care if Nagios can connect to it, I just want to know if its running.

3. Monitoring a different subnet...
I've got a block of static IPs (5 useable), of which 1 IP is assigned to the router which hosts my local network.  I would like to be able to just ping the computers setup on static IPs on the local network to see if they are up and running.

The IP Block sits outside the router which handles the localnet, and the IP Block is a 206.166.227.x while the localnet is 192.168.10.x.

Would the perferred method be setting up something like SSH and having Nagios hit ports on the router which forward to the SSh ports configured on each machine?  Or is there a way to scan past the router?  I'm pretty sure the former is the best solution, but I would like to minimize the amount of things I have to setup on the client side.

---

### Post by johng4 on 2007-09-06
bump... looking for even a shot in the dark here

---

