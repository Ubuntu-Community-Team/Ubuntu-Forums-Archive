---
title: "Where are ports blocked, other than iptables?"
date: 2007-05-23
forum: Server Platforms
---

### Post by dexter2 on 2007-05-23
Hi,
I'm running service that should be listening on ports 8080,1099. This service is working only when accessed from local machine. Also look at this:

$ nmap -p 8080,1099 dunaj
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-23 17:25 CEST
Interesting ports on dunaj.madalbal (127.0.1.1):
PORT     STATE SERVICE
1099/tcp open  unknown
8080/tcp open  http-proxy
Nmap finished: 1 IP address (1 host up) scanned in 0.214 seconds

$ nmap -p 8080,1099 localhost
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-05-23 17:25 CEST
Interesting ports on localhost (127.0.0.1):
PORT     STATE  SERVICE
1099/tcp closed unknown
8080/tcp closed http-proxy
Nmap finished: 1 IP address (1 host up) scanned in 0.105 seconds
$

I use shorewall to setup iptables - i don't thing there is a problem. I also did not find problem in service configuration.

Is there something between iptables settings and service, that can block ports?

Thanks
      Dexter2

---

### Post by craigp84 on 2007-05-23
It depends what IP(s) your process is setup to listen on. Do a ```
netstat -antu | egrep '(8080|1099)'
``` to see exactly where it's listening.

Also, sort out your /etc/hosts - your dunaj hostname is pointing to 127.0.1.1

-c

---

### Post by dexter2 on 2007-05-23
vilok@dunaj:~$ netstat -antu | egrep '(8080|1099)'
tcp        1      0 127.0.1.1:60109         127.0.1.1:8080          CLOSE_WAIT
tcp        1      0 127.0.1.1:60110         127.0.1.1:8080          CLOSE_WAIT
tcp        1      0 127.0.1.1:10839         127.0.1.1:8080          CLOSE_WAIT
tcp        1      0 127.0.1.1:10840         127.0.1.1:8080          CLOSE_WAIT
tcp6       0      0 ::ffff:127.0.1.1:1099   :::*                    LISTEN
tcp6       0      0 ::ffff:127.0.1.1:8080   :::*                    LISTEN
vilok@dunaj:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       dunaj.madalbal  dunaj

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
vilok@dunaj:~$

---

### Post by dexter2 on 2007-05-24
Thank you craigp84, you directed me the right direction. Problem was my setting: 
127.0.0.1 dunaj
in /etc/hosts. 
Like this when i have run setup for service, it has registered IP address 127.0.0.1 in it's config file. After i changed this entry in /etc/hosts, service is listening also on outside IP.
Thanks you.

---

