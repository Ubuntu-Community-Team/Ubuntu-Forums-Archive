---
title: "Ubuntu Server + workstation"
date: 2016-12-06
forum: Server Platforms
---

### Post by kc_2 on 2016-12-06
I installed Ubuntu Server, during install I selected all of the available server-type applications (it was just a handful but I went with all of them anyway).

Currently, with the default/stock install, no changes made yet, when I turn the computer on, it looks like it auto loads the server components, even if I don't log in, which is great if it does that.

I would like to also use the computer as a personal desktop/workstation, however, I do not want anything to auto-load except the server components.

I'm guessing the next thing to do then would be to install a GUI and workstation-type applications. Any recommendations on what GUI and what apps to use?

This is for general computer purposes. Also, I want to make sure absolutely nothing loads except server stuff when I power on, log in, or even when I manually load the GUI, until I manually load any additional services/apps beyond that point.

I will also use it for server virtualization and software development. I don't want the dev stuff to auto-load, only manual, when I want to use it. Although, I will eventually want to use the virtualization features as an auto-load add-on to the main server system itself.

---

### Post by Jeroen_Mathon on 2016-12-06
Hey kc_2,

I my self recommend a light desktop environment like lxde or xfce, if you don't want much overhead.

Above all i would recommend offloading the server side tasks to a bare metal or virtual machine.
And keeping your desktop and development activities on a dedicated machine.

Some times server software will interfere with your development tasks(Occupied ports).

What you can also do is invest in a powerful machine to put KVM(Visualization) on and make a virtual machine for your server, and one for your personal tasks.

It's all up to your budget.

As a final advice i would not install all server components.
But instead evaluate what you really need to eliminate unneeded overhead, and conflicts between software.

---

### Post by dudumomo on 2016-12-06
Best is of course to install exactly what you need and keep the rest for later.

For the interface, you could install the interface you want (Gnome is okay too) and ensure it won't start at the beginning. (Yet the installation might add quite some libraries..., a light version like fluxbox,... might limit the number of lib).
Then, to start the interface, you will need to run: startx

So the best for you is first to decide which GUI you want, the rest will follows.

---

### Post by Jeroen_Mathon on 2016-12-06
I agree with Dudumomo,

Follow the Arch Linux philosophy.

> **dudumomo said:**
> Best is of course to install exactly what you need and keep the rest for later.

For the interface, you could install the interface you want (Gnome is okay too) and ensure it won't start at the beginning. (Yet the installation might add quite some libraries..., a light version like fluxbox,... might limit the number of lib).
Then, to start the interface, you will need to run: startx

So the best for you is first to decide which GUI you want, the rest will follows.

---

### Post by kc_2 on 2016-12-06
> **Jeroen_Mathon said:**
> Hey kc_2,

I my self recommend a light desktop environment like lxde or xfce, if you don't want much overhead.

Good idea. I'm a big fan of fluxbox, I'll go for that.

> Above all i would recommend offloading the server side tasks to a bare metal or virtual machine.

I was wondering about that, if the server tasks should be... oh wait do you mean put server tasks on a completely different computer? I will need to do all of it on the one computer. Or do you mean running server tasks on the VMs instead of putting any of them on their host machine?

> And keeping your desktop and development activities on a dedicated machine.

That will eventually be the case, when I can budget in getting more physical computers, but have to maximize potential with the single physical machine for now.

> Some times server software will interfere with your development tasks(Occupied ports).

Maybe I can spin up a dev VM/instance for development tasks.

> What you can also do is invest in a powerful machine to put KVM(Visualization) on and make a virtual machine for your server, and one for your personal tasks.

Eventually, something like that would be great.

> It's all up to your budget.

Yeah that's the only thing really holding me back, so I'm aiming to make the most out of what I have.

> As a final advice i would not install all server components.

Yeah, a weee bit too late for that, at least with the base Ubuntu Server install, I selected all the options. lol I haven't done anything with the computer yet, just install the system. I might just give it a completely fresh start and reinstall (this time with an actual internet connection). The initial install was so amazingly fast I couldn't believe it. Maybe a minute. I've never experienced an OS install so fast. (Same with a Windows 10 Pro install on an extra drive.)

