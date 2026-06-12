---
title: "An alternative solution for SSH attacks"
date: 2015-04-07
forum: Security
---

### Post by indy99 on 2015-04-07
Hi
The idea is keep close SSH daemon if not use. No open port no attack. You can try it. It is open source
[https://github.com/indy99/nnet_port_guard](https://github.com/indy99/nnet_port_guard)

...

---

### Post by TheFu on 2015-04-08
So - is this a [port-knocking]("https://www.digitalocean.com/community/tutorials/how-to-use-port-knocking-to-hide-your-ssh-daemon-from-attackers-on-ubuntu") solution or something else?
How is it different from fail2ban, denyhosts, or just having specific static source subnets for ssh allowed using either iptables or /etc/hosts.allow/.deny rules which are highly popular solutions?

Why the "magic numbers" in the source files? Talking about javascript stuff. 

A webapp that controls whether ssh is available or not? I'm I seeing this correctly?  Also, I see a custom encryption function. Why?

When it comes to new security ideas, some discussion would be nice.

---

### Post by indy99 on 2015-04-08
[FONT=Verdana]
[/FONT]Hi TheFu, thanks for your reply. Let me try to explain


This is not a port knocking solution. 
Port knocking looking for a sequence incoming connections than opens port. Good idea but  if someone can listen connection, can hack this sequence. .?? Or try different sequences?


The programs like fail2ban and others are about firewall and iptables settings. Your CPU will be busy to reject connections. And you will need to update rules.


This method completely stops SSH daemon. Nnet port guard program runs on server and connects to another server named Nanonet. The user also connects Nanonet via web browser. Then user can start or stop SSH by sending commands. When you need it, start SSH than stop it again. So hackers have nothing if SSH  is closed. 


Magic numbers are keys to login to Nanonet. 


Webapp controls SSH ON/OFF and checks SSH current status.
Custom encryption for connection between Nononet and programs.

---

### Post by Habitual on 2015-04-08
If someone can listen in on your connection, you have bigger fish to fry.

---

### Post by indy99 on 2015-04-09
if we talking about security there is always someone listening us :)
Port knocking is like a dialing telephone number. Send SYN packets to specific ports. if someone can capture this connection than can repeat same sequences.

---

### Post by kevdog on 2015-04-12
Honestly the discussion about port knockers -- although it makes sense about some implementations -- it doesn't hold for all. Your talking about a replayable packet sequence.  Many port knockers use this scheme, however not all of them do.  For years I've used the fwknop port knocker for my server that implements a non-replayable, encrypted packet implementation. Once the packet has been issued to the server and detected, it can't be replayed to gain future access.  

Security, in addition to security through abscurity, is a multilayered approach.  I'm not saying one should rely on a port knocker alone for security, rather implement this into their overall scheme of security if its applicable.  fail2ban, iptables, appropriate access controls within the ssh server config file, use of rsa keys rather than passwords, possible incorporation of ssh jail if this is appropriate -- are all part of this multilayered approach.  Never rely on one method.  In terms of logging into a service such as Nanonet --- I think that's ridiculous!!

---

### Post by TheFu on 2015-04-12
> **indy99 said:**
> Hi
The idea is keep close SSH daemon if not use. No open port no attack. You can try it. It is open source
[https://github.com/indy99/nnet_port_guard](https://github.com/indy99/nnet_port_guard)

...

Forgot to ask - no LICENSE file?  Which license?  "Open source" means nothing, since it can still have a highly restrictive license.  I.e. free to look, but not touch.

---

### Post by indy99 on 2015-04-13
> **TheFu said:**
> Forgot to ask - no LICENSE file?  Which license?  "Open source" means nothing, since it can still have a highly restrictive license.  I.e. free to look, but not touch.

You can see LICENSE file now

---

### Post by indy99 on 2015-04-13
> **kevdog said:**
> Honestly the discussion about port knockers -- although it makes sense about some implementations -- it doesn't hold for all. Your talking about a replayable packet sequence.  Many port knockers use this scheme, however not all of them do.  For years I've used the fwknop port knocker for my server that implements a non-replayable, encrypted packet implementation. Once the packet has been issued to the server and detected, it can't be replayed to gain future access.  

Security, in addition to security through abscurity, is a multilayered approach.  I'm not saying one should rely on a port knocker alone for security, rather implement this into their overall scheme of security if its applicable.  fail2ban, iptables, appropriate access controls within the ssh server config file, use of rsa keys rather than passwords, possible incorporation of ssh jail if this is appropriate -- are all part of this multilayered approach.  Never rely on one method.  In terms of logging into a service such as Nanonet --- I think that's ridiculous!!

Main difference is Nnet port guard Stopping the SSH daemon. Program connects to Nanonet. TCP connection is inside to outside. Waiting for commands just from Nanonet. (commands mean just START, STOP or get STATUS of SSH daemon. not system commands) 
So there is no any open port listening for trigger SSH daemon from outside. If there is not any open port about SSH, it is impossible to reopen it.


On the other methods there are open ports. You can make harder, hardest but not impossible to LOG in. Even if hackers (or automatic programs)  cannot log in, will try to log in, and rejecting coming packets will increase your CPU usage.


As I say this  an alternative, an idea. it can be another server, not should be Nanonet.

---

### Post by TheFu on 2015-04-13
On a multiuser system, after one person connects with ssh, the port is open for the duration of their, or any, ssh connection.  Basically, it will always be open 24/7, correct?

---

### Post by indy99 on 2015-04-13
> **TheFu said:**
> On a multiuser system, after one person connects with ssh, the port is open for the duration of their, or any, ssh connection.  Basically, it will always be open 24/7, correct?

in a SSH server enabled system SSH port always open and listens for incoming connecitons 24/7. anybody connected or not.

---

