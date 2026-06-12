---
title: "apache not loading - fails on restart"
date: 2006-10-01
forum: Server Platforms
---

### Post by goneskiing on 2006-10-01
just loaded ubuntu on a new machine and having trouble with apache 2 - no pages will load (cannot find localhost).  

ports.conf set to Listen 127.0.0.1:80

if I try sudo /etc/init.d/apache2 restart - I get 
"Forcing reload ....   [fail]"

any ideas?

---

### Post by ola on 2006-10-01
I have no precise idea about how to help you but I had the same problem once when I had removed my loopback device from /etc/network/interfaces

Ensure that you have the loopback device set, something like:

```
# The loopback network interface
auto lo
        iface lo inet loopback
```

I also have a vague feeling that I had some problems with my routing table preventing Apache from working. Mine looks like this (if it's to any help):

```
route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

Hope you solve it! Best regards,

Ola

---

### Post by goneskiing on 2006-10-01
where do I find the routing table ?

---

### Post by chrisfay on 2006-10-01
```
route
```

---

### Post by sonic2000gr on 2006-10-01
The advice by ola is good. 
You may also want to check that your /etc/hosts contains a line like:

127.0.0.1   localhost.localdomain    localhost

A lot of services will not work without it.

---

### Post by goneskiing on 2006-10-01
sonic  thks - my host file looks like this:

127.0.0.1 localhost mylocaldomain 

but I tried it as 127.0.0.1 localhost.mydomain localhost with no luck

chrisfay:
so where is route ?  a path would be helpful

---

### Post by sonic2000gr on 2006-10-01
Ok let's see where exactly apache fails to start.

First off, have you run apache successfully before? Have you modified any other configuration file except ports.conf? Are you just trying to get the default apache installation going?

You should have a file called error.log in /var/log/apache2
Try to start apache again and post the last couple of lines from the above file.

---

### Post by goneskiing on 2006-10-02
Well, I tried the age old process - deleting Apache and reinstalling and got an error msg pointing to a syntax error in my apache2.conf file - fixed it and it's fine.  For some reason the restart command does not give out this error msg - that would have saved a lot of time.  thks for all the comments.

---

### Post by sonic2000gr on 2006-10-02
Yes the restart command will not normally say what is wrong, however the error.log in /var/log/apache2 will almost certainly point you to the right direction.

---

