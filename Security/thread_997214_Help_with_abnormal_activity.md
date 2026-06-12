---
title: "Help with abnormal activity"
date: 2008-11-29
forum: Security
---

### Post by brandon88tube on 2008-11-29
Just recently I have been having abnormal activity dealing with UFW. It keeps blocking some input from something and it is happening really often, so much that it is taking up a HUGE portion of my log files. Its lines and lines of UFW BLOCK INPUT. When I am at home I never even once had UFW block anything, but right now I am down visiting family for the holidays and I am using their internet connection on my laptop. All of the SRC addresses are from the same IP, which looks to be local as the number starts with 192.xxx.x.xxx I'm not sure if it is though. Still why is it trying to connect to my ports? As I said this never happened at home and now its like every minute I get around 1-3 of these messages with a few minutes of nothing and then it starts up again. Can someone help me figure out what this is and how to possibly fix it besides saying, "Don't use their internet." Anyone please?

---

### Post by Kinstonian on 2008-11-29
We need to be able to see the firewall logs that are being generated in order to get any idea on what is happening.  You might as well post the firewall rules as well.

---

### Post by brandon88tube on 2008-11-29
The firewall is set to block all by default. This is what keeps popping up in the log file ```
Nov 29 18:27:07 name kernel: [19714.567834] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=192.168.1.254 DST=192.168.1.95 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=6974 DF PROTO=TCP SPT=1992 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
```

---

### Post by lovinglinux on 2008-11-30
Looks like the IP address of the DSL modem or router. What seems odd to me is the SYN flag and the destination port, which is 80.

---

### Post by The Cog on 2008-11-30
Yup, 192.168.1.254 is trying to connect to a web server on 192.168.1.95. I presume that 192.168.1.95 is the address of your PC. But what is 192.168.1.254? Is is the router? The command route -n will show what the default gateway (your router) is - it's the gateway for destination 0.0.0.0.

---

### Post by Kinstonian on 2008-11-30
I figured it was just going to be some NetBIOS or some other normal traffic.  Then when I saw it was probably the router I figured it would of been something like UPnP traffic.  To tell you the truth, I don't know why what appears to be a router's IP, would be repeatedly trying to connect to a HTTP service on your computer.  I suggest you do what *The Cog* said and see if it really is your router.  If so, I'd login to it and see if there is some option enabled that could be the cause.  From the one log entry I've seen, it's probably nothing malicious, but it wouldn't hurt to investigate it a little further.

---

### Post by cariboo on 2008-11-30
I would suggest that it is an infected computer on your relatives network.

Jim

---

### Post by brandon88tube on 2008-11-30
Thanks guys for helping me out. Unfortunately I can no longer check the router etc. because I am back home now... after about a 12 hour drive. It is very possible that they had an infected computer because it had a ton of crap on it. I might give them a heads up though and let them know they might have a problem. Also just for info sake, I believe 192.168.1.254 was the router.

EDIT: Actually I am wondering if you could tell me anything that I could tell my relatives to run on their Windows machine to check it out. They are not really great with computers, but I still want to have them check it out.

---

