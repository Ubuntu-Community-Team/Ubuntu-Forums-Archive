---
title: "ping and apache can't find local domains"
date: 2008-08-09
forum: Server Platforms
---

### Post by sawatdee on 2008-08-09
My system has a name server which works fine (I've tested it with dig, named-checkzone, nslookup, etc.). The system has a web server running but the server can't see any of the sites that are set up in the name server, and ping can not find them either. The only way these programs can see those domain names is if I explicitly put them in /etc/hosts. I will need to test the sites from other machines on the local network and I really need to make the system resolve those domains from the name server.

Other info:
The system was installed as a desktop installation and the bind9 package was added after that. I can't see why that would matter though. I can't think of anything that is missing or not configured properly to make this work. I have set up several name servers in the past and have never had any problems.

/etc/resolv.conf looks fine (192.168.123.1 is my local server):
```
search hsd1.co.comcast.net.
nameserver 192.168.123.1
nameserver 192.168.123.254
nameserver 68.87.85.98
nameserver 68.87.69.146

```

Does anyone have any idea what could be wrong? I am new to ubuntu and am starting to have doubts about using this distro as a reliable server. I would hate to have to set up the whole system all over again.

---

### Post by Dedoimedo on 2008-08-10
Hello,

We've talked in the last post, let's go through this one:

**1. I suggest you use view statements, separately for localhost, internal and external and not declare zones in the main body of the named.conf.**

**2. In the localhost zone:**

```
include "named.root.hints"
include "named.rfc1912.zones"
```

**3. In the internal zone:**

```
include "named.root.hints"
```

You will find these files, including instructions how to download the root hints zone file in the sample package in the /usr/share.

Then, add your own zones, don't forget the reverse zone.

Make sure the name servers are declared properly and that they match the relevant IPs and host names.

**4. Make sure the firewall is not obstructing the communication:**

A. Port 53 needs to be open.
B. Forwarding needs to be enabled if the machine also serves as the intranet/internet gateway.

**5. You must allow the system to use dns BEFORE hosts files, this is set by the system switch - /etc/nsswitch.conf:**

Under hosts, you should have

```
hosts: dns files
```

This means, query dns first, /etc/hosts file second

**6. Make sure the /etc/resolv.conf is configured properly:**

Should include:

```
nameserver xxx.xxx.xxx.xxx[/b]

The IP address of the server that needs to be used, both on the server and the clients. And if the server itself is using another machine as its own nameserver, then it should be there.

I see you've figured it out.

**7. Important question: is BIND pre-compiled to run chrooted? If so, then you need to place the files in the chroot jail and not in the standard location.**

**Standard:**

[code]/etc/named.conf
/var/named/
```

**Chroot:**

```
/var/named/chroot/etc/named.conf
/var/named/chroot/var/named/
```

Cheers,
Dedoimedo

---

### Post by sawatdee on 2008-08-10
Thank you so much!!! It seems to have been /etc/nsswitch.conf which had dns in its hosts list, but it was not first. I don't understand why it doesn't use dns if the domain name is not found in /etc/hosts.

---

### Post by Dedoimedo on 2008-08-11
Hello,
Good, mark your thread as solved. And ... it's my pleasure to help. I'll give you a more detailed answer to your question "why it doesn't ..." a little later.
Cheers,
Dedoimedo

---

