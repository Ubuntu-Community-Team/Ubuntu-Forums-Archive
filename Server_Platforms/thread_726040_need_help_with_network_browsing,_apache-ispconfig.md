---
title: "need help with network browsing, apache-ispconfig"
date: 2008-03-16
forum: Server Platforms
---

### Post by revenegofweed on 2008-03-16
network structure:

                            wan 
                   I          -         I
               my pc         webserver
          192.168.0.3   192.168.0.4

i'm using ubuntu server and ISPCconfig on my webserver. i wanted to use more than 1 site on that server. there is nothing to worry about that. the web server is reachable from outfield. but when i enter the domain name into my browser (own pc on same lan), it forwards me to /var/www/sharedip folder. it's not forwarding to folders which opened for seperate domains. i don't know too much that what can I do for that issue but according to my readings, the apache should forward to requests the seperate web sites to their folders. 

my /etc/resolv.conf : 

root@192:/# cat /etc/resolv.conf
nameserver 127.0.0.1

my /etc/hosts :

root@192:/# cat /etc/hosts

192.168.0.4    localhost [www.domain.com](www.domain.com) [www.domain2.com](www.domain2.com)

# The following lines are desirable for IPv6 capable hosts

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and I also changed my pc's dns server's to webserver's ip address. nothing change.
-------------------------------

I used "The Perfect Server" document from the howtoforge.

---

