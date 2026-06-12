---
title: "FireStarter Question"
date: 2010-05-18
forum: Security
---

### Post by Aleutian89 on 2010-05-18
So im rather new to linux, I have been using wubi with 9.10 past 3 months, and 3 days ago took the plunge and change completely over to linux ubuntu 10.04 So thx in advance with dealing with my newbie question.    So I understand firestarter is a frontend gui more or less.  I also know from reading on install of ubuntu ports are closed by default.    1. So my question is by installing firestarter does it open any of these ports by default?  All I did was use wizard to setup and nothing more.    2. When firstarter is not on does that mean my firewall is not up?     I just get alittle paranoid when I change things or install things that could mess with security. Its that windows mind set.    Thx Aleutian  I hope I put this in the right place.

---

### Post by cdenley on 2010-05-18
1. No. The only way to open a port is to install a server. If there is no process listening for connections on a port, it isn't open.

2. No. Firestarter's configuration is loaded at startup.
```

sudo iptables -L -n

```

Firestarter is old and no longer maintained. I don't recommend using it. I suggest UFW or GUFW if you insist on having a firewall.

---

### Post by Aleutian89 on 2010-05-18
Thx  

Also like I said im new to linux and such which would u recomend then for being newbie an all in regards to UFW or GUFW, I am learning terminal commands but a simple gui is more what I need till i get further along
Off to explore some more :P

---

### Post by Paddy Landau on 2010-05-18
To clarify, unlike Windows, you don't install a firewall. Linux has a firewall already built in, and it's good.

Something like firestarter is simply a front-end to change the settings of the firewall.

For the average user such as myself, there is absolutely no point in changing the settings; they're already high.

When I went to [GRC's Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") tester, I found that the default Linux installation had a higher security rating than my Windows did with a paid-for firewall and antivirus. I haven't done it for some time, but you may want to check it out.

---

### Post by Aleutian89 on 2010-05-18
It was funny I was making a "To Do List" when I install 10.04 the other day and for security programs and setup I was like well thats not a long list at all compared to windows, I am not into setting up servers and such so not a really a need on that end I would say I am a average user. 

On the note of firestarter I just really like to watch the "Active Connections" sections and watch what program was connecting to what, Im sure there are other ways, plus I had been reading the security stickie at the top of this forum section and it had talked about firestarter and I figured I would take a look at it. Though seems I will be getting rid of it really no point to it.

Thx for the responses, I have barely scratched the surface of linux and or ubuntu. So far I am having a blast and even converted a friend now to like a "linux accountability buddy"

Aleutian

---

### Post by Paddy Landau on 2010-05-18
> **Aleutian89 said:**
> It was funny I was making a "To Do List" when I install 10.04 the other day and for security programs and setup I was like well thats not a long list at all compared to windows
No, you don't need to worry about things like defragmenting or [CCleaner]("http://www.ccleaner.com/") (the equivalent of CCleaner is [Bleachbit]("http://bleachbit.sourceforge.net/"), which you can find in the [repositories]("apt:bleachbit"), but you don't need it).

> **Aleutian89 said:**
> So far I am having a blast and even converted a friend now to like a "linux accountability buddy"
What a cool idea! Have fun.

---

### Post by bodhi.zazen on 2010-05-18
Be careful with Bleachbit. In general it is not needed and if you use it aggressively, without understanding what you are removing, it can cause damage to the system.

If you do not know what file Bleachbit is suggesting you remove is for, do not remove it.

Linux is not Windows and I suggest you relax and enjoy your new OS. Linux has issues, but I would not worry about firewalls, monitoring network traffic, defragemntation, antivirus, or cleaning files at this point in time.

---

### Post by The Cog on 2010-05-18
Don't confuse closed ports with blocked ports.

On a default Ubuntu install, all ports are closed - there are no services listening for incoming connections, so nothing can connect to your machine. This is different to windows, which has many ports open by default.

A firewall can block access to ports whether they are open or closed. On windows, you need a firewall blocking ports because there are so many open ones with services listening. In Ubuntu, the inbuilt firewall (known as iptables or netfilter) doesn't block any ports by default. This doesn't matter because there are no open ports to connect to anyway - imagine a doorman guarding a closed/locked door. 

You will want to configure the firewall in Ubuntu if both these are true:
* You install a service that accepts incoming connections, and
* You want to prevent some IP addresses from gaining access.

Of course, if you install a public server then there is still no point installing a firewall because you'll just have to configure it to let everybody through again.

---

### Post by Paddy Landau on 2010-05-18
> **bodhi.zazen said:**
> ... I suggest you relax and enjoy your new OS. Linux has issues, but I would not worry about firewalls, monitoring network traffic, defragemntation, antivirus, or cleaning files at this point in time.
Absolutely agree. Linux has given me peace of mind, not just because of security but also because of its reliability and speed.

---

