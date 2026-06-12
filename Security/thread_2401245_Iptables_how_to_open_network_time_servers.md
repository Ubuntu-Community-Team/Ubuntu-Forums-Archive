---
title: "Iptables: how to open network time servers"
date: 2018-09-15
forum: Security
---

### Post by webmiester on 2018-09-15
Hi everyone,

I placed this command to protect my computers:

/sbin/iptables -A OUTPUT -j REJECT

I realized though that this closes the computers from receiving time from it's network time servers.  How do I keep the computer's access to network time servers open?

---

### Post by Doug S on 2018-09-15
Actually, the rule prevents your computer from even asking for NTP stuff in the first place. You have to allow your computer access to external port 123, or if you know the IP address of the NTP server you could allow that IP address. Something like:
```

/sbin/iptables -A OUTPUT --dport 123 -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

```
You might find you need to also allow traffic to/from the local interface:
```

/sbin/iptables -A OUTPUT -o lo -j ACCEPT
/sbin/iptables -A OUTPUT --dport 123 -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

```Without the bigger context of what you are trying to do, it is hard to comment further.

---

### Post by webmiester on 2018-09-16
Is this the line that opens the local interface?

/sbin/iptables -A OUTPUT -o lo -j ACCEPT

Io is a small "L" right, it's not a big "i"?

---

### Post by Doug S on 2018-09-16
> **webmiester said:**
> Is this the line that opens the local interface?

/sbin/iptables -A OUTPUT -o lo -j ACCEPT

Io is a small "L" right, it's not a big "i"?Yes and yes.

---

### Post by webmiester on 2018-09-17
> **Doug S said:**
> 
```

/sbin/iptables -A OUTPUT -o lo -j ACCEPT
/sbin/iptables -A OUTPUT --dport 123 -j ACCEPT
/sbin/iptables -A OUTPUT -j REJECT

```Without the bigger context of what you are trying to do, it is hard to comment further.

How about:

/sbin/iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

Will this do the same thing?

---

### Post by The Cog on 2018-09-17
> **webmiester said:**
> How about:

/sbin/iptables -A OUTPUT -d 127.0.0.1 -j ACCEPT

Will this do the same thing?

No. That only allows the host to talk to itself on its own loopback port. 

I don't recommend blocking OUTPUT. It will break lots of things.

Oh, and when specifying a port number, you have to specify tcp or udp as well. Like this:
```
/sbin/iptables -A OUTPUT -p tcp  --dport 123 -j ACCEPT
```

---

### Post by webmiester on 2018-09-17
> **The Cog said:**
> No. That only allows the host to talk to itself on its own loopback port. 

I don't recommend blocking OUTPUT. It will break lots of things.

Oh, and when specifying a port number, you have to specify tcp or udp as well. Like this:
```
/sbin/iptables -A OUTPUT -p tcp  --dport 123 -j ACCEPT
```

Oh thanks.

---

### Post by Doug S on 2018-09-17
> **The Cog said:**
> Oh, and when specifying a port number, you have to specify tcp or udp as well. Like this:
```
/sbin/iptables -A OUTPUT -p tcp  --dport 123 -j ACCEPT
```My syntax mistake, sorry.

---

