---
title: "Configure iptables to allow webmin traffic"
date: 2009-03-06
forum: Server Platforms
---

### Post by uim on 2009-03-06
I'm a complete newbie, and I needs some advice/pointers on how to add a rule to iptables to allow [webmin]("http://webmin.com") traffic.  I know how to edit the iptables rules file, but what would the contents of the line be that would allow the appropriate traffic?  Thanks in advance.

---

### Post by uim on 2009-03-06
I've been trying to research this, and have come up with this rule (given that I'm using port 30000).  Is this right or am I missing something?

```
-A INPUT -p tcp -m tcp --dport 30000 -j ACCEPT
```

---

### Post by gombadi on 2009-03-06
> 
-A INPUT -p tcp -m tcp --dport 30000 -j ACCEPT


You can drop the -m tcp if you want so the rule becomes -

```

-A INPUT -p tcp --dport 30000 -j ACCEPT

```

Append to the input chain, match tcp packets with a destination port of 30000, jump to accept.

The -p tcp will match any tcp packets so the -m tcp is not needed.

---

### Post by Mobadder on 2009-03-06
Me too i need to control bandwidth via iptables, i have installed webmin and squid cache server on the same machine.
any ideas thanks

---

### Post by hictio on 2009-03-06
FYI, Webmin's default port is 10000.

You can add more parameters, to make it more robust/ secure:
```

-A INPUT -d your.ip.address -s 0/0 -i eth* -p tcp --dport 10000 -j ACCEPT

```

Where on '-d' the destination of the packets, you have to use the IP address that Webmin is listening, as returned by the ifconfig command.
On '-s', the source, you can limit which network or hosts IP addresses are allowed to connect to Webmin, or set it to '-s 0/0' to leave it open to the public.
On '-i eth*' you have to set the interface on which Webmin is listening (the same one that you use on '-d')

As usual, when you are editing iptables rules, check, double and triple check for typos, to avoid being locked out of your own box, specially if you only have remote access thru the network.

---

### Post by uim on 2009-03-07
Thanks for the help guys, I appreciate it.

---

