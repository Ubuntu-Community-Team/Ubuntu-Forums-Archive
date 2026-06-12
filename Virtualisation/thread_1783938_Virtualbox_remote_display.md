---
title: "Virtualbox remote display"
date: 2011-06-16
forum: Virtualisation
---

### Post by createdcreature on 2011-06-16
I am using Virtualbox on an Ubuntu 10.04 machine and want to remote into it from a computer running Windows XP Home. Don't just say 'Type in your IP address', what is my IP address?

---

### Post by Jake.Debord on 2011-06-20
open command prompt and type in ifconfig

then open remote desktop and type in your [noparse]IP:Port [/noparse]

the port will be something you specified when you setup the VM.

ex: 192.168.0.2:5000

---

### Post by createdcreature on 2011-07-03
Not working............ I don't understand.................

---

### Post by CharlesA on 2011-07-04
> **Robert Moyse said:**
> Not working............ I don't understand.................
What don't you understand?

---

### Post by createdcreature on 2011-07-04
What am I meant to do?

---

### Post by mister_p_1998 on 2011-07-04
No he's wrong! if you look at the ip in your main system, it will be a diffrent one than in VirtualBox, Virtualbox creates a virtual Network card with a different IP address.

My main system IP is: 192.168.1.104

and Natty running in VirtualBox is: 10.0.2.15
you need to connect to the VB ip address
Steve

---

### Post by createdcreature on 2011-07-04
So, how would I find this address, and how would I connect to it?

---

### Post by CharlesA on 2011-07-04
> **Robert Moyse said:**
> So, how would I find this address, and how would I connect to it?

Do you have remote display enabled in VirtualBox?

If you do, it'll give you a port number (probably 3389)

Connect by typing this into the terminal services client:

ipofhost:3389

In my case it would look like this:

192.168.1.2:3389

---

### Post by createdcreature on 2011-07-04
How would I find the IP of the host?

---

### Post by CharlesA on 2011-07-04
> **Robert Moyse said:**
> How would I find the IP of the host?

If you are on a linux box, open a terminal and type:

```
ifconfig
```

It'll look like this (the host IP address is in blue):

```
charles@Thor:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:20:87:36
          [COLOR="Blue"]inet addr:192.168.1.2[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe20:8736/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:274240526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:676721060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:253394507839 (253.3 GB)  TX bytes:910908535823 (910.9 GB)
          Interrupt:29 Base address:0xc000

```

---

### Post by createdcreature on 2011-07-05
So, on XP, what would I type in to remote desktop if my host IP is 192.168.0.4?

---

### Post by CharlesA on 2011-07-06
> **Robert Moyse said:**
> So, on XP, what would I type in to remote desktop if my host IP is 192.168.0.4?
Try this:

192.168.0.4:3389

---

### Post by createdcreature on 2011-07-07
Still not working. Do I type in the VM's IP address?

---

### Post by CharlesA on 2011-07-07
Are you using virtualbox 3 or 4?

---

### Post by createdcreature on 2011-07-07
4

---

### Post by CharlesA on 2011-07-07
> **Robert Moyse said:**
> 4
Ok. Do you have the extension pack installed?

---

### Post by createdcreature on 2011-07-08
Yes.

---

### Post by CharlesA on 2011-07-08
> **Robert Moyse said:**
> Yes.

Do you have the remote display set up like this?

See attachment.

---

### Post by createdcreature on 2011-07-09
Still not working. What I am doing is using VNC to remote into the host system, and then access the VM from there.

---

### Post by CharlesA on 2011-07-09
Only other thing I can think of is that the firewall is blocking access. Glad you got it working even if it wasn't ideal.

---

### Post by createdcreature on 2011-11-20
Do I need port forwarding set up on a wireless router to make it work?

---

### Post by CharlesA on 2011-11-20
> **Robert Moyse said:**
> Do I need port forwarding set up on a wireless router to make it work?
Shouldn't have to unless you want to access the VM directly from the internet (which isn't a good idea imo).

I access mine by connecting to the host via SSH and tunneling VRDP over SSH. Works the same as tunneling VNC over SSH except you use different ports. ;)

---

