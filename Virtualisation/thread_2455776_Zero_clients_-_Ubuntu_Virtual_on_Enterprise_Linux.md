---
title: "Zero clients - Ubuntu Virtual on Enterprise Linux"
date: 2020-12-27
forum: Virtualisation
---

### Post by good+not-nice on 2020-12-27
I am not an expert, neither programmer. I have used OpenSuse and Kubuntu for my desktop for many years. Really like Kubuntu.
I am building a home server with zero clients. The question is: 
Should the virtual Ubuntu be a server version in order to connect several zero clients or desktop version will do the job?

Thank you !

---

### Post by TheFu on 2020-12-27
I have no clue what a 'zero client' is.  What is the point of a server that doesn't have any clients?

In general, desktop and server can run all the same network services. There are reasons for each. Setting networking on Ubuntu Server s text config files.  Many default apps/tools that desktops get are not loaded. Also, the included drivers on Desktop are vastly expanded. I don't think Server gets any wifi or bluetooth drivers, for example.

What do you mean by 'virtual ubuntu'?

---

### Post by good+not-nice on 2020-12-27
Zero client is smaller than a thin client. Does not have OS, storage, everything is on the server. Less maintenance. But it is a client, just quieter.
Ubuntu will be installed as virtual OS onto SuSe Linux Enterprise Desktop.

---

### Post by QIII on 2020-12-27
Let's cut the topology down to just the Ubuntu server -- however you have that set up, as a virtual machine on an OpenSUSE machine or not.

When you say you want an Ubuntu server, what exactly is it that you intend for it to do? What is it serving to these ethereal and ephemeral "Zero Clients"?  What do you want to do with them?

---

### Post by good+not-nice on 2020-12-27
The idea is to be a home network with one centralized host and several clients. Less maintenance, saved money for stupid laptops and chromebooks every 1.5 year, hardened security of only one well made linux OS. It definitely includes GPU passthrough for gaming experience.

---

### Post by QIII on 2020-12-28
Centralized host for what? Virtual machines?  Game server?

---

### Post by good+not-nice on 2020-12-28
Yes, game server and individual desktops.

---

### Post by TheFu on 2020-12-28
> **good+not-nice said:**
> Yes, game server and individual desktops.

Don't think what you seek is realistically possible today, unless the games are Solitaire or Sudoku.  The client hardware will be extremely important too. We just aren't there yet outside highly custom solutions like what nVidia + Google make. nVidia is charging fees for their software to connect into their high-end GPUs remotely.

It is a nice dream.

I'd love to use a $40 client and get 120 fps games working from my $70 nVidia GPU running in a VM somewhere on my LAN. That just isn't reality in 2020 or 2021.

---

### Post by rsteinmetz70112 on 2020-12-28
If you have SUSE why do you need Ubuntu? Can't you just run a hypervisor on SUSE?

---

### Post by QIII on 2020-12-28
^This is what I was getting at, but trying to coax you to getting there on your own by asking leading questions.

Having virtual machines within a virtual machine, although certainly possible, is not particularly desirable.  Best to use VMs on physical machines that offer a more reasonable amount of processor and memory resources.

Remember that a VM runs in a software environment that virtualizes the hardware in an abstraction layer.  Software within software is bound to produce less than optimal results.

Just put several VMs in your OpenSUSE host.  There is nothing at all wrong with that -- Ubuntu is not the whole show and even here at the UF we wouldn't tie you to the whipping post for using it!  :)

And to tag on to TheFu -- a consumer-grade gig ethernet home network is simply not going to transmit graphical data between the host and the client machine fast enough to have smooth game play -- even if the client has the best graphics in the world.  You can do pretty well if you do a pass-through when the guest OS is on the same host machine you are in front of, but you really need a second GPU for that because the guest will take full control of the GPU assigned and leave the host with nothing.

---

### Post by TheFu on 2020-12-28
SuSE s a fine distro!  I ran it for a few years and don't remember many issues.  A few guys in my LUG use SuSE today. The do because their employers are SUSE-Enterprise customers.

Well, if the guest VM runs on KVM with SPICE/qxl support, and the LAN performance is reasonable, I'm seeing 200+ fps with glxgears demos using openGL.  My setup is this:
[LIST]
[*]Ryzen 2600 w/ $70 nVidia GPU as kvm server 16.04
[*]GuestVM running 20.04 ubuntu-Mate with qxl + SPICE  
[*]Laptop running 16.04 sng virt-viewer SPICE client. Core i5-8250U/8B RAM.
[*]2 GigE network hops between the client laptop and server VM host using cheap (15 gige switches).  No wifi. No realtek NICs.
[/LIST]

