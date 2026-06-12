---
title: "Ubuntu Blocking"
date: 2007-03-22
forum: Server Platforms
---

### Post by Megahalo on 2007-03-22
Well I am trying to start up a Source Dedicated Server and I have been asking around what this error could mean and one of my friends told me that it looks a bit like Ubuntu is causing it. Well since nowhere else seems to be helping me, I decided maybe someone here can. 

Quote from the other forum (srcds.com) I asked for help.:
> I have run SRCDS servers on Windows many times before so I know my router, SRCDS, and basically everything when it comes to srcds on Windows. So I recently got upgraded to a business internet account and got a static IP so I decided to start back up my CSS server after about a 4 month break. I wanted to set up a "real" server and not just one that I run off my laptop because if I go anywhere I still want my server to be running. So I put my other much older laptop in a permanent place and set it up with Windows. Well this isn't any problem I can fix here, but I had used my CD key to many times and couldn't activate it. So I decided to try Linux since my friend really likes linux. So I installed Ubuntu 6.10 and everything works fine. I have a Linksys router (not wireless, wired) and have already DMZed my laptop (which runs on 192.168.1.102, which I keep checking every time I attempt to run the server to make sure it hasn't changed and it has never changed so I don't think thats a problem). I installed XAMPP (The Linux Webserver) and it works on port 80 (Normal HTTP port for those who don't know). Other people can get to my webserver. Now of course I'm trying to run my SRCDS on the exact same computer, but I can't figure out why it does not work. I have tried everything and it just keeps pissing me off more and more than I can not get it! If I try to run it on my static IP I get a could not allocate UDP port error which I now understand means I am not allowed to take an IP that the computer does not own because my router owns the IP. If I removed the +ip it works on 127.0.0.1. I told my friends to try and connect, but had no luck. I then tried on my DCHP address (192.168.1.102) and thought it might work. Again no luck. I can connect to my server on LAN by adding it to my favorites as 192.168.1.102:27015 and I can play it, but no one can get to it using my static IP. I tried tons of different ports, no luck. It is just really starting to piss me off because I know that the server is starting up because I can get to it on LAN! I decided to test running the SRCDS on my windows comp (LAN IP 192.168.1.100, with ports 0-65535 opened manually.). Well I study what my Windows version says my IP is and it says that the servers IP (that it uses) is 192.168.1.100, which is correct. And of course the Windows SRCDS works. That is why I don't get when I set my Linux one to 192.168.1.102 why no one can join. Even though all ports are opened. Well I said I would post the long version and I did so can someone help me now please.

Can anyone explain what this error might mean? :confused: 

```
net.cpp (932) : Assertion Failed: 0 == iRet && iValLen == sizeof( iVal ) && cSendBufSize <= iVal
net.cpp (940) : Assertion Failed: 0 == iRet && iValLen == sizeof( iVal ) && cRecvBufSize <= iVal
```

Thanks,
Megahalo

---

### Post by Megahalo on 2007-03-24
Anyone? Please I need some help here.

---

### Post by bastupungen on 2007-03-26
I have the same problem. I found this that have a similar problem

[http://www.opensubscriber.com/message/hlds_linux@list.valvesoftware.com/3320808.html](http://www.opensubscriber.com/message/hlds_linux@list.valvesoftware.com/3320808.html)

try issuing the command:
kern.ipc.maxsockbuf: 262144 -> 524288  

and see if that helps. I do not have sudo om my machine so I cant try it right now but I will try later

---

### Post by marci on 2007-04-01
HELO!

How do you execute the komand to change this value? 

sysctl -w kern.ipc.maxsockbuf=524288 is not working :S

---

### Post by rsermilik on 2007-04-01
kern.ipc.maxsockbuf is FreeBSD stuff. You can't use it in Linux.

Why do you use the same subnet for Secure LAN and DMZ? Does the Linksys have a true DMZ lan or is DMZ just a single host on your secure lan?

Have you configured the Linksys to route incomming port 27015 (or what you use) UDP to 192.168.1.102?

You must start srcds with +ip 192.168.1.102

---

### Post by cmoz on 2007-06-20
anyone get a solution for this I'm still having the issue described here

---

### Post by Mr. C. on 2007-06-20
Assertions are unexpected conditions in a program that the programmer thought should not happen, but is not certain, and tries to protect subsequent code from catastrophe.  They are useful to catch errors before they cascade into more or greater problems.

The only way to know what that assertion means is to either review the code and see what is causing the error condition, or contact the developers.

I certainly am not going to try to read through that long quoted story.  ( Does anyone understand the value of punctuation and paragraphs anymore!? )

MrC

---

