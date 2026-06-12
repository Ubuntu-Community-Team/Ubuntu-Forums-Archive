---
title: "LTSP general questions"
date: 2007-12-23
forum: Server Platforms
---

### Post by gersep on 2007-12-23
I have some general questions regarding LTSP, and I hope someone could help me. Here's what i want to do. I want to set up an LTSP system in a very small business (maximum 5 clients working at the same time), however I'm not sure if LTSP is for me

Let me describe what i want to do with the whole setting:
- 5 LTSP clients
- 1 LTSP server

I don't know if what i'm going to describe is even possible so please let me know if it's not. I want the LTSP server to be able to do the following:
- Provide full processing for the LTSP clients
- Allow internet access to the LTSP clients
- Run Web, apache and mysql servers (For runing the Point of Sale [POS] System which is to be designed under this techonologies)
* This point brings me to the next question... would the clients be able to access the webserver even considering that they're actually processing from the server itself? I mean the clients would still be able to access the server's web through [http://localhost/](http://localhost/) ?
- Be a usable workstation by itself... i mean sitting in front of the server and work on ubuntu as a normal user.

I also have an extra question. What will be displayed on the LTSP clients. If i install ubuntu 7.10 and then over it install LTSP server... the clients are going to bootup and work on an ubuntu 7.10 desktop? I'm not really sure how the whole LTSP system works, I've been reading but there's some doubts I don't seem to find an answer to so any *extra* information would be of a lot of use.

All help would be GREATLY appreciated. Thanks.

---

### Post by reckless2k2 on 2007-12-23
all good questions. some may answer in different ways. depending on the volume of hits, i wouldn't run the webserver on the same box as the LTSP server. your LTSP box would have to be VERY high end to support both. ltsp is designed for thin clients to pixie boot and run all services from the ltsp server. the clients would be actually accessing the server for everything hence the services. i suggest that you look at the edubuntu site andit gives good info on what ltsp is and how it all works. it also explains how the network all works and inter-relates with machines.

---

### Post by gersep on 2007-12-24
thank you for your quick response... actually you helped me out on one of my biggest concerns about the server being able to run all those services at the same time.

I will be reading more about LTSP on the edubuntu site since i was planning on buying a pc specifically for this use. Still researching what will the thin clients display on their screens, since i can't find this pointed out explicitly anywhere...

Thanks for your help

---

