---
title: "Is my server idea plausible?"
date: 2009-12-05
forum: Server Platforms
---

### Post by holastickboy on 2009-12-05
Hi all!

I have a spare computer that I want to use to serve my website to the world wide web.  I want it to run Ubuntu, because I am most familiar with that OS.  Unfortunately, it seems that I might also have to run a few games that dont seem to have Linux servers available, so I might have to install Windows on it.  And here is where I had an idea, and I was wondering if anyone could help me with it.

I was looking to install windows on the machine, and run ubuntu server on a vmware image or something like that.  Is this possible for the machine to run both, and for people to be accessing my web page as well as my servers for the games?  Would the vmware image of ubuntu have its own ip address, or is it an ipaddress that windows would see only?

Does anyone have any other ideas that might help if this just doesnt work?

The machine in question is:

- AMD Athlon X2 4800+
- 4gb ddr800 RAM
- 1tb hdd

---

### Post by volkswagner on 2009-12-05
I would suggest the opposite of what you propose.  Install Ubuntu server, then install a windows VM inside.

Each Virtual Machine you decide to launch will get a dedicated ip address, which you could foward ports from your router.  

You may run into issues if you need to forward the same port 80 to each server/virtual server.  If your windows VM does not need port 80, then you could have your web server on Linux and game server on Win-VM.

There are several VM server software choices, such as KVM, VMware, virtual box, etc.

---

### Post by holastickboy on 2009-12-05
thanks for the reply volkswagner!  That's a good idea indeed!  Do you think that running processor intensive things like a game server would still run nicely within a virtual environment?  I might have other ideas for it too, like media streaming etc

---

### Post by brettg on 2009-12-05
In my experience, most "game servers" are text console apps, making them perfect for running in wine. You might like to try that before you bother adding all the extra bloat of running a virtual server host plus full copy of windows with gui just to run a console based app.

If that doesn't work, then I agree with the previous poster that running windows in a virtual machine would be the preferable option for security reasons alone.

---

### Post by Jekshadow on 2009-12-05
> **holastickboy said:**
> thanks for the reply volkswagner!  That's a good idea indeed!  Do you think that running processor intensive things like a game server would still run nicely within a virtual environment?  I might have other ideas for it too, like media streaming etc

I recommend a server that supports hardware virtualization, and then using KVM. Also make sure to give the guest enough RAM (1.5-2.0GB is normally good). If it has enough ram and supports it through the hardware, it should run nicely.

---

### Post by holastickboy on 2009-12-05
I suppose I could use something like esxi as a hypervisor and install ubuntu and windows side by side?

---

### Post by Jekshadow on 2009-12-05
> **holastickboy said:**
> I suppose I could use something like esxi as a hypervisor and install ubuntu and windows side by side?

I would go with Xen.

---

### Post by brettg on 2009-12-05
I've been experimenting lately with different hypervisors. I started out wanting to install a type 1 "bare metal" hypervisor on my home server which is based on an Atom 330 dual core + HT *

I started with ESXi. I found that ESXi *only* supports two types of LAN adaptors. An intel one and a broadcom one (if I recall correctly). It won't even install if one of them is not present. The single PCI slot in my server holds a raid adaptor and the onboard adaptor was a realtek so that ruled out ESXi

I looked at KVM, but the Atom doesn't have VT extensions which KVM requires. So KVM is out too.

I even looked at MS hyper-V. Same problem as KVM, VT is required.

Initially, I intended to take a look at XEN. Xen does paravirtualisation (works without VT extensions) as does vmware server.

There is some debate as to whether XEN is a type 1 or type 2 hypervisor. It claims to be a type 1, but apparently you have to install it on linux, so I couldn't really get my head around that. 

In the end I figured that I am already well versed in vmware server so if I was going to go type 2 I'd stick with what I know so now I'm back to running that.

Oh well

* Yes, you read that correctly, I am indeed running virtual machines on a lowly atom. I currently have 4 servers running, one as a virtual firewall, one as a torrent client, one running amanda for backups and the other to do everything else. I'm gonna try building a LDAP server on that one.

Granted, each server has low utilisation (home server, duh) and can run perfectly well in 128Mb RAM. In fact all the above services were previously running in "native" mode on the same machine with worse performance. I think sticking the firewall and torrent apps on different "machines" has had something to do with that.

---

### Post by windependence on 2009-12-06
Well you're really not running any type of real world situation. I love the ATom systems and run them as workstations, firewalls, etc, but really, you should grab an old server, even if it's a PIII for what you want to do. I have some here I'd GIVE you if you cover shipping. :-)

The way to do this is bare metal VMs on decent hardware with a good amount of RAM. ESXi actually does support more than you have experienced. I rarely have problems with NIC cards, but more so with storage. Just remember, ESXi 4 only installs on 64 but hardware.

-Tim

---

### Post by brettg on 2009-12-06
Dude, I am running a home server. I wasn't *recommending* that the OP should buy an Atom as a commercial web server and I'm not sure how you came to that conclusion. I merely described *my* situation and what I'd found. I even put my atom reference as an addendum by using the asterisk (*)

I like the atom because I can run it 24/7 and it uses ~8W per hour. Your P3 would be no faster and use a lot more power. Also, your P3 doesn't have multiple cores or even HT, which is important for virtual hosts. The atom has 2 cores and HT, it performs quite well in the scenario I'm running and runs cool and quiet. I have the OS booting off an 8Gb Compact Flash card and storage on WD "green" drives. I have 4Tb in 4 drives and the machine is virtually silent. Compare that to the Athlon64 machine I had before that which sounded like a 747 and I am very happy. 

As for ESXi supporting "much more" that is simply not true. If you don't have NICs based on one of the few chip families it supports it simply wont install. Chip families that it does not support includes 3Com and Realtek amongst others. Not sure about netgear and davicom, but I sincerely doubt they are supported either.

---

