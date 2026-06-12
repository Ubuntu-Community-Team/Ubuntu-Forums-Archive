---
title: "Questions about Nmap and services"
date: 2011-05-18
forum: Security
---

### Post by Noob2.0 on 2011-05-18
Hi,

I would like some advice on securing my newly installed Ubuntu machine. I pretty much got the firewall, permissions, and password aspects down pat, but I'm stuck on limiting services. Could anyone tell me how to find out which services my machine is running online and how to limit them?  Can I use Nmap on a localhost? If anyone's willing, I would love some help. Can someone point me on the right direction to securing my box?

---

### Post by Rubi1200 on 2011-05-18
Hi and welcome to the forums :-)

First, you should definitely read the security stickies at the top of this forum. There is a wealth of information there.

Second, here is a nice command that will show you information on services facing the internet:

```
sudo lsof -i -n -P
```

---

### Post by Lars Noodén on 2011-05-18
> **Noob2.0 said:**
>  Can I use Nmap on a localhost? 

Yes, but it would not provide any useful information.  You'll need to run it from another machine to see how your host actually looks from another machine.

---

### Post by bodhi.zazen on 2011-05-18
> **Lars Noodén said:**
> Yes, but it would not provide any useful information.  You'll need to run it from another machine to see how your host actually looks from another machine.

Well ...

NMap provides useful information when run against localhost, you just need to know how to interpret the information.

For most users new to nmpa, yes I agree, run it from a second machine.

Once you are familiar with nmap you can certainly run it against localhost.

Also, zenmap is a graphical front end for nmap, some people like graphical front ends, especially early in the learning process.

---

### Post by Noob2.0 on 2011-05-19
@ Rubi

Thank you for your help. I tried your command line options and found some very alarming services running as root. dhclient and cupsd are elevated to root status. I believe I need dhclient for IP allocation but cupsd has to go. Does anyone know how to remove that from my system? It's a printing program so I won't need it.

---

### Post by Noob2.0 on 2011-05-19
> **bodhi.zazen said:**
> Well ...

NMap provides useful information when run against localhost, you just need to know how to interpret the information.

For most users new to nmpa, yes I agree, run it from a second machine.

Once you are familiar with nmap you can certainly run it against localhost.

Also, zenmap is a graphical front end for nmap, some people like graphical front ends, especially early in the learning process.


Thank you so much for your advice. I will run it from a foreign computer. I'm not much into front end graphical interfaces. I prefer the old fashion command line terminals for my operations. I've been hearing great reviews for Nessus. Would you recommend that?

---

### Post by Lars Noodén on 2011-05-19
> **Noob2.0 said:**
>  Would you recommend that?

Nessus was good but not an option any longer as it's no longer free/open source.  [OpenVAS](http://www.openvas.org/) might be a better choice.  It's in the repository.

---

### Post by Noob2.0 on 2011-05-19
> **Lars Noodén said:**
> Nessus was good but not an option any longer as it's no longer free/open source.  [OpenVAS]("http://www.openvas.org/") might be a better choice.  It's in the repository.

I've never heard about OpenVAS before. Is it simple to use? 

Nessus is no longer open source, but they do offer a free VT for home servers. Have you heard anything about Samhain? I was reading "Linux Administration Third Edition" and they recommended it to their readers.

---

### Post by Lars Noodén on 2011-05-19
OpenVAS should be about the same as any other package to use.  It was previously called gNessus and, IIRC, was a fork of the last Free/OpenSource version of Nessus.  Project web sites are weak on project history these years.

---

### Post by Noob2.0 on 2011-05-19
> **Lars Noodén said:**
> OpenVAS should be about the same as any other package to use.  It was previously called gNessus and, IIRC, was a fork of the last Free/OpenSource version of Nessus.  Project web sites are weak on project history these years.


 I'm getting ready to install it from the repositories. Thank you so much for pointing me in that direction. Being a noob sucks but we all have to start somewhere :)

I've been studying computers and linux for about 7 months now. At times I feel so disheartened. There are so many things to learn about. I feel like I am keeping a snail's pace. Got any encouraging words for those beginners that seem lost?

