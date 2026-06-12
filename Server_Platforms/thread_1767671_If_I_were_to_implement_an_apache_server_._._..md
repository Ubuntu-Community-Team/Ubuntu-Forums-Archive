---
title: "If I were to implement an apache server . . ."
date: 2011-05-26
forum: Server Platforms
---

### Post by ClientAlive on 2011-05-26
Hi,

I was wondering . . .

If I were to run an apache server on my desktop does that mean I could host my website right on my own computer? If so, are there any considerations like computer resources I should be considering?

I sure appreciate it. I'm just trying to determine the right direction to go in for what I'd like to do.

:confused:

Thanks

---

### Post by Lars Noodén on 2011-05-26
If you're just running a small business web site, then your existing hardware should be fine.  Eventually you might want to hire a hosting service so that someone else has to worry about the hardware and availability (power supply, fire suppression, drive failure, etc)  The cost is about $100 - $200 or so per year.

You can monitor the load on the system but it is not going to be that much.  If you want lighter than Apache, there is Lighttpd and even nginx. A CMS (plone, drupal, joomla, etc.) or e-Commerce system with a database is obviously going to be more of a load on the CPU than static HTML+CSS+SSI.  

It will also help to have a static IP address so that you won't have to mess with chasing a dynamic IP using No-IP or DynDNS.

---

### Post by ClientAlive on 2011-05-26
> **Lars Noodén said:**
> If you're just running a small business web site, then your existing hardware should be fine.  Eventually you might want to hire a hosting service so that someone else has to worry about the hardware and availability (power supply, fire suppression, drive failure, etc)  The cost is about $100 - $200 or so per year.

You can monitor the load on the system but it is not going to be that much.  If you want lighter than Apache, there is Lighttpd and even nginx. A CMS (plone, drupal, joomla, etc.) or e-Commerce system with a database is obviously going to be more of a load on the CPU than static HTML+CSS+SSI.  

It will also help to have a static IP address so that you won't have to mess with chasing a dynamic IP using No-IP or DynDNS.


Lars you talked to me on my other thread about ssh. I just thought I should share that my main motivation for looking into these things, well, I guess it's two-fold. One, maybe there's a way to get the same services we pay for at a lower expense. And two, maybe there's a way to extend the services we could have that would really benefit us but that we could never justify paying for. I guess for me it follows the old adage: "if you want something done right do it yourself."

Reading your response, somehow, makes me realize I need to start digging around to learn what factors effect system resources and how they are tied together. I have to thank you. Seeing some of the things you've been saying to me - I think I'm actually starting to form a strategy here. Amazing, isn't it? (That was a joke).

Time to buckle down now I think. You've given me some great direction and I think I have a real good idea what I need to be learning.

Have a great night man. Sorry about the way I cried around in the other thread at the end there. I was just having a rough day. Guess I'm not exactly 10 feet tall and bullet proof but I think I'll get it sorted.

I'm still a little uncertain about the minimum skill level required to do some of the things I'm looking into but I've never been afraid to jump into this kind of thing. Sometimes I think it's a blessing sometimes I think it's a curse.

Well, there I go again. I guess I'm just me.

Have a good night man. Thanks for everything.
--------------------------------------------

Edit: Hey I just thought of something. Can you point me to any good resources on the internet to learn how various system resources are calculated? Can or do people ever use a "per hit" unit of measure? I guess that would have to factor in all system resources - processing power, memory, bandwidth, maybe others. Then maybe there's breaking things down by the type of resourse I would assume?

I'm asking because I have an old desktop sitting here in the living room. It's broke down right now but I plan to get it up and running soon. I'm thinking the best way to approach a project like this is to determine my capabilities with the hardware I have available and compare that with what it will take to run what I want to run. Maybe I can use that knowledge to find a good balance, then - "execute" the plan. I love that word.

---

### Post by Lars Noodén on 2011-05-26
> **ClientAlive said:**
> ... I've never been afraid to jump into this kind of thing. ...

That's the main attribute needed and once you get comfortable working/navigating with the documentation sources.  Doing these yourself will also help you get a better idea of what services and tools you actually need, so that way when you do spend money, you can spend it more focused.

---