> But instead evaluate what you really need to eliminate unneeded overhead, and conflicts between software.

Great idea. I'll just add what I need one piece at a time, would need to determine exactly what I'll need of course.

> **dudumomo said:**
> Best is of course to install exactly what you need and keep the rest for later.

Yep, great idea. I'm going to start fresh and do that.

> For the interface, you could install the interface you want (Gnome is okay too) and ensure it won't start at the beginning. (Yet the installation might add quite some libraries..., a light version like fluxbox,... might limit the number of lib).

Good thinking, I'm a huge fan of fluxbox. :) I enjoy customizing the menus, actually I had saved a backup of a good one at one point, might be able to dig that back up again, or might just start fresh.

> Then, to start the interface, you will need to run: startx

I want to make sure the GUI won't load at boot or login.

> So the best for you is first to decide which GUI you want, the rest will follows.

Yep, Fluxbox. :guitar:

> **Jeroen_Mathon said:**
> I agree with Dudumomo,

Follow the Arch Linux philosophy.

I also agree. I don't want to bloat the machine with unused stuff.

---

### Post by Jeroen_Mathon on 2016-12-07
Hey kc_2,

> I was wondering about that, if the server tasks should be... oh wait do  you mean put server tasks on a completely different computer? I will  need to do all of it on the one computer. Or do you mean running server  tasks on the VMs instead of putting any of them on their host machine?

You could do what i did, and use lxc containers to keep software from interfering,

I have a vostro420 with 4GB ram and 4 cores that runs 8 containers with an IRC server, Data / seedbox, Gentoo desktop(Sharing the kernel from the host), My personal server and a Database server.

All connected trough UFW and iptables DNAT's(Tho i am still trying to figure out how to make them talk to eachother)

In short: you don't really need powerful hardware to achieve what you want. You just need to think out of the box and go unconventional.

Try researching technologies like: UFW and lxc(NOT DOCKER!)

And later when you have the metal you can move everything to KVM.

The only downside of containers is that you will have to route ports to other ports because i was limited(For lacking knowledge on bridging interfaces) to 1 ip.

This is what the forwarding part of my /etc/ufw/before.rules file looks like:
```
# LXC forward
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

#[Main container routing]
# Redirect incoming traffic to containers
-A PREROUTING -i enp3s0 -p tcp --dport 2222 -j DNAT --to 10.0.3.10:22
#-A PREROUTING -i enp3s0 -p tcp --dport 2221 -j DNAT --to 10.0.3.10:21
-A PREROUTING -i enp3s0 -p tcp --dport 2322 -j DNAT --to 10.0.3.11:22
-A PREROUTING -i enp3s0 -p tcp --dport 2422 -j DNAT --to 10.0.3.12:22
-A PREROUTING -i enp3s0 -p tcp --dport 6697 -j DNAT --to 10.0.3.12:6697
-A PREROUTING -i enp3s0 -p tcp --dport 2622 -j DNAT --to 10.0.3.20:22
-A PREROUTING -i enp3s0 -p tcp --dport 80 -j DNAT --to 10.0.3.20:80
-A PREROUTING -i enp3s0 -p tcp --dport 33101 -j DNAT --to 10.0.3.10:33101
-A PREROUTING -i enp3s0 -p tcp --dport 443 -j DNAT --to 10.0.3.20:443
-A PREROUTING -i enp3s0 -p tcp --dport 2722 -j DNAT --to 10.0.3.15:22
-A PREROUTING -i enp3s0 -p tcp --dport 3306 -j DNAT --to 10.0.3.11:3306
-A PREROUTING -i enp3s0 -p tcp --dport 7777 -j DNAT --to 10.0.3.13:7777
-A PREROUTING -i enp3s0 -p tcp --dport 2221 -j DNAT --to 10.0.3.20:22
-A PREROUTING -i enp3s0 -p tcp --dport 1697 -j DNAT --to 10.0.3.17:22

COMMIT
```

