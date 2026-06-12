---
title: "How to use ubuntu server without monitor or keyboard"
date: 2012-02-19
forum: Server Platforms
---

### Post by dhilipsiva on 2012-02-19
Hi all, 
I am a newbie. I installed Ubuntu 11.10 server 64 bit edition. everything was successful. I installed it in my desktop CPU. Because I want to set up a server at home. I borrowed a monitor and a keyboard from my friend to do the installation. Now I want to return him the monitor and keyboard back. I am trying to use ssh into server with my laptop. Everything works fine when I have the monitor and keyboard attached to the server. But it wont boot without monitor and keyboard. And I need to auto login automatically when the server starts. I ll be returning the keyboard n monitor to my friend once it is fixed. Is there anyway I can fix this? please help me. I don't think there is a problem in bios.

---

### Post by Iowan on 2012-02-19
Some machines won't boot without a keyboard - at least without adjusting a BIOS setting. Some have a "server" mode, some flag the keyboard error, but boot anyway (default setting is to stop on error). Years ago, I had a Compaq that needed a program run from the autoexec.bat.

What type/model is the computer?

---

### Post by dhilipsiva on 2012-02-19
Nope that is not the problem in my case. looked like there were some troubles with display problem. Fount a solution the using 'vesa' drivers would fix the problem. and it got fixed. thatnks for the response :D

> **Iowan said:**
> Some machines won't boot without a keyboard - at least without adjusting a BIOS setting. Some have a "server" mode, some flag the keyboard error, but boot anyway (default setting is to stop on error).
What type/model is the computer?

---

### Post by Iowan on 2012-02-19
[[SOLVED]?]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by dhilipsiva on 2012-02-19
yes, solved!!!

---

