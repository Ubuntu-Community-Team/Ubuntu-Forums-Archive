---
title: "usb-serial &amp; console terminal problems"
date: 2013-05-28
forum: Server Platforms
---

### Post by xris_xcess on 2013-05-28
Hi...

I'm trying to get a serial-console terminal going on a server that I run.

I have a usb-serial adapter with the pl2303 chipset and a null modem cable.

At the moment I have tested it with ubuntu 12.10 running as a server (a xubuntu installation actually) and my macbook as the "terminal" (using screen and coolterm).

I know what you are going to say, that I should check my drivers on the mac and the software, but bear with me please.

I do actually get a connection (i get most of the kernel messages when booting the server in fact) but when ttyS0 starts I only manage to get about 8 lines of output. Basically the login, my password and a few lines of the welcome messages.

I, assume (wrongly maybe), that if my drivers or software were not working properly, I would't get any connection at all. It's like the terminal "freezes" on the server. I have set both the server and terminal to 9600n8 with no apparent benefit.

I used to connect with screen, and if I killed the window (cntl-a,cntl-k) and then restarted, I get back on... sometimes.

I'm trying to isolate the problem. My next step it to set up another ubuntu machine with a serial port and go over the null-cable, to see if it's the usb-serial cable or drivers or both. I have been reading that some of the cheaper adapters are not always very reliable, but even then people report success on different platforms or drivers from different sources.

Anybody had similar issues that they managed to solve?

---

### Post by xris_xcess on 2013-05-30
Well I have tested again with the usb-serial adapter, this time with ubuntu in a vm in macosx, using minicom and it seems to work well. Every now and again it seems to stall, but if I unplug and replug the adapter it reconects ok.

At least this means that the adapter is not a dud (like many have said with generic knockoffs).

I guess now it's about trying to find a new driver (maybe written by another manufacturer).

I wonder if it could be any of the connetion settings?

---

