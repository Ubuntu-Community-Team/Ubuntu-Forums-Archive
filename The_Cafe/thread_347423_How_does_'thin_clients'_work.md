---
title: "How does 'thin clients' work?"
date: 2007-01-27
forum: The Cafe
---

### Post by Sunnz on 2007-01-27
I heard about it, and I think I has used it at school too... but can anyone tell me how actually can it do/

Say if I buy something like this for my parents: [http://h10010.www1.hp.com/wwpc/au/en/sm/WF05a/1090261-1126487-1126487-1126487-1140827-12235624.html](http://h10010.www1.hp.com/wwpc/au/en/sm/WF05a/1090261-1126487-1126487-1126487-1140827-12235624.html)

Given that my own machine is on 24/7, does that mean they can boot from my computer across the network, and starting surfing the net?

To take it a bit further, if I have some friends came over, can they use the thin client and load something like Quake, and start a lan game with me, running the 'server'?

Please tell me if I got this all wrong or just crazy... :confused:

---

### Post by Tomosaur on 2007-01-27
A thin client can mean a number of things, all of which are very similar, and really rely on the capabilities of the server. A two tier client/server system, looks like this:

client ------> App server.

This solution is generally more suitable for a small, home network. Here, the client holds all of the data files - ie, word documents, music, blah blah blah. This means that each client computer only has access to the data stored on that computer. Perfectly acceptable for home networks, but not great for offices and business. The app server holds all of the software and such, meaning any client machine can use that software, rather than only being able to run the software stored on its own hard drive. The actual processing can be done on the App server itself, or the client can request a 'copy' of the software, and does the processing itself. If the former, the App server will need plenty of RAM, and a quick processor / set of processors, to handle multiple instances of the program, or a whole bunch of different programs.


A three tier system MIGHT (not always) look like this:

client -------> data server ------> app server.

It's actually a little more complicated than that, and can be configured completely differently, but it's ok for the purposes of illustration. In this scenario, any client machine can access the data stored on the data server. This means that Mr Smith can log onto machine A, or machine B, and have access to exactly the same data and software. This is truly thin client, because nothing is really stored on the client computer, save some rudimentary stuff to enable the whole system to work fluently. The software processing can again be done on the app server, or the client machine.

Yes, you can set up a client/server system for your parents, but remember - the server will need to be able to handle the workload, or it'll grind to a halt and crash.

---

### Post by ssam on 2007-01-27
a thin client across the internet will be very slow to use.

---

### Post by koenn on 2007-01-27
> **ssam said:**
> a thin client across the internet will be very slow to use.

not necessarily. 
The working of a "thin client" is actually much like a remote desktop or a vnc-session : all the work is done on "the server"  - the client limits itself to send key strokes/mouse movements to the server - the server executes whatever action is required and sends back the screen output to the client. Think of a thin client as a keyboard and a mouse, a monitor, and a network connection. 

Usually, a thin client will be diskless - it does not have a hard disk (doesn't need it), so to boot a minimal OS needed to make keyboard, monitor and network connection work, the thin client boots off some "bootcode" on the network card, connects to a server, and downloads a minimal operating system to its memory, and runs it. 

Edubuntu and other "Linux Terminal Services" Projects work roughly that way. 
It will be obvious that the thin client will only be able to run software that is available on the server.

---