Octane 2.0 in the chromium browser was about 29,700 rnning in this environment.

Physical Server - hadar:
```
$ inxi -z
CPU~Hexa core AMD Ryzen 5 2600 Six-Core (-HT-MCP-) speed/max~1432/3500 MHz Kernel~4.15.0-128-generic x86_64 Up~15 days 
Mem~18557.8/32160.8MB HDD~1012.2GB(61.8% used) Procs~569 Client~Shell inxi~2.2.35  
```

Virtual Machine - regulus:
```
$ inxi -z
CPU: 2x Single Core AMD Opteron 23xx (Gen 3 Class Opteron) (-SMP-) speed: 3493 MHz Kernel: 5.4.0-58-generic x86_64 Up: 10d 7h 21m
Mem: 1453.9/3936.2 MiB (36.9%) Storage: 40.00 GiB (46.1% used) Procs: 176 Shell: bash 5.0.17 inxi: 3.0.38

```
Laptop Client:
```
$ inxi -z
CPU~Quad core Intel Core i5-8250U (-HT-MCP-) speed/max~956/3400 MHz Kernel~4.15.0-128-generic x86_64 Up~6 days 
Mem~3632.3/7863.1MB HDD~564.1GB(15.1% used) Procs~376 Client~Shell inxi~2.2.35
```

I didn't do anything special.  You can see the uptime on each system.

SPICE is the best performing remote desktop that I know, by far.  The connection from the laptop, to the KVM server, that makes the SPICE client/server connection: 
```
    /usr/bin/virt-viewer --connect qemu+ssh://hadar/system regulus &
```
SPICE is not encrypted, however.

[LIST]
[*]Seeing 200-270 fps with glxgears over SPICE.
[*]Using **x2go** as the remote desktop, glxgears runs around 45 fps for comparison.  
[*]Running with **ssh -X glxgears** gets around 32 fps.
[*]Running natively on the laptop, glxgears runs around 60 fps.  
[/LIST]

SPICE is faster than native!  I think that is more abot LLVMPipe in 20.04 than anything else.

SPICE rocks!

Visually, I can't tell the difference for anything over 60 fps.  The laptop runs at: 1920x1080@60.01hz.

---

### Post by Tadaen_Sylvermane on 2020-12-30
I've been messing about with Steam's remote play. I was getting 50fps in World of Warcraft on my living room tv over a regular cat5e network at gigabit. But the client certainly isn't a zero client, i5 3470 + 8gb of ram. It is pxe booted though via LTSP. Even with something like that the client still  matters. Over the same network I have an AM1 Sempron with 2gb of ram, it barely hits 30fps with the same load.

---

### Post by good+not-nice on 2020-12-31
Thank you for the answers and efforts. I am not a passionate gamer. But I definitely believe the project is possible. And the quality of the video will be more than you have described, yes maybe not 200 fps.
The host will have a Teradici 2240 processor card installed and the clients will be about 3-4 with TERA 2321. It is a proven technology in much bigger networks. The PCoIP sends pixels over LAN. It works.

I am going to continue.

---

### Post by TheFu on 2020-12-31
Much of this roundabout could have been avoided by saying - Teradici 2240 processor card and PCoIP with TERA 2321 clients in the first post.

[https://www.teradici.com/web-help/ter1702006/2.8/Content/_common_topics/Requirements/Common/system_reqs_by_env.htm](https://www.teradici.com/web-help/ter1702006/2.8/Content/_common_topics/Requirements/Common/system_reqs_by_env.htm) says 16.04 Ubuntu or RHEL 7.2.  EoL for 16.04 arrives in about 4 months.  I didn't see any other supported OSes.  I thought RHEL 7.2 was EoL years ago. Yep, ended November 30, 2017.  I suppose this is the reason to run Ubuntu inside a VM under SuSE? So much for "more secure."

And from the VMware forums:
> At this time, VMware still plans on supporting PCoIP because our customers still have zero clients in use.  However, we will not be adding any new features in PCoIP for Horizon.  All new features are going to be developed with Blast Extreme.
Thanks Tony
VMware Horizon Product Manager

The only articles I see on this PCoIP stuff is from Teradici and VMware or old from before SPICE being stable.  VMware has left the building.  Teradici doesn't really say "why" to use their stuff and their "how" documentation is old.  A $250-$700 used adapter to support 4 $80-$200/ea clients in a server seems like shifting the costs, processing, towards a non-standard solution with lock in for hardware from 1 company, Teradici on the client and server sides.

Good luck. Of course, if you get it working and document it, we'd love to learn more!  More alternatives are always nice.

People are usually going for r-pi like clients these days, which was where my head initially went.

---

