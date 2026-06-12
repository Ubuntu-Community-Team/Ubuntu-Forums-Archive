---
title: "KVM limits"
date: 2009-07-21
forum: Virtualisation
---

### Post by abraham.varricatt on 2009-07-21
I don't mean to be rude, but can someone help me out with these questions I have about KVM on Ubuntu 8.04 LTS ? ( I tried the IRC, but I don't think any activity is going on there now... :( )

1. Is there any upper limit on the number of virtual machines I can run on a server ?

2. I have a server with 8GB RAM. So does this mean that the total RAM I allocate to my virtual systems should not exceed 8GB ?

3. What is the minimum amount of spare RAM I need to leave for the server to function? (On a 512MB desktop, I could not run a virtual 256MB RAM system)

4. When configuring hard-disk space for the virtual systems, is it better to refer to an actual partition on my drive, or am I better off creating a big file? ( And which might be more easier to backup ?)

Thank you for reading my questions.

---

### Post by xOrphenochx on 2009-07-21
> **abraham.varricatt said:**
> I don't mean to be rude, but can someone help me out with these questions I have about KVM on Ubuntu 8.04 LTS ? ( I tried the IRC, but I don't think any activity is going on there now... :( )

1. Is there any upper limit on the number of virtual machines I can run on a server ?

2. I have a server with 8GB RAM. So does this mean that the total RAM I allocate to my virtual systems should not exceed 8GB ?

3. What is the minimum amount of spare RAM I need to leave for the server to function? (On a 512MB desktop, I could not run a virtual 256MB RAM system)

4. When configuring hard-disk space for the virtual systems, is it better to refer to an actual partition on my drive, or am I better off creating a big file? ( And which might be more easier to backup ?)

Thank you for reading my questions.

I have not been using it for that long, but it's not that hard compared to other systems.

1. I assume no, I have seen people with dozens of machines.

2. Yes, unlike some of the other virtualization servers, it seems to allocate it all from the start, so I would suggest not using more than 7gb of your 8 for the machines.

3. I'd say use your best judgement, if you're doing this all through ssh/shell, go with something like 1gb to 512mb if nothing else is being used on the computer.

4. Good question, I have not tried using a seperate partition yet. I personally think its easier to manage them as files on the host's filesystem.

---

### Post by abraham.varricatt on 2009-07-21
Thank you [xOrphenochx]("http://ubuntuforums.org/member.php?u=82800").

It's good to know that there is no upper limit on the number of virtual systems I can have. :)

About usage, I'm not really sure how high/low it will go, so to be on the safer side, I'll reserve 1GB for my host-OS.

I've been looking around the web, and while I've not seen solid benchmarks, from comments here and there, it seems that the benefits of running the client systems on a dedicated partition are not large enough to overcome the ease of management if they were in a file. And also, to my understanding, if they are stored in a file, its more easier to re-size them.

---

### Post by xOrphenochx on 2009-07-21
> **abraham.varricatt said:**
> Thank you [xOrphenochx]("http://ubuntuforums.org/member.php?u=82800").

It's good to know that there is no upper limit on the number of virtual systems I can have. :)

About usage, I'm not really sure how high/low it will go, so to be on the safer side, I'll reserve 1GB for my host-OS.

I've been looking around the web, and while I've not seen solid benchmarks, from comments here and there, it seems that the benefits of running the client systems on a dedicated partition are not large enough to overcome the ease of management if they were in a file. And also, to my understanding, if they are stored in a file, its more easier to re-size them.

Yeah, I haven't done any real testing, but I did install Server 2008 in under 15min last night for the first time, I did it twice to make sure(also building a domain/exchange environment). I know that VMWare server 2 took about 30min or so last time I remember.

---

### Post by bodhi.zazen on 2009-07-21
xOrphenochx answered your questions quite well.

I will make a small suggestion - OpenVZ.

Minimal ram usage depends on what you aer going to do with the guest. I can run a reverse proxy in openvz with less then 10 mB RAM.

With KVM , for most things, 128 would be bare bones. Boot a minimal system and run :

```
free -m
```

---

### Post by abraham.varricatt on 2009-07-22
bodhi.zazen,

Thank you for your input.  OpenVZ is new to me. (I surprised that I didn't hear of it before) and I've spent a lot of time analyzing it.

I'm in a chicken-and-egg situation here. I need to pick a virtualization option, but I don't have any experience to select one! In this event, I think I'll stick with KVM. Not because I think it's better, but,

1. There seem to be more people using KVM , IMO
2. KVM has a front-end GUI interface that can be installed on another system.

The tilting point for me is the GUI thing. I'm not going to install a GUI on my server, but as I'm relatively new to this, I think I'll stick with something that has a graphical interface.

EDIT:
PS - Before anyone gets the wrong idea, I'm perfectly comfortable installing apache and configuring a subversion repository on it from the bash shell with vim.

---

### Post by bodhi.zazen on 2009-07-22
Take a look at something like proxmox. 

Debian host
OpenVZ + KVM (you can use both together).
Web (GUI) interface to manage guests.
VNC into both OpenVZ and KVM guests via a Java panel.

[http://www.montanalinux.org/proxmox-ve-review.html](http://www.montanalinux.org/proxmox-ve-review.html)
[http://www.linux-mag.com/id/7333](http://www.linux-mag.com/id/7333)

There are other web interfaces as well.

---

### Post by abraham.varricatt on 2009-07-23
proxmox looks good. Their web-based interface looks easy to use and it's the kind of thing that fits my needs. Almost.

What is a concern for me is the project maintainer. I have better confidence in Canonical than Proxmox Server Solutions for updates. Thus, I have a HIGH preference to use ubuntu as the host-OS in my virtual setup.

I did a LOT of searching and studying about running KVM or Xen on Ubuntu. And I decided on KVM, due to withdrawal of support from Ubuntu.

OpenVZ is something that I still haven't got my head around to. I *think* I understand what KVM does (virtualization), but how is that different from OpenVZ's containers? Initial looks, they both look alike to me. :confused:

EDIT/UPDATE:
Ahh! I get it now !! With OpenVZ the virtualization is happening at the kernel level and not on the hardware side. Hmm... explains what everyone was talking about containers for. Now, in my opinion, doesn't that impose a constraint? It sounds similar to para-virtualization where the guest OS needs to be aware that it is virtualized. Or in this case, we need to tell everyone that we have a common kernel. Basically, there must be 2 limitations to using OpenVZ,

1. The distro we use will need to be customized for the environment. I can't see how we could use Fedora,Mandrake,CentOS,Ubuntu ISO's un-modified with this.
2. I'm limited to Linux OS's.

Now, I can be wrong with my first point, but for the purposes of this thread, the second point is vital. I don't plan to be virtualizing Windows any time soon, but if we need to, I'd rather not remove the option. 

So, it's KVM for me!

And bodhi.zazen, thanks a LOT! I may not be implementing any of your suggestions, but I do know a lot more about the landscape now. :D

---

### Post by bodhi.zazen on 2009-07-23
Awesome, no OpenVZ will not do windows.

And Proxmox is updated regularly.

---

