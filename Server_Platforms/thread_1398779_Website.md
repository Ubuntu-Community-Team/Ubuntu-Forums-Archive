---
title: "Website"
date: 2010-02-04
forum: Server Platforms
---

### Post by rkitecht on 2010-02-04
I am beginner to UBUNTU. I installed UBUNTU server edition in one of my PC and created an ISP using one of the tutorials online.....

[http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-9.10-karmic-koala-ispconfig-2)

Now my problem is my website works fine in the local network how do I make it global

Thanks in advance

---

### Post by bpalone on 2010-02-05
You need to open port 80 on your router to that machine, AND ONLY TO THAT MACHINE.  I am assuming that your server has a static address in your LAN.

If my memory is correct, most routers call it port forwarding.  Look in your routers manual and it should give instructions for doing it.

It could also be that your ISP is blocking port 80.  I can't remember where I saw it, but there was a link to a website that checked your ports for being open.  Do a search and maybe you will find it.

Good luck.

---

### Post by dalitso on 2010-02-05
Port checking site [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by rkitecht on 2010-02-05
> **dalitso said:**
> Port checking site [http://www.canyouseeme.org/](http://www.canyouseeme.org/)
[COLOR=Black]
[/COLOR] [COLOR=red][COLOR=Black]I get the following error message [/COLOR]

Error:[/COLOR] I could **not** see your service on **55.25.15.11** on port (**80**)
Reason: Connection timed out

---

### Post by Kiwi76 on 2010-02-06
That doesn't ***necessarily*** mean your ISP is blocking it. By default, you'll probably get such a result, since most routers are not forwarding (and instead blocking, masking, or hiding) ports. If you get that even after you've forwarded port 80 to a PC, then your ISP may be blocking it.

Who is your ISP? Someone may know if they're blocking it. I know, in general, cable providers are more prone to block port 80. I think Cox [s]and Road Runner (Time Warner)[/s] does, and Comcast may as well.

---

### Post by FuturePilot on 2010-02-06
> **Kiwi76 said:**
> Road Runner (Time Warner) do, 

Negative. Not blocked, or at least it's not block here.

---

### Post by mushwars on 2010-02-06
[http://portforward.com/](http://portforward.com/)

choose your router, and follow the steps.

When I made my first webserver back on windows 98 no one ever told me about port forwarding, I spent weeks looking at settings, finally decided to look at my router, and did some research on something I found called "port forwarding"

11 years later and I still run my own servers. :)

portforward.com is a great resource and I wish it was around when I first got started.

---

### Post by Kiwi76 on 2010-02-08
> **FuturePilot said:**
> Negative. Not blocked, or at least it's not block here.Good to know. Either I was mistaken in my thinking, or it was in another location (I'd lean towards the former since if they block it, they wouldn't porbably wouldn't not apply that policy elsewhere).

---

### Post by lisati on 2010-02-08
> **Kiwi76 said:**
> Good to know. Either I was mistaken in my thinking, or it was in another location (I'd lean towards the former since if they block it, they wouldn't porbably wouldn't not apply that policy elsewhere).
Sometimes it takes a combination of research and inspired guesswork. When I was adding email capabilities to my home server a few weeks back, I followed the tutorials to the letter, and was able to send and receive emails on my home lan but none coming in or going out. This was followed by some head scratching until it occurred to me that my ISP might be blocking port 25 (the one used by email). Some reseach on my ISP's website: sure enough they were, and I immediately opted out. Still didn't work, even after checking with the ISP. A day or so later, it occurred to me that they might want me to use a static IP address. A bit more research, yes they did. Now why didn't they have that information on their port blocking page? ](*,)](*,)](*,)

---

