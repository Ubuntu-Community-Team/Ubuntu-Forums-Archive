---
title: "socket application - bind permission denied"
date: 2006-10-11
forum: Server Platforms
---

### Post by Amalaye on 2006-10-11
Hello I have a socket application written in C ... that is acting up ... I am runnung on an Ubuntu Desktop install running on an x86 box. When I try to do a bind on a socket, I get a permission denied error.

This application works without complaint on Fedora ... so I am wondering what is up. Naturally I have checked /etc/hosts, resolv.conf, hosts.allow | deny ... I have checked ip-tables ... so I am generally confused.

How do I modify/change/set the rules on binding to a port.

---

### Post by paul.maddox on 2006-10-11
What port number are you trying to bind to?

Are you running the script as your user, or as root?

As far as i'm aware, only root can bind to ports under 1024, i'm sure there is a way around this somehow but i've never needed to do it.

---

### Post by paul.maddox on 2006-10-11
Ok, you got me curious!

Apparently you can use IPtables to take all traffic coming in on a low port (<1024) and redirect it to your application

sudo /sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp -d <your ip> --dport 
<low port> -j REDIRECT --to-port <high port your script listens on>

---

### Post by Amalaye on 2006-10-18
The applications are started when they are forked from another program. I switched back to Fedora Core 3 and they worked (no connection refused) ... so I think it as a result of what happens when they are forked which I need to understand better.

I think forked applications inherit resources from the parent ... I need to study this more.

---

