---
title: "invalid response from Proxy dns lookup failure in my domains"
date: 2011-01-10
forum: Server Platforms
---

### Post by tapas_mishra on 2011-01-10
I am having a server which is in a corporate data centre.
So on  a lot of firewall DNS and similar stuff it is the sys admins of company who have a control than me.
I had to setup a cluster where I have 4 Virtual Machines and each of them has a different websites and several different applications would be served on them.
The only connection allowed to me is via an Apache Reverse Proxy.
So I do not have a DNS entry in my hand.
Some one else booked a Domain name and pointed to the public IP (which was given to me by people in my organization)


Since I do not have DNS (and also not allowed to have one on the server above where I mentioned all) so I added in 
```
/etc/hosts
127.0.0.1       localhost
192.168.1.10  [myserver.com]("http://myserver.com/")
192.168.1.16  [site4.myserver.com]("http://site4.myserver.com/")
192.168.1.13  [site1.myserver.com]("http://site1.myserver.com/")
192.168.1.14  [site2.myserver.com]("http://site2.myserver.com/")
192.168.1.15  [site3.myserver.com]("http://site3.myserver.com/")

```
and /etc/host.conf
```
order hosts,bind
multi on


```
 nsswitch.conf entry

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

```
Things seem perfect upto here.


My proxy pass entries look as follows

```
   ProxyPass /app1 [http://192.168.1.3:8080/app1](http://192.168.1.3:8080/app1)
  ProxyPass / [http://192.168.1.3]("http://192.168.1.3/")
  ProxyPassReverse /app1 [http://192.168.1.3:8080/app1](http://192.168.1.3:8080/app1)
  ProxyPassReverse / [http://192.168.1.3]("http://192.168.1.3/")

```
If I use the entries as above then some one from internet is able to
access the sites.But from within LAN people are unable to access it.

How ever if I use

```
   ProxyPass /app1 [http://site1.myserver.com:8080/app1](http://site1.myserver.com:8080/app1)
  ProxyPass / [http://site1.myserver.com]("http://site1.myserver.com/")
  ProxyPassReverse /app1 [http://site1.myserver.com:8080/app1](http://site1.myserver.com:8080/app1)
  ProxyPassReverse / [http://site1.myserver.com]("http://site1.myserver.com/")


```then things work on LAN but from internet it is not accessible and
errors are the ones I mentioned above in the thread and people get an error 
```
invalid response from Proxy dns lookup failure in my domains
```
So what can be a feasible solution since in any case I will not be allowed to have a DNS within corporate environment for my project.

---

