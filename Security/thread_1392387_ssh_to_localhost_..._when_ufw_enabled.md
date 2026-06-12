---
title: "ssh to localhost ... when ufw enabled"
date: 2010-01-28
forum: Security
---

### Post by mistakentridgell on 2010-01-28
I enabled ufw on my laptop.

I used the rule which blocks all the incoming traffic. However, I added a rule so that I can use ssh for outbound traffic, so I can use my laptop to connect to some remote server using ssh.

After this I tried ssh localhost, and it worked. I am confused at this point as to why this works, because I blocked all the incoming traffic and I thought ssh localhost SHOULD NOT work. But it is working.

Can anyone explain the reason behind this

---

### Post by Lars Noodén on 2010-01-28
> **mistakentridgell said:**
> I enabled ufw on my laptop.

I used the rule which blocks all the incoming traffic. However, I added a rule so that I can use ssh for outbound traffic, so I can use my laptop to connect to some remote server using ssh.

After this I tried ssh localhost, and it worked. I am confused at this point as to why this works, because I blocked all the incoming traffic and I thought ssh localhost SHOULD NOT work. But it is working.

Can anyone explain the reason behind this

Localhost is accessed using the local network interface and that generally does not get filtered.  If you try to ssh on that machine to your external IP number (instead of 127.0.0.1 or anything else in the 127.0.0.0/8 range) the firewall should block it because it will go through an external interface.  

Out of curiosity, why do you have an ssh server running on the machine if, as you say, you are blocking all incoming traffic?

---

### Post by kiranmurari on 2010-01-28
Hi,

As Lars has mentioned, loopback interface doesn't get filtered by ufw. If you intend to block loopback traffic, you can add an iptables rule for that. 

Apart from that, if you have added the allow rule for outbound SSH with the following commands:
```
$ sudo ufw enable
$ sudo ufw allow 22
```This would infact, allow inbound ssh, rather than allowing outbound ssh. Even from gufw, you would be achieving the same result. All outbound traffic is anyway allowed by default.

---

### Post by mistakentridgell on 2010-01-29
> **Lars Noodén said:**
> Localhost is accessed using the local network interface and that generally does not get filtered.  If you try to ssh on that machine to your external IP number (instead of 127.0.0.1 or anything else in the 127.0.0.0/8 range) the firewall should block it because it will go through an external interface.  

Out of curiosity, why do you have an ssh server running on the machine if, as you say, you are blocking all incoming traffic?

I was just trying hadoop on single cluster machine and at one point you have to use ssh localhost.

That was the only instance where I wanted my laptop to be a server

---

### Post by BkkBonanza on 2010-01-29
If you only want ssh to handle requests on localhost then you should tell it to listen only on localhost, otherwise you're better off to just disable it. The firewall isn't helping you in either case. There's no point in firewalling a port that you want open and you don't need a firewall if the port is closed. Unless you want to add extra filtering for bad IPs and abnormal packets, in which case it may be useful, but likely only for a port open on your public interface.

---

### Post by Lars Noodén on 2010-01-29
> **mistakentridgell said:**
> I was just trying hadoop on single cluster machine and at one point you have to use ssh localhost.

That was the only instance where I wanted my laptop to be a server

Ok, then as BkkBonaza points out, you can [set sshd](n/) to listen only to the local address and not accept any external connections.  

```

# see man page sshd_config(5) for more details
ListenAddress 127.0.0.1:22

```

Or / And:

Usually sshd is compiled to be tcpd-aware, so you can even put a line in /etc/hosts.deny blocking everything, and an exception for the localhost (127.0.0.0/8) in [/etc/hosts.allow](http://linux.die.net/man/5/hosts_access)

```

# /etc/hosts.allow:
sshd: 127.0.0.0/8

```

```

# /etc/hosts.deny:
sshd: ALL

```

YMMV

---

### Post by The Cog on 2010-01-29
Blocking traffic from the computer to itself on the loopback port will break all sorts of things. Printing will be impossible for a start. I can think of no good reason to prevent the computer from talking to itself.

---

