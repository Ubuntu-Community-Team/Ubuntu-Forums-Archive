---
title: "A green Linux distribution?"
date: 2015-04-22
forum: Ubuntu, Linux and OS Chat
---

### Post by quixotic-cynic on 2015-04-22
Hello all,

For some time now I have been thinking of making a 'green' Linux distribution/Ubuntu flavour.

By 'green' I mean:
1) The repo server uses clean energy (or at least carbon-neutral energy).
2) The set up is very light (openbox e.t.c.) so that energy consumption is minimal.
3) It uses advanced power management software to minimise energy consumption.

It wouldn't be a completely separate distro since there are a whole load of reasons why yet another 'from scratch' distro would be a bad idea.

I have begun working on a script that installs a simple working system from a minimal Ubuntu base.

I was wondering what people here think about such an idea?

Note: I realise some people do not believe that climate change or other environmental issues are a problem. Please avoid turning this thread into a discussion about such issues since a different thread in "The Cafe" or similar would clearly be more appropriate to such a discussion.

Note 2: I also realise that the project might not make *that* much difference environmentally, but it is better than feeling completely helpless/not trying (which just makes me depressed).

If people are interested in the idea, I can flesh it out more than I have at the moment...

Thanks for reading.

---

### Post by ian-weisser on 2015-04-23
You might look at developer discussions for preserving phone battery life as one starting point. Ubuntu has already spent many person-years of effort reducing power consumption, most recently with the Ubuntu phone. Many phone-inspired improvements (like stopping a process when it  disappears off the screen) are still working their way through the rest  of the ecosystem.

If you discover an application that needlessly consumes resources, including  excess power, please file a bug report. Developers generally do not knowingly resort to inefficient solutions.

I think there's room to reduce the number of embedded, always-on, single-purpose systems around us. But I see that as a design issue, not a distro issue. Ubuntu already has the tools to do that.

---

### Post by quixotic-cynic on 2015-04-23
> **ian-weisser said:**
> You might look at developer discussions for preserving phone battery life as one starting point. Ubuntu has already spent many person-years of effort reducing power consumption, most recently with the Ubuntu phone. Many phone-inspired improvements (like stopping a process when it  disappears off the screen) are still working their way through the rest  of the ecosystem.

Thank you very much for the response, and for this particular pointer. I will have a look at the discussions.

> **ian-weisser said:**
> I think there's room to reduce the number of embedded, always-on, single-purpose systems around us. But I see that as a design issue, not a distro issue. Ubuntu already has the tools to do that.

One more reason to build off Ubuntu with a custom install script rather than use LFS or something.

I *am* wondering if Lubuntu is a bit too close to the project idea already, but I think there might be a sufficiently large niche for it to be workable.

---

### Post by grahammechanical on 2015-04-23
How low is low energy? Here is a machine that uses 50 - 80 Watts under full load and only 1.8 Watts on standby. And it runs Ubuntu 14.04

