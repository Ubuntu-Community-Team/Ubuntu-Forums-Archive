---
title: "Virtualisation of hardware"
date: 2017-02-02
forum: Virtualisation
---

### Post by michal332 on 2017-02-02
Hello guys,

I want to ask for some interresting things before I can start doing what I want. What about: I want to setup my roommate's PC to Ubuntu Server in the way I can access to it from my laptop (a.k.a I want to virtualised his PC). 

I'm not asking for steps like "how I can do that, please help", no no no, I can use google :)

His PC has installed Windows 10 on HDD. Also has Intel i5 / 16 GB of RAM etc. I want to add my personal HDD to his PC and on this HDD (separate from his one) want to install server and virtualised hardware.

My question: If I do this and all hardware tranform to VM so I can work on it and then I close the session / VM and reboot PC back to Win10, will be the hardware de-virtualised or stay in some king of virtualised-form and will not be used in other way (also in way, that I fully shut the server and the server will not longer use these components).

Thanks for your opinnion :)

Also I'm sorry if someone create same thread and this is just a copy...

Cheers,
Michal

---

### Post by QIII on 2017-02-02
Your post is somewhat hard to follow, but let me see if I understand so I can respond is a similarly hard to follow manner.

(First, I am going to avoid quibbling about the definition of a "server".)

You want your roommate's computer, which is running Windows 10, to host a virtual machine that runs Ubuntu.  You want the virtual disk for that virtual machine to reside on your HDD housed in your roommate's computer.  You want to access that virtual machine remotely.  Correct?

Yes, that can be done.  It is done all the time.

You may, however, have some misapprehension about what virtualization is all about.  A guest OS on a virtual machine does not have direct access to the host's hardware.  The virtualization software, running as a program on the host (that is, Windows 10 is running as the host and the virtualization software, in which the virtual machine is running as a guest, is running on that) provides communication between the host's hardware and the virtual hardware presented by the virtualization software to the guest OS running within the context of the virtual machine.  The virtualization software presents what is known as a hardware abstracton layer to the guest OS.  An OS within a VM does not run on actual hardware (although there are things like VGA-passthrough, that is beyond the scope of what you are asking.)

The virtual machine cannot be assigned the entirety of the host's resources because the host still needs to use some of those resources to continue running itself.  There is also a good deal of overhead, and therefore loss of efficiency, associated with virtualization.  That aside, the resources assigned to the virtual machine are release when the virtual machine is shut down.  

The big question to be asked before any of this matters is whether or not your roommate agrees to this arrangement.  The virtualizaton software will need to be installed on his/her machine. He/she will have to be willing to work on a machine whose resources are being shared when you are running your virtual machine.

That said, what it seems you are actually driving at is dispensing with virtualization completely, setting the other machine up as a dual boot, booting to Ubuntu and then gaining remote access to the other machine and controlling it.  That would give you direct access to the remote machine's actual hardware.  However, there is some latency and overhead associated with that and the graphics performance on your local computer will not be very good.

Further, there is the option to run the other machine as an actual server without a GUI, gain access to it via SSH (Secure SHell) and run applications on it.

---

### Post by SeijiSensei on 2017-02-03
Is your roommate committed to leaving his laptop running 24/7, or at least for all the hours that you might want to use it?

Before you do anything to your roommate's computer, what kind of computer do you have?  Maybe the first thing for you to try is running a copy of Ubuntu Server 16.04 on top of your own machine's OS (Windows or Linux).  Install [VirtualBox]("http://www.virtualbox.org/"), set the virtual network interface to "bridged," then install Server from its [downloaded ISO image]("http://cdimage.ubuntu.com/ubuntu-server/xenial/daily/current/").  On a newish machine you should be able to virtualize a 64-bit OS on top of a 64-bit OS if the virtualization features in the BIOS are enabled.   Otherwise download a 32-bit Ubuntu ISO your first time out.  With a bridged adapter the virtual machine will be visible by other computers on the network.  Once you can do all this successfully on your own computer, maybe then you can talk to your roommate about what to do next.

---

### Post by michal332 on 2017-02-03
Hello guys, thanks for reply. 

