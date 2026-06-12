---
title: "What is the best free way to manage vm server?"
date: 2015-09-09
forum: Virtualisation
---

### Post by Higgins909 on 2015-09-09
I have a ubuntu server with a bunch of ubuntu vm's on it.
I need a easy free way to manage them, as sometimes they don't want to shutdown and I need to force it.
Also to make and delete them and change their hardware.

I currently got windows 10 and it was the same when I had windows 7.
I normally use mtputty as it can kinda sometimes save passwords and its got its own little window manager for multiple ssh sessions.
Then I have x2Go and putty.
Putty has to have some x11 forwarding then x2go is needed for some reason that I can't remember and then you have to go back to the putty and type virt-manager.
Basically I hate juggling 3 programs on my monitors like that and want a way simpler solution.

I've got some spare computers laying around that I could even install ubuntu or some linux on.. altho it would have to have a light gui.

Thanks,
    Higgins909

---

### Post by TheFu on 2015-09-09
virsh - for CLI
virt-manager on X/Windows

But you never said which hypervisor was being used. That matters. Both those tools support libvirt, but some hypervisors are not supported by libvirt.

Also - I always assume you have a Linux X/Windows machine to run stuff from. Using Windows is just too hard. 

From Windows, use putty, but only for non-GUI programs- - the CLI.
If you must use an X/Windows program from Windows - you need either an X/Server - there are some commercial ones - or use the x2go-client for windows to connect to a X/Windows desktop running the x2go-server somewhere. No need for putty at all that way.

---

### Post by sandyd on 2015-09-09
> **Higgins909 said:**
> I have a ubuntu server with a bunch of ubuntu vm's on it.
I need a easy free way to manage them, as sometimes they don't want to shutdown and I need to force it.
Also to make and delete them and change their hardware.

I currently got windows 10 and it was the same when I had windows 7.
I normally use mtputty as it can kinda sometimes save passwords and its got its own little window manager for multiple ssh sessions.
Then I have x2Go and putty.
Putty has to have some x11 forwarding then x2go is needed for some reason that I can't remember and then you have to go back to the putty and type virt-manager.
Basically I hate juggling 3 programs on my monitors like that and want a way simpler solution.

I've got some spare computers laying around that I could even install ubuntu or some linux on.. altho it would have to have a light gui.

Thanks,
    Higgins909

If your interested in setting up a VM-only server, take a look at [Proxmox]("https://www.proxmox.com/en/proxmox-ve"). It has a web gui, supports both KVM/OpenVZ, and has a nice active community for support.

---

### Post by Higgins909 on 2015-09-10
Will take a better look at Proxmox tomorrow.
x2go will crash/close session when I type virt-manager.  That is why putty is needed.
hypervisor... I think its the default that comes with tasksel... or whatever its called.
edit: not really sure what a hypervisor is.

---

### Post by TheFu on 2015-09-10
> **Higgins909 said:**
> Will take a better look at Proxmox tomorrow.
x2go will crash/close session when I type virt-manager.  That is why putty is needed.
hypervisor... I think its the default that comes with tasksel... or whatever its called.
edit: not really sure what a hypervisor is.

x2go is rock solid, so if that is failing, you have some other issue.

It is hard to do virtualization without a hypervisor (impossible).

Don't know that "tasksel" is. Never used it.

So - which hypervisor are you using? Wikipedia has an explanation.

---

### Post by Higgins909 on 2015-09-10
QEMU? ...thats what the virtualmachine software is called... if thats what a hypervisor is.
tasksel is shown when you first install the os, to select what packages you want, like webserver, samba, virtualmachinehost, mail, etc.
Been a while but you're supposed to be able to reopen it somehow but I've heard its not advasable to use then.

---

### Post by Higgins909 on 2015-09-11
Not sure how much you know about x2go, but I have a session managed for specific user and ip then terminal 1024x768 sound disabled.
Every time I type in virt-manager it popup x2go - 50 the connection with the remote server was shut down.  Please check the state of your network connection.
I've googled it up and down and got nowhere.
Also if QEMU is not a hypervisor what is and how can I find it out?