[http://translate.google.co.uk/translate?hl=en&sl=de&u=http://www.cirrus7.com/produkte&prev=search](http://translate.google.co.uk/translate?hl=en&sl=de&u=http://www.cirrus7.com/produkte&prev=search)

[http://www.omgubuntu.co.uk/2014/04/cirrus-7-nimbus-1-pc-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/04/cirrus-7-nimbus-1-pc-ubuntu-14-04)

I am not convinced that the blame for energy consumption can be put on the OS. No, it falls on both high power hardware and the users who demand ever more powerful hardware. 

I used to work for a major high street retailer. My employer had a scheme where employees would be given rewards if they came up with a good idea for saving money. I said that they should switch off computer monitors during the hours the stores were closed. The specialists employed to judge the good ideas could not see sense in my suggestion. So, being happy to be energy rich is another source of energy use.

If you want a minimal OS where the user chooses which applications to have, then keep an eye on Ubuntu Snappy Core.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

[http://www.ubuntu.com/things](http://www.ubuntu.com/things)

Regards.

---

### Post by quixotic-cynic on 2015-04-23
> **grahammechanical said:**
> How low is low energy? Here is a machine that uses 50 - 80 Watts under full load and only 1.8 Watts on standby. And it runs Ubuntu 14.04

[http://translate.google.co.uk/translate?hl=en&sl=de&u=http://www.cirrus7.com/produkte&prev=search](http://translate.google.co.uk/translate?hl=en&sl=de&u=http://www.cirrus7.com/produkte&prev=search)

[http://www.omgubuntu.co.uk/2014/04/cirrus-7-nimbus-1-pc-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/04/cirrus-7-nimbus-1-pc-ubuntu-14-04)

Thanks for the info. I didn't know about that PC. Actually, I use a laptop now. However, before that I used a PC from [http://www.tinygreenpc.com/computers.html](http://www.tinygreenpc.com/computers.html). Their range of PCs only uses about 25 watts under load. So, I am aware that hardware is also an issue.

> **grahammechanical said:**
> I am not convinced that the blame for energy consumption can be put on the OS. No, it falls on both high power hardware and the users who demand ever more powerful hardware.

I agree that the demand for energy-inefficient hardware is part of the problem. Personally, however, I think that the OS shares some of the blame. OS development almost certainly is associated with emissions and all the servers e.t.c. are also associated with emissions.

> **grahammechanical said:**
> I used to work for a major high street retailer. My employer had a scheme where employees would be given rewards if they came up with a good idea for saving money. I said that they should switch off computer monitors during the hours the stores were closed. The specialists employed to judge the good ideas could not see sense in my suggestion. So, being happy to be energy rich is another source of energy use.

It's sad, but a lot of people have views like that IMHO.

> **grahammechanical said:**
> If you want a minimal OS where the user chooses which applications to have, then keep an eye on Ubuntu Snappy Core.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

[http://www.ubuntu.com/things](http://www.ubuntu.com/things)

Thanks! I hadn't looked at Snappy Core yet.

---

### Post by mastablasta on 2015-04-24
> **quixotic-cynic said:**
> 

I agree that the demand for energy-inefficient hardware is part of the problem. Personally, however, ***I think that ***the OS shares some of the blame. OS development almost certainly is associated with emissions and all the servers e.t.c. are also associated with emissions.
.

use facts rather than opinion when making an argument :P

you have servers that use low power out there. in fact major players are trying to move them to ARM or similar architecture. There are some reasons why server use as much power as they do. one of them is that a lot of users can be working on them at the same time or all the time. which means CPU never get's a chance to power down/idle. 

what part of OS development increases the emissions? I mean most is aimed at low power consumption so the OS can fit on tablets/phones. next they design it to fit on notebooks where usually battery usage is important. and when they design it the usually do it with this in mind. if the hardware enables 9 hours with 3cell battery you can bet that OS (or rather drivers) will be designed to support that. now if the manufacturer provides the drivers is another story.

---

### Post by quixotic-cynic on 2015-04-25
Hello mastablasta,

> **mastablasta said:**
> use facts rather than opinion when making an argument :P

Fair enough.

> **mastablasta said:**
> you have servers that use low power out there. in fact major players are trying to move them to ARM or similar architecture. There are some reasons why server use as much power as they do. one of them is that a lot of users can be working on them at the same time or all the time. which means CPU never get's a chance to power down/idle.

I realise this. However, most servers are still not run using energy solely from renewables but, rather, use a conventional energy mix that includes energy from coal, oil and gas (and nuclear).

> **mastablasta said:**
> what part of OS development increases the emissions? I mean most is aimed at low power consumption so the OS can fit on tablets/phones. next they design it to fit on notebooks where usually battery usage is important. and when they design it the usually do it with this in mind. if the hardware enables 9 hours with 3cell battery you can bet that OS (or rather drivers) will be designed to support that. now if the manufacturer provides the drivers is another story.

All OS development contributes to emissions (unless the company/individuals in question are very very careful).

Thanks & regards,
QC

---

### Post by vasa1 on 2015-04-25
Try to figure out how to use differential updates for software. There was a move in that direction but I think the idea was dropped, at least in the *buntu ecosystem.

---

### Post by quixotic-cynic on 2015-04-26
Hi vasa1,

An interesting idea, thank you. Probably not one of the first things to target but worth looking at.

Thanks & regards,
--QC

---

### Post by quixotic-cynic on 2015-04-28
OK, so I am looking for a green (or at least carbon neutral) hosting company that has a package suitable for running an Ubuntu mirror.

I've been looking at [http://www.memset.com](http://www.memset.com) at the moment.

There are a few problems:
1) I have no idea which package is relevant (if, indeed, any are) and
2) I am unsure how much it is going to cost.

If anyone has any ideas with regards to 1 & 2 it would be much appreciated. I need to work out if this is achievable or a pipe dream.

Indirect pointers to relevant information would also be appreciated.

Thanks & regards,
--QC

---

