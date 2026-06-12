---
title: "Output port security"
date: 2017-08-22
forum: Security
---

### Post by gd3 on 2017-08-22
Hi, 

If a port is open for OUTPUT only can it be exploited by intruders?  For example when a browser or any other app is a Websockets client it allows bidirectional communication and the server can send messages to the client as well. 
How safe is this (0-10)? In other words how difficult it is to hack a PC with no open INPUT port?

---

### Post by HermanAB on 2017-08-22
Note that a Berkeley port is not really a physical thing.

A Berkeley port is a number in the header of a datagram.  The header contains many bits of information, including also the IP addresses of the sender and receiver.

So, in short, an output port is simply the number that a service on the distant device that the datagram is sent to, is supposed to listen for, whereas the input port is the number that a service on the local machine is listening for.  To add to your possible confusion, the input and output port numbers may very well be the same also, but don't have to be.

Go to the IEEE 802.3 web site and read up a bit.

---

### Post by gd3 on 2017-08-24
Herman,

thank you for your answer.

I understand all the basics (definition of port, headers ...). What I do not know is what hackers can or cannot do. Vulnerabilities  in a system are not obvious, they are found by extensive research.  I assume system admins responsible for  sensitive data has to be up to date about the types of vulnerabilities. My hope is that some serious professional with such background can give me reliable information or point me to the right direction where I have a chance to find reliable answers concerning ports which are configured output only for the firewall. Can these be a potential entry point for hackers in any way? If such possibility exists the next natural question would be: is it possible to do something about  it.

---

### Post by HermanAB on 2017-08-25
OK, the network stack is a kernel module that is always loaded, since all computers these days need it.  In addition, there is a packet filter module that can look at the packet headers and decide whether to accept, reject or forward them.  The packet filter module is configured with iptables or some or other firewall script.

For someone to connect to your computer, his packets need to be forwarded to a daemon listener.  So output ports are generally safe, since netfilter will drop the wrong headed packets.

Once in a blue moon, some horrid bug is found, as with SSL some time ago, but the Linux network stack is remarkably strong, so I would not worry too much about it.

If you are required to be paranoid - military/government - then you have two choices: Redhat or OpenBSD.  Anything else is generally frowned upon by the security establishment, since they don't want to audit every single distribution - they don't have time for that.  (Yes, the military use Ubuntu, Suse and many other things also, but if you go to a military test centre, you will pretty much only see Redhat and OpenBSD).  So if you install one of the preferred distros, then you will have a much easier time with them and the mil admin will likely say: "Go ahead install it and when you are done, give me a call and I'll give you a few pointers on what to change" (passwords, timeouts, screen saver) - as opposed to: "Submit three systems for testing and we'll call you back in 2 years".

---

### Post by gd3 on 2017-09-03
Herman,

sorry for the late reaction. Your answer has valuable info, thank you.

---

### Post by Habitual on 2017-09-03
Herman:
Been through FIPS at all?

---

### Post by gd3 on 2017-09-04
No, not yet anyway . :)

---

