---
title: "Need help trouble shooting firewall!"
date: 2011-05-11
forum: Security
---

### Post by SwarfEye on 2011-05-11
Hello,

I have been having trouble getting my firewall to pass ssh traffic.

I am running a standard default installation of 10.10.  I have ufw which I believe is sitting on top of a standard iptables installation.

Here are the symptoms.

First I run...
> sudo ufw reset
...and that clears my rules and disables my firewall completely.

Now I can access my machine from my local network using ssh on port 22.

Then I run...
> sudo ufw allow ssh
sudo ufw allow OpenSSH
sudo ufw enable
... I figure that at this point I should have a fully functioning firewall that is allowing ssh to pass on port 22... but no.  I am not able to connect to my machine with ssh.

Then I run...
> sudo ufw status verbose
... and I see the following output...
> Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
22                         ALLOW IN    Anywhere
22/tcp (OpenSSH)           ALLOW IN    Anywhere


... looks to me like I should be able to get in with ssh!

...then I run
> sudo ufw disable
... and ssh works again.

Clearly the firewall is not working right, but I don't know what is going on.  

Suggestions?

Thanks,

Bill

---

### Post by jramshu on 2011-05-12
Try this, it works for me.

```
sudo ufw reset
sudo ufw allow 22
```

---

### Post by SwarfEye on 2011-05-12
Yeah, 

Tried that... didn't work.

Tried it again at your suggestion... didn't work.

I think that I'm having a problem that is more than simply not knowing how to use the interface.  I believe that I am using the interface correctly, but that the results are not what they are supposed to be.

By the way, if I do exactly what you suggest, things do work, but if I then turn the firewall back on with...

> sudo ufw enable

Same old don't work.

How do I go about tracking this issue down?

Thanks,

Bill

---

### Post by WthIteh on 2011-05-12
Instead of ufw simply use the iptables (avoiding headaches, etc.).
First disable ufw completely and then use
```
iptables -L -v -n
```
to see current iptables state. If it was OK, you should see three lists INPUT, OUTPUT FORWARD and all default policies set to ACCEPT.
Then use
```

iptables -P INPUT DROP
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

```
to prevent all incoming packets else of 22/ssh ones.
Check your settings by
```
iptables -L -v -n
```
again.

---

### Post by SwarfEye on 2011-05-12
Ok, 

So I've taken your suggestion and gotten rid of ufw and started working straight with iptables.

First off, I had to spend some time cleaning all of the ufw chains out of iptables.  In the end I got to the basic installation... but things still aren't working the way that I expect them to, so I figure I am missing something pretty basic (or the damned thing just don't work?)

So I start off running the following command which yields the following results...
> sudo iptables -L -v
Chain INPUT (policy ACCEPT 2137 packets, 1478K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2714 packets, 384K bytes)
 pkts bytes target     prot opt in     out     source               destination

As far as I can tell, this is equal to a fresh install.  This configuration does not seem to block any traffic.  I can both ssh off of the machine and also on to the machine from the outside.

Then I run...
> $ sudo iptables -A INPUT -p tcp --dport ssh -j ACCEPT
$ sudo iptables -A INPUT -j DROP
$ sudo iptables -L -v
Chain INPUT (policy ACCEPT 2183 packets, 1481K bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpt:ssh 
    0     0 DROP       all  --  any    any     anywhere             anywhere            

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 2765 packets, 390K bytes)
 pkts bytes target     prot opt in     out     source               destination

At this point I figure that I should be able to ssh both into and out of the computer... BUT I can't do either!!!!

What am I missing?

Where am I going wrong here?

Thanks so much,

Bill

---

### Post by CandidMan on 2011-05-12
I think that second rule in your input chain is causing the problem.
As it stands, incoming tcp connections to port 22 are allowed, everything else is dropped.
You need a rule that allows established and related connections before the drop rule

EDIT: See if this works
```
 iptables -v -I INPUT 2 -p all -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
```

---

### Post by SwarfEye on 2011-05-13
Yes!  That worked!

Thanks so much!

Wow, you have to dig pretty deep in the man pages before you come up with "conntrack" and "-ctstate".

I don't think I would have found that with out you.

Thanks again.

B

---

### Post by spynappels on 2011-05-13
Just as an aside, it is normally a good idea to allow all traffic on the loopback (lo or localhost) interface as a lot of programs on servers interact with each other using the TCP/IP stack.

```
sudo iptables -I INPUT 1 -i lo -j ACCEPT 
```

---

### Post by JKyleOKC on 2011-05-13
> **SwarfEye said:**
> Yes!  That worked!Be sure to have a look at the man pages for iptables-save and iptables-restore, now that you have it working. You can use the "save" program to keep a copy of your working setup, and "restore" at boot time to put it back, since the plain iptables configuration starts out totally empty at power-up.

I have my "restore" call in my /etc/network/interfaces file as a "post-up" action for interface eth0, to make sure that it's done each time the interface comes up, but it can just as easily be placed in /etc/rc.local if you prefer.

---

