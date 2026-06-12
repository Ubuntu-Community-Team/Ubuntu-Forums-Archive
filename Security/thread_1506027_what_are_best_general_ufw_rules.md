---
title: "what are best general ufw rules?"
date: 2010-06-09
forum: Security
---

### Post by friv_livs on 2010-06-09
I googled this question, no relevant results.

I don't samba, ssh, or any P2P file sharing.
Is udp neccesary for general web browsing/file downloading?

What would be the best general ufw rules to set for above conditions and varying ip address? I know how to use the full ufw syntax in command line.

Thanks in advance,
friv_livs

---

### Post by woody79_00 on 2010-06-09
Since you know the ufw syntax well

the steps you need to follow are simple

1. sudo ufw default deny

that command means all traffic coming in your computer by default is blocked unless your machine requested it. its a good setting.

i would block ports 21, 22, 137, 138, 139, 445, and 5900

using the syntax** sudo ufw deny 22** for example blocks traffic on port 22 (ssh)

you can also install **gufw **to have a gui for ufw its in the repos. you can search for it in synaptic if you like.

I would say adding deny rules to the ports listed above would be a very good start to deny the most common remote access methods to your Ubuntu box.

---

### Post by lykwydchykyn on 2010-06-09
UDP is generally only used for local-network services, often in a broadcast application.  For example, my CUPS print server advertises its printers via UDP; if I want my printers auto-configured, I have to open UDP on the relevant port.

But if you're just browsing and dowloading files, UDP should not be necessary.

---

### Post by bodhi.zazen on 2010-06-10
> **woody79_00 said:**
> Since you know the ufw syntax well

the steps you need to follow are simple

1. sudo ufw default deny

that command means all traffic coming in your computer by default is blocked unless your machine requested it. its a good setting.

i would block ports 21, 22, 137, 138, 139, 445, and 5900

using the syntax** sudo ufw deny 22** for example blocks traffic on port 22 (ssh)

you can also install **gufw **to have a gui for ufw its in the repos. you can search for it in synaptic if you like.

I would say adding deny rules to the ports listed above would be a very good start to deny the most common remote access methods to your Ubuntu box.

You do not need to do any of that.

```
sudo ufw enable
sudo ufw default deny
```The "default deny" will cover ports 21,22,137,138,138,445, 5900, and well all the ports.

The OP is not running any services , so no need to open ports either,

so sudo ufw default  deny is sufficient. No need to make firewalls more difficult then they are.

The default deny applies to new connections, established connections are allowed.

---

### Post by friv_livs on 2010-06-10
Thanks so far.

Any advice on what ports to not allow out?

---

### Post by bodhi.zazen on 2010-06-11
> **friv_livs said:**
> Thanks so far.

Any advice on what ports to not allow out?

In general, blocking outbound ports is more hassle then it is worth.

ports 1-1024 are "privileged" and when you use an application such as firefox , firefox will use a random port > 1024 to connect to port 80 on the server. Any potential malware on your system would use the same non-privilaged ports to connnect to port 80 , so it is impossible to allow firefox but block potential malware.

On the other side of the coin there are no known active spyware or viruses so there really is nothing to restrict.

---

