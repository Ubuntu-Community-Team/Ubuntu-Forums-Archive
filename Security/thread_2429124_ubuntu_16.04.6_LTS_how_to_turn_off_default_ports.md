---
title: "ubuntu 16.04.6 LTS how to turn off default ports"
date: 2019-10-13
forum: Security
---

### Post by dave219 on 2019-10-13
hello team:

i just installed ubuntu 16.04 and found out a lot of ports opened by default. how could i turn those ports off?

```
user@home:~:$ nmap -Pn 192.168.1.10
Starting Nmap 7.80 ( [https://nmap.org](https://nmap.org) ) at 2019-10-13 23:13 EDT
Nmap scan report for 192.168.1.10
Host is up (0.0079s latency).
Not shown: 984 filtered ports
PORT      STATE SERVICE
1/tcp     open  tcpmux
53/tcp    open  domain
79/tcp    open  finger
111/tcp   open  rpcbind
119/tcp   open  nntp
143/tcp   open  imap
1080/tcp  open  socks
1524/tcp  open  ingreslock
2000/tcp  open  cisco-sccp
6667/tcp  open  irc
12345/tcp open  netbus
31337/tcp open  Elite
32771/tcp open  sometimes-rpc5
32772/tcp open  sometimes-rpc7
32773/tcp open  sometimes-rpc9
32774/tcp open  sometimes-rpc11


Nmap done: 1 IP address (1 host up) scanned in 5.77 seconds
```

---

### Post by DuckHook on 2019-10-14
*Thread moved to **Security** as the more appropriate forum.*

I recommend that you read the link in my sig: "Security Basics"

The usual method used to configure ports is UFW (_U_ncomplicated _F_ire_W_all). The graphical equivalent is GUFW. UFW is the firewall configuration tool already built into Ubuntu. GUFW is available in the repos as a simple download. It is nothing more than a graphical front end for UFW.

You need to be careful closing ports. Doing so may break functions that you may not realize are needed. For example, 119 is needed for network time sync. 143 is needed for your e-mail client. If you run IRC or have a client with that functionality, it will open a high port like 6667.

Your instincts are good. It is good practice to lock down everything and open only those ports that you know are needed. Just go about them one at a time and test thoroughly for broken functionality to avoid breakage and frustration.

Good Luck and Happy Ubuntuing!

---

### Post by dave219 on 2019-10-14
thanks for advice. i will turn the UFW on later.

but i would like to turn some ports off such as 119, 79, 12345 etc. i really don't want people to finger my server, also am not sure i would ever run a network news server on this machine. that thing is a target for hackers, besides my bandwidth will be clogged with traffic.

---

### Post by uRock on 2019-10-14
> **dave219 said:**
> thanks for advice. i will turn the UFW on later.

but i would like to turn some ports off such as 119, 79, 12345 etc. i really don't want people to finger my server, also am not sure i would ever run a network news server on this machine. that thing is a target for hackers, besides my bandwidth will be clogged with traffic.

Once you turn on UFW, those ports will not be visible to other hosts, unless you specifically allow them in a rule. I'd recommend checking out the security sticky threads. 

You may also uninstall the services running those ports.

---

### Post by TheFu on 2019-11-11
I've never seen a stock Ubuntu Server step anything I didn't request at the install with a listener.  I always only install the ssh-server and nothing else at install time. Doing that, only 22/tcp is listening. Nothing else.

Did you install a stock Ubuntu Server from a reputable location or was it something else?

---

