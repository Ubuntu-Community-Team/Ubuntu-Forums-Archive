---
title: "Tutorial proposal: andlinux to run your ubuntu apps"
date: 2008-05-24
forum: Virtualisation
---

### Post by Virtual DarKness on 2008-05-24
For now I'm posting it here as it doesn't meets the "Criteria for threads in the Tutorials and Tips section"

I've also wrote a post suggesting to create a sub-forum of the Tutorials and Tips section for tutorial drafts.

So.. here his my first post.. let's see if someone will find the topic interesting and if in the end it can became a tutorial.

"disclamer:" On my post there are some questions cause in order to make a tutorial I think is right to find the best solution but I'm not trying to mask a request of help for a tutorial proposal as I'm already fine with what I was able to do ;)

That said, here is my original post:
---------------------------------------------

Today I've managed to install [andlinux]("http://andlinux.org") and configure it so that I achieved (all) these results:  

- run applications as a normal user
- mount my ubuntu root and home partitions
- dist upgraded ubuntu in andlinux to 8.04
- run applications (like thunderbird) using settings and data of my real ubuntu installation (so I can run thunderbird and firefox with the same data and configuration in both linux and windows)
- run applications that I've installed in my ubuntu install but not in the andlinux install from window with my settings / data like konqueror, gftp (so I don't have to install them again in andlinux's ubuntu) .. this last thing using schroota

The only problems are:
- sound does not longer works in andlinux (problems with permissions of pulseaudio with the normal user I guess)
- I was not able to run revelation both in andlinux and in andlinux from my ubuntu install using schroot (guess has something to do with the fact that it is written in python but I could be wrong)

so.. does someone would like to have a tutorial on how to do this? I'm asking cause I plan to write some notes for myself but writing a tutorial would require me lot more time. also would be nice if someone would like to help me writing it and of course if there are better methods (like using directly colinux) let me know. I've started with andlinux cause it already has lot of pre-configured things like the X server and so on.

btw.. I've used cofs instead of samba to share a folder with the windows install.

bye,
Giovanni.

---

### Post by p_quarles on 2008-05-25
Moved from Community Cafe --> Virtualization at poster's request.

---

