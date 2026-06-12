---
title: "Installing Windows Server 2008 in VirtualBox on Server 11.10"
date: 2011-12-29
forum: Server Platforms
---

### Post by petarpetrovic on 2011-12-29
I have this old desktop machine and I installed Ubuntu Server 11.10 on it so I can do some serious web development & testing. I have successfully set up a LAMP system and the server resides on a local network at 192.168.2.20.

What I want to do is virtualize Windows Server 2008 on this machine so I can setup a IIS server and do some ASP.NET development & testing in parallel with my LAMP server. I would like the virtual machine to reside at 192.168.2.21 address.

I have followed the procedure outlined [here]("http://www.virtualbox.org/manual/ch07.html"), I successfully created a virtual machine and when I run VBoxManage startvm "Windows Server 2008" & it starts up the virtual machine successfully.

But when I try to access it from my Windows 7 laptop using Remote Desktop, I get the following error:

"Remote Desktop can't connect to the remote computer for one of these reasons:

1) Remote access to the server is not enabled
2) The remote computer is turned off
3) The remote computer is not available on the network

Make sure the remote computer is turned on and connected to the network, and that remote access is enabled."

I then did sudo ufw allow 3389, since that's the default port for RDP sessions, but things still don't work.

Any solution for this?

---

### Post by b0b138 on 2011-12-29
What is the ip address of the win server?

You will also want to make sure the network adapter of the vm is set to bridged adapter.

---

### Post by petarpetrovic on 2011-12-29
I don't know the IP address of the Windows Server because I cannot RDP to it. I would like it to reside at 192.168.2.21, but I do not know how to set up a bridged adapter in CLI.

---

### Post by lukeiamyourfather on 2011-12-29
If you want the virtual machine to have a unique IP address you'll need a dedicated NIC for it. The default networking method is NAT which allows outgoing traffic and port forwarding (must specify ports manually).

---

### Post by petarpetrovic on 2011-12-29
That's why I want it to use bridged adapter rather than NAT. I guess I should be able to access the virtual machine's web server from all parts of the local LAN, then?

The main problem is that I cannot login to my virtual machine to install an operating system on it.

---

### Post by b0b138 on 2011-12-29
Ah..

VBoxManage modifyvm yourvmname --nic1 bridged

---

### Post by petarpetrovic on 2011-12-29
Now, when I try to start the virtual machine, I get the following error:

Error: failed to start machine. Error message: Failed to open/create the internal network 'HostInterfaceNetworking-' (VERR_INVALID_PARAMETER).
Failed to attach the network LUN (VERR_INVALID_PARAMETER)

---

### Post by lukeiamyourfather on 2011-12-29
I see what you mean. You're trying to access the built in RDP server so you can install the operating system, not the RDP server from the Windows guest (since it isn't installed yet anyway). Your first post was a little vague so I didn't catch that.

Have you installed the extension to enable the RDP server? It doesn't come with VirtualBox by default and must be installed manually.

[http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

---

### Post by petarpetrovic on 2011-12-29
All I did was sudo apt-get install virtualbox-4.1 and that should have installed the neccessary RDP extension, which it obviously didn't. Which package should I install in addition?

---

### Post by lukeiamyourfather on 2011-12-29
> **petarpetrovic said:**
> All I did was sudo apt-get install virtualbox-4.1 and that should have installed the neccessary RDP extension, which it obviously didn't. Which package should I install in addition?

See the instructions linked in my previous post. The extensions are proprietary (i.e. not in the repositories) and are only available directly from Oracle.

---

### Post by petarpetrovic on 2011-12-29
I have successfully installed the Extension Pack, but now when I start the virtual machine, I get this error:

Oracle VM VirtualBox Headless Interface 4.1.8
(C) 2008-2011 Oracle Corporation
All rights reserved.

VRDE server is listening on port 3389.
Error: failed to start machine. Error message: Failed to open/create the internal network 'HostInterfaceNetworking-' (VERR_INVALID_PARAMETER).
Failed to attach the network LUN (VERR_INVALID_PARAMETER)

---

### Post by lukeiamyourfather on 2011-12-29
The VRDE message is about the internal RDP server, so that's good. The other message is saying your network configuration for the guest is no good. I'm not familiar enough with the command line configuration to help there, but the documents probably cover configuring the network.

---

### Post by CharlesA on 2011-12-29
It would be easier just to forward the VirtualBox GUI over SSH in order to get the network set up.

As for the network interface, check to make sure the bridge is attached to the host interface:

[https://forums.virtualbox.org/viewtopic.php?f=7&t=31746](https://forums.virtualbox.org/viewtopic.php?f=7&t=31746)

---

### Post by b0b138 on 2011-12-29
keep in mind you actually have to install windows to the vm just like you would a physical computer...virtualbox doesn't come with it

---

### Post by lukeiamyourfather on 2011-12-30
> **b0b138 said:**
> keep in mind you actually have to install windows to the vm just like you would a physical computer...virtualbox doesn't come with it

I think you're missing the point like I was earlier. There's an RDP server built into VirtualBox that runs on the host. It doesn't matter what operating system the guest has because the RDP server has nothing to do with the guest. The point of getting the RDP server functionality is to be able to see the screen to install Windows in the guest.

---