---

### Post by Lars Noodén on 2011-05-19
> **Noob2.0 said:**
> Got any encouraging words for those beginners that seem lost?

You're doing great: You've already learned to ask questions that's by far the most important.  There are so many things that it's not possible to learn them in advance, but you can learn to find things and where to look when you need them.

---

### Post by Noob2.0 on 2011-05-19
> **Lars Noodén said:**
> You're doing great: You've already learned to ask questions that's by far the most important.  There are so many things that it's not possible to learn them in advance, but you can learn to find things and where to look when you need them.

You are  absolutely right. The hardest part and the most discouraging was not knowing where to find the information one needed. Once that problem was eliminated, I felt better about the long journey ahead. That's what is so great about this place. It gives people an opportunity to share ideas, information, and get guidance. Thank you for those encouraging words.

---

### Post by spynappels on 2011-05-19
A good way to cement what you have learned is to participate in the forums. If someone asks a question that you can answer, go ahead and answer it. If someone else comes along and adds information or corrects aspects of your answer, view it positively as refining of your knowledge.

It also helps to really believe in the ethos of what you're learning and to understand why it has developed to where it is now, it often makes unfamiliar concepts easier to understand if you can understand why the developers approached it in a certain way.

Above all, don't be afraid of making mistakes and asking for help, it's how most of us learn. I lost track of how many times I had to completely re-install DOS on my first computer(s) before I learned.

---

### Post by rookcifer on 2011-05-19
> **Noob2.0 said:**
> @ Rubi

Thank you for your help. I tried your command line options and found some very alarming services running as root. dhclient and cupsd are elevated to root status. I believe I need dhclient for IP allocation but cupsd has to go. Does anyone know how to remove that from my system? It's a printing program so I won't need it.


You misinterpreted the results.  dhclient and cups are *not *listening to the Internet at large but are bound to localhost.  Here is how you tell the difference:

```
cupsd     1267       root    7u  IPv4  40993      0t0  TCP **127.0.0.1:631** (LISTEN)
dhclient  1331       root    5w  IPv4   8686      0t0  UDP ***:68 **

```

Any time you see 127.0.0.1, this means the service is bound locally.  Any time you see ***:**12345 this means it is listening to the Internet at large.  In the example above, cupsd is bound locally and dhclient is listening to the Internet at large on a UDP port (which is safe since UDP is not TCP.)

I like to run the following command since it only lists TCP ports:

```
sudo netstat -atpvn
```

When you run that command look under "LOCAL ADDRESS" and if you see "127.0.0.1" then the port is closed to the outside world.  If you see *:12345, then it's open.

Ubuntu comes with no open ports by default -- the only ports open are those bound to localhost.

---

### Post by Noob2.0 on 2011-05-22
> **rookcifer said:**
> Y
Ubuntu comes with no open ports by default -- the only ports open are those bound to localhost.


Thank you so much for the comment, Rook. I rechecked everything and it shown them closed to the internet. Again, thank you for your wonderful advice. 

One more question. 

Since all ports are closed, can anyone still exploit applications within your system?

---

### Post by bodhi.zazen on 2011-05-22
> **Noob2.0 said:**
> Thank you so much for the comment, Rook. I rechecked everything and it shown them closed to the internet. Again, thank you for your wonderful advice. 

One more question. 

Since all ports are closed, can anyone still exploit applications within your system?

Exploitation of applications / software is not the same thing as open / closed ports / firewall.

A firewall is used to regulate what traffic can connect to listening servers.

All the non-server software has potential for vulnerabilities and exploits, from firmware (video drivers) to your browser.

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Thus a firewall is but one part of security, and as there are no listening servers of significance by default, a firewall is much less important for Linux then it is on Windows.

I suggest you read the security sticky ;)

---

### Post by solidblogger on 2011-05-24
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

First, you should definitely read the security stickies at the top of this forum. There is a wealth of information there.

Second, here is a nice command that will show you information on services facing the internet:

```
sudo lsof -i -n -P
```


Thanks for the command believe it or not i have been looking for this for weeks

---

