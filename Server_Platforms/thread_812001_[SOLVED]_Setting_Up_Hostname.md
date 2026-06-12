---
title: "[SOLVED] Setting Up Hostname?"
date: 2008-05-29
forum: Server Platforms
---

### Post by EMCGFX on 2008-05-29
I've installed Ubuntu 8.04 x32 Server (home server, not public) yesterday. I've installed Apache2,PHP,MySQL,phpMyAdmin. Now what I need to due is to have hostname setup properly. I need to be able to type; [http://myserverbox/](http://myserverbox/) and be able to access it, instead of typing the ip. Any help will be appreciated.

Also, If I am running this server for my self at home. What is the minimal software I need. I know I need Apache2, MySQL, PHP5. What else?

](*,)

---

### Post by ibutho on 2008-05-29
One option is to map the hostname and ip in /etc/hosts e.g.
```
192.168.1.2   myserverbox.somedomain    myserverbox
```

---

### Post by freebeer on 2008-05-29
To take the previous replay a bit further, you'd do that on each of the machines on your LAN that you want to have access to the server.

So if MachineA is your server running Apache2, and it has an IP address of 192.168.1.100, you'd put:

192.168.1.100  MachineA

in each of the computers' /etc/hosts file.  Once done, you can use "MachineA" in, say, the address bar of firefox, and that computer will know that "MachineA" translates to an IP address of 192.168.1.100.

---

### Post by sDoky on 2008-05-29
Or make it act as an DNS server and define it there. I'm using Bind9 on my home server and it works just fine. You can define the translations by webmin web interface [configuration tool]("http://www.webmin.com/"). That makes it translateable by other machines than linux-powered (e.g. windows) but you MUST set the IP address of this server to be the default DNS on each machine.

---

### Post by EMCGFX on 2008-05-29
I take it "somedomain" can be anything, or does it need to much my other box ?

---

### Post by sDoky on 2008-05-29
Well it does not really matter what you will call it it can be "shitty_wok" if you want it to be, even if it is not the real name of the system. Just define some hostnames in /etc/hosts or set up the DNS server.
> **EMCGFX said:**
> I take it "somedomain" can be anything, or does it need to much my other box ?

---

### Post by EMCGFX on 2008-05-29
Do I need to have bind9 ?

---

### Post by freebeer on 2008-05-29
It can be anything.  In fact, it can be different on each machine, since the translation of the name results in the same IP address, but I wouldn't recommend such a set up.  ;)

MachineB could call it "Server", MachineC could call it "HoneyPie" - the translation of the name to the IP is local to that particular machine.  But you'd have to remember that when you're on MachineB it's "Server"... messy to use and maintain.  I only use the example as a means of trying to explain what's going on.

---

### Post by freebeer on 2008-05-29
> **EMCGFX said:**
> Do I need to have bind9 ?

Nope.  I don't on my server.

---

### Post by sDoky on 2008-05-29
No, if you do not want to use the hostname from a windows machine. For windows you have to have Bind9.
> **EMCGFX said:**
> Do I need to have bind9 ?

---

### Post by EMCGFX on 2008-05-29
OK, I've decided to use webmin on my home server. How would I due hostname there, os I can access it by domain instead of ip (exp. [http://myserverbox/](http://myserverbox/)) ?

---

### Post by EMCGFX on 2008-05-30
SOLVED ;) I just edited my local file instead of the servers.
/etc/hosts
192.168.0.200 server

That all.

---

