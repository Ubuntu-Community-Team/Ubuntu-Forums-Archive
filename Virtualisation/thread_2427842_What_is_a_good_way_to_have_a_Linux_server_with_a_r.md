---
title: "What is a good way to have a Linux server with a robust virtual environment?"
date: 2019-09-26
forum: Virtualisation
---

### Post by natiya on 2019-09-26
I'd like to have Linux-based server with a robust virtual platform, same as ESXI is for Windows. The hardware is a HP Server with 16GB of RAM, 1TB of hard drive and Intel XEON 3.7GHz.

[COLOR=#242729][FONT=Arial]The hosts are going to be sending/receiving Internet traffic and running some security applications (firewalls, IPS-intruder prevention systems...). The traffic will be also analyzed by a commercial tool similar to Wireshark.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Based on what I understood, I may consider these options:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]Ubuntu Server + KVM + vSwitch[/FONT]

[*][FONT=inherit]CentOS + KVM + vSwitch[/FONT]

[*][FONT=inherit]CentOS + Xen + vSwitch[/FONT]

[*][FONT=inherit]openSUse + KVM + vSwitch[/FONT]

[*][FONT=inherit]Debian + KVM + vSwitch[/FONT]

[*][FONT=inherit]oVirt?[/FONT]
[/LIST]
[COLOR=#242729][FONT=Arial]What would be the best option for the applications I want to run?[/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2019-09-26
Going about it backwards I think. Do you even need either? Have to build around your plan, not build looking for a plan. Otherwise you end up with either not enough, or more stuff that you don't need.

How many vms?
Will containers work better? An lxd container is far superior to a full vm in hardware use. More per host ultimately. For full vms 16gb of ram isn't a lot tbh.
What will they do?
Do you even need something as intense as OpenVSwitch, or can you just use a network bridge off the main ethernet and put them all on the lan? OpenVSwitch seems like using a 90 pound jackhammer to drive a half inch nail, for home use anyway.

---

### Post by TheFu on 2019-09-26
I've run 20+ "full VMs" on 16GB of RAM. 1 was running Windows. The rest either Debian and Ubuntu Server.  If you avoid Windows, RAM use is much less.

OpenVSwitch is only needed on 10Gbps networks. For 1Gbps networking, normal bridges work fine for much less hassle.

LXD isn't virtualization. It is a container.  That might be important.  Also, Windows can't be run in any Linux container.

I've run most x86/AMD64 hypervisors over the years.  Migrated to KVM around 2010 and have never regretted it.  No comparison with ESX or ESXi, which are too picky about hardware and want $1000 to have a good backup.

But if you are Windows-centric, you should pay for a hypervisor and pay for backups and pay for any other things needed.  Moving to Linux, just for VMs that run Windows is a waste of your expertise and time.  Just write MSFT a check and point-n-click for your happiness.

Don't use latest version.  Servers should always be LTS releases.  18.04 is the current LTS.  Newer releases aren't something any server should run without very good reason, like hardware compatibility.  Non-LTS releases get 9 months of support from the release date. LTS get 5 yrs. LTS get HW refresh updates.  Stability is the primary goal for a server.

Load kvm + libvirt + bridge-utils + ssh + fail2ban on the "server".
Load libvirt + virt-manager + ssh + fail2ban on the "client workstation" you will use to manage all the VMs.
Setup ssh between the client and the server following normal methods which use ssh-keys.
On both the client and the server, put your userid into the libvirt group. This should be automatic, sometimes it doesn't happen.
On the server, setup a linux bridge.  The automatic bridges are NAT.  
On the server, setup any backend storage you like.  File-based will be slower.  Block devices will be faster, but a little harder for a noob to manage.   I use LVM and LVs for each VM.  This has the pluses that LVM has and the performance that block storage provides.  But if you are new to LVM, it is likely too complex for a first attempt.  If you know Veritas Volume and file system, LVM is the same with just slightly different terms.

Beware that some HP servers fail with Ubuntu Server due to non-standard BIOS.  You'll never know if it works until tried.

Hopefully, you know that Linux servers don't have GUIs.

---

### Post by SeijiSensei on 2019-09-26
The virtual machines at [Linode]("https://www.linode.com/") run on KVM. Since that's their business, I consider that a vote in its favor.

---

### Post by natiya on 2019-09-27
Thanks a lot, guys! I added more infomation on my question, you can have a better picture. The security tools can be in the host, the guest or just connected through a network connection

---

### Post by TheFu on 2019-09-27
If you don't list the exact guest OSes and exact programs, nobody can really help.  
IMHO .... 

In general, security tools need to be run directly on hardware in full production. That's because places using those tools generally have so much traffic they need to avoid any overhead. The processing involved is high CPU and high RAM use, which doesn't work nicely on VMs.  

Find a local DefCon group. Go to their meetings. Ask questions. I tend to sit near the IDS/IPS guys, since that is closest to my infrastructure background.

Firewalls MUST be on dedicated devices for security reasons.  Don't lose the beachhead and then lose the war.  Just because something is possible, that doesn't make it a good idea.

openvswitch is overkill.  Avoid if you can.

You are in Ubuntu forums, right?  I haven't touched OpenSUSE since around 2006.  Haven't touched RHEL since before RHEL existed. Ran a RH server for 3-5 yrs around 2000.  Only played with CentOS enough to prepare for RHEL tests.  I've been using Ubuntu Servers as VM hosts since 2008.

oVirt is just RH's combination of F/LOSS tools with a little glue and a webgui.  It is designed for setups with hundreds of VMs and physical servers.

I ran Xen VMs for about 3 yrs in production.  Maintenance issues forced us to move to KVM.   Besides the maintenance/patch issues and VMs refusing to boot, it was stable enough.  Moved to KVM and never had any issues like that again.

---

### Post by kevdog on 2019-09-27
You might want to take a look at xcp-ng which is a bare metal open-source hypervisor.  This is the free open source version of Citrix.  Runs CentOS beneath.  This is well supported with many graphical tools that help manage the VM -- you really don't need to use a lot of command line tools to monitor and configure the VM.  There are a lot of You-Tube videos and resources that are available on the internet.  A guy named Lawrence (this is his forum address: [https://forums.lawrencesystems.com/](https://forums.lawrencesystems.com/)) does really awesome videos on installing xcp-ng and configuring xcp-ng along with Xen Orchestra.  I've virtualized my pfSense Router along with an Ubuntu installation within xcp-ng, and it works really well for home use.  I don't work in the industry so I don't know how well this situation scales however I would guess it scales fairly well since the largest VM providers are either (Linux/KVM, Oracle's ESXi, or Citrix.  One thing I personally like about xcp-ng is the ability to perform delta snapshots for backing up the VM.  I'm not aware of KVM or ESXi having an equivalent type of free backup model.

---

### Post by TheFu on 2019-09-28
> **kevdog said:**
>  One thing I personally like about xcp-ng is the ability to perform delta snapshots for backing up the VM.  I'm not aware of KVM or ESXi having an equivalent type of free backup model.

KVM doesn't force a backup model onto the admin.  It supports whatever model the admin chooses, since backups are more about quiescence of storage and needing any specific hypervisor support.  To that end, KVM allows almost any back-end storage to be used and a few KVM-only storage solutions have been created. 

These only work with KVM.  For example, sheepdog is a replication storage backend for KVM that uses compute nodes for storage as well.  Just configure how many copies/nodes you'd like used for storage of the KVM VMs and that number of block copies will be enforced.  It supports storage failover, so if a node fails, taking storage with it for any reason, the storage isn't pulled out from beneath any users of the storage, provided at least 1 extra copy has been specified.

ZFS - I don't use ZFS for VM storage, so I haven't delved into how well it works with any hypervisor, but I'd be shocked if it wasn't fully supported.  [https://libvirt.org/storage.html](https://libvirt.org/storage.html) - yep, ZFS pools are supported and understood.  Years ago, when BTRFS was new, there were some critical problems with running any hypervisor on BTRFS storage. I think those have been addressed.  The issue was about CoW storage being used with CoW hypervisor settings, I believe.

Xen would support all the same storage methods, IME, except kvm-only solutions like sheepdog pools.

Back to backups - KVM and libvirt understand LVM, so snapshots in the true sense of the word, not like what some other hypervisors claim, are available.  Use LVM to make a snapshot, backup the snapshot using **any** backup tool you like.  Remove the snapshot and those blocks are unfrozen. Any new blocks since that point which replace those in the snapshot are automatically used.  A busy DBMS can keep running the entire time. No interruption. No downtime needed to have consistent backups. No need to dump a DB to get around this issue. The DBMS files and journal-logs are sufficient at restore.

In short, if Linux supports it, then it can be accomplished with kvm as the hypervisor. That's one of the many reasons why having KVM included in the core kernel development is so great.  That and performance.

I should disclose that I ran Xen for about 3 yrs and was a stock holder in the company.  When Amazon moved to KVM, I sold my Citrix stock.

---

### Post by natiya on 2019-09-29
> **Tadaen_Sylvermane said:**
> Going about it backwards I think. Do you even need either? Have to build around your plan, not build looking for a plan. Otherwise you end up with either not enough, or more stuff that you don't need.

How many vms?
Will containers work better? An lxd container is far superior to a full vm in hardware use. More per host ultimately. For full vms 16gb of ram isn't a lot tbh.
What will they do?
Do you even need something as intense as OpenVSwitch, or can you just use a network bridge off the main ethernet and put them all on the lan? OpenVSwitch seems like using a 90 pound jackhammer to drive a half inch nail, for home use anyway.


I will install OpenStack and use these VMs to send traffic between them.

---

### Post by TheFu on 2019-09-29
> **natiya said:**
> I will install OpenStack and use these VMs to send traffic between them.

Openstack isn't really worth the effort until you have 10+ physical machines.  Moving to a new release of openstack is generally a fork-lift upgrade.

Perhaps the better answer for a small setup is Proxmox.  You can start with 1 machine. There is a web interface to control start/stop of each VM. Containers are supported.  You can add other physical machines and they can join into the same Proxmox "cluster", though I wouldn't really call it a cluster.  Run that for a few months, see if you like it.  Proxmox is for non-Admin people who have 1-10 physical machines they want to leverage as VM servers.

All depends on your purpose.  Seems you aren't interested in learning system admin and infrastructure, but want to concentrate on security tools.  Sorta like someone has a choice between freeNAS and Ubuntu Server for network storage.  FreeNAS is pre-built to handle network storage. Ubuntu Server is much more flexible, but requires much greater skill to setup as a storage server.  However, once setup, you don't have just a storage server, so many other programs can be loaded.

---

### Post by kevdog on 2019-10-10
Ubuntu Server vs FreeNAS??  Not really an equal comparison.  FreeNAS is specifically meant to be a NAS thats its main purpose.  However through incorporating the use jails and VMs -- FreeNAS essentially can be anything you want it to be.  FreeNAS also runs with ZFS natively (Ubuntu looks like it will in the future).  Idk, I'm not trying to argue since there are many ways to skin a cat, but I'm not sure how you could say Ubuntu Server is definitively better than FreeNAS for network storage.

Also on the subject of hypervisors -- the one thing I mentioned about delta backups and such --- it wasn't to say that's the only backup solution there is.  What I like about Xen is that it can be run with Xen Orchestra which makes it very easy to manage things.  By default I think Xen Orchestra has about 5-6 different backup options available, but since its run on CentOS, if you wanted I'm sure you could probably run whatever you wanted.  I unfortunately do IT for a living -- if I did I probably would be exposed to so much more.  For Home use however, I really like xcp-ng (open source version of Xen hypervisor) where I can virtualize my pfSense router and also virtualize Ubuntu which runs Xen Orchestra.  Although I love working from the command line, managing a lot of VMs can sometimes be tricky so its nice that a GUI is available for things were options can be deployed rather rapidly and its easy to get a feel for whats going on. 

I ran proxmox prior to xcp-ng.  I didn't think the product was bad, however the documentation isn't all that great, and their forums are very inactive.  Many of the user questions go unanswered.  For someone not as technical with all the KVM stuff, I really didn't like it all that much.

---

### Post by milesweb on 2019-10-17
> **natiya said:**
> I'd like to have Linux-based server with a robust virtual platform, same as ESXI is for Windows. The hardware is a HP Server with 16GB of RAM, 1TB of hard drive and Intel XEON 3.7GHz.

[COLOR=#242729][FONT=Arial]The hosts are going to be sending/receiving Internet traffic and running some security applications (firewalls, IPS-intruder prevention systems...). The traffic will be also analyzed by a commercial tool similar to Wireshark.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Based on what I understood, I may consider these options:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]Ubuntu Server + KVM + vSwitch[/FONT] 
[*][FONT=inherit]CentOS + KVM + vSwitch[/FONT] 
[*][FONT=inherit]CentOS + Xen + vSwitch[/FONT] 
[*][FONT=inherit]openSUse + KVM + vSwitch[/FONT] 
[*][FONT=inherit]Debian + KVM + vSwitch[/FONT] 
[*][FONT=inherit]oVirt?[/FONT] 
[/LIST]
[COLOR=#242729][FONT=Arial]What would be the best option for the applications I want to run?[/FONT][/COLOR]

They would all work quite well. Basically, the operating system is not that important; it's a matter of individual inclination, I'd tell. I don't have an idea about Xen. oVirt is a front-end to KVM with a more convenient administration of virtual machines, virtual networks, and virtual storage.

---

### Post by kevdog on 2019-10-28
I'd take a look at Xen Orchestra in relation to oVirt.  Xen Orchestra is a program that can run on top of any linux installation that can manage clusters of Xen hypervisors or xcp-ng hypervisors.  xcp-ng is the open source version of Xen.  A lot of people in the these forums champion open-source so if they don't like Xen's closed nature they can run xcp-ng as an alternative. xcp-ng is a similar model to Ubuntu in that the product is free and they have a user forum.  They also however provide a $$ service model for example if you're running many many machines and need professional help

---

### Post by johnarnold on 2019-11-04
Openstack itself is going to take a lot of your resources and is complex to setup and maintain so I wouldn't suggest that. For a single physical machine stick with something simple such as [COLOR=#000000]xcp-ng. Also, there is a free license for VMware ESXi if your physical server has 2 or less CPUs. [/COLOR]

---

