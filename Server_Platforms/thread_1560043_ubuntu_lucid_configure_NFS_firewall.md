---
title: "ubuntu lucid configure NFS firewall"
date: 2010-08-24
forum: Server Platforms
---

### Post by capo1949 on 2010-08-24
Hi All

I have a laptop and a Desktop both systems only used by myself behind a router. Ubuntu Lucid on both and 64 bit systems.

I have installed NFS with the desktop as server and Laptop as client.

The NFS only works with the firewalls (UFW) disabled on both machines.

I have spent hours googling for a solution to this problem, some help would be appreciated.

My current setup on the desktop ufw is
To                         Action      From
--                         ------      ----
51413/tcp                  ALLOW       Anywhere
Anywhere                   ALLOW       192.168.1.64
Anywhere                   ALLOW       192.168.1.65
Anywhere                   ALLOW       192.168.1.66
2049                       ALLOW       Anywhere
32771                      ALLOW       Anywhere
111                        ALLOW       Anywhere

53,137,138/udp             ALLOW OUT   Anywhere
20,21,22,25,80,139,443,5900,8001/tcp ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere
 
And the laptop ufw is 
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       192.168.1.64
Anywhere                   ALLOW       192.168.1.65
Anywhere                   ALLOW       192.168.1.66
2049                       ALLOW       Anywhere
32771                      ALLOW       Anywhere
111                        ALLOW       Anywhere

53,137,138/udp             ALLOW OUT   Anywhere
20,21,22,25,80,139,443,5900,8001/tcp ALLOW OUT   Anywhere
Anywhere                   DENY OUT    Anywhere


Mnay thanks in anticipation

---

### Post by clrg on 2010-08-24
Do you allow passive ranges for NFS to use?

---

### Post by arrrghhh on 2010-08-24
Ew.  I wouldn't allow all of those ports out to everyone.  For better or worse, I allow any traffic on my local network to get to the server.  If someone's already on my LAN, I probably have bigger issues.

---

### Post by clrg on 2010-08-24
I'm sorry, I don't understand your answer. Does this mean no? If so, you found a possible cause of the problem. If yes, its something else related to your firewall configuration (since it works without).

---

### Post by arrrghhh on 2010-08-24
> **clrg said:**
> I'm sorry, I don't understand your answer. Does this mean no? If so, you found a possible cause of the problem. If yes, its something else related to your firewall configuration (since it works without).

Uhm, I'm not the OP, just trying to help.  Suggesting what I do on my network, never had any nfs issues.

---

### Post by capo1949 on 2010-08-24
Hi
Thanks for your replies, all. Passive ranges I don't understand. I use IP address to describe the client to server.

so my /etc/exports/ is
/home 192.168.1.64(rw,root_squash,async)

Which lines in ufw should I delete for better security?

---

### Post by arrrghhh on 2010-08-24
> **capo1949 said:**
> Which lines in ufw should I delete for better security?

Anything that says "ALLOW Anywhere".  Basically you should ONLY open these ports externally if you need external services running on them (apache, ssh, etc).

For other stuff that should stay local - samba, nfs, you should NOT open those ports to the world so to speak.

So for example, if I wanted to allow any IP on my LAN the only rule I would need is:
```
sudo ufw allow from 192.168.0.0/24
```

That way you allow any LAN traffic to your server.  If you want it even more secure, give static IPs to your workstations and allow rules based on the workstation.  Drilling down to the port number can be cumbersome, but it is the most secure option.

---

### Post by capo1949 on 2010-08-24
hi aarghhhhhhhh

Thanks your reply

Could you please give me an amended configuration for the server and client.

---

### Post by arrrghhh on 2010-08-24
> **capo1949 said:**
> Could you please give me an amended configuration for the server and client.

Clear out all your UFW rules, and put that rule I listed above in on the server.  Client shouldn't need UFW enabled, but if you do want it enabled it may need that same command to allow traffic from the server.

---

### Post by capo1949 on 2010-08-24
Hi
I have reconfigured ufw on the server as follows

status: active
To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       192.168.1.64
Anywhere                   ALLOW       192.168.1.65
Anywhere                   ALLOW       192.168.1.66
51413/tcp                  ALLOW       Anywhere
2049                       ALLOW       Anywhere
2049                       ALLOW OUT   Anywhere

Rather than allowing anyone on lan, I a ony allowing those addresses in use as I feel its more secure.

the client ufw is as follows
Status: active

To                         Action      From
--                         ------      ----
2049                       ALLOW       Anywhere
80/tcp                     ALLOW OUT   Anywhere
110                        ALLOW OUT   Anywhere
2049                       ALLOW OUT   Anywhere

Now I can only mount the directories at the client when the client ufw is off, after mounting I can switch the client ufw back on and transfer files between both systems.

Comments on my revised ufw configuration and things to try to enable mounting wihout disabling the client ufw please.

Thanks in anticipation

---

### Post by arrrghhh on 2010-08-24
If you want to be more secure than why do you have these three:

```
51413/tcp ALLOW Anywhere
2049 ALLOW Anywhere
2049 ALLOW OUT Anywhere
```

On your server?  Plus, if you insist on enabling UFW on the client (to me it seems entirely unnecessary) why don't you just have the client allow any traffic from the server's IP as you did on the server for the clients...?

I really don't understand why you have the client set to allow all of these ports out.  There shouldn't be any reason to run UFW on the client, unless you have some services listening on it.

---

### Post by capo1949 on 2010-08-26
Hi All
Thanks for your input

resolved the mounting problem by allowing my server to access the client,
with firewall rule 
Anywhere                   ALLOW       192.168.1.65

The client now mounts the required files with firewall up

---

