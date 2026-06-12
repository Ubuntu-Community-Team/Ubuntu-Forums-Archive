---
title: "Basic iptable setup for server"
date: 2011-07-21
forum: Security
---

### Post by sneakyimp on 2011-07-21
Per unSpawn's email previously, I would like to:
> 
- allow ALL traffic in and outbound between your management IP 
range (return traffic plus logins) and the host AND
- only allow ESTABLISHED,RELATED inbound traffic from other sources 
(only return traffic).


The basic idea is that I want at this point to allow SSH traffic between my management IP (which, sadly, is via DHCP through Time Warner Cable and may change) and my server.  I've been reading [this article](https://help.ubuntu.com/community/IptablesHowTo) which describes some iptables commands but doesn't seem to show an example that denies SSH traffic from every IP address except a *block* of IP addresses.  I don't want to lock myself out -- that would be very bad.

I've also tried reading [this ponderous document](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#IPFILTERING) and reading the man pages.  I could certainly use some tips here.  In particular, these are my goals in order:
* not to exclude myself from SSH access to the server, even if my IP address changes, which it will
* block unwelcome visitors (meaning pretty much the entire world) from ever speaking to my machine via ssh
* allow incoming requests for web traffic on port 80 and 443
* allow this machine to make mysql queries to another machine
* allow this machine to make secure (and possibly non-secure) curl requests to another web server
* allow this machine to send mail on another machine
* allow this machine to always fetch and install upgrades/updates
* close every other port down

Any thoughts or input would be most appreciated.

---

### Post by stlsaint on 2011-07-21
Make this your new best friend!! :guitar: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by Lars Noodén on 2011-07-22
If the server is on the Internet for all to see, then you might want to limit the rate that SSH can be tried.  Something like the following might work.  YMMV.

```


   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;

   # add host to "recent" list
   ip6tables -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;
   iptables  -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;

   # allow finite number of new connections per time limit
   ip6tables -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT
   iptables  -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT


```

Edit: this is for mitigating brute force attacks

---

### Post by 2F4U on 2011-07-22
Here is an accessible article about securing ssh

[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

---

### Post by Lars Noodén on 2011-07-22
> **2F4U said:**
> Here is an accessible article about securing ssh

[http://www.ubuntugeek.com/securing-ssh.html](http://www.ubuntugeek.com/securing-ssh.html)

DenyHosts / AllowHosts is only good for whitelisting, a trick that only works if you know where all the logins will come from in the future.

---

### Post by HermanAB on 2011-07-22
I secure my servers with a single iptables rule:

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

You don't really need anything beyond that, since the IP stack of Linux has been much improved over the years and most of what you can read about firewalls is not needed anymore.  The days of kilometer long Shorewall rule sets are over.

---

### Post by Lars Noodén on 2011-07-22
> **HermanAB said:**
> I secure my servers with a single iptables rule:

```
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT
```

You don't really need anything beyond that, since the IP stack of Linux has been much improved over the years and most of what you can read about firewalls is not needed anymore.  The days of kilometer long Shorewall rule sets are over.

Good point.

The old, complicated, outdated ones from years ago tend to show up best in search results and online notes.  Any ideas about how to change that?

---

