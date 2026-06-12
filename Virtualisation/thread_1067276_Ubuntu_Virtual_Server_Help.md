---
title: "Ubuntu Virtual Server Help"
date: 2009-02-11
forum: Virtualisation
---

### Post by eangulus on 2009-02-11
Hi everyone.
 
I am currently running a Samba File Server using Ubuntu Server 8.10 and I would like to run some Virtualisation on it as well.
 
Is there a way to run a VM Image of another OS on the server that I can then VNC into?
 
I would like to setup for eg, Ubuntu Desktop and Windows installations on the server as Virtual HDD's that I can then VNC into to use.
 
Mainly for Support for my customers I can then VNC into an their OS so I can direct them properlly over the phone.

---

### Post by bodhi.zazen on 2009-02-11
Yes, you can do this with any virtualization platform. VirtualBox, VMWare, KVM ....

Just install a VNC server on the guest, or KVM has a built in vnc server (so you do not have to install a vnc server on the guest, just specify a port on starting the guest)

---

### Post by eangulus on 2009-02-11
Thats all well and good. I know how to do that using Ubuntu Desktop with a GUI.
 
But are there instructions on how to such a thing via the command line in Ubuntu Server?
 
Also if I am using a commandline how do I go about installing the OS initially.

---

### Post by eangulus on 2009-02-11
Also what would my best option for the software?
 
VMWare, Xen, KVM etc?
 
And is it possible (and if yes how) to boot a diskless computer (thin client) using one of the images on the server using maybe a network boot or a little boot floppy or USB?

---

### Post by bodhi.zazen on 2009-02-12
You are asking for very detailed information and instructions, which is great.

But, the answers would take a long time to type.

Yes, you can do everything from the command line. Yes there are detailed instructions on how to do this, see the sticky at the top of these forums :

[http://ubuntuforums.org/showthread.php?t=973756](http://ubuntuforums.org/showthread.php?t=973756)

The "best" option is a matter of opinion, if you are using this beyond personal use you may run into licensing issues with all but KVM. XEN is an option, but I do not think it will run Windows guests and it has been falling out of favor recently in both Ubuntu and Fedora (in favor of KVM).

Once you start with virtualization I think you will find the differences between the various options are (IMO) minimal for most tasks.

---

### Post by Dedoimedo on 2009-02-12
> **eangulus said:**
> Hi everyone.
 
I am currently running a Samba File Server using Ubuntu Server 8.10 and I would like to run some Virtualisation on it as well.
 
Is there a way to run a VM Image of another OS on the server that I can then VNC into?
 
I would like to setup for eg, Ubuntu Desktop and Windows installations on the server as Virtual HDD's that I can then VNC into to use.
 
Mainly for Support for my customers I can then VNC into an their OS so I can direct them properlly over the phone.

The answer is yes. Your best bet would be to setup VMware Server.
But the detailed procedure can be quite lengthy ... :)
Dedoimedo

---

### Post by eangulus on 2009-02-12
[LEFT]Well from that sticky thread, I noticed that VMWare Server 2 is the only that specifies that it does not need X.
 
Would this be a suitable candidate.
 
Also I just tried isntalling KVM and it seems to want to have a CPU that supports virtulization. No one mentioned that as mine is just an old 1Ghz Celeron.
 
Also the VMWare server 2 also has a web based interface. Do any of the others or do any of them have a webmin module.[/LEFT]

---

### Post by eangulus on 2009-02-13
Just a little update and a couple of questions.

I have installed VMWare Server 2. Seems to be pretty close to what I wanted. But not sure if this is the program or just incompatibility but I setup a VM for Vista and it throws errors to install Windows 7. Also setup a VM as Ubuntu and it throws errors at booting the Moblin ISO.

Currently in the middle of a W2K Pro install so far so good.

How would I remote boot a computer into one of these VM's?

I was hoping that I could do a Network boot on a Diskless computer and run the VM as if it was local.

---

