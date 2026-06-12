---
title: "Services And Ports"
date: 2009-06-07
forum: Security
---

### Post by pedja_portugalac on 2009-06-07
Do you know what service is running on port 56468 in ubuntu 9.04?

I have 2 active network services running on my installation. 

- 56468  ???????????????
- 5353   it's mdns (Multicast DNS)

What are this services doing and do we really need them? If not, how can we stop them? 

I've already disabled cups (printing sharing) from the GUI, cause I don't need that but for remaining 2 services I need help.

Thank You in advance

---

### Post by rookcifer on 2009-06-07
```
netstat -atlpvn
```

This should provide a list of all listening TCP services and give you the name of the process on each port.  Likely the 56468 port is Firefox.

---

### Post by sgosnell on 2009-06-07
Are you sure those are ports, and not process IDs (PIDs)?  You can open the system monitor and see all the processes running on your computer.

---

### Post by pedja_portugalac on 2009-06-07
netstat -atlpvn give no result. I get the informations of active network services form netstat GUI. 

System > Administration > Network Tools > Netstat > Active Network Services 

Can you please see if you to have them or it came with some of the packages I have lately installed?

---

### Post by bodhi.zazen on 2009-06-07
I like this one too :
```
sudo lsof -i -n -P
```

---

### Post by cdenley on 2009-06-08
That's probably avahi, which is UDP. The netstat GUI you were looking at should give the protocol (UDP) in the left column.
```

sudo netstat -tulnp

```
This is similar to the previous command, except it lists UDP listening processes as well as TCP.

EDIT: Or the command bodhi.zazen gave should do the same thing, but list active network connections as well as listening processes.

---

### Post by pedja_portugalac on 2009-06-08
@ bodhi.zazen

> lsof: illegal option character: /
lsof: illegal option character: 3
lsof: illegal option character: 7
lsof: illegal option character: 5
lsof: illegal option character: 0
lsof: illegal option character: 2


This morning I've connected ones again to the internet trough vodafone 3G connect box (ppp0) and the port/service from yesterday has changed into 37502. It should be my Mobile Broadband service so I think there's nothing to worry about but still I'd like someone to tell me what services are running on fresh install?To do that someone please click

System > Administration > Network Tools > Netstat > Active Network Services

and then click on button Netstat

Thank You anyone

---

### Post by cdenley on 2009-06-08
> **pedja_portugalac said:**
> @ bodhi.zazen




This morning I've connected ones again to the internet trough vodafone 3G connect box (ppp0) and the port/service from yesterday has changed into 37502. It should be my Mobile Broadband service so I think there's nothing to worry about but still I'd like someone to tell me what services are running on fresh install?To do that someone please click

System > Administration > Network Tools > Netstat > Active Network Services

and then click on button Netstat

Thank You anyone

Avahi listens on a UDP port by default, and possibly the dhcp client as well depending on your network configuration. Try running the command I posted. Also, bodhi.zazen forgot a character when using the code tag, which I assumed you would notice. His command was
```

sudo lsof -i -n -P

```

---

### Post by pedja_portugalac on 2009-06-08
> **cdenley said:**
> That's probably avahi, which is UDP. The netstat GUI you were looking at should give the protocol (UDP) in the left column.
```

sudo netstat -tulnp

```
This is similar to the previous command, except it lists UDP listening processes as well as TCP.

EDIT: Or the command bodhi.zazen gave should do the same thing, but list active network connections as well as listening processes.
Yes it's avahi and it's UDP.
> Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           3258/avahi-daemon: 
udp        0      0 0.0.0.0:37502           0.0.0.0:*                           3258/avahi-daemon: 


What is Avahi?

Avahi is a system which facilitates service discovery on a local network. This means that you can plug your laptop or computer into a network and instantly be able to view other people who you can chat with, find printers to print to or find files being shared. This kind of technology is already found in Apple MacOS X (branded Rendezvous, Bonjour and sometimes Zeroconf) and is very convenient. Avahi is mainly based on Lennart Poettering's flexmdns mDNS implementation for Linux which has been discontinued in favour of Avahi. 

OK. Now I understand what's avahi. Thank you cdenley. I will kip it running because I need it on this laptop. 

PS. Love your city, I was there 4 times.

---

### Post by cdenley on 2009-06-08
> **pedja_portugalac said:**
> Yes it's avahi and it's UDP.

Is it something I have to care about or stop?

I don't think it's something to be concerned about, but you can probably disable it with System>Administration>Servies by unchecking "Multicast DNS service discovery" (if you don't use it).
[http://en.wikipedia.org/wiki/Avahi_(software](http://en.wikipedia.org/wiki/Avahi_(software))

---

### Post by pedja_portugalac on 2009-06-08
Thank you very much.

---

### Post by bodhi.zazen on 2009-06-08
> **cdenley said:**
> Also, bodhi.zazen forgot a character when using the code tag, which I assumed you would notice. His command was
```

sudo lsof -i -n -P

```

Thank you , I fixed my sloppy post, my apologies for the confusion.

---

