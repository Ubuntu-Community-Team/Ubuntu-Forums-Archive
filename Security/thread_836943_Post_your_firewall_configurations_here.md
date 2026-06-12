---
title: "Post your firewall configurations here?"
date: 2008-06-22
forum: Security
---

### Post by Lord Xeb on 2008-06-22
Is this allowed? If so, post them up!

---

### Post by lisati on 2008-06-22
My ADSL modem has its default firewall settings, and my wireless+cable router has MAC access restricions. Beyond that, I'm not saying (for now!)

---

### Post by tubbygweilo on 2008-06-22
> **lisati said:**
> Beyond that, I'm not saying (for now!)
Neither am I! (a retired social engineer):)

---

### Post by Lord Xeb on 2008-06-22
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Lokkit-0-50-INPUT (0 references)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     0    --  anywhere             anywhere            
ACCEPT     udp  --  dns-cac-lb-03.ohiordc.rr.com  anywhere            udp spt:domain 
ACCEPT     udp  --  dns-cac-lb-04.ohiordc.rr.com  anywhere            udp spt:domain 
REJECT     tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp reject-with icmp-port-unreachable 

```

This is effective :D It thwarted one of my hacker friends <_<

---

### Post by lisati on 2008-06-22
No offense intended to the OP but I'd rather be spending my time browsing these forums (while my other machine's making sense of video footage I've recorded for friends and family) than trying to repair damage done by someone malicious soul who might stumble on an unintentionally revealed weakness in my setup. I have absolutely no idea who might be viewing these forums as a guest.

---

### Post by fahadsadah on 2008-06-22
Posting firewall configs?
No thanks...

---

### Post by Miademora on 2008-06-22
Well id prefer to find that weakness by posting here instead of praying that there isnt one.

---

### Post by hyper_ch on 2008-06-22
my computer has only default firewall settings... meaning let pass everyting ;)

---

### Post by Chayak on 2008-06-23
My firewall?
Cisco 1841 ISR with the security image (1st layer)
Cisco ASA 5505 w/ security plus (2nd layer)

Yeah I have a lot of cisco gear but I'm working on my CCNP/CCSP

That's the physical configuration.  The running-config(s) will never cross the internet.  I'll share them for peer review with other security guys that I know but posting on a public forum?  That's like giving the plans of the Deathstar to the rebels.  It may be hard to destroy but the contractors forgot to put a grate over an exhaust port the size of a womp rat.

---

### Post by MythosLegend on 2008-06-27
I'm running a client desktop and sitting behind a end-user router. 
I only have a basic understanding of iptables.

Here it is

```

Chain INPUT (policy DROP)
target     prot opt source               destination         
DROP       0    -f  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:domain state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:www state ESTABLISHED 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:https state ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-reply 
           tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: SET name: DEFAULT side: source 
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh state NEW recent: UPDATE seconds: 60 hit_count: 8 name: DEFAULT side: source 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh 

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Poke holes if you want.

---

### Post by fahadsadah on 2008-06-27
You want a good configuration?
What's wrong with dropping everything? (unless you run servers, in which case accept traffic to them)

---

### Post by MythosLegend on 2008-06-27
If I drop everything, I won't be able to use the internet.

---

### Post by firsttimeuser on 2008-06-27
here is mine
@noname:~$ sudo iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     tcp  --  127.0.0.1            0.0.0.0/0
ACCEPT     esp  --  0.0.0.0/0            0.0.0.0/0
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:514
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpts:135:139
DROP       udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:2223
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:5353
LOGDROP    all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain LOGDROP (1 references)
target     prot opt source               destination
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4 prefix `IPTABLES '
DROP       all  --  0.0.0.0/0            0.0.0.0/0

---

