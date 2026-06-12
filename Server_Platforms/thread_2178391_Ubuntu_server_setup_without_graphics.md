---
title: "Ubuntu server setup without graphics"
date: 2013-10-03
forum: Server Platforms
---

### Post by daniel-gator on 2013-10-03
I have a bunch of old parts I have assembled into a what I hope to turn into a server. I want to run a mail server, a minecraft server and maybe something for streaming videos. 

I have a general understanding of how I'm going to do this however the build I want to do this in has not graphics of any kind (it's a cheap AMD CPU). I'm guessing I'll need to set this up in a VM could anyone suggest the best way to do this?

oh, almost forgot. I'm putting this at an office which has access to optical fibre (which is a big deal here in Perth) the office also has a 3D printer in it I would like to be able to use octoprint to start a print from home and then drive there

---

### Post by sanderj on 2013-10-03
Download Ubuntu Server from [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) and install it just like you would install Ubuntu Desktop. No VM needed.

Wait ... you have already installed once Ubuntu Desktop on some other system to gain experience ... ?

Out of curiosity: how much RAM and which CPU in your server hardware?

---

### Post by houstonbofh on 2013-10-03
You will need a display to install it, but you will not need on to run it.  Are you saying you want to run headless, (OK for servers) or in your collection of parts you do not have a video card?

---

### Post by sandyd on 2013-10-03
> **houstonbofh said:**
> You will need a display to install it, but you will not need on to run it.  Are you saying you want to run headless, (OK for servers) or in your collection of parts you do not have a video card?

Can be done via PXE, but dont know why you would want to do it

---

