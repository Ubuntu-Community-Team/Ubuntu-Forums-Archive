---
title: "Remote Desktop Virtual Machine Help"
date: 2009-04-24
forum: Server Platforms
---

### Post by zeroroom on 2009-04-24
We are running 9.04 AMD64 on a "test" server that we have.

We did run Windows Server 2008 on the machine and would RDP into it and run Virtual Box to play with different operating systems and configurations.

We discovered that Virtual Box's memory management in Windows was crap (it seemed to just grow the page file instead of using available memory.) compared to how Ubuntu handled it. So we thought we would install Ubuntu Server on the machine and try the same thing.

I have read through various posts about using the Windows based RDP stuff to connect to Ubuntu. From what I gathered, this isn't possible yet. And if it were it seems like it would be less secure than some of the other options out there.

I was wondering if I even need a RDP solution. Because Linux and Ubuntu are clever, I was wondering, is there some way to remotely fire up a virtual machine on the test server and connect directly to the virtual session?

I hope this makes sense. Please let me know if I can expand on anything and thanks for any help.

---

### Post by HermanAB on 2009-04-24
RDP to a Windows virtual machine works exactly the same as RDP to a physical machine.  Forward port 3389/tcp in your router, enable RDP and connect to is from Linux using rdesktop.

---

### Post by zeroroom on 2009-04-24
> **HermanAB said:**
> RDP to a Windows virtual machine works exactly the same as RDP to a physical machine.  Forward port 3389/tcp in your router, enable RDP and connect to is from Linux using rdesktop.


We are doing this on a local network using Active Directory. Something I forgot to mention. I don't see a need to forward any ports. Is there something I missing there?

I will however, get a Virtual OS installed first so I can try what you are saying.

Thanks HermanAB

---

### Post by BkkBonanza on 2009-04-24
If you're going to try out Ubuntu server are you planning to add a desktop/gui? 

If not then just use ssh to access the console on your server. That's very, very easy, installed and running by default and how most admins handle remote management. 

If you do want the gui then you can use ssh to do X windows forwarding. I don't do that myself but I understand it's easy and works well. I think it's just a simple -X option for ssh but likely need a bit more config. There are some tutorials around that google will turn up quickly.

Regarding virtual machines - I do most of my testing of OS and server development using VirtualBox under Ubuntu. It works great and they have some RDP options there built in as well (which I don't use as I mostly use ssh and sshfs for local mounts).

---

### Post by TwiceOver on 2009-04-25
Ubuntu + VMWare Server.

You can manage and view your virtual machines and their consoles from any web browser.  No need to RDP or even run a GUI on the machine.

---

### Post by albinootje on 2009-04-25
> **zeroroom said:**
> 
I have read through various posts about using the Windows based RDP stuff to connect to Ubuntu. From what I gathered, this isn't possible yet. 

Are you saying that you are limited to build-in RDP software on the MS-Windows desktops ?
Or are you allowed to install for example Nomachine NX client software to use for your Ubuntu server running FreeNX ?

---

### Post by zeroroom on 2009-04-27
[QUOTE=BkkBonaza]If you're going to try out Ubuntu server are you planning to add a desktop/gui? 

If not then just use ssh to access the console on your server. That's very, very easy, installed and running by default and how most admins handle remote management. 

If you do want the gui then you can use ssh to do X windows forwarding. I don't do that myself but I understand it's easy and works well. I think it's just a simple -X option for ssh but likely need a bit more config. There are some tutorials around that google will turn up quickly.

Regarding virtual machines - I do most of my testing of OS and server development using VirtualBox under Ubuntu. It works great and they have some RDP options there built in as well (which I don't use as I mostly use ssh and sshfs for local mounts).[/QUOTE]

I do already have the GUI installed. I just assumed I would need it accomplish my goal.

You raise a point I was also meaning to ask. Can I launch a Virtual Machine from the console? Or does it not work that way?

Thanks for recommending ssh for X I will see if my google-fu is strong enough.

[QUOTE=TwiceOver]Ubuntu + VMWare Server.
[/QUOTE]

I went to the VMWare website. VMWare server appears to be a pay for application. Is there a free version? I have a budget of $0 so having to pay for things is out.

[QUOTE=albinootje]Are you saying that you are limited to build-in RDP software on the MS-Windows desktops ?
Or are you allowed to install for example Nomachine NX client software to use for your Ubuntu server running FreeNX ?
[/QUOTE]

I am free to install applications, but I am trying to do this without having to alter Windows. Multiple people are going to be accessing the machine and I don't want to have to maintain client side software. If all else fails, it is nice to have that option.

Thanks for the help everyone. You have certainly given me some options to try out.

---

### Post by albinootje on 2009-04-27
> **zeroroom said:**
> 
Can I launch a Virtual Machine from the console?

Yes, you can, I'm using it with VirtualBox, and I read that VMware can also do that, as should Qemu.

Personally I dislike the free-of-charge VMware options like VMware server (I haven't tried the commercial variations).
I don't like the setup, but more important I don't like the VMware GUI at all, I find VirtualBox much much more pleasant to work with.

Last night I tested MS-Windows server 2008 within VirtualBox. 

(VMware with the same specs for the guest VM left my machine heavily swapping, I had to use ctrl-alt-backspace to recover from this, while VirtualBox was incredibly snappy with it).

Here's an example how I tested the VirtualBox guest VM from the command line :
```

VBoxManage startvm windows-server-2008 -type vrdp (to start)
VBoxManage controlvm windows-server-2008 poweroff (to stop)

```

See also here :
[http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-2.0-on-a-headless-ubuntu-8.04-server)
(A bit old, install VirtualBox 2.1 or 2.2 if you can)
[http://vmetc.com/2008/07/12/creating-and-configuring-headless-vms-in-virtualbox/](http://vmetc.com/2008/07/12/creating-and-configuring-headless-vms-in-virtualbox/)

---

### Post by HermanAB on 2009-04-27
The VMware Server 2.x series is a total POS.  Either use the older 1.x version, VMware Player or Virtualbox.

---

### Post by drave on 2009-04-27
look in the VirtualBox manual under the chapter "Alternative front-ends:remote virtual machines"

you can  connect via ssh to start the vm'z and then rdp

---

