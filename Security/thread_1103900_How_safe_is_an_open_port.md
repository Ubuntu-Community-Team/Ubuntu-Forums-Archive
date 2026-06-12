---
title: "How safe is an open port?"
date: 2009-03-23
forum: Security
---

### Post by joshaman on 2009-03-23
Do I risk anything by allowing inbound connections through a high port, say 5000+?  Can someone hack me using telnet through this port?

---

### Post by brian_p on 2009-03-23
> **joshaman said:**
> Do I risk anything by allowing inbound connections through a high port, say 5000+?

The security of a service has nothing to do with the port number it is listening on.

> Can someone hack me using telnet through this port?

That depends on how well you have secured the service.

---

### Post by joshaman on 2009-03-23
how well i secured the telnet service?  how do i secure my service?

---

### Post by brian_p on 2009-03-23
> **joshaman said:**
> 

how do i secure my service?

What service do you have in mind to be listening on this port?

---

### Post by joshaman on 2009-03-23
Transmission BT client.

---

### Post by brokenLockpick on 2009-03-23
Are you talking about leaving some port on your router open for use with Transmission?

---

### Post by brian_p on 2009-03-23
> **joshaman said:**
> Transmission BT client.

Transmission is a secure application. It does not accept requests from telnet.

---

### Post by joshaman on 2009-03-23
brokenLockpick: yea - that's what I'm talking about.

brian_p: so the only way that an open port can be unsafe is if the service listening on the port can be hacked?  I read that that was the deal but wasn't sure.  Is there anything else I should be aware of?  Some people talk about open ports as if they're holes in the security of a system.

---

### Post by Bachstelze on 2009-03-23
> **joshaman said:**
> Some people talk about open ports as if they're holes in the security of a system.

Those people most likely know very little about security. It's just as you said: an open port is as much of a security risk as the aplication that listens on it. Maybe tomorrow a security vulnerability will be discovered in Transmission, and in that case, yes, the fact that you have it listening on a port will be a security flaw in your system.

Security is all about that: to which extent can you trust your software to be secure, and whether the risk of using it is more important than the benefits.

---

### Post by joshaman on 2009-03-23
thanks.  That's great news.  

I'm not familiar with telnet and don't understand it at all.  That's mainly what I was worried about.

---

### Post by Bachstelze on 2009-03-23
> **joshaman said:**
> 
I'm not familiar with telnet and don't understand it at all.  That's mainly what I was worried about.

Basically, when someone will connect to your Transmission port using Telnet, Transmission will see just another incoming connection, and will send the exact same data than it would to another bittorrent client. Since this data is supposed to be interpreted by a bittorrent client and not displayed as text on a terminal, it will just look like gibberish on the Telnet client.

By the way, you can see this for yourself:

```
telnet 127.0.0.1 5555
```

(or whichever port you chose)

---

### Post by joshaman on 2009-03-23
Thanks for the info.  i'll try that out when I'm at work later today.

I had a complete misconception of telnet.  I was under the impression that anyone could gain remote access to my computer through any open port.  The misinformation that's posted all over the internet by people who have no idea what they're talking about...

Thanks very much for clarifying.

---

### Post by bodhi.zazen on 2009-03-23
An open port is only as secure as the server using the port, in this case transmission.

I suggest you confine transmission with apparmor.

---

### Post by ccw on 2009-03-23
> **joshaman said:**
> Thanks for the info.  i'll try that out when I'm at work later today.

I had a complete misconception of telnet.  I was under the impression that anyone could gain remote access to my computer through any open port.  The misinformation that's posted all over the internet by people who have no idea what they're talking about...

Thanks very much for clarifying.

Having NEEDLESS open ports is a security risk. Basically the more services you have available, the more possibilities for intrusion.

Run what you need, and only what you need.

(And be mindful of your workplace's computer use policy)

---

### Post by The Cog on 2009-03-23
The fear of open ports is windows think. Windows tends to have lots of open ports running all kinds of services. So a firewall is an easy way to block them off from attempted hacks. In contrast, Ubuntu installs with very few listening services so there isn't much "attack surface" for attackers to work on. So the only listening ports are the ones for programs / services that you installed and ran yourself.

telnet is a service that normally listens on port 23 and provides a text login like the console. It's regarded as insecure because it's not encrypted - a network monitor could pick out the password, as well as see everyting else the user is doing. And of course, attackers can just keep trying passwords till they get in. It's not installed on Ubuntu by default, and if you try to install it, a warning tells you it's not regarded as secure are you really sure (or something like that). SSH is the recommended service to install if you want to enable remote login, but make sure your passwords are all good strong ones first.

---

### Post by Bachstelze on 2009-03-23
> **The Cog said:**
> 
telnet is a service that normally listens on port 23 and provides a text login like the console. It's regarded as insecure because it's not encrypted - a network monitor could pick out the password, as well as see everyting else the user is doing. And of course, attackers can just keep trying passwords till they get in. It's not installed on Ubuntu by default, and if you try to install it, a warning tells you it's not regarded as secure are you really sure (or something like that). SSH is the recommended service to install if you want to enable remote login, but make sure your passwords are all good strong ones first.

True, but you're talking about the telnet *server*. It's irrelevant here, since we're talking about the telnet *client*, which can connect to all kinds of servers, not only telnet servers, and is a very useful tool to have on your system.

---

### Post by lovinglinux on 2009-03-23
+1 for Apparmor

---

### Post by joshaman on 2009-03-23
> **bodhi.zazen said:**
> An open port is only as secure as the server using the port, in this case transmission.

I suggest you confine transmission with apparmor.

Thanks, I'll check it out.

---

### Post by lovinglinux on 2009-03-23
> **joshaman said:**
> Thanks, I'll check it out.

[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

Transmission profile: [http://ubuntuforums.org/showpost.php?p=5279341&postcount=6](http://ubuntuforums.org/showpost.php?p=5279341&postcount=6)

---