Yes, my roommate agreed with it. He has terrible working time (8 AM leaving house and around 8-9 PM come back), so he has no problem if I will using his PC :)

About virtualisation, I have some experience with VMware, which I tried to run on my laptop (Win / many distro of Linux), there is no problem with it. (but this will be my first experience with server version of linux :D ).

I want to tried both Windows or Ubuntu and decide which one is better for me (yes, I want to dual boot on his PC), also I know about latency etc. but the connection will be done by single cross-connect cable from my laptop to his PC, so I think that there will no such latency.

All I want is setup his PC to provide my VM to which I can access and work on it, because I need much more resources than I have on my personal laptop for my work / projects. But I don't know (until you response) if the hardware will be released once I shut down the VM and start up normal OS (like his W10), or if there will be some hardware still associated his VM even if the VM will be down (properly closed / shutdown, not only sleep) and then he will have some bad experience during his using of PC.

Michal

---

### Post by SeijiSensei on 2017-02-03
As QIII said, your question indicates you still don't understand how virtual servers work.  VMs run entirely in software.  If you reboot the machine, and it is not configured to restart the virtualization manager and the VM at boot, then there is nothing left around.  A virtualization layer like VirtualBox is just like any other program.  If it's not running, it's not consuming any resources.

If you intend to run Ubuntu Server, you can easily limit that to 1 GB of his machine's total memory.  Even if it's running full-time, its effect on other programs will be negligible.

---

### Post by ODTech on 2017-02-03
OP has to be more clear.

To me it sounds like he wants to dual booth the original Windows 10 and Ubuntu server and then setup a Windows VM in ubuntu server that he can RDP into from his laptop.

---

### Post by 1clue on 2017-02-03
I read that:
[LIST=1]
[*]You want to create a VM on your roommate's laptop.
[*]Your roommate is away during the times you want to use the VM and has given permission.
[*]You want to install Ubuntu Server, which is a first-time event for you.
[*]You want the VM to use your separate hard drive.
[*]You want that hard drive to boot direct hardware when installed on your computer?
[/LIST]

Things we need to know:  The brand and model number of your PC and your roommate's laptop.

Things I know:
[LIST=1]
[*]Your roommate's computer, as far as I can tell, is capable of running any normal VM. This assumes certain hardware qualifications we don't know yet. Check your BIOS and turn on:
[LIST=1]
[*]You need VT-x or AMD-v, depending on what CPU you have.
[*]You need VT-d or AMD IOMMU, depending on what CPU you have.
[/LIST]

[*]You will need to donate the hard drive to the VM. This is what VT-d is for. I've never done it, so you'll need to research it or get someone else to help.
[*]You will need two sets of drivers.  One will be virtualized drivers used by VMware, and the other will be actual hardware drivers for whatever your personal system needs.
[/LIST]

It would be much simpler to have a dedicated VMware image of Ubuntu Server on your roommate's laptop and another completely separate boot disk on your personal hardware.  You could move the hard disk from one box to the other and use the data on it in both places perhaps, but moving a disk from a VM to a physical machine is not normally done.

---

### Post by QIII on 2017-02-03
Again:  I really think that if the roommate will be away while this is going on, virtualizing adds an extra layer of unnecessary complexity for what you are trying to accomplish:  using the resources of another machine.

Just set up a dual boot (with Ubuntu installed on the drive you are going to add), boot the machine to Ubuntu while your roommate is away, and connect remotely to the Ubuntu running on bare metal.

I have 5 machines at home.  My daily driver and main machine with Ubuntu 16.10.  One with Windows.  One with Fedora 25.  One with Ubuntu Mate.  One with Ubuntu Server.  For those with a GUI, I use NoMachine NX to log in to them and operate them remotely.  The server I SSH into as needed.

