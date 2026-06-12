---
title: "connecting to a remote desktop via a ssh tunnel?"
date: 2009-01-23
forum: Security
---

### Post by easytek on 2009-01-23
Hi this is my first post on the forum sorry for the hassle but thanks for looking:

Is it possible to connect to a windows remote desktop via a ssh tunnel? if yes, how would i do it?
currently i connect to my remote desktop via this command:
rdesktop domainname

i also have a shell which i bought online.

also would it be possible to divert all my outgoing and incoming traffic through this shell? if yes, how would i do it?

Thanks for looking
btw im using Ubuntu 8.10- the Intrepid Ibex

---

### Post by pdtpatrick on 2009-01-23
i dont quite understand what you are trying to accomplish. 

You want to be able to access your windows machine using the ssh protocol? 

What you might want to do then i create an ssh server on your windows machine that listens for ssh traffic. you can use programs like RealVNC or Cygwin to setup your windows box and then connect to it.

---

### Post by easytek on 2009-01-23
hi thanks for the reply, i want to connect to the windows remote dekstop via a ssh tunnel.

for example to create the ssh tunnel i use this command to divert my internet traffic:  -D 1080 -fN user@host , and then i change the proxy settings on firerfox to be localhost:1080 socks 5, so my traffic is routed through the shell.

so i was wondering if it would be possible for me to do this to connect to my windows remote desktop?

---

### Post by easytek on 2009-01-23
in other words i create a proxy using that command: ssh -D 1080 -fN user@host

but how do i get to connect to the windows remote desktop via this proxy?

---

### Post by HermanAB on 2009-01-24
Windows RDP is secure.  You need not tunnel it through SSH.  Doing so will slow it down and won't do anything useful.

Cheers,

Herman

---

### Post by kevdog on 2009-01-24
> **easytek said:**
> in other words i create a proxy using that command: ssh -D 1080 -fN user@host

but how do i get to connect to the windows remote desktop via this proxy?

Do you want remote desktop management -- like VNC/RDP, or do you want to tunnel your internet connection through the proxy?  The above command creates a proxy.

---

### Post by easytek on 2009-01-25
i want to connect to my windows rdp via a proxy, is it possible?

---

### Post by HermanAB on 2009-01-25
RDP is a secure protocol (bought from Citrix), using RC4 encryption I think.  It runs on port 3389 TCP by default (not 1080 as in your example).  You should be able to proxy it if you use the correct port.

Cheers,

Herman

---

### Post by svines on 2009-06-01
> **HermanAB said:**
> RDP is a secure protocol (bought from Citrix), using RC4 encryption I think.

Regarding RDP being secure, you may want to have a look at this:

[http://www.oxid.it/downloads/rdp-gbu.pdf](http://www.oxid.it/downloads/rdp-gbu.pdf)

---

### Post by Fatman_UK on 2009-09-29
I'd like to do this myself. I've done exactly what the OP did ("ssh -D 8081 user@host"), but there doesn't seem to be a way to tell rdesktop to connect via proxy. Something like "rdesktop -proxy localhost:8081 user@192.168.23.5" would be ideal, but rdesktop has no -proxy switch. :/

[EDIT]

Found a solution that works for me - tsocks. Had to tweak the configuration file a bit, but it's small and easy. Don't know if you're still interested, OP...

$ sudo aptitude install tsocks
$ sudo nano /etc/tsocks.conf
$ tsocks rdesktop -u user 192.168.23.5

---

### Post by supertechguy on 2009-10-13
To answer your question:

Set up your SSH tunnel like this:
ssh [user]@[ip of ssh server] -L3389:[ip of RDP server]:3389

example:
ssh me@10.0.0.1 -L3389:192.168.0.2:3389

Then...

Launch RDP and connect to yourself at 127.0.0.1

The only major problem with this is that it has to be done host by host.  You could set up multiple hosts with one ssh connection but you would have to assign them to different ports.

example:
ssh me@10.0.0.1 -L3389:192.168.0.2:3389 -L3390:192.168.0.3:3389 -L3391:192.168.0.4:3389

Then..
RDP 127.0.0.1 -> 192.168.0.2
RDP 127.0.0.1:3390 -> 192.168.0.3
RDP 127.0.0.1:3391 -> 192.168.0.4

and so on......


Two major issues:
1. RDP is not as secure as you would think, never never never open it up to the public!
2. SSH has its own set of problems, and it is not always a good idea to open it up to the world.  Make sure you take some initiative to secure it!

---