That is how i route the ports of my VM's to my main ip.

But i am sure that if you can figure out network bridging in lxc you can avoid this mess.

---

### Post by kc_2 on 2016-12-07
> **Jeroen_Mathon said:**
> You could do what i did, and use lxc containers to keep software from interfering,

What kind of software interference have you had?

Regarding containers, I'm curious about the similarities/differences between lxc & docker.

> I have a vostro420 with 4GB ram and 4 cores that runs 8 containers with an IRC server, Data / seedbox, Gentoo desktop(Sharing the kernel from the host), My personal server and a Database server.

A little confused about your mention of the gentoo container sharing the kernel, do they all share the host kernel, even if technically some run their own?

Containers are lightweight, it's a good approach to running more systems on a single physical. I'm still learning more about all of that, but will probably end up going that route.

> All connected trough UFW and iptables DNAT's(Tho i am still trying to figure out how to make them talk to eachother)

Maybe static snat & full nat will do the trick (to talk to each other).

> In short: you don't really need powerful hardware to achieve what you want. You just need to think out of the box and go unconventional.

Or a powerful box **and** think outside the box. :D

> Try researching technologies like: UFW and lxc(NOT DOCKER!)

Docker's going to be included, even if I just use it short-term before moving on to lxc, or heck I might use a bit of both at first, then stick with one.

UFW's basically debian/etc.'s version (and a little fancier) of rhel's firewalld. A lot of that stuff tends to fall back to iptables. I have an OpenStack setup (not running one, although want to eventually, this is a paid service I use) and I'm just using iptables (with rhel/centos).

> And later when you have the metal you can move everything to KVM.

I wonder if there's a checklist or HowTo step-by-step on building an IaaS from scratch out there somewhere. There probably is, or it would be fairly simple to throw together.

> The only downside of containers is that you will have to route ports to other ports because i was limited(For lacking knowledge on bridging interfaces) to 1 ip.

Yeah, there's no way around that without basically running a business that can drop the cash on a corporate-level network.

> This is what the forwarding part of my /etc/ufw/before.rules file looks like:
```
# LXC forward
*nat
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]

#[Main container routing]
# Redirect incoming traffic to containers
-A PREROUTING -i enp3s0 -p tcp --dport 2222 -j DNAT --to 10.0.3.10:22
#-A PREROUTING -i enp3s0 -p tcp --dport 2221 -j DNAT --to 10.0.3.10:21
-A PREROUTING -i enp3s0 -p tcp --dport 2322 -j DNAT --to 10.0.3.11:22
-A PREROUTING -i enp3s0 -p tcp --dport 2422 -j DNAT --to 10.0.3.12:22
-A PREROUTING -i enp3s0 -p tcp --dport 6697 -j DNAT --to 10.0.3.12:6697
-A PREROUTING -i enp3s0 -p tcp --dport 2622 -j DNAT --to 10.0.3.20:22
-A PREROUTING -i enp3s0 -p tcp --dport 80 -j DNAT --to 10.0.3.20:80
-A PREROUTING -i enp3s0 -p tcp --dport 33101 -j DNAT --to 10.0.3.10:33101
-A PREROUTING -i enp3s0 -p tcp --dport 443 -j DNAT --to 10.0.3.20:443
-A PREROUTING -i enp3s0 -p tcp --dport 2722 -j DNAT --to 10.0.3.15:22
-A PREROUTING -i enp3s0 -p tcp --dport 3306 -j DNAT --to 10.0.3.11:3306
-A PREROUTING -i enp3s0 -p tcp --dport 7777 -j DNAT --to 10.0.3.13:7777
-A PREROUTING -i enp3s0 -p tcp --dport 2221 -j DNAT --to 10.0.3.20:22
-A PREROUTING -i enp3s0 -p tcp --dport 1697 -j DNAT --to 10.0.3.17:22

COMMIT
```

