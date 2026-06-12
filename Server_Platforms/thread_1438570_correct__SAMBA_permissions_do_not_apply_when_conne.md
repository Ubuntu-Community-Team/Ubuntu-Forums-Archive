---
title: "correct  SAMBA permissions do not apply when connected to the server by typing IP"
date: 2010-03-25
forum: Server Platforms
---

### Post by rockercya on 2010-03-25
Hi
 
i have configured a SAMBA server and it is in a windows domain, the server is configured to authenticate users from the AD, the server is named as **linuxsvr** and the ip address is **10.10.168.173** ,
 
my problem is when a user is accessed the server with the server name which is **[\\linuxsvr]("file://\\linuxsvr")** they can access the shares and the correct permissions are applied ,
 
but if someone access the server by typing the ip address [\\10.10.168.173]("file://\\10.10.168.173") it gives access denied errors even if the users have read and write permissions to the samba shares, the correct permissons do not apply when connected by typing the ip address.
 
why this hapens?? anyone can help??
 
regards
 
chamara

---

### Post by byStanderone on 2010-03-25
...are you in dhcp?

---

### Post by rockercya on 2010-03-25
HI

no , we do not have a DHCP server, all the ip addresses are configured manually


regards

chamara

---

### Post by byStanderone on 2010-03-25
...i see, was thinking the problem is dhcp related but since you are not in dhcp, hard to say what the problem is from this point.

---

### Post by rockercya on 2010-03-25
could this be a bug in the server version?
 
regards
 
chamara

---

### Post by amp_man on 2010-03-26
> **rockercya said:**
> could this be a bug in the server version?
 
regards
 
chamara

What version are you running? Might be helpful.

I'm by no means an AD expert, never had any reason to use it. I'm thinking though AD might be configured to lookup the permissions based on hostname. Try adding "10.10.168.173 linuxsvr" to /etc/hosts. No guarantees it will work, or that it won't completely fubar the network for a few minutes...

---

### Post by rockercya on 2010-03-26
hi
 
 
im using ubuntu server 9.10, when you say host file do you mean host 
file in windows xp?
 
 
 
regards
 
chamara

---

