---
title: "Ubuntu server edition questions"
date: 2009-02-21
forum: Server Platforms
---

### Post by Rumbl3 on 2009-02-21
Ok well I switched my server box over to ubuntu server edition today 8.04. 

I know how to do everything in windows no problems what so ever. But when it comes to server type stuff on linux i'm very new. 

But i'll give a run down of what i'm trying to do and maybe someone can point me to some websites or tutorials or something.

I want to set my server box up directly off the cable modem, and run a UrT server from it and also route internet to my gaming box from it.

I have no clue how to set up a IIS on linux (if thats what its called here). I want to be able to remotely control it. I can do it no problems with a router but it seems like having the server sit behind the router lessens its power for running a server as to when i've hooked it up directly off the modem.

Any help or links or whatever be awesome thx.

---

### Post by E_K on 2009-02-22
my best solution for this, if you want to setup a box to be used as a hardware firewall and router (you prob. already know that it needs to have at least to NIC's) uninstall ubuntu and install smoothwall on the box.

then disable dns on your existing router if you have one, and make sure it has a different ip address as the smoothwall box.

then you can connect the old router to the box, and use it as a switch to connect your other boxes to it

It is a very rocking solution :) you should def. look into it. :)

---

### Post by Iowan on 2009-02-22
Guess I don't understand why having the server behind the router lessens it's power.  As mentioned, that machine will need a healthy firewall installed.  Shorewall is another option.

---

### Post by Rumbl3 on 2009-02-22
> **Iowan said:**
> Guess I don't understand why having the server behind the router lessens it's power.  As mentioned, that machine will need a healthy firewall installed.  Shorewall is another option.

Might of just been windows lol. But or maybe QoS on my router don't work for crap. When i tried dedicating 512k to the server on the router back when i was running windows on it left 4 dead would start lagging like crazy. I get 2.5 up to chicago constant and 1.5 to cali constant. So should be no reason i can dedicate 512 to the server. But when that was off it seemed to work pretty good. I just thought skipping the router would give it a little bit of a boost.

But maybe not oh well i'll try hooking it up and running a UrT server on it and see what happens. Looking to run a 10 player.

---

