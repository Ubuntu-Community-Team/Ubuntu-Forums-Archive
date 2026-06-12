---
title: "Intel Atom 330 2GB RAM Enough NFS-Samba-CUPS-Squid-Apache-SSH-FreeNX 20 Clients?"
date: 2010-03-22
forum: Server Platforms
---

### Post by AlexanderDGreat on 2010-03-22
Hi!

I need your opinion, currently I have an Intel E7400 C2D, 4GB Ram, ATI 1650, Raid 1 (2 Cheetah 40GB), 1 TB Seagate HD, 2 NICS, and a Raptor 500W PSU computer. We use this in the office for, CUPS server, NFS/Samba File Sharing - Movies, Music and Files, sometimes I connect via FreeNX or SSH, a local Intranet of 20 users, and a Squid Proxy Server.

It doesn't really have a big load because I think we just use basic "office" computing like: surfing the Internet, typing, share files, make brochures, and print.

Now, can I replace my server with an Intel Atom 330, 2GB Ram to save electricity? The reason I'm asking is if my server is OVERKILL? Or Intel Atom would compromise performance? Also, I have no experience with this yet.

Thanks for reading. :)

---

### Post by tgalati4 on 2010-03-22
You need to calculate people's time waiting for tasks vs the electrical cost.  Your machine probably burns 150 watts continuously, 24/7.  An atom machine can probably bring that down to 30 watts.

You could also consider turning the server off at night and using wake-on-lan and just put a wol launcher on each machine.  Then whoever needs the server first can launch it in the morning and the machine can turn itself off by itself at night at some appointed hour, or use a script to monitor load and shut off if load is 0 at a certain hour.

If you are not running web-based applications, then the atom would be fine for simple file and print serving.

Do you use this machine as desktop as well?  If not, then you can pull the graphics card and run it as a headless server.  GPU's tend to burn a lot of power.

---

### Post by AlexanderDGreat on 2010-03-23
> You need to calculate people's time waiting for tasks vs the electrical cost. - I see... Well, they can wait for a few delays I guess because some of them just waste time anyway. I'll check.

> Your machine probably burns 150 watts continuously, 24/7. An atom machine can probably bring that down to 30 watts. - I see...

> You could also consider turning the server off at night and using wake-on-lan and just put a wol launcher on each machine. Then whoever needs the server first can launch it in the morning and the machine can turn itself off by itself at night at some appointed hour, or use a script to monitor load and shut off if load is 0 at a certain hour. - this is probably more advanced for my skills as of the moment, can you suggest where do I start to do these things? I'm familiar of WOL, and shell scripting a little.

> If you are not running web-based applications, then the atom would be fine for simple file and print serving. - um sorry but I'm running a simple CMS for our company's Intranet, so does that mean Atom is a no-no!

> Do you use this machine as desktop as well? If not, then you can pull the graphics card and run it as a headless server. GPU's tend to burn a lot of power. - Actually no, yes, this is a great idea, thanks.

---

### Post by waloshin on 2010-03-23
my website survivorfun.com is running on an intel atom n330 server 2 gigabytes of ram and no problems.

---

### Post by tgalati4 on 2010-03-23
Is the atom330 a dual processor?   If not, then stick with what you have.

---

### Post by waloshin on 2010-03-23
> **tgalati4 said:**
> Is the atom330 a dual processor?   If not, then stick with what you have.

It's a **dual core** with hyperthreading so in theory' you will have 4 threads.

---

### Post by AlexanderDGreat on 2010-03-24
> Is the atom330 a dual processor? If not, then stick with what you have. - it is. Thanks.

> my website survivorfun.com is running on an intel atom n330 server 2 gigabytes of ram and no problems. - that's great! :)

---

### Post by KB1JWQ on 2010-03-24
Greening is an interesting solution, but I don't think it's the right way to go for you yet.

As it stands now I'd bet your actual power usage is closer to 70-100 watts, the same as an incandescent lightbulb.

How long would you have to leave a lightbulb on to justify the cost savings of building a completely new rig, the time you'd spend migrating, and the potential inconvenience of having to wait to 20 clients?

It sounds like there's not a lot driving this past "let's be eco-friendly!"  Am I mistaken?

---

### Post by AlexanderDGreat on 2010-03-25
@KB1JWQ - what interested me in your post is this:

> Postfix problems? Come find me in #postfix on the freenode IRC network.  - I'm planning to build a mail server, for educational purposes, will let you know if I'm there.

Anyway, the truth, I already have a spare Intel Atom 330, and I don't want to be green, it's just electricity is so expensive in my third-world-country, Philippines. :) Yup, you're right the migrating is the difficult part, but I'm just curious because I'm going for Lucid anyway, thanks for your ideas. :)

---

### Post by tgalati4 on 2010-03-25
In Los Angeles, electrical power is about $0.13 (US) per kilowatthour.  What is it in the Philippines?  My servers cost me about $60/year in electrical costs.

---

### Post by plausible on 2010-05-25
> **waloshin said:**
> It's a **dual core** with hyperthreading so in theory' you will have 4 threads.

:lolflag:

Multicore processing is really quite unrelated to multithreaded processing. Might want to educate yourself.

[http://www.eetimes.com/news/design/showArticle.jhtml?articleID=202102042](http://www.eetimes.com/news/design/showArticle.jhtml?articleID=202102042)

---

### Post by ian dobson on 2010-05-25
Hi,

Why not try just underclocking/undervolting your current PC? I have a MythTV frontend which runs on a e5200 that I underclocked to 1600MHz (max) and 800MHz in idle mode. At the same time I've reduced the CPU voltage to 0.95volt.

When idle the box uses about 30 watts and under full load (Mainly the graphic card for playing back HD videos) it uses 50-60watts.

Regards
Ian Dobson

---

### Post by KegHead on 2010-05-25
Hi!

A little off subject, but I use an atom 330 w/2gigs ram with no problems on a desktop.

KegHead

---