Looks like that goes along with:
[https://www.flockport.com/lxc-networking-guide/](https://www.flockport.com/lxc-networking-guide/)

Although there's also this:
[https://wiki.debian.org/LXC/SimpleBridge](https://wiki.debian.org/LXC/SimpleBridge)

> That is how i route the ports of my VM's to my main ip.

But i am sure that if you can figure out network bridging in lxc you can avoid this mess.

I'm going to need to find or figure out a basic outline of all the steps before proceeding, from what to do and how, after the base (ubuntu server) installation, to completion of the IaaS.

---

### Post by Jeroen_Mathon on 2016-12-07
> Regarding containers, I'm curious about the similarities/differences between lxc & docker.
docker uses lxc as its base.
So i advice using lxc because it offers more functionality than docker.

Docker is more for application development than half visualization.

> A little confused about your mention of the gentoo container sharing the  kernel, do they all share the host kernel, even if technically some run  their own?
All half visualized instances(containers) use the host's kernel.

In a nutshell all a container is is an instance ran in a chrooted environment.
This allows for situations where certain libraries might interfere with each other.
And is also cleaner if you want to clean up junk. and unneeded containers.

> Yeah, there's no way around that without basically running a business that can drop the cash on a corporate-level network.

I am sure that you can achieve that with iptables and routing on a LAN but i doubt you can easily obtain more WAN ip's without a corporate license.

> I'm going to need to find or figure out a basic outline of all the steps  before proceeding, from what to do and how, after the base (ubuntu  server) installation, to completion of the IaaS.

LXC is really easy, dig into the config files.

My recommendation is that you slam /usr/lxc/ on your data drive. and then symlink or fstab mount it to /usr/lxc.
This will safe space and unneeded disk io.

I have 2 drives 100GB(OS) and 1.7TB(DATA/HOME).

---

### Post by alexjpowell on 2016-12-07
I'd actually virtualise the desktop environment
Or, I'd install gnome-core and VNC into the desktop

---

### Post by Jeroen_Mathon on 2016-12-08
> **alexjpowell said:**
> I'd actually virtualise the desktop environment
Or, I'd install gnome-core and VNC into the desktop

Which is exactly what we have just discussed.
If you read our previous messages you can see we already discussed Full and half Visualization.

---

### Post by kc_2 on 2016-12-08
> **Jeroen_Mathon said:**
> docker uses lxc as its base.
So i advice using lxc because it offers more functionality than docker.

That's a little confusing, it seems like something (docker) that is an extension of a base (lxc) would actually offer more functionality.

> Docker is more for application development than half visualization.

With app dev it could come in handy, I will probably end up using it anyway at some point to get more familiar with the inner workings. Before that, I have vagrant to run for testing purposes, in my dev environment, like testing on dev.mysite.tld, before going staging/sandbox/etc., and prod. Beyond vagrant, I'll give a trial run to each of the container types, get a better idea via hands-on experience. Docker requires a docker hub (basically a repo for the docker images / containers), I'm guessing lxc does too, or something similar. What I like about docker are the cloud computing and cluster computing aspects of it.

> I am sure that you can achieve that with iptables and routing on a LAN but i doubt you can easily obtain more WAN ip's without a corporate license.

Number of IP addresses depends on the provider. As a customer of a company providing OpenStack services, I can request as many networks as I want, it'll just cost more. As a private user setting up a cloud infrastructure, I can request additional IPs from my ISP, but they'll switch it over to a business account and gladly bump up the cost.

> LXC is really easy, dig into the config files.

My recommendation is that you slam /usr/lxc/ on your data drive. and then symlink or fstab mount it to /usr/lxc.
This will safe space and unneeded disk io.

Good to know, I'll try that out.

> I have 2 drives 100GB(OS) and 1.7TB(DATA/HOME).

I'm using 2 OS drives (1 drive/OS), 2 storage drives (raid1), and an external drive (backup).

The OS drives are separate, one's linux, the other's windows (gaming).

This time I'm using a lightweight approach that's not the most stable, but at least plan on still using backups once I get the new system setup.

With the next build, I'll probably do something like, well, build 2 computers or a 2nd and re-purpose this one, and:

Previous computer - re-purpose for gaming only.
Next computer - purpose it for server only.

The dedicated host could then include:
OS drives x2, RAID1 (just the 1 system)
Storage drives x2, RAID0
External backup drives x4, RAID10

I might change up how I do the raid, but will always have the backup process following OS and storage. My backup process is actually a lot more involved than just a single backup drive or environment, it's layered and different formats, different physical locations, etc.

Anyway, so you put lxc on storage. I can do that too.

My current OS drives are SSDs, each 500GB, and storage drives are each 3TB, but instead of 6TB it's only 3TB via RAID1, and since my current build is splitting *that* space between 2 OSs, it gets cut in half again, with 1.5TB storage per OS. Such a wonderful _waste_ of space, lol, but that's fine. I get the only real, singular advantage of using RAID1 (on a budget so I can't get a gazillion drives, and prioritizing that budget for different things), and also have enough to share between the 2 systems. I might end up taking space away from windows and giving more space to linux. It all depends on my particular use cases of each.


> **Jeroen_Mathon said:**
> [QUOTE=alexjpowell;13579931]I'd actually virtualise the desktop environment
Or, I'd install gnome-core and VNC into the desktop
Which is exactly what we have just discussed.
If you read our previous messages you can see we already discussed Full and half Visualization.[/QUOTE]

That is a little confusing, though... virtualize the DE... when I power on my physical machine, I don't have a GUI, so I'd have to have a GUI in the first place, before I could virtualize another one. ...unless there's a way to virtualize one directly from the CLI, skipping the main host's GUI. That sounds weird but would certainly be nice.

I won't install gnome if I can help it. Rather than go the DE route, I'm going to stick with the super light, window manager, and use fluxbox. I went ahead and installed xorg and fluxbox. I'm running into an issue with it right now though, after loading fluxbox I get a mouse pointer stuck in the top left corner of the screen, unable to move it, but can still use the mouse, just with an "invisible" pointer. I love fluxbox, though, so I just need to figure out what's wrong with the mouse pointer.

Anyway, I don't think I'm understanding what you're saying about connecting into the desktop or virtualizing it. I'm getting incomplete info.

Mapping it out simply putting it:

{physical.machine}-->{physical.OS(host(CLI-to-GUI))}-->{virtual.OS(client(CLI)}

What I'd like to do, after I set up the system to run its own virtual infrastructure, is have it set up to auto-load all the virtual instances (multiple nodes networked together) after the physical machine starts up or restarts, but without having to login and without having to load the physical machine's GUI.

At that point, the purpose I will have in the physical machine's GUI will be for personal computing when I don't want to run the cloud lab. ...not to be confused with gaming, the windows system is exclusively for gaming, the linux system is everything else. I just take turns using one or the other, each for different purposes.

---

### Post by Jeroen_Mathon on 2016-12-08
You can use KVM or LXC to visualize and manage from a CLI level. eliminating unneeded overhead.

---

### Post by kc_2 on 2016-12-08
> **Jeroen_Mathon said:**
> You can use KVM or LXC to visualize and manage from a CLI level. eliminating unneeded overhead.

Sounds good. I just found this:
[https://www.sumologic.com/blog-code/lxc-lxd-explaining-linux-containers/](https://www.sumologic.com/blog-code/lxc-lxd-explaining-linux-containers/)

It sounds like LXD (which uses LXC) might be a better route than LXC.

The Docker vs (other) thing, considering the ephemeral nature of docker containers and the more prolonged nature of LXD containers, that in itself could determine which option someone might want to use. Likewise, if someone wants a full system or lightweight system.

For my purposes, I might benefit from both. Some nodes would function with only the purpose of specific services, but that need to be networked into the larger group. Other nodes would have more complete functionality.

Getting back to visualization, it's good to know those work from CLI only.

---

### Post by Jeroen_Mathon on 2016-12-08
> **kc_2 said:**
> 
Getting back to visualization, it's good to know those work from CLI only.

In some cases you have no choice because you can also route the video card directly to a VM.
A colleague at my work is doing that giving VM's direct access to Graphic Cards.

---

### Post by kc_2 on 2016-12-08
> **Jeroen_Mathon said:**
> In some cases you have no choice because you can also route the video card directly to a VM.
A colleague at my work is doing that giving VM's direct access to Graphic Cards.

I have a powerful video card, would love to use it directly with them. How can that be done?

---

### Post by Jeroen_Mathon on 2016-12-08
> **kc_2 said:**
> I have a powerful video card, would love to use it directly with them. How can that be done?

I think that this is what you are looking for [https://wiki.debian.org/VGAPassthrough](https://wiki.debian.org/VGAPassthrough)

---

### Post by kc_2 on 2016-12-08
> **Jeroen_Mathon said:**
> I think that this is what you are looking for [https://wiki.debian.org/VGAPassthrough](https://wiki.debian.org/VGAPassthrough)

Coolthankyou!

This is interesting (watching [https://www.youtube.com/watch?v=90oxad2r8_E](https://www.youtube.com/watch?v=90oxad2r8_E))...

{physical machine + kernel + host OS} + {VM + kernel + host OS + **workload**} = KVM

versus

{physical machine + kernel + host OS} + {**workload**} = LXD

LXD's also a full linux operating system. It can hold docker/etc. containers.

I'm all about removing duplication of components. Don't need redundancy of machine+kernel+os before the app? Then don't use it.

LXD goes straight to init but doesn't have bios, drivers, etc.

The host does more work in this case... where VMs manage things somewhat independently.

I need to pack multiple systems onto the host, and keep it light on what I can, so that the ones that are heavy will have those resources available to them.

That video compares again, showing that LXD can load nearly *15x more systems* than KVM all on 1 host.

Memory comparison, LXD loads more instances with optimal use of memory, while KVM uses fewer and runs out of memory, cutting into swap.

LXD startup time a little over 1 second.

KVM startup time, nearly half a minute.

Latency is similar... KVM's twice that of LXD, remote and local.

And just found this video, more info on LXD: [https://www.youtube.com/watch?v=yEr_EIZG0ZM](https://www.youtube.com/watch?v=yEr_EIZG0ZM)

Edit - Graber really uses LXC more than anything in that video.

Here's another one of his videos on it: [https://www.youtube.com/watch?v=MtEVohQNSFI](https://www.youtube.com/watch?v=MtEVohQNSFI)

---

### Post by Jeroen_Mathon on 2016-12-08
> I'm all about removing duplication of components. Don't need redundancy of machine+kernel+os before the app? Then don't use it.
Then AUFS might be interesting to look into as well, check out this article [https://en.wikipedia.org/wiki/Aufs](https://en.wikipedia.org/wiki/Aufs)

Since you will have a lot of the same configs when having multiple containers you can eliminate the extra space by using this intelligent union filesystem.

---

### Post by kc_2 on 2016-12-09
That is interesting, I went ahead and stuck with the default on ubuntu server install, and opted for ext4 on storage.

I'm currently running into a roadblock with the server+workstation setup... I'm working on setting up the workstation side of it, the mouse isn't properly working in the window manager (xorg/fluxbox). Using another system for normal computer stuff until I get the workstation setup on the new computer.

---

### Post by Jeroen_Mathon on 2016-12-09
> **kc_2 said:**
> That is interesting, I went ahead and stuck with the default on ubuntu server install, and opted for ext4 on storage.

You do not want AUFS as your main FS.
What you want to do is assign a partition for LXC, and turn that into AUFS and then mount it.

---

### Post by kc_2 on 2016-12-09
> **Jeroen_Mathon said:**
> You do not want AUFS as your main FS.
What you want to do is assign a partition for LXC, and turn that into AUFS and then mount it.

For main fs, I'm going to switch storage to xfs but keep ext4 on the system drive.

I thought aufs required both host & client systems but okay, cool, I'll check it out. :)

---

