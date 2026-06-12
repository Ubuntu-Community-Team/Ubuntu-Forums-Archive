---
title: "beginner's iptables problem"
date: 2009-02-07
forum: Server Platforms
---

### Post by PryGuy on 2009-02-07
Good day to all of you!
I'm going to write a firewall that would have all ports disabled but the ones that I enable. It looks like this:```
#!/bin/sh

INET=eth1
LAN=eth0

# Flush all tables to default:
iptables -F
iptables -F -t nat

# Setting up default politics:
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# Allow all for loopback:
iptables -A INPUT -i lo -s 0/0 -d 0/0 -j ACCEPT

# Allow ICMP for all
iptables -A INPUT -p icmp -j ACCEPT

# Allow SSH
iptables -A INPUT -i $LAN -s 0/0 -d 0/0 -p tcp --dport 22 -j ACCEPT
```SSH works like a charm What do I do to enable http? Opening of port 80 is not enough... :(

---

### Post by Dr Small on 2009-02-07
Why are you doing this anyhow? All ports are 'open' by default, but so long as nothing is listening on that port, no one can connect to it. Setting up firewall rules just to 'open' ports is generally a waste of time, especially if you are behind a firewall/router already.

---

### Post by PryGuy on 2009-02-07
I'm doing this for my ICS Server actually... Does it make sense then? I also want to learn how to block some ports just in case.

---

### Post by madverb on 2009-02-07
It seems to me that HTTP won't work because you are blocking all incoming connections... you will want to set it up depending on the state of the connection. If the incoming is a response from an outgoing request you will need the state to be ESTABLISHED.

---

### Post by PryGuy on 2009-02-07
Thanks, but it didn't work.:( Guess I have not allowed something else 'cause I can't even ping any host. How DNS resolution is made? Over ICMP?

---

### Post by madverb on 2009-02-07
```
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
```

---

### Post by PryGuy on 2009-02-07
> **madverb said:**
> ```
iptables -A INPUT -m state --state ESTABLISHED -j ACCEPT
```Works, But can I enable the ESTABLISHED connection for port 80 only?

---

### Post by madverb on 2009-02-07
The response won't be on port 80. You can set it to particular protocols. You might be able to set it so that it only accepts responses from connections originating on port 80.
Not sure how to do that though.

---

### Post by PryGuy on 2009-02-07
> **madverb said:**
> The response won't be on port 80. You can set it to particular protocols. You might be able to set it so that it only accepts responses from connections originating on port 80.
Not sure how to do that though.Thanks for actually helping me out, but please explain me this thing: the above set of rules works perfectly for SSH, and I didn't have to set the state to ESTABLISHED for that. And as we know both SSH and HTTP are basically client/server things, so SSH would not be able to operate without the ESTABLISHED state too, but it works anyway. I'm lost here... :(

---

### Post by madverb on 2009-02-07
The SSH connection will always work on port 22

HTTP connections won't always work on port 80, they begin on port 80.

ESTABLISHED will receive a response on any port but only if the connection originated internally.

---

### Post by PryGuy on 2009-02-07
So there's basically no need for this rule?
```
iptables -A INPUT -i $LAN -s 0/0 -d 0/0 -p tcp --dport 80 -j ACCEPT
```

---

### Post by madverb on 2009-02-07
No.
You only need that if you have a web server internally. Then you would point port 80 directly to the server though.

---

### Post by tad1073 on 2009-02-07
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-4_Common_TCP_and_UDP_Match_Criteria]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Table_14-4_Common_TCP_and_UDP_Match_Criteria")

---

### Post by PryGuy on 2009-02-07
Thanks, pals!

---

### Post by PryGuy on 2009-02-07
Should I set the state to RELATED,ESTABLISHED or ESTABLISHED only? Is there a big difference?

---

### Post by madverb on 2009-02-07
yeah RELATED,ESTABLISHED will help avoid problems

---

### Post by PryGuy on 2009-02-07
Another question. This perfectly works for INPUT chain. But as I learnt INPUT chain is a chain that is made for the traffic, that comes from the outside world targeting the machine. So should I make the same things for the FORWARD chain? They are not connected I guess, and the FORWARD traffic passes by without going through the INPUT (or OUTPUT) chain. Am I right?

---

### Post by koenn on 2009-02-07
yes

---

