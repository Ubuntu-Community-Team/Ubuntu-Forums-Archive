---
title: "HTTP server in virtual machine"
date: 2009-05-21
forum: Server Platforms
---

### Post by timbim on 2009-05-21
Sorry if this is in the wrong place, but I'm not quite sure where to put it, and sorry if this seems a little silly, but I've not got any experience with this sort of thing.

I want to set up an internal HTTP server to test websites with PHP and maybe other scripting, as I work on them.  To do this, I was thinking of running ubuntu server edition on a VM provided by VirtualBox on a desktop that's normally on.  I don't want it running on my laptop as I don't think it's up to the task, and I want to run it in a VM to keep it separate from the rest of this desktop so that I can easily remove all traces if it turns out to adversely affect performance.

What does anyone think of this idea, does anyone think that it will work at all, any easier ways I may have missed, and any advice as to how to get this to work will be greatly appreciated.  Also, do you think that Ubuntu server is the right platform to be using?

Many thanks,
Tim

---

### Post by stefangr1 on 2009-05-21
This is a great idea. Not only for testing: a lot of servers are virtualized nowadays.

I believe the server installer cd even has an option to do a special minimal install for virtual machines.

---

### Post by apel_2804 on 2009-05-21
It really is a good idea, ubuntu server will work fine in a virtual box environment. You may want to use bridged networking to get easy access to your webserver.

---

### Post by BkkBonanza on 2009-05-21
This is the smart way that most web developers work nowadays. Instead of building a dev machine they just run a VM server and bring it up when working and shut it down when not. I've been doing it this way using VirtualBox for a few years and it does work very well. 

There a several network modes available and bridged mode is likely the easiest to use for this as long as you have a router connected. If not then you would be better off with "host only" mode. The default NAT mode will work but you have to configure some port forwarding in the host. And to make testing the sites easy on port 80 (due to it being a privelaged port) you need some port redirection too. 

I have also configured the guest server with two virtual network adapters, one in nat mode for easy internet access (from the server), and one in host only for local (same machine) testing of served sites. This works well but you need make sure both interfaces are setup in /etc/network/interfaces.

If you're concerned about server load and resource usage then install nginx instead of apache. It is very good, will work fine in most situations and uses a fraction of the RAM/CPU of apache. And it's easier to config and use. I run Ubuntu 8.04 (jeos) with nginx, mysql, php and tinydns as a dev platform in both 128MB an 256MB VMs and it works very, very well. Nginx is well worth getting to know - despite everyone and their brother using apache.

---

### Post by timbim on 2009-05-22
I only want to test internally from a different machine.  I'm not really up to speed on bridged mode etc, could someone explain a little bit?

Also, is Ubuntu server less load than say a BSD release or Debian?  The computer it'll be running on is an XP rig with 2GB ram and an athlon 2.3GHz processor running outlook, firefox and quickbooks and really not much else, so do you think that Ubuntu would be the wisest choice?

Thanks

---

### Post by apel_2804 on 2009-05-22
In bridged mode your virtual maschine share the same nic/network as your host server. So if you have a router running with dhcp the virtual maschine will be connectable from all systems in that network.

In my personal opinion, a minimal installation of debian will be the smartest way. If you install debian with the help of the minimal net-install image and don't install the dektop e.g. you have a system with a minimal footprint.

---

### Post by timbim on 2009-05-22
Right, so bridged mode is a setting inside virtualbox?  I've got DHCP on in my router, and I know the IP of the computer that will have the VM on it, is there anything else I need to set up in the router?  Also, I've already got a copy of the ubuntu server CD, so I'd prefer to use that if it won't affect performance too much, so do you think that ubuntu server will be much slower?  Another reason I'm leaning towards ubuntu server is the wonderful support that there is here for it!

---

### Post by windependence on 2009-05-22
> **timbim said:**
> I only want to test internally from a different machine.  I'm not really up to speed on bridged mode etc, could someone explain a little bit?

Also, is Ubuntu server less load than say a BSD release or Debian?  The computer it'll be running on is an XP rig with 2GB ram and an athlon 2.3GHz processor running outlook, firefox and quickbooks and really not much else, so do you think that Ubuntu would be the wisest choice?

Thanks

