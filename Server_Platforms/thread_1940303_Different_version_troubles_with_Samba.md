---
title: "Different version troubles with Samba"
date: 2012-03-13
forum: Server Platforms
---

### Post by marineco on 2012-03-13
I'm pretty new to Linux, almost posted in Absolute beginners section. But I think this section is more relevant. I've decided to use Ubuntu in our office, starting out as a NAS. I ran a test on an old laptop. I loaded Ubuntu Server on it. Fairly sure it was 10.04 32 bit, but it may have been one of the newer ones. I had installed the gnome desktop to it as well, but the core was server edition. My test worked perfectly. All my computers could see and communicate with Samba.

I ordered an actual server. A Fujitsu TX100 S2 if it's relevant. I had to turn off the onboard RAID controller in order to get Ubuntu Server 64bit version to install. I also set up a software RAID. No desktop this time. Using to the best of my knowledge the same settings as before, only my XP machine will even _see_ the server, but even that one won't communicate with Samba. (Oh, and now I have a new router)

So the short version:
No DE installed this time
64 bit vs 32 bit versions
RAID set up
Hardware - laptop vs server
New router

I headed over to the samba troubleshooting page, and I got a little way with that, before it went over my understanding. But I did get one important piece of information. Apparently both the server and client should be able to ping each other by name. I can ping the server by IP, but not name. The server can ping my desktop either way. I don't remember the wording, but whatever it said made me decide to leave DNS proxy as no. I hadn't touched it in my test run.

Thanks in advance for any help

---

### Post by marineco on 2012-03-21
Edit: Had replied to the wrong thread of mine. This one wound up being a typo problem.

---

