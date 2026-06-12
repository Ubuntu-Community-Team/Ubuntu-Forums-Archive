---
title: "Need Help installing Xen on Jaunty"
date: 2009-09-07
forum: Virtualisation
---

### Post by gk_manutd on 2009-09-07
Hi Guys...

This is my first post in an Ubuntu Forum... I just registered.. 

I've just begun to understand & appreciate how great Linux is... I'd been a Windows user all my life... The thing is.... since I'm a novice... I can't quite manage to understand how I would have to go about installing XEN on Jaunty...


I looked and looked online... I found SOME stuff... nothing concrete...

I ended up installing:

1)  the ubuntu-xen-server using Synaptic
2) I downloaded & installed:  linux-image-2.6.26-2-xen-686_2.6.26-15lenny2_i386.deb

I followed guidelines from a (on hindsight) questionable blog-post.

What do I do now.... Could one of you please guide me as to how I might go about installing Xen on Jaunty?  A step-by-step guideline would be welcome (I repeat- I'm a complete novice!)  :confused:

I'd really love to be able to experiment with the likes of Fedora on XEN (I don't want to leave Ubuntu... I LOVE it!!!)


I know that OTHER tools such as Virtualbox exist... but I need to install Xen... 

Please do help...

Thanks a lot guys!

---

### Post by bogdan.veringioiu on 2009-09-07
Hi.

I don't have much experience with xen myself, but found this:
[http://www.howtoforge.com/high-performance-xen-on-ubuntu-8.04-amd64](http://www.howtoforge.com/high-performance-xen-on-ubuntu-8.04-amd64)

The article is for hardy server.
Maybe it helps.
Cheers.

---

### Post by joel_ezekiel on 2009-09-07
[http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html](http://www.infohit.net/blog/post/running-xen-on-ubuntu-intrepid-and-jaunty.html)

that will get you exactly what you want, few links on there as well for installing domU's etc.

but i seriously suggest, if you really want to play with xen to start with CentOS or OpenSUSE, as they both support Xen out of the box.

see this thread for some more information on what ive done
[http://ubuntuforums.org/showthread.php?t=911576](http://ubuntuforums.org/showthread.php?t=911576)

---

### Post by xOrphenochx on 2009-09-08
Hate to say it, but Amen to CentOS. I had wasted more than enough hours on trying to do what you did per all the documentation I could find, and no luck. Most of the time it would just constantly reboot.

---

### Post by joel_ezekiel on 2009-09-08
yeah its been rock solid for me
at the moment the only ubuntu install im using is xbmc live disk in my htpc :D

i couldnt get it installed as a domu which i wanted to use so i could easily get sabnzbd running, fedora i cant even remember why that didnt turn out as planned... im sure i wrote it in the other thread :D and centos as domu manually installing sabnzbd+ and all the tools it needs is working spot on... i remember now, sabnzbd+ dont support python 2.6 yet.

anyway i supose thats what you get with enterprise linux clone, i was using 8.04 for a while as dom0, now i think about it, its probably a good alternative, should be stable uses the same kernel but a later xen version, vant remember if libvirt worked properly though.

---

