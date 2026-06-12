---
title: "Using iptables for pop attacks"
date: 2007-09-08
forum: Server Platforms
---

### Post by FakeOutdoorsman on 2007-09-08
I can use iptables to help slow down dictionary SSH attacks with the following (from [howtoforge]("http://www.howtoforge.com/preventing_ssh_dictionary_attacks_with_denyhosts#comment-1411")):

```

iptables -N SSH_CHECK
# here come checks for integrity, portscans(psd) etc
# here allow related traffic
iptables -A INPUT -p tcp --dport 22 -m state NEW -j SSH_CHECK
iptables -A SSH_CHECK -m recent --set --name SSH
iptables -A SSH_CHECK -m recent --update --seconds 60 --hitcount 4 --name SSH -j DROP

```

What the above does is bans the ip for 60 seconds if there are more than 3 connections within 60 seconds.  Is there a way to use iptables to do this for another port or service?  ipop3d is being hammered by bots trying to guess users/password and something like this would work well.

---

### Post by p_quarles on 2007-09-08
That kind of rate limiting can be used on any and/or all ports. The key point here is that you don't need to specify a service, just the port on which it operates. The following link refers specifically to ssh, but you can easily substitute your POP port number and start slowing these attacks.
[http://www.debian-administration.org/articles/187](http://www.debian-administration.org/articles/187)

---

### Post by HermanAB on 2007-09-08
Yes, just change the port number and copy the rules.

---

