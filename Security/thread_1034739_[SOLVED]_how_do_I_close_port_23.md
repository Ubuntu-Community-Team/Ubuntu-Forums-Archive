---
title: "[SOLVED] how do I close port 23"
date: 2009-01-09
forum: Security
---

### Post by Dumbestcrayon on 2009-01-09
I just scanned with nmap and found that my port 23 is open. This is not safe. Can anybody tell me how to close it?

---

### Post by lykwydchykyn on 2009-01-09
First step is to find out what's running on port 23 and see if you can't shut it down or uninstall it:
```

sudo netstat -tunap|grep 23

```

That should show you what's running on 23.  Post what you get from that, and we'll help from there.

---

### Post by Dumbestcrayon on 2009-01-09
tcp        0      0 0.0.0.0:23              0.0.0.0:*               LISTEN      4829/inetd      
udp        0      0 239.255.255.250:1900    0.0.0.0:*                           14872/twonkymediase
udp        0      0 239.255.255.250:1900    0.0.0.0:*                           14872/twonkymediase
udp        0      0 239.255.255.250:1900    0.0.0.0:*

---

### Post by hyper_ch on 2009-01-09
why is having port 23 open not safe?

---

### Post by Dumbestcrayon on 2009-01-09
Its easily hacked.

Port 23 is for telnet

---

### Post by hyper_ch on 2009-01-09
does a telnet server run?

---

### Post by Dumbestcrayon on 2009-01-09
I don't know what you're asking me but my port 23 is open and I was able to connect to it from another pc with telnet.

---

### Post by hyper_ch on 2009-01-09
telnet can just about to connect to any daemon running...

after setting up postfix I use telnet to connect to it to check that everything is fine. Does that now make postfix insecure?

---

### Post by adamlau on 2009-01-09
If it is not already installed:

```
sudo apt-get install ufw
```

```
sudo -i
ufw deny 23
ufw enable
ufw status
```

Or simply have ufw deny connections to all ports:

```
ufw default deny
ufw enable
ufw status
```

---

### Post by cdenley on 2009-01-09
Or better yet, disable the telnet server. Even better, don't install it to begin with. Post this output.
```

cat /etc/inetd.conf

```

---

### Post by cariboo on 2009-01-09
You could also configure Twonky Media server to use a different port.

Jim

---

### Post by pgmer6809 on 2009-01-09
> **Dumbestcrayon said:**
> I don't know what you're asking me but my port 23 is open and I was able to connect to it from another pc with telnet.

If you can connect to it, then you have something listening on that port.
If it is in fact telnet and you are not behind a firewall then indeed it is not safe.

The file that allows listening on various ports is 
/etc/services
There are a LOT of them defined in there but of course unless the server is actually started then any connection attempts are ignored.

If you are connected to the internet you should be behind a firewall.
Either an external firewall, or one built into your machine. ( see the post that describes how to use ufw for internal one.)
Typically you can set the firewall to block all incoming attempts unless the attempt is part of a connection that was established by your own outgoing attempt.
External hardware firewalls typically have easy setup and management via a web page and are good to have if you have more than one computer on your own 'in-house' network. You want your various computers to be able to talk to each other but you dont want to allow outsiders in.

Regardless of firewall or not, most security concious people no longer use telnet. Instead they use ssh. But that is another discussion. That is only to say that you can afford to make sure that the telnet service is not running and not lose functionality.
Frankly I am surprised it IS running. I would not have thought that Ubuntu would enable it by default.
pgmer6809

---

### Post by Dumbestcrayon on 2009-01-10
> **cariboo907 said:**
> You could also configure Twonky Media server to use a different port.

Jim


Twonky is not using 23. Telnet is.

---

### Post by Dumbestcrayon on 2009-01-10
> **adamlau said:**
> If it is not already installed:

```
sudo apt-get install ufw
```

```
sudo -i
ufw deny 23
ufw enable
ufw status
```

Or simply have ufw deny connections to all ports:

```
ufw default deny
ufw enable
ufw status
```



Thanks a lot. Thats what I was looking for.
Problem solved.

---

### Post by brian_p on 2009-01-10
> **Dumbestcrayon said:**
> Its easily hacked.

No it is not. You're labouring under a misconception.

> Port 23 is for telnet

Telnetd to be precise. If it is running removing it is the sensible way of closing the port.

```
apt-get remove --purge telnetd
```

---

