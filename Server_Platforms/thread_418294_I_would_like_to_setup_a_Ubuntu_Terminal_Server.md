---
title: "I would like to setup a Ubuntu Terminal Server"
date: 2007-04-22
forum: Server Platforms
---

### Post by bobsta63 on 2007-04-22
Hi all,

I would like to setup a Ubuntu Terminal Server like Microsoft Windows 2003 Terminal Server so that I can allow my friends and family to connect to it and work remotely on it. Not only to improve there low powered home PC's but also there bandwidth issues as most of them use dial-up etc. Ideally would like the users to be able to use the Microsoft Remote Desktop software to connect to it.. but not essential.

I have read a post on these forums about using NX Server (Free version) however I realise now that you can only have two users logged on at one time. I would say that there would normally be atleast 4 people logged on at once.

Does anyone know of any good tutorials for setting up a Terminal Server on Ubuntu? Like I said above, I would prefer not to use NX Server (Free) as it only supports a couple of users connected at once.


Thanks in advance. :)

Kindest Regards,

Bobby

---

### Post by visik7 on 2007-04-22
you are wrong freenx doesn't lock you to 2 user at the same time

---

### Post by bobsta63 on 2007-04-22
> **visik7 said:**
> you are wrong freenx doesn't lock you to 2 user at the same time

Are you sure?... 

I used this tutorial and if you look at the bottom of the page, (In the comments section):

[http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake](http://www.urbanpuddle.com/articles/2006/08/23/install-nx-server-on-ubuntu-dapper-drake)

```
wilbur.harvey@spirentcom.com  said 5 days later:

The only problem is that the NX server from NoMachines only supports 1-2 users. It appears that if one user is logged in using NX, and another is logged in via ssh, a third user cannot log in using NX. NoMachines web site does not make it easy to see this limitation.
```


Also, Should I install FreeNX on Dapper Desktop version or Server version?

---

### Post by jon21 on 2007-04-23
There are two NX servers available:

1) NoMachines NXServer: The free version of this only allows 2 people connected at once, and only 2 usernames even authorized to connect.  NoMachines offers non-free versions of their server that allow more users, admin tools, etc.

2) FreeNX Server: A totally free NX server.  Allows as many authorized and simultaneous users as you would like.  No fancy admin tools (afaik).  Installation instructions can be found at 

[COLOR="Blue"][https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")[/COLOR]

- Jon

---