I run ALL my production and dev servers in VMs. When we create a new web server, we make an exact copy of it (which is easy with a VM) and that becomes the "staging" machine. All patches or new dev work is tested on the staging machine before being pushed to the prod box. 

OK this is just my opinion but I also run all my web servers on BSD because it's wayyyy smaller, much more efficient and simpler than any Linux distro out there. Take a look at netcraft.com and see what people run on. Not too many Linux or Windoze. Usually some form of Unix. It just works.

One comment though. Don't run your VMs on Windoze, run them the other way around or better yet, don't even run a host OS, run them on bare metal with something like ESXi (VMware) it's free and I think being a n00b, you are going to find setting up a network MUCH easier than Virtual Box or KVM. ESXi has a nice web interface where you can set up virtual switches, etc visually in the GUI from your laptop. I call it "data center in a box". I do not work for VMware, I'm just a consultant and i am a VMware partner, but I have used most of the solutions out there and VMware is the most mature of them all and it just works. If you wanna see the setup, I can post some screen shots.

-Tim

---

### Post by timbim on 2009-05-22
I'd like to run a dedicated server, but I can't.  I have to run it as a VM under windows, as the only computer I can run it on has to run windows, and has to be running windows all the time and only occasionally does it need to run as a server.  Is VMware free?  That is a requirement for me, as I need a free system. (I'm only doing this as a hobby, I can't afford to spend any money on it)  Also, how much better is VMware than virtualbox?

Looking at freeBSD, would I want the AMD64 edition, seeing as the system is an AMD X64 2.41GHz Athlon dual core system, or does the use of a VM effect that?

Which BSD release would you suggest using in that case?

Many thanks, and sorry for asking so much,
Tim

---

### Post by windependence on 2009-05-22
Well I was suggesting you convert your Windoze box to a VM and run that on the VMware bare metal hypervisor. That way, you can do whatever you want with the server. VMware has a free tool called VMware Converter that will convert physical boxes into VMs. Then, you load the VMware hypervisor on your box (no OS) and load your Windoze VM that you converted on that machine. It will be exactly as you ran it before, but probably faster. 

VMware is not necessarily "better", just more mature technology, and for you, MUCH easier to configure networking and other things with no experience with virtualization. Yes, VMware has two free products. One is VMware Server. This one runs on top of another OS and would run fine on your Windoze box. The other is ESXi, which runs right on the hardware with no OS required. It is much faster and takes less resources than a hypervisor that runs on top of another OS, plus it removes one more layer of complexity. It can even be run off a flash drive as the footprint is only about 32 MB.

For BSDm you can always be sure the latest "release" version will be fine. 7.1 is current now and runs great. You will find it will use so much less resources than a Linux distro because typically Linux distros include a whole bunch of crap you don't really need. I run either FreeBSD or OpenBSD and do a minimal install which includes basically nothing, and then custom build in exactly what I need and nothing more. You can get much more info at daemonforums.com

-Tim

---

### Post by timbim on 2009-05-22
I'd rather leave the Windows box as it is for the moment, as I won't always be around to make sure that the box is working properly, and the box is business critical.  So you think that the VMware server would be a better and easier choice than virtualbox?  I'll have a look now.  Does it have the option like virtualbox to load an iso image straight into it without having to burn it and use the CD drive?

---

### Post by windependence on 2009-05-22
Certainly. You can load it either way. ESXi would let you load it - from your laptop's CD - cool eh?

-Tim

---

### Post by timbim on 2009-05-22
Hmm.  I'll look into VMware server, but I think using Ubuntu server to have the brilliant support there is here.  Also, which server functions/packages will I want to be installing?  To start with, I'm looking at dealing with http, php and javascript.

---

### Post by timbim on 2009-05-24
OK, I've decided to go with Ubuntu server edition 8.04 and VirtualBox, as it seems to work fairly easily, and has a simple interface.  I'm following [this]("http://www.howtoforge.com/perfect-server-ubuntu8.04-lts") guide to getting it set up, I'm wondering if you guys have any comments on it.  Also, with the network setup stage on page 3, if any of those IP's are the same as anything else (I'm thinking mainly of the gateway one, that's the same IP as my router) will it matter? Also, what do each of those IP's do?

Many thanks,
Tim

---

