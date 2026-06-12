---
title: "About ssh and security"
date: 2015-04-06
forum: Security
---

### Post by sponge2 on 2015-04-06
Hi there,

I was reading about public and private keys for ssh:

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

and I was just curious after seeing this statment extracted from the same link: 

'My computer - a perfectly ordinary desktop PC - had over 4,000  attempts to guess my password and almost 2,500 break-in attempts in the  last week alone."

Is this a common thing computers being attacked by hackers? why would someone try to access a random PC?

---

### Post by slickymaster on 2015-04-06
*Moved to the ***Security*** sub-forum*

---

### Post by Lars Noodén on 2015-04-06
> **sponge2 said:**
> Is this a common thing computers being attacked by [s]hackers[/s]? why would someone try to access a random PC?

It is common for [crackers](http://www.catb.org/jargon/html/C/cracker.html) to try to get in with automated tools and it usually starts the minute you connect the machine to the Internet.  The reasons for attacking a random PC is to get in, it is, after all, connected to the Internet and that connection is valuable to them as well as any disk space.  Windows machines form valuable botnets that are bought, sold, traded and fought over.  It has become a large black market industry.  These are used to send spam, launch DDOS attacks, launch other attacks or host warez or illegal files.  If a Linux machine ends up in a botnet it can be used as command-and-control for the Windows botnets or for any of the other things already mentioned.  

Sometimes complaining to the netblock owner where the attacks originate can reduce them a little, especially if they look like manual or custom attacks rather than automated.  However, there are usually too many to deal with and only the most annoying worth dealing with.

---

