---
title: "IRCD-IRC2 Server Always In Split Mode"
date: 2010-03-25
forum: Server Platforms
---

### Post by cusinndzl on 2010-03-25
I set up an IRC Server and it is always in split mode. The split mode will not allow operator rights to me even though it is in the config file. 

```

M:cusinndzlhomeserver.co.cc::ZL Studios Ubuntu IRC Server::000A

# A-Line
A:ZL Studios IRC Server running Ubuntu Server <cusinndzl@zlstudios.net> ::ExampleNet

# Y-Lines
Y:1:90::100:512000:5.5:100.100
Y:2:90::300:512000:5.5:250.250

# I-Line
I:*:::0:1
I:127.0.0.1/32:::0:1

# P-Line
P::::6667:


O:cusinndzl@192.168.1.3:passwordishere:cusinndzl:6667:<Class>:A:


```

Can anyone help me with this?

---

### Post by KB1JWQ on 2010-03-25
Sorry-- I'm a bit better with Dancer / ircd7.  I haven't touched whichever one this is.

-- KB1JWQ
Volunteer Staff, freenode IRC network

---

### Post by cusinndzl on 2010-03-25
> **KB1JWQ said:**
> Sorry-- I'm a bit better with Dancer / ircd7.  I haven't touched whichever one this is.

-- KB1JWQ
Volunteer Staff, freenode IRC network


Do you know what split mode means?

---

### Post by KB1JWQ on 2010-03-26
All right, I'll get off my duff and actually answer the question. :-p

The ircd you're using isn't set to use standallone mode-- it thinks it'll be part of a network, and the fact that it can't talk to other servers it thinks it should be peering with means it's stuck in split mode-- check wikipedia for their article on netsplits to see what these are, as well as why a server won't auto-grant ops while in split mode.

Did you compile this ircd yourself, or are you using a package?  What ircd is it?

---

### Post by cusinndzl on 2010-03-26
> **KB1JWQ said:**
> All right, I'll get off my duff and actually answer the question. :-p

The ircd you're using isn't set to use standallone mode-- it thinks it'll be part of a network, and the fact that it can't talk to other servers it thinks it should be peering with means it's stuck in split mode-- check wikipedia for their article on netsplits to see what these are, as well as why a server won't auto-grant ops while in split mode.

Did you compile this ircd yourself, or are you using a package?  What ircd is it?

I'm using the IRC server that was in the Ubuntu Server 9.10 documentation. It is a package. [https://help.ubuntu.com/9.10/serverguide/C/irc-server.html]("https://help.ubuntu.com/9.10/serverguide/C/irc-server.html")

---

### Post by KB1JWQ on 2010-03-26
ruh-roh.

[http://www.irc.org/mla/ircd-users/2005/msg00015.html](http://www.irc.org/mla/ircd-users/2005/msg00015.html) seems to think you'll have to do a recompile, which sounds decidedly odd to me.  

At this point you might consider an ircd that's more flexible in this respect, or a software-specific support forum.  :-/

---

