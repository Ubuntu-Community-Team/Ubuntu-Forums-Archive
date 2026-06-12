---
title: "best virtual software for Ubuntu"
date: 2008-01-17
forum: Virtualisation
---

### Post by Matt26 on 2008-01-17
i would like to know which is best virtual software to be using on Ubuntu 7.10.  i have ready alot about vmware workstation vs virtualbox vs qemu.  from what i have researched i see that vmware workstation and virtualbox are the more popular choices of the 3... which of these is the best to go with overall in terms of performance, stability, features and networking?  i am planning to install both windows xp pro sp2 and vista ultimate.  thanks.

---

### Post by tajreed on 2008-01-17
With the help of the forum, I have the most success with VMware Server. Everything work with XP as the VM. It also seems to use less of my processor.

---

### Post by dcstar on 2008-01-17
> **Matt26 said:**
> i would like to know which is best virtual software to be using on Ubuntu 7.10.  i have ready alot about vmware workstation vs virtualbox vs qemu.  from what i have researched i see that vmware workstation and virtualbox are the more popular choices of the 3... which of these is the best to go with overall in terms of performance, stability, features and networking?  i am planning to install both windows xp pro sp2 and vista ultimate.  thanks.

I can run XP, Ubuntu 32bit, Kubuntu 64bit and Ubuntu Hardy 64bit as VMs in VMware server on my Ubuntu 64bit system - all work (apart from some issues with the Hardy alpha software and vmware tools crashing, but what do you expect with development software..........)

---

### Post by anaconda on 2008-01-18
I would also recommend VMWare server.  

I have tried virtualbox, but didnt ever get internet working with it.. VMWare had it working automatically..

And when I found out that virtualbox isn't even free for use at work I switched back to vmware... (OK virtualbox does have a completely free version, but that has some limitations I dont like.. eg no usb support...)

---

### Post by gvartser on 2008-01-18
> **anaconda said:**
> I would also recommend VMWare server.  

I have tried virtualbox, but didnt ever get internet working with it.. VMWare had it working automatically..

And when I found out that virtualbox isn't even free for use at work I switched back to vmware... (OK virtualbox does have a completely free version, but that has some limitations I dont like.. eg no usb support...)

I use virtualbox with Windows Vista as guest OS, and there were no problem with internet/network connection. Just make sure you set the networking configuration setting for the virtual machine to use NAT.

One thing I had to do though was to install the network card manually in VISTA, as the default one that comes with the "Installation of Guest Additions" was not able to install the drivers by itself.
The driver is found on the disk inside the guestOS after you click "Devices -> Install Guest Additions" disk. In the AMD_PCnet folder.

Best regz,
/g

---

### Post by Matt26 on 2008-01-20
i have read reviews that say virtualbox lacks USB 2.0 support and it's networking functionality doesn't operate seamlessly if at all in some cases (some manual configuration/tweaking may be required)?  plus i have read it's desktop integration within linux isn't the best- in terms of how easily you can move between your host and guest OS?  i have a need for all of these functions to work out-of-the-box if possible.  can virtualbox handle these functions as well as VMware?

---

### Post by fjgaude on 2008-01-20
I've used them both and have come to settle on VMware Server. Both are good VMs but I do believe overall VMware has the edge. The features you wish are there...

---

### Post by alexdbkim on 2008-01-21
VMware is definitely the best virtualization package for not only Linux but also all other operation system platforms including Windows and Mac OSs.

---

### Post by dark_phantom on 2008-01-21
I'm using both virtual box and vmware server, I like how virtual box integrates well.  One thing I didn't like is that I couldn't get to install Solaris 10 8/07.  In vmware, I was able to install Solaris but it doesn't support the vmware tools.  I'm going to try and install on both windows xp and see which one is better.  JMHO.

---

### Post by dpj23 on 2008-01-21
vmware... hands down...

---

### Post by FrankVdb on 2008-01-22
I'm using VirtualBox on Gutsy (installed XP in a virtual machine) and until now have been very satisfied. No hiccups, simple configuration, internet just works.

I don't need USB under Windows. Ubuntu and Linux are sharing a folder. I copy everything I need to my shared folder and haven't had any issues until now.

---

### Post by bmichel on 2008-01-22
I used qemu, vmware (server and workstation) and now I'm running virtualbox inside a gutsy 32 bit box, 2GB ram.

For my purpose (web applications checking with IE/FF/Opera) vbox is easy to configure, quick to start, light to run, good copy/paste  and shared folders between guest and host. I'm not using usb or any multimedia features.

Network was a little tricky at first and requires some manual setup (bridge) but now works flawlessly.

vmware server was also very good but heavier to run.

---

### Post by olavjunior on 2008-02-09
I have used VirtualBox from day one. Everything works, usb, networking, nice integration, so I haven't felt the need for trying vmware. I've used the none-free verision with usb support though. I'm very satisfied. But maybe Vmware is lighter on the processor? 

One thing I do miss though, is a better graphics card in the guest os. I couldn't get cover flow in itunes to work in xp, and now I wan't to try LinuxMCE, but I'm sure that won't be a pleasant experience. How do VmWare do there? And is there a guest-addon for other then xp? (the addon gives you seamlessly integration ect)

---

