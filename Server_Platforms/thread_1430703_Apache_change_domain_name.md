---
title: "Apache change domain name"
date: 2010-03-15
forum: Server Platforms
---

### Post by blakep2 on 2010-03-15
I am using apache to create a webpage for my private network. But the domain is the ip address. I would like to change this but i cant figure it out. I have read many tutorials but they are not helpful.  I am running apache2 on ubuntu 9.04.

---

### Post by cariboo on 2010-03-15
Alias the name to an ip address in /etc/hosts, like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	chilanko
192.168.1.250	willy
192.168.1.225	alexis
```

I use single names, but you could use for example:

```
willy.aplus.net
```

or whatever domain name you want to use. Class A and C ip addresses are non-route-able for the most part, so it doesn't matter what domain name you use on your local network.
.

---

### Post by Ryan Dwyer on 2010-03-15
Decide on a domain name then make sure all the clients on the network resolve that name to the server's IP. If you have a DNS server which you can configure, add an A record for that domain. If not, you'll probably have to add an entry in the hosts file of each computer on the network.

Once that's done, browsing to the domain name should serve up Apache's default host unless you have a specific virtual host configured for that domain.

---

### Post by blakep2 on 2010-03-19
> **cariboo907 said:**
> Alias the name to an ip address in /etc/hosts, like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	chilanko
192.168.1.250	willy
192.168.1.225	alexis
```

I use single names, but you could use for example:

```
willy.aplus.net
```

or whatever domain name you want to use. Class A and C ip addresses are non-route-able for the most part, so it doesn't matter what domain name you use on your local network.
.



This works for the machine that has apache on it but does not work for computers in the network how do i do that

---

