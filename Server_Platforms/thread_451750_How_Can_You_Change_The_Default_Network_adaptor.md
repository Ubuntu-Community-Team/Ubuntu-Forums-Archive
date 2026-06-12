---
title: "How Can You Change The Default Network adaptor"
date: 2007-05-22
forum: Server Platforms
---

### Post by etechship on 2007-05-22
I have a server with 4 network cards, and I want to change the default card that it uses. 

You set the Default network card when you install the OS, but I would like it to change it to a differant card.

thanks
dave

---

### Post by Endless Bard on 2007-05-22
Hello,

In /etc/network you should have a file called "interfaces."  In that file there should be these lines:

```


auto ethx
iface ethx inet dhcp


```

Change ethx to whatever you want your default adapter to be.  I know that a reboot will make the change, but this being Linux, there's probably something in /etc/init.d that makes it happen.  Probably:

```


/etc/init.d/networking restart


```

Cheers,
-EB

---

