---
title: "Fail2ban - how to set it up."
date: 2012-06-10
forum: Security
---

### Post by jaho22 on 2012-06-10
I need to set an login security for my server.

I have the fail2ban, how do i need to setup my jail file to make all connects to fail after 3 failed login attemps for 3600 seconds.

Aften one hour there can be 3 more login attemps, and so on.

im ubuntu noob.

---

### Post by lisati on 2012-06-10
Which service to you want to monitor for failed logins? SSH? IMAP? Something else?

I'm off to bed soon. Some documentation for fail2ban can be found at [https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban).

---

### Post by bodhi.zazen on 2012-06-11
> **jaho22 said:**
> I need to set an login security for my server.

I have the fail2ban, how do i need to setup my jail file to make all connects to fail after 3 failed login attemps for 3600 seconds.

Aften one hour there can be 3 more login attemps, and so on.

im ubuntu noob.

FYI you can do all this with iptables. 

If you are going to be doing some reading, learning iptables pays off in spades.

```
sudo iptables -A INPUT -p tcp -m state --state NEW -m limit --limit 3/hour -j ACCEPT
```

You can adapt iptables to specific services as well.

```
sudo iptables -A INPUT -p tcp -m tcp --dport 22 -m tcp -m state --state NEW -m recent --set --name SSH --rsource

sudo iptables -A INPUT -p tcp -m tcp --dport 22 -m recent --update --seconds 600 --hitcount 8 --rttl --name SSH --rsource -j DROP

sudo iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
```

The above block of rules is for ssh and blocks more then 8 connection attempts in 10 minutes.

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

Why use iptables ? iptables is not *that* difficult to learn, will accomplish what you want, and without installing and learning to configure any additional service.

---

