---
title: "tomcat6 config issue"
date: 2009-01-27
forum: Server Platforms
---

### Post by javadoode on 2009-01-27
Hi

I've recently installed tomcat6 on intrepid. 
and I'm facing a really weird problem accessing it remotely.

Tomcat is running on port 8009 (confirmed by the following netstat command):
root@mybox:~# netstat -t -l -e | grep tomcat
tcp6       0      0 [::]:8009               [::]:*                  LISTEN
tomcat6    20369
tcp6       0      0 [::]:http-alt           [::]:*                  LISTEN
tomcat6    20366 

The startup goes fine , no errors in logs as well. Only problem is that I get a "Failed to Connect" while trying to access this  instance from a remote location. I'm fairly new to unix, but the above netstat output seems to suggest that tomcat is listening on a non-loopback interface, aint' it?

Note that this is after a fresh install of tomcat on intrepid ibex. 
TIA
-Avy

---

### Post by javadoode on 2009-01-29
Some updates:
I tried switching to port 80, (changed tomcat/conf/server.xml) and every thing works as it should. 
I guess there is something wrong with the way I've setup my firewall rules,
I really want to be able to run tomcat on 8080.. 
I've already executed the following command to add port 8080 to the firewall "ACCEPT" list.. but still no good :(
iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 8080 -j ACCEPT

---

