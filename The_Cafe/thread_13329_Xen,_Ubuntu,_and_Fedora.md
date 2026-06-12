---
title: "Xen, Ubuntu, and Fedora"
date: 2005-01-30
forum: The Cafe
---

### Post by TravisNewman on 2005-01-30
After getting fed up with trying to get Xen (see xen.sourceforge.net for details) on Ubuntu set up the way I want it, I decided to give Fedora a shot, because it's more integrated in the development release of Fedora.

I don't know how it will work, because I haven't had a chance to use it. I'm still waiting on Yum to do dependency checks. It just occured to me that you can use apt in Fedora, and I don't know why I hadn't thought of that yet, but long story short, I'm still waiting, and this is freakin' insane.

Seriously, I have no clue how Yum has made it this long with the wait times the way they are. Apt knows the dependencies almost instantly, but depending on how much you're installing, Yum can take up to 5 minutes.

Also, I had forgotten how disgusting the Bluecurve theme is. Yuck. 

But I'm still getting used to things. I remember Fedora being pretty stable, but I could just never figure out how to do what I wanted to there, hopefully I'll get better.

Note: I am NOT switching, I'm just trying to set up Xen for educational purposes basically. It's something that can be done that I don't know how to do, so I thought I'd learn it.

---

### Post by jdong on 2005-01-30
[QUOTE=panickedthumb]
Seriously, I have no clue how Yum has made it this long with the wait times the way they are. Apt knows the dependencies almost instantly, but depending on how much you're installing, Yum can take up to 5 minutes.

Also, I had forgotten how disgusting the Bluecurve theme is. Yuck. 
Note: I am NOT switching, I'm just trying to set up Xen for educational purposes basically. It's something that can be done that I don't know how to do, so I thought I'd learn it.[/QUOTE]

Funny thing... YUM works fine here. There's a strong, pro-YUM favorament in the Fedora world, so I stick with it. True, it does take slightly longer than APT... I'm pondering a switch.

Bluecurve... Well, I won't comment on its attractiveness. But I will say that it's an awesome concept! For example, whether I run K3b in GNOME or evolution in KDE, I get the same, consistent feel. Ubuntu / Kubuntu needs similar integration for a near future release...

Xen... Once I settle down, I'll give it a shot...

---

### Post by jdong on 2005-01-30
P.S. Fedora tip: To reduce swap-thrashing on sub-768MB-RAM systems, add the following line to /etc/sysctl.conf and REBOOT:

```

vm.swappiness=10

```

---

### Post by TravisNewman on 2005-01-30
[QUOTE=jdong]P.S. Fedora tip: To reduce swap-thrashing on sub-768MB-RAM systems, add the following line to /etc/sysctl.conf and REBOOT:

```

vm.swappiness=10

```[/QUOTE]
 OK be careful when you start installing Xen. For the Fedora custom Xen stuff that integrates so well, you have to be using the development release, from what I gather, and I completely borked Fedora already because it picked up a few dev packages and didn't exactly settle dependencies well.

---

### Post by poofyhairguy on 2005-01-30
[QUOTE=jdong]Funny thing... YUM works fine here. There's a strong, pro-YUM favorament in the Fedora world, so I stick with it. True, it does take slightly longer than APT... I'm pondering a switch.
[/QUOTE]


Apt4rpm is just so much better. Especially for the Repos that are hated by the official ones. Damn. That just reminded me of something I don't miss about Fedora.

I mean.....Yum works....but it is sooooo slow.....like a Fedora reboot.....

---

### Post by jdong on 2005-01-31
[QUOTE=poofyhairguy]Apt4rpm is just so much better. Especially for the Repos that are hated by the official ones. Damn. That just reminded me of something I don't miss about Fedora.

I mean.....Yum works....but it is sooooo slow.....like a Fedora reboot.....[/QUOTE]

Hey, aren't I pulling a FreshRpm/Dag myself? ;)

Yum's too slow. I've switched to APT, too... True, YUM' s an improvement over FC2's, but still not good enough to make me use it on a regular basis.


Fedora reboots.... Perhaps with an AMD64 I don't see speed issues! LOL ;)

---

### Post by piedamaro on 2005-01-31
However apt4rpm is still times slower than apt on debian /ubuntu. Yum is really unusable for me, I've asked at fedoraforum why I should use yum over apt, because I didn't see any advantage. 
The only thing they could say was: "yum is officially supported by fedora".
This sounds to me like: "yum sucks but fedora wants to push it anyway" :D

The single thing on earth slower than yum to fetch updates is => emerge.
I remember the first time it took half an hour to fetch the portage tree.

---

### Post by jdong on 2005-02-01
Actually, because YUM is written in Python, and integrates with Anaconda.

---

### Post by jdong on 2005-02-01
Hey, while you're playing with FC3, enable SELinux Targeted Policies (if it isn't already!), and install Apache + php.

Using a simple PHP "echo `ls -al`" type script, check out how locked down SELinux makes Apache!

Hackers who get in are stranded on little islands of nothing!

---

### Post by TravisNewman on 2005-02-01
I really want to get SELinux and a hardened kernel working really well in Ubuntu. That would make Travis a very happy boy.

I might do that though. I plan on breaking Fedora a few times at least, basically just dabbling with different things and seeing how far I can push them.

---

### Post by jdong on 2005-02-02
It took Redhat 2 fedora releases to come close to perfecting SELinux.... I don't think it'll be a one-man effort to port their work over to Debian/ubuntu...

---

