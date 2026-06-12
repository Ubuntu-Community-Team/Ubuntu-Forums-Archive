---
title: "Can I distribute video rendering work load to cloud"
date: 2009-12-23
forum: Server Platforms
---

### Post by papadeath on 2009-12-23
I am new to Linux so please bare with me.

I am trying to figure out if cloud serving can decrease my rendering times for crunching video.

I do a lot of amateur video and my computer takes forever to render it. also while my computer is working on video it is useless for anything else. so I am looking to answer  the following questions

1) is there a program that can be used on ubuntu server for rendering video?
2) can this kind of work load be distributed across many servers? 
3) if this all can be done where do I start?

hardware available for cloud.

2 each IBM 235 servers with dual xeon 3.06Ghz cpu's and 2 gig ram each
2 each dual opteron 2Ghz servers with 2 gig ram each
2 each quad xeon 2Ghz cpu IBM 360 servers with 2 gig ram each
My desktop is a dual xeon 2 Ghz Dell precision 650 workstation with 1 gig ram
all of this is tied together via a 24 port dell gigabit switch.

---

### Post by HighCommander540 on 2009-12-23
> **papadeath said:**
> I am new to Linux so please bare with me.

I am trying to figure out if cloud serving can decrease my rendering times for crunching video.

I do a lot of amateur video and my computer takes forever to render it. also while my computer is working on video it is useless for anything else. so I am looking to answer  the following questions

1) is there a program that can be used on ubuntu server for rendering video?
2) can this kind of work load be distributed across many servers? 
3) if this all can be done where do I start?

hardware available for cloud.

2 each IBM 235 servers with dual xeon 3.06Ghz cpu's and 2 gig ram each
2 each dual opteron 2Ghz servers with 2 gig ram each
2 each quad xeon 2Ghz cpu IBM 360 servers with 2 gig ram each
My desktop is a dual xeon 2 Ghz Dell precision 650 workstation with 1 gig ram
all of this is tied together via a 24 port dell gigabit switch.

I would bet that there is a video rendering package for Ubuntu, I have never used it. All you would have to do is install it on the cloud (theoretically), and it should work. There are some programs that it just won't work with.

---

### Post by BkkBonanza on 2009-12-24
If you're talking pro quality I think Linux is very far behind the capabilities available on Windows or Apple. I looked around quite a bit before and found several barely usable programs with lots of deficiencies. It is improving over time and I think one day we may get there. 

On Windows I've used Vegas quite a bit and it has render clients that you can run on any number of servers (for a license fee) in a LAN. I tested that out once and it seemed quite good. It may be worth money if it saves you a lot of time. I'd love to see a good solution forr this on Linux, so if you find one please post details.

I tried Cinelerra, kept crashing. OpenShot looks potentially nice (no render client yet). There are ifx Piranha and Ant (commercial) but when they don't tell you the price you know it's a lot ($$$). Some people use Blender but when I tried it I couldn't see how. There was a few others I tried and mostly they don't have render clients either.

---

### Post by papadeath on 2009-12-24
Thanks BKK,
 
Hopefully someone here has done this before and can elaborate with a working solution.

---

### Post by wildhostile on 2009-12-26
> **papadeath said:**
>  . 

Cinelerra has got a renderfarm feature. You can ask on the mailing list ([http://cinelerra.org/mailinglists.php](http://cinelerra.org/mailinglists.php)) or on the IRC channel (irc://freenode.net/cinelerra).

---

### Post by Jekshadow on 2009-12-27
I like using LuxRender, it is free software (open source) and easily scales from a single computer to many.

[http://www.luxrender.net/](http://www.luxrender.net/)

To set a computer up as a LuxRender server, just open up luxconsole with the -s argument from a shell, and then take note of the IP/port to connect to it from the client.

---

### Post by HighCommander540 on 2009-12-27
> **Jekshadow said:**
> I like using LuxRender, it is free software (open source) and easily scales from a single computer to many.

[http://www.luxrender.net/](http://www.luxrender.net/)

To set a computer up as a LuxRender server, just open up luxconsole with the -s argument from a shell, and then take note of the IP/port to connect to it from the client.

This looks like good software. I checked it out.

---

### Post by papadeath on 2009-12-29
Thanks for the information.

Still looking to get a little more info though.

Anyone?

---

### Post by cariboo on 2009-12-30
Have a look [here]("http://helmer.sfe.se/") for a render farm howto, and if you do a Google search for : **linux render farm**, you should find enough links to keep you busy for a while.

---

### Post by papadeath on 2010-01-28
Thanks for all the responses and yes looks like the google search responds with quite a bit. sometimes the simplest things just evade me.

---

### Post by Volomike2 on 2010-03-03
> **BkkBonaza said:**
> If you're talking pro quality I think Linux is very far behind the capabilities available on Windows or Apple.

The major motion picture movies Avatar and Shrek were rendered on Linux clouds, according to news sources.

---

