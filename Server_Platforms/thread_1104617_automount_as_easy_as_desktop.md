---
title: "automount as easy as desktop"
date: 2009-03-23
forum: Server Platforms
---

### Post by Stargazer989 on 2009-03-23
i need a program that runs on startup and automounts my devices i insert or are already inserted.

Running Ubuntu Server 8.10 on an Eee PC 900a. 1gB RAM, 1.6GHz CPU(@667).

i know y'all ask; everyone does: i run server on a laptop because it doesn't have much extra than what i need to learn programming and, tbh, i've learned more than i did 4 months ago when i tried on the desktop version. cli, nano + gcc = all i need.

---

### Post by BkkBonanza on 2009-03-23
I guess I'll jump in with my two cents here regarding the "right" way to learn programming/web server admin on a laptop...

Install the desktop version and have a normal workspace. Then install VirtualBox (virtualbox.org) that gives you virtual machine ability. Now install the server version of Ubuntu (or WinXP or Centos or FeeBSD or whatever you want to learn) as a virtual machine. Now you are more like a real world situation except instead of the server being miles away in a data center it's actually a "box" running on your machine. You interact with it the same way you would if working at a job - either through a web control panel for easy stuff or through ssh for console access programing and tweaking. 

Now you can program using desktop tools/editors and at the same time be running your test/dev servers just as if they were real servers - independent and in the same configurations. This is the way to do this nowadays. Gone are the early years when people actually built home servers just to test and learn. This is far, far more flexible due to machine snapshots and cloning.

And it's actually easy to setup and do that.

---

### Post by nbotticelli on 2009-03-23
BkkBonanza,

I agree with what you wrote above but after looking at the type of laptop that he will be running this on I am not sure whether or not an Eee 901 would be able to handle a full desktop along with a virtualized os on top of that.

Though, if you can, I would be interested to know, these little netbooks keep amazing me everyday.

---

### Post by BkkBonanza on 2009-03-23
You could be right there. I didn't really notice the Eee part before I wrote that. He does have 1GB though - it may work. I used to do this on a machine with only 512MB. I installed the mini Ubuntu server (Jeos) and had a machine that emulated closely my real vps server. I was able to develop / test everything in that virtual machine before rsyncing it up to the vps (in the data center). It would be worth trying to see how performance is. Those machines are so small and convenient for working anywhere. I noticed that virtualbox only adds about 2-3% of cpu usage overhead so it ought to work fairly well. It's not like there will be any real web traffic.

---

### Post by Stargazer989 on 2009-03-23
I had trouble running the desktop let alone using Firefox, too. little chance i'll be able to use Vbox on it.

anyways, as i stated: 'the CLI helps me concentrate', you don't know how many times i strayed off because i got bored and knew games were available.

back to the topic:
someone suggest 'ivman' but it's couple years unmaintained... any suggestions/opinions.

---

### Post by BkkBonanza on 2009-03-23
Maybe have a look at the regular (desktop) init scripts in /etc/rc3.d and see if there are ones that you can run to start the services for automounting. I don't know what they actually use on an Eee PC but must be some daemons running for that.

---

