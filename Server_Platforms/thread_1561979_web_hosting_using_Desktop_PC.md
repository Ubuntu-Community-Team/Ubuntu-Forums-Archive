---
title: "web hosting using Desktop PC ?"
date: 2010-08-27
forum: Server Platforms
---

### Post by Zacinfinite on 2010-08-27
Im a nube in networking and servers.
I want to make a website for my Dads business but dont want to go to any commercial hosts.
Is it possible to make my desktop PCs as webserver and DNS and publish my own website through it? i got 120kb/s broadband.
will other people be able to open my website around the world? What are the limitations?

---

### Post by lisati on 2010-08-27
Moved to "Server Platforms."

Yes, it is possible for you to use a "desktop" computer as a server. I have a 5-year old "desktop" set up as one, running [Ubuntu server edition]("http://www.ubuntu.com/server"), with "Apache" dishing out web pages and "Postfix" handling email. (See my sig. for some links to different parts of my web page.)

If you are to make the website accesible by the public, a Domain Name will be useful - I use free domain names from [no-ip]("http://no-ip.com") and [dyndns]("http://dyndns.com")

Chances are there will be one or two things you'll need to learn: take one thing at a time, feel free to ask questions, and you should be fine.

---

### Post by Zacinfinite on 2010-08-27
Thanks alot i just need to know that to start learning stuffs. I'll definitely checkout your links.
Thanks again

---

### Post by Nick_Jinn on 2010-08-27
I wonder if he means 'use his dads desktop while still leaving it functional as a day to day desktop for nomral web browsing purposes', rather than 'take my old hardware and use it for a server'.

---

### Post by lisati on 2010-08-27
> **Nick_Jinn said:**
> I wonder if he means 'use his dads desktop while still leaving it functional as a day to day desktop for nomral web browsing purposes', rather than 'take my old hardware and use it for a server'.

That's a good question.

My $0.02: Although servers are often machines dedicated to the task (mine is), it is possible to have a GUI available for day-to-day stuff. My server has a minimal install of a GUI for when I'm feeling too lazy to figure out how to do something with the remote management tools I have installed. Part of the answer would depend on how much of a workload that each role would demand from the computer.

---

### Post by Nick_Jinn on 2010-08-27
If its a small personal business it might only have a handful of people browsing at a time....if its more intensive, a typical PC thats a few years old might not cut it....Im guessing.

---

### Post by Zacinfinite on 2010-08-27
No Nick_Jinn. I meant to setup a desktop PC as dedicated webserver as my dad got many thrown in the trash mostly P3.
And Dads an NGO so i need to make the website available in whole of country and abroad for government projects.

---

### Post by Zacinfinite on 2010-08-27
And please tell me what limits the website traffic? Simultaneous user limit and downloading concerning technical input.

---

### Post by snek on 2010-08-27
I would not suggest using an old P3 as a business-critical webserver. Considering the age of the hardware you have quite a lot of chances of it having a serious hardware failure.

However, I would definitely use one of the machines to learn how to setup my own webserver! It's a great learning experience. 

I run a regular AMD Athlon II system as my home server, and have it configured with Apache, MySQL, PHP, Postfix and have a couple of domains hooked up to it :)

Once you have that down you can rent a cheap VPS from slicehost or linode and set that up.. Then you have some quality hosting with options to upgrade if that's ever needed.

---

