---
title: "Open ports"
date: 2008-04-29
forum: Server Platforms
---

### Post by Mr.Carramba on 2008-04-29
hi!

I did security scan today and found following:

> 

22/tcp   open     ssh OK
80/tcp   open     http apache
135/tcp  filtered msrpc
136/tcp  filtered profile
137/tcp  filtered netbios-ns
138/tcp  filtered netbios-dgm
139/tcp  filtered netbios-ssn
445/tcp  filtered microsoft-ds
646/tcp  filtered unknown
1720/tcp filtered H.323/Q.931

2 of open ports are ok and I know that I'm using them, but whats up with the rest?
I don't remember opening then and 445 port? how can microsoft port be open on ubuntu?
So my question is do I need to close these ports? if yes how?

thank you in advance!

---

### Post by Dr Small on 2008-04-29
Are you behind a router / firewall?
If so, it is just simpler to drop all firewall rules for your computer and simply use your firewall / router instead, for incoming requests.

---

### Post by Mr.Carramba on 2008-04-29
> **Dr Small said:**
> Are you behind a router / firewall?
If so, it is just simpler to drop all firewall rules for your computer and simply use your firewall / router instead, for incoming requests.

no, it's wide open from the net :), or at least those ports are

---

### Post by agim on 2008-04-29
those ports are not open. They are filtered. Only Apache and ssh are open.

"Apart from the ssh port, all the other ports are firewalled off
somewhere, either by firewall settings on your desktop, or by some other
firewall that's between the scanning machine and the desktop machine.

The difference is that a firewall will silently drop any packets
arriving on these filtered ports, whereas a system that is just not
listening on these ports will respond with a negative acknowledgement.
Utilities such as nmap use this to distinguish the two cases."

Found this answer (and quoted it) from this address:
[http://ubuntuforums.org/showthread.php?t=249931](http://ubuntuforums.org/showthread.php?t=249931)

filtered means not open

---

### Post by Mr.Carramba on 2008-04-29
> **agim said:**
> those ports are not open. They are filtered. Only Apache and ssh are open.

"Apart from the ssh port, all the other ports are firewalled off
somewhere, either by firewall settings on your desktop, or by some other
firewall that's between the scanning machine and the desktop machine.

The difference is that a firewall will silently drop any packets
arriving on these filtered ports, whereas a system that is just not
listening on these ports will respond with a negative acknowledgement.
Utilities such as nmap use this to distinguish the two cases."

Found this answer (and quoted it) from this address:
[http://ubuntuforums.org/showthread.php?t=249931](http://ubuntuforums.org/showthread.php?t=249931)

filtered means not open

ah, ok
I have no firewall, 
but why they are open/filtered anyway?
this is server so why  1720/tcp filtered H.323/Q.931 is there? 
can it be because of ip telephony?

---

### Post by agim on 2008-04-29
It would really be worth checking out that other post.
Those ports are labeled as "filtered" because unlike a closed port, which will send a message back to a computer trying to communicate with yours, a filtered port just drops the packets.
At least this is my understanding. Check out that link. Read the nmap documentation.

---

### Post by cdenley on 2008-04-29
When nmap says filtered, that means it never received a reply from the server, presumably because the server never received the request because it was filtered. When nmap says a port is closed, that means the server sent a reply saying the connection wasn't established, presumably because there isn't a server listening on that port.

On a default ubuntu system without any firewall between it and the client, all ports will be closed. A firewall can either drop or reject the packets.

drop=filtered
```

sudo iptables -A INPUT -p tcp --dport 666 -j DROP

```

reject=closed
```

sudo iptables -A INPUT -p tcp --dport 666 -j REJECT

```

---

