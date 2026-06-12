---
title: "Setting up on a Poweredge 4400"
date: 2008-03-07
forum: Server Platforms
---

### Post by frozenjake on 2008-03-07
Hola! I am, as described in other posts, a uber-n00b to linux, but I am learning. I recently was given a Poweredge 4400 Dual Xeon 900mhz w/1.5 GB ram. I wanted to experiment with Ubuntu on it, but every time I try to install, I get odd errors or it freezes in boot. I tried the 32bit ubuntu server install, but I while I could get limited sh functionality (spotty with occasional freezes), I couldn't get ANY x-windows system to run. I
I tried the regular install, but it wouldn't even boot. (froze) Dell calls it a dual-32 bit system....should I run a 64bit install?
 I am trying to quit my dependency on Windows XP/ Various Servers here darnit.....it's not easy tho.

Any (patient) help out there?

---

### Post by linuxh8ter on 2008-03-07
What is the point of running X on a server environment? Also, I don't believe the server install of ubuntu has x packaged with it.

---

### Post by frozenjake on 2008-03-07
:-) see what I mean about noob? I was trying to install X myself. Considering the PM i just got about how pointless that endeavor was, I think I will give up. But it 's immeterial to my freezing problem. I guess I should rephrase my question "am I a tard and am trying to use the wrong distro?"

---

### Post by jonabyte on 2008-03-07
> **frozenjake said:**
>  I guess I should rephrase my question "am I a tard and am trying to use the wrong distro?"

No and maybe to your questions.

What version of the server are you trying to install. If its the latest, try an older version.

You can't run a 64bit install if the box is not 64bit.

What else are you installing with the server, anything??

---

### Post by rickyjones on 2008-03-07
> **linuxh8ter said:**
> What is the point of running X on a server environment?

Some people find it easier to manage a server when they have a GUI in front of them, even if the GUI is just running an xterm prompt. Many times while stuck in the datacenter I've been happy to have a GUI there for the instance where a particular problem pops up and you need a web browser to find the solution. Much easier and faster than leaving the datacenter, going back to your desk, finding the solution, printing it out, and then going back in and realizing that you forgot one part of it.

-Richard

---

### Post by jonabyte on 2008-03-08
> **rickyjones said:**
> Some people find it easier to manage a server when they have a GUI in front of them, even if the GUI is just running an xterm prompt. Many times while stuck in the datacenter I've been happy to have a GUI there for the instance where a particular problem pops up and you need a web browser to find the solution. Much easier and faster than leaving the datacenter, going back to your desk, finding the solution, printing it out, and then going back in and realizing that you forgot one part of it.

-Richard

At my one work place we had a special box for just that purpose, it does make it handy, but management did not want a gui on the production servers.

---

