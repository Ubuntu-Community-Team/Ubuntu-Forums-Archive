---
title: "Teaching synaptic(or not?)"
date: 2009-09-19
forum: Testimonials &amp; Experiences
---

### Post by Jestersage on 2009-09-19
Occassionally I help teach in a workshop about Ubuntu, and recently one of my superior want us to install DVD codecs. So the obvious solution is:
a) Get Medibuntu
b) install libdvdnav and libdvdcss thru apt-get or synaptic

The problem is that, due to the workshop's regulation, we have to do the two aforementioned steps by teaching the students; We cannot install them before hand. (We tried to use "add/remove", it's not there)

And the issue is thus:
a) If we teach them synaptic, they may majorly screw up their machine
b) If we do not teach them synaptic or terminal, there are no way we can install DVD
c) If we do it for them during workshop without explaining, it seems to be counter the directive of the workshop.

So it feels like we are in somekind of catch22. Can someone find a solution that enable us to teach them to install DVD codec without using synaptic or Terminal?

Or alternatively, is my worry on synaptic overblown?

---

### Post by Elfy on 2009-09-19
I'd say your worry was overblown - how can you teach someone to use the system without telling them how to install things as well ;)

Better to teach how to do so in my opinion.

You can use apt://packagename in firefox - but the repo's has to be set up beforehand

---

### Post by 3rdalbum on 2009-09-19
> **Jestersage said:**
> And the issue is thus:
a) If we teach them synaptic, they may majorly screw up their machine

True. But there are lots of occasions where there's a possibility of screwing up the machine. As the instructor, it's your job to advise caution when dealing with Synaptic, and say "don't remove any package unless you're absolutely sure".

It's harder to screw up a system by installing software, but it's possible.

The good news is that you can always recover. Even if it involves booting a live CD, mounting the partition and using chroot to run apt-get within the context of the installed system.

---

### Post by pwicken on 2009-09-21
Teach them Synaptic, tell them about deb-packages, alien and make-install too. 

[I]You cannot control or limit what they are learning, 
you can only control how they are learning from you. 
[/I] 
If you want them to meet Synaptic unprepared leave it out. You cannot prevent most of them from finding out anyhow. Those who don't will probably never touch Linux/Ubuntu again. At least I would never use an OS that can't play DVDs, add new repositories etc. If you don't give them this crucial information they will either have to discover for themselves, without your guidance, or return to MS/Apple for a system that does what they need.

---

### Post by SeePU on 2009-09-22
> **Jestersage said:**
> Occassionally I help teach in a workshop about Ubuntu, and recently one of my superior want us to install DVD codecs. So the obvious solution is:
a) Get Medibuntu
b) install libdvdnav and libdvdcss thru apt-get or synaptic

The problem is that, due to the workshop's regulation, we have to do the two aforementioned steps by teaching the students; We cannot install them before hand. (We tried to use "add/remove", it's not there)

And the issue is thus:
a) If we teach them synaptic, they may majorly screw up their machine
b) If we do not teach them synaptic or terminal, there are no way we can install DVD
c) If we do it for them during workshop without explaining, it seems to be counter the directive of the workshop.

So it feels like we are in somekind of catch22. Can someone find a solution that enable us to teach them to install DVD codec without using synaptic or Terminal?

Or alternatively, is my worry on synaptic overblown?
Imho, Synaptic is the best package manager so why would you worry about them screwing up their machine?  When they leave the workshop, there is always that chance.  The best thing to do is to show the two ways, GUI and CLI (apt-get install etc.).  Maybe explain the ways in which you could mess your machine up and say 'don't do this.'  :P

Also, tell them not to try things (i.e. installing packages etc.) when they're sleepy.. :)

---