---

### Post by CharlesA on 2015-09-11
> **sandyd said:**
> If your interested in setting up a VM-only server, take a look at [Proxmox]("https://www.proxmox.com/en/proxmox-ve"). It has a web gui, supports both KVM/OpenVZ, and has a nice active community for support.

Vouching for that. I use it at home and so far I haven't run into any issues I haven't been able to solve.

> **Higgins909 said:**
> Not sure how much you know about x2go, but I have a session managed for specific user and ip then terminal 1024x768 sound disabled.
Every time I type in virt-manager it popup x2go - 50 the connection with the remote server was shut down.  Please check the state of your network connection.
I've googled it up and down and got nowhere.
Also if QEMU is not a hypervisor what is and how can I find it out?

QEMU is similar to KVM. Have a read: [http://serverfault.com/questions/208693/difference-between-kvm-and-qemu](http://serverfault.com/questions/208693/difference-between-kvm-and-qemu)

---

### Post by TheFu on 2015-09-11
> **Higgins909 said:**
> Not sure how much you know about x2go, but I have a session managed for specific user and ip then terminal 1024x768 sound disabled.
Every time I type in virt-manager it popup x2go - 50 the connection with the remote server was shut down.  Please check the state of your network connection.
I've googled it up and down and got nowhere.
Also if QEMU is not a hypervisor what is and how can I find it out?

What do I know about x2go?  Well, I've been using it for about 2 years from Windows and Linux clients around the world. x2go is NX and I used FreeNX for about 4 yrs prior to switching to x2go.
 I was an X/Windows C/C++ programmer writing native X/Windows code with Xt, Xm and Xlib in the 1990s, so writing and using apps from different machines is something I'm very familiar with.  [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) might help your understanding a little.

I've never used qemu directly as a hypervisor beyond a few play VMs on Windows a long time ago, but I have used almost every other one out there - on x86 systems: VMware (Workstation, Player, ESX, ESXi, Server), Virtualbox, KVM, Xen and hyper-v for about 10 minutes.  Since 2010, I've been on KVM almost exclusively.  KVM and QEMU are related.  If you can use KVM - your hardware supports it - then the VMs will run faster.  Both are supported by libvirt, provided you setup the system correctly and create the VMs.  The only tricks with libvirt are:
* setup ssh with keys first (or you should install askpass-something)
* ensure your normal userid is in the libvirtd group

If you ssh into the qemu server, can you start and stop VMs with virsh? It is likely that your VMs aren't "known" to libvirt, so this won't work. For VMs to be known by virsh/virt-manager, there must be a config file that libvirt understands.  These are created automatically when libvirt is used.  It is possible to "point" the qemu VM file into libvirt's XML config file for that specific VM. 

Not certain any of that makes sense. Sorry if it doesn't.

I've never used proxmox, but know people who swear by it. It you want a VM server, it would not be a bad choice.

---

### Post by Higgins909 on 2015-09-11
Confused is Proxmox free? its the free edition good?

edit: 
failed to get a virtual box going...
about x2go when I have x2go and putty and type virt-manager in putty it works it looks like a gnome style window, that pops up.
am I doing it wrong? am I supposed to be using something else then terminal?
the vm host has no gui as far as I know but then how to explain the x2go + putty way?

---

### Post by CharlesA on 2015-09-11
> **Higgins909 said:**
> Confused is Proxmox free? its the free edition good?

edit: 
failed to get a virtual box going...
about x2go when I have x2go and putty and type virt-manager in putty it works it looks like a gnome style window, that pops up.
am I doing it wrong? am I supposed to be using something else then terminal?
the vm host has no gui as far as I know but then how to explain the x2go + putty way?

Proxmox is free for the "community" edition - community support. If you want the enterprise edition, you'll have to pay a fee per server the software is installed on.

I use the community edition.
[https://www.proxmox.com/en/proxmox-ve](https://www.proxmox.com/en/proxmox-ve)

I'm not all the familiar with X-forwarding over SSH or x2go, so I'll defer that to TheFu. :)

---

### Post by TheFu on 2015-09-11
Which GUI is installed on the remote system?  

Did you follow the x2go installation directions?  Are you using the x2go PPA, as the instructions say?
Unity is NOT supported by x2go. LXDE is suggested. XFCE is too. I use openbox with special settings, but I avoid any DE, preferring a pure WM-only environments. In the x2go-client settings, be certain to select the DE you installed.  
If you have ssh-keys setup for authentication, the client/server x2go connection "just works."  From Windows, most people use a password login - this is still over ssh.  Then just use the menu or open a terminal inside the x2go-client and run virt-manager.  Virt-manager is a GUI program (X/Windows). Trying to run a GUI from putty without managing the DISPLAY will probably not work, unless you are just really lucky.  Did you read my link in #9 above?

BTW, I haven't used putty more than 2 times the last 3 yrs.  x2go is really solid.  OTOH, when I travel, I don't use Windows and ssh is a way of life for me - local or remote ... *the network is the computer* for me. ;)

