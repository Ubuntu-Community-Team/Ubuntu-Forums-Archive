---
title: "Blocking linhost274.prod.mesa1.secureserver.net"
date: 2011-02-03
forum: Security
---

### Post by paulkater on 2011-02-03
Hi all,
I am trying to keep linhost274.prod.mesa1.secureserver.net (IP 208.109.14.77) from accessing my machine. Several times per evening (as far as I see) it connects to my machine, each time on a different port, and pushes up data transfer. I can't find what it does, it just pushes a GB or more over the line and then stops.

I try to keep it out with UFW:

paul@Kelutral:~/$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   REJECT      208.109.14.77
208.109.14.77 80           DENY        208.109.14.77 80
208.109.14.77/tcp          REJECT      208.109.14.77/tcp
Anywhere                   REJECT OUT  208.109.14.77

But that does not work. The transfer keeps coming.

Anyone have a clue how to stop this?

Thanks

---

### Post by cariboo on 2011-02-03
What application is connecting to the server?

---

### Post by paulkater on 2011-02-03
I don't have a clue. It connects over another port everytime. The IP points to godaddy.com, and on that IP there are a HOST of servers, over 1000 or so it seems.

iptraf shows me this:

IPTraf
&#9484; TCP Connections (Source Host:Port) &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Packets &#9472;&#9472;&#9472; Bytes Flags Iface &#9488;
&#9474;&#9484;192.168.1.11:43613 > 19612 1021936 --A- eth0 &#9474;
&#9474;&#9492;208.109.14.77:80 > 48196 36249757 -PA- eth0 &#9474;

and a little later:

&#9474;&#9484;192.168.1.11:43613 > 37871 1974192 --A- eth0 &#9474;
&#9474;&#9492;208.109.14.77:80 > 94173 72871963 --A- eth0

Over 72MB has been sent already.

&#9474;&#9484;192.168.1.11:43613 > 65863 3433064 --A- eth0 &#9474;
&#9474;&#9492;208.109.14.77:80 > 163575 110169881 -PA- eth0 

I'm entirely at a loss. Will have to investigate how to close all ports on my machine except a few that I have services running for, like http.

---

### Post by lisati on 2011-02-03
You might want to check out the [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") website as part of your toolkit. It can help you discover which of your ports are open and closed.

---

### Post by paulkater on 2011-02-03
Thanks for that. I ran the full check and all ports come back stealth.
> Your system has achieved a perfect "TruStealth" rating. Not a single packet — solicited or otherwise — was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet.
Getting more interesting all the time...

---

### Post by cariboo on 2011-02-03
Try:

```
lsof -i -P
```

it will show what's connected to what.

---

### Post by paulkater on 2011-02-03
Cool! Now we're getting somewhere!!
Thanks, this showed me something I can act on!

---

