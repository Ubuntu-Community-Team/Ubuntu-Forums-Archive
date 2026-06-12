---
title: "Editing /etc/hosts"
date: 2005-10-21
forum: Server Platforms
---

### Post by n!x on 2005-10-21
I'm trying to set up a mail server using [this]("http://www.howtoforge.com/perfect_setup_ubuntu_5.04_p3") guide.

But i'm a bit confused about the /etc/hosts. Here's what's confusing me: 

```
       
      (1)                     (2)                      (3)
192.168.0.100        server1.example.com             server1

```

(1) The first thing is my LAN IP address which is 10.0.0.2 on my server.

(2) The next thing is confusing. Let's say i'm hosting this domain on my Ubuntu box [www.123.com](www.123.com) and my mailaddress should look something [email]mail@123.com[/email].
What should the "server1.example.com" look like in my case?

(3) This make a bit sense to my (alias, wright?)

Thanks - hope not that this is a too stupid question :???: 

/n!x

---

### Post by n!x on 2005-10-23
Anybody??

---

### Post by cactus on 2005-10-23
/etc/hosts is where the local machine looks to resolve addresses..first...before doing a dns request to the servers in /etc/resolv.conf

So...what you are setting in /etc/hosts..is how the server can find hosts it needs quickly. The most useful thing to put in there is...the host itself.

if you ip address is 192.168.1.100, then you want something like this..
```

127.0.0.1   localhost.localdomain localhost
192.168.1.100   www.123.com 123.com

```

Note that these entries are only for LOCAL LOOKUPS. If you want everyone else in the wide world to know anything about that domain, you have to set up appropriate dns information.

---