Also - it is best to stick with 1 issue per thread. I started the x2go, because you mentioned it and because I'm always shocked when people use RDP or VNC instead. They just don't know how great the performance is with x2go.

---

### Post by Higgins909 on 2015-09-14
Its still kinda about managing the server tho. ;)
That think I got 403 error.

There is no GUI installed on my server.
I've been trying to using Published applications now instead of terminal but it still don't work.
With published app I can select virt manager that way.

Idk how to get a rsa/dsa key.  I was able to find C:/Users/Ben/.x2go/.ssh/authorized_keys
but the keys file is empty and when I try to use it, it asks for a password to decrypt a key

When I log in
```

NXPROXY - Version 3.5.0 

 Copyright (C) 2001, 2010 NoMachine.
 See http://www.nomachine.com/ for more information.
 

 Info: Proxy running in client mode with pid '5420'.
 Session: Starting session at 'Mon Sep 14 19:21:03 2015'.
 Info: Connecting to remote host 'localhost:31001'.

 Info: Connection to remote proxy 'localhost:31001' established.
 Info: Connection with remote proxy completed.
 Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
 Warning: Failed to read data from the X auth command.

 Warning: Generated a fake cookie for X authentication.
 Info: Using LAN link parameters 1536/24/1/0.
 Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
 Info: Not using NX delta compression.
 Info: Not using ZLIB data compression.
 Info: Not using ZLIB stream compression.
 Info: Not using a persistent cache.
 Info: Forwarding X11 connections to display 'localhost:0'.
 Session: Session started at 'Mon Sep 14 19:21:03 2015'.
 Info: Established X server connection.
 Info: Using shared memory parameters 0/0K.
 
```
I don't really remember how the install went for x2go client or the server... been too long.

---

### Post by TheFu on 2015-09-14
Setup ssh keys using **ssh-keygen**. Then use **ssh-copy-id** to push those keys from the "workstation" to the remote server. x2go will use standard, normally installed ssh-keys.  Any pre-installed keys that are part of x2go (if there are any, I've never looked), need to be deleted. They are of ZERO use, actually, they are dangerous.

Oh ... you use Windows as the client. Sorry - can't help for ssh key stuff there. Putty probably has a key-gen tool that you'd need to use, then copy the file somewhere into your HOME (whatever Windows uses) for x2go-client to find.  Maybe the x2go website has instructions for this?  Yep - 
[http://wiki.x2go.org/doku.php/wiki:advanced:authentication:passwordless-ssh](http://wiki.x2go.org/doku.php/wiki:advanced:authentication:passwordless-ssh) - they include a keygen tool, so you don't need to use putty version. Nice.

If you don't have a GUI installed on the remote machine, then x2go WILL NOT WORK! Plus that GUI cannot require 3D accel video graphics either (no Unity or KDE).  Use openbox or lxde or xfce. You cannot run virt-manager without the client-side X/Windows software installed on the system running virt-manager either.  The machine you are sitting behind needs to run an X-server. All of this is easier if you just run a Linux workstation locally.

---

