---
title: "Problem with services in seperated machines"
date: 2011-08-21
forum: Ubuntu Cloud and Juju
---

### Post by vahid_63 on 2011-08-21
Hi 
I need a cloud with separated machines so I used architecture like this:
 
machine1: CLC/Walrus
machine2: CC1
Machine3: CC2
6 machines for CC1
6 machines for CC2

My problem is when I tried to register nodes in every CC I got this error:
```
grep: //var/lib/eucalyptus/db//*auth*: No such file or directory ERROR: cannot locate entry in eucalyptus database, try logging in through the admin web interface ERROR: cannot get credentials.
```

and another problem is that eucalyptus services in CLC ans CC machines never got tor start and when i try to start them it takes some time and finally start like this:
```
eucalyptus-sc stop/post-start, (post-start) process 17716

```
and when I check eucalyptus service in CLC I get this:
```
eucalyptus start/running, process 3918
eucalyptus-network stop/waiting
eucalyptus-sc stop/waiting
eucalyptus-cc-publication start/running, process 3844
eucalyptus-sc-publication start/running, process 3811
eucalyptus-cc stop/waiting
```

What is this problem why services goes to post start and and stop.
I really appreciate your help I stuck in this problem for a month.

---

### Post by vahid_63 on 2011-08-22
Really nobody has a idea about this problem. Im really dissapointed Iv tried lots of waays but havent found any solution about it.

---

### Post by Rusty au Lait on 2011-08-26
I've never tried to build so big a cloud and have yet to put CC on another machine.

How were the servers installed? CD? installed over established servers?

Make sure all the machines have access to each other through SSH. Could be the eucalyptus user cannot get through.

I would then work with CC1 and one node (3 machines). I'd then establish that the connection between CLC and CC1 is correct (CLC knows that CC is on another machine, etc.). Use euca_conf to check CC's host name.
Then try to register one node.

my 2¢,
Ciao

---

### Post by vahid_63 on 2011-09-14
Hi 
Thanks for reply I found the problem.
Im using 192.168.82.* as a domain for internet and my CCs had IPs on this range for installing updates. After updating and upgrading CCs I changed their IPs to 10.3.1.* to be separate from Gateway range (because of isolating from enterprise network in my organization). at the end I restart them and deregistered and registered them but cant start services normally and they key issue is here that in Network configuration there must be a gateway. If not services doesn't start normally. In my last configuration I didn't have any gateway in the range of 10.3.1.* so I gave it a fake IP for gateway like 10.3.1.10 and restart machine. It solved the problem completely. looks like having gateway in network/interfaces config file is a strict rule even its fake. I repeated it over and over to be sure about the source of the problem and Im certain about it.
I think its kind of bug for UEC.

---

### Post by rezacloud on 2011-10-28
salam vahid khan, manam yek projeye marboot be cloud daram anjam midam.in skype man hast agar toonestid mano add konid baham sohbat konim: mohammadreza.1990

---

