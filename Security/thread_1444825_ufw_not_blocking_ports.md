---
title: "ufw not blocking ports?"
date: 2010-04-01
forum: Security
---

### Post by tcpdump on 2010-04-01
After reading a lot about networking and security I decided to check the security of my own ubuntu box.
So I went installing Nmap and discovered that port 139 was "open".
Since I 'd read how to use ufw I created a deny rule for port 139.

After a second scan with Nmap it still said that port 139 was open as shown below.

robin@Gateway:~$ sudo su
[sudo] password for robin: 
root@Gateway:/home/robin# ufw status
Status: active

To                              Action          From
--                                    ------                   ----
139    DENY         Anywhere

root@Gateway:/home/robin# nmap 192.168.0.101 (my DHCP ip)

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-04-02 01:08 CEST
Interesting ports on 192.168.0.101:
Not shown: 996 closed ports
PORT     STATE SERVICE
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
1024/tcp open  kdm

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds
root@Gateway:/home/robin# 

The question here, is ufw failing , or is Nmap giving a false positive?

---

### Post by uRock on 2010-04-01
C next post.

---

### Post by uRock on 2010-04-01
If you scan your own system from your system you will see different values than what another system will see. 192.168.1.9 is the system I am on. 192.168.1.12 is my daughter's sytem with ufw enabled. Check out the results. ```
root@rabbit-desktop:~# ufw enable
Firewall is active and enabled on system startup
root@rabbit-desktop:~# nmap 192.168.1.9

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-01 17:06 PDT
Interesting ports on 192.168.1.9:
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 0.53 seconds
root@rabbit-desktop:~# nmap 192.168.1.0/24

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-01 17:08 PDT
Interesting ports on 192.168.1.9:
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
5900/tcp open  vnc

All 1000 scanned ports on 192.168.1.12 are filtered
MAC Address: 00:0F:B5:DD:BF:88 (Netgear)

Interesting ports on 192.168.1.14:
Not shown: 996 closed ports
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
49152/tcp open  unknown
49158/tcp open  unknown
MAC Address: 00:23:69:04:E1:5F (Cisco-Linksys)

Nmap done: 256 IP addresses (3 hosts up) scanned in 7.24 seconds
root@rabbit-desktop:~# nmap 192.168.1.12

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-01 17:08 PDT
All 1000 scanned ports on 192.168.1.12 are filtered
MAC Address: 00:0F:B5:DD:BF:88 (Netgear)

Nmap done: 1 IP address (1 host up) scanned in 21.71 seconds
root@rabbit-desktop:~# 

```

---

### Post by tcpdump on 2010-04-01
> If you scan your own system from your system you will see different values than what another system will see.Never thought of that, Thanks!

And indeed an Nmap scan from an other client said all ports are filtered.

---

### Post by uRock on 2010-04-01
> **tcpdump said:**
> Never thought of that, Thanks!

And indeed an Nmap scan from an other client said all ports are filtered.

I didn't either. I was expecting different results. When I seen that the first scan brought up what it did, I scanned the network to find my other system and scan it. We learn something new every day.

Cheers,
Ronnie

---

### Post by HermanAB on 2010-04-02
Hmm, why do you want to 'block ports'?  

On a Linux system, you have complete control over the running services.  If you have something listening on port 139 (probably Samba) and you don't want it to listen, then you should stop Samba.

Adding a band aid to block the port is the way one would do it on a Windows system, since on Windows it is impossible/difficult to control the running services.

This is why Ubuntu ships with 'no firewall' configured, since it isn't really needed.

Hope that helps!

---

### Post by cariboo on 2010-04-02
+1, if you don't use/need a service, uninstall it.

---

### Post by tcpdump on 2010-04-09
I was just kinda worried because I'm dual booting ubuntu & windows, and heard a lot about port 139 being very vulnerable on windows and all.

---

### Post by CharlesA on 2010-04-09
> **tcpdump said:**
> I was just kinda worried because I'm dual booting ubuntu & windows, and heard a lot about port 139 being very vulnerable on windows and all.

Block it (or turn off file sharing)? There are firewalls for Windows afterall.

---

### Post by airtonix on 2010-06-20
tcpdump,

If you send packets to an IP address that matches the IP address of a network card on the machine you are sending the packets from, then usually what happens is that those packets don't leave the machine.

Instead they get sent to 127.0.0.1 (transparently)

Which is why you should do those tests externally from other machines.


> **HermanAB said:**
> 
Hmm, why do you want to 'block ports'?  

Because I can?


> **HermanAB said:**
> 
On a Linux system, you have complete control over the running services.  If you have something listening on port 139 (probably Samba) and you don't want it to listen, then you should stop Samba.

Because stopping a service will stop sharing to certain devices on a network....

Point of a firewall is to limit/allow access to our computer(s) to a subset of hosts.

Maybe I have four network cards on the machine...

Stopping samba would deprive access to networks on all interfaces...


> **HermanAB said:**
> 
Adding a band aid to block the port is the way one would do it on a Windows system, since on Windows it is impossible/difficult to control the running services.

No it isn't.

> **HermanAB said:**
> 
This is why Ubuntu ships with 'no firewall' configured, since it isn't really needed.

Hope that helps!

Not really, you've just repeated a party line that doesn't answer the question.

For example you haven't explained why a windows machine requires a firewall by default and a Linux based machine does not.

---

### Post by CharlesA on 2010-06-20
> **airtonix said:**
> 
For example you haven't explained why a windows machine requires a firewall by default and a Linux based machine does not.

Normally a Linux based machine has no listening services by default, which is why you don't need a firewall.

---

