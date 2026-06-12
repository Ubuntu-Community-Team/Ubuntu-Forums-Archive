---
title: "General Issues (Just Me?)"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by saneearth on 2012-04-21
Not really a complaint, just observation. Graphics programs, picture programs like Geeqiie and others are less responsive to input. I am not a coder and don't have time, so not sure of the specific issues. I am a "tech" for my living so not totally an "idiot". I support Win 7 and XP (still), but at home for years now have primarily been Ubuntu. Been with 12.04 since Alpha and understand it is/was Alpha, but now that we are close to production I am concerned. The reason I have been with Linux and Ubuntu is responsiveness and file transfer. It appears things in Gnome now are starting to "lag". It does not seem to matter whether in Unity Desktop or Gnome, the responsiveness of some of the programs are loosing it just the same. 

There may be an issue of development on some programs not keeping up with Gnome 3, but I really don't know. What I do know is that the real reason that I have been with Linux/Ubuntu/Gnome seems to be getting away. Doesn't matter what Desktop I am using now, things are getting "buggier". Is it just me? I am a Gnome guy primaily, but other desktops seem to have the same or similar issues. Right now I feel I could stay with Gnome 2 forever, but of course I can't. Guess I am just wondering if I am the only one that is having issues. I am wondering if development is leaving behind the programs that most of us use.

---

### Post by neu5eeCh on 2012-04-21
I visit Phoronix every so often and, by what I can tell, Linux file transfer speeds, esp. with ext 4, have steadily increased and are generally _better_ than comparable Windows machines. In fact, Linux tends to outperform Windows in a number of areas, according to Phoronix. But that's "raw" linux... So it's peculiar that you're noticing "lag". Are your observations limited to Gnome, or to DEs like XFCE or LXDE as well? As for myself, I *do* notice that Unity/Gnome is laggy, not "slow", but unresponsive. There is frequently a lag between when I pull the trigger and when the gun fires. It's one of the reasons I've been favoring Xubuntu but, to be fair, I haven't used Xubuntu 12.04 nearly as much as Unity.

---

### Post by jerrylamos on 2012-04-21
I've been on Ubuntu since Dapper Drake Beta, usually development testing.

For whatever reason Precise has a noticeable lag in desktop response even on my 3.3 GHz 2 GB, with Unity-2D (3D fuzzy foggy out of focus Compiz not for me).  On Ubuntu 10.04 and 10.10 the 3.3 GHz has eye blink response by the time the keystroke hits bottom or the mouse clicks.

My 2005 Thinkpad R31's been running Ubuntu right along, then Lubuntu LXDE for usable desktop response. Now, Precise any flavor won't install bugs written.

So I'm trying Linux Mint LXDE on the R31 - installed like a breeze, nice and fast and responsive for a 1 GHz 512 MB.  I don't have any measurements but I do wonder what's happened to Ubuntu.

Jerry

---

### Post by Mathor on 2012-04-21
> **saneearth said:**
> Not really a complaint, just observation. Graphics programs, picture programs like Geeqiie and others are less responsive to input. I am not a coder and don't have time, so not sure of the specific issues. I am a "tech" for my living so not totally an "idiot". I support Win 7 and XP (still), but at home for years now have primarily been Ubuntu. Been with 12.04 since Alpha and understand it is/was Alpha, but now that we are close to production I am concerned. The reason I have been with Linux and Ubuntu is responsiveness and file transfer. It appears things in Gnome now are starting to "lag". It does not seem to matter whether in Unity Desktop or Gnome, the responsiveness of some of the programs are loosing it just the same. 

There may be an issue of development on some programs not keeping up with Gnome 3, but I really don't know. What I do know is that the real reason that I have been with Linux/Ubuntu/Gnome seems to be getting away. Doesn't matter what Desktop I am using now, things are getting "buggier". Is it just me? I am a Gnome guy primaily, but other desktops seem to have the same or similar issues. Right now I feel I could stay with Gnome 2 forever, but of course I can't. Guess I am just wondering if I am the only one that is having issues. I am wondering if development is leaving behind the programs that most of us use.

If you've been with 12.04 since alpha, it's completely possible you have residual configs and leftover unused kernels etc that are bogging down your system. Clean it up with Synaptic Package manager.

I might also add that 11.10 was very laggy and buggy for me, and that 12.04 has perfected a lot of the issues I had with Unity, speed, and lag. 12.04 runs like  dream for me, and it's probably the fastest system I've ever used. in 11.10 I had to use XFCE to get the speed I want. If I were to run something like XFCE on 12.04 it'd be amazing, but I haven't tried it. Ultimately, 12.04 is great :)

---

### Post by JHCKX on 2012-04-21
Your problems could be due to your graphics card. I had a similar issue upgrading from 9.04 to 10.04.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125)

For _me_, a solution was to install the xorg-edgers ppa, which gives you the newest drivers. That can be risky though, other people experienced crashes.

On this computer, 12.04 running gnome-classic with no effects is just fine, graphics seem smooth and fast (at least as fast as this beast will go, it was never a very good laptop and it's 5 years old by now).

---