(I also have a web server in another State running on a VPS, but that's out of the scope of this discussion.)

*None* of the machines at home runs virtual machines.  I have direct access to the bare metal hardware via remote access.  It's much simpler that way.  VMs make great sense for some security considerations, when multiple users need to use one machine (less expenditure in hardware), VPSes or other specific reasons.  A VM does not seem to make much sense in your situation.

The one possible irritation for your roommate would be having to use GRUB to boot to Windows.

---

### Post by 1clue on 2017-02-04
As a counterpoint to QIII's perfectly valid points above, I manage dozens of VMs. I can't imagine a scenario where I would ever use dual boot again, even between two Linux machines.

By using dual boot you have guaranteed that no more than half of the software installed on the system is available. Whatever you haven't booted to requires that you shutdown and restart into the other OS before you can use it, which means there's also a significant time spent getting to what you need.

Pretty much every personal computer spends most of its time idling. The times people use them are fairly random and unpredictable. There is a significant chance, especially if you're in college and studying for finals (an assumption on my part), that both of you need access to all your resources at the same time.

By using a virtual machine, you both get access to everything simultaneously. The chances that your roommate needs all his laptop's capability at the same time you need your VM is smaller than the chance that your roommate needs to use his machine for everyday, low-powered stuff like email, writing papers or even watching netflix, while you need your functionality installed on his pc.

---

### Post by efflandt on 2017-02-04
Not sure what "resources" you want to use on your roommate's computer, since you only outline what you are trying to do, but not exactly why or intended purpose. For example maybe you want to "cluster" your roommate's computer with yours to use resources on that computer as though they were part of yours
[https://en.wikipedia.org/wiki/Computer_cluster](https://en.wikipedia.org/wiki/Computer_cluster)

If you only want to cluster when your roommate is away, dual booting your roommate's computer is a possibility without any virtual machine involved. Or with a capable multi-core CPU and plenty of RAM, maybe the clustered server could be in a virtualbox, but that would not be as fast, especially if a guest vbox in Windows host. And I have never run Windows in a virtualbox, which can run into licensing issues when running on virtual hardware that it is not registered with. The only things I run in virtualbox are 32-bit Linux under 64-bit Linux to use 32-bit only WebEx  w/32-bit browser & java, or Lexmark network scanner (sane) driver that works in 64-bit 14.04, or 32-bit version works in 32-bit 16.04, but 64-bit version does not work in 64-bit 16.04 or 16.10.

I have never done clustering, so I do not know how easy that is to do, or connect/disconnect other computers in the cluster. But people have even clustered Raspberry Pi computers (Raspberry Pi is a $35US ARM computer on credit card size board that can run Linux)
[http://www.zdnet.com/article/build-your-own-supercomputer-out-of-raspberry-pi-boards/](http://www.zdnet.com/article/build-your-own-supercomputer-out-of-raspberry-pi-boards/)

Or the simplest form if you just want to run certain apps on your roommate's computer when they are away would be to dual boot it and run those apps over ssh. If you have X installed on that other system, you can run gui programs on the other computer through ssh with ForwardX11 enabled which would display the gui in X on your computer.

With dual boot, each OS can use all of the hardware when it is running, but not while not running. So when your roommate boots Win10, that will have access to all hardware and should not even know that Linux is there.

---

### Post by 1clue on 2017-02-04
@efflandt,

Clustering is a completely different thing. Very few if any normal "user" tasks scale well to clustering systems. I spend most of my time on Raspberry Pi forums telling n00bs that those clusters are not in any way cost effective compared to a mainstream box of similar price.  When I first saw an article about spending roughly $2k USD on a pi cluster I did some quick math. Based on the benchmarks released by the article describing the pi cluster, I priced out a box using a mainstream i7 and compared the same benchmarks.  The pi cluster had 1/35th of the performance of the i7, and no limitations on the type of task you would be able to perform using it.

Let me restate that:  To make a Raspberry Pi cluster to match the speed of an i7 costing $2k, you would need to spend about $70k using the B+ boards that were new at the time.

I haven't done the math again since then, but I seriously doubt the numbers have changed a lot.

There are exactly two reasons to make a cluster of pi's:
[LIST=1]
[*]To learn how clustering works on the hardware level, including different networking arrangements.
[*]To learn how to model software algorithms for clusters, which requires an actual cluster.
[/LIST]
Both of these reasons apply to college students and possibly somebody in an industry with a need for clustering, who wants to educate himself/herself before spending a ton of money on a real cluster.

---

