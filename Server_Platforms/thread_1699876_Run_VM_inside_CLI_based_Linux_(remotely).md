---
title: "Run VM inside CLI based Linux (remotely)"
date: 2011-03-04
forum: Server Platforms
---

### Post by fela on 2011-03-04
Hi

I have a command line only Debian-based Linux server with which I would like to create a VM where anyone can remotely connect and have a play around. The guest OS that I have my eye on at the moment is either Gentoo (for it's customizability), or Arch (gentoo takes an age to install and I've never done it before).

Basically I'd have the VM running behind a NAT firewall provided by the VM software, and have specific ports forwarded to it. For example, with VNC's port 5900:

My friend contacts my IP at port **59001** with their VNC client software;

My modem gets a request for port **59001** and forwards it to my server;

The VM software running on my server is listening for this port, and is configured to forward again, this time to **5900** on the **guest OS**;

The guest OS has a VNC server running, listening at **5900**, which responds to the request.

Some problems that I would need to resolve are:

1) What virtualization software to use on the server
2) Make sure it can run inside a NAT network and supports port forwarding from the host
3) An X server running VNC

For 1) I'm looking at **QEMU**. It seems to support everything I need it to. 2) is covered by 1) (supposedly).

About 3), well I was thinking of running tightVNC for this.

Thanks very much for any help/suggestions :)

---

### Post by samosamo on 2011-03-05
I had a pleasant experience with VMware Server 2.0.

Do not allow VNC over the internet.  It is insecure.  Either use VPN or X11 forwarding with SSH.

---

### Post by Demented ZA on 2011-03-05
> **samosamo said:**
> I had a pleasant experience with VMware Server 2.0.

Do not allow VNC over the internet.  It is insecure.  Either use VPN or X11 forwarding with SSH.


Ditto :-)

---

### Post by fela on 2011-03-05
> **samosamo said:**
> I had a pleasant experience with VMware Server 2.0.

Do not allow VNC over the internet.  It is insecure.  Either use VPN or X11 forwarding with SSH.

So is there a CLI-only version of VMware server?

I fail to see how VNC would be insecure in this scenario:

Random hacker contacts my IP, port 59001
Router responds, forwards to my server
QEMU running on my server hears the request, forwards it to the VM
VM handles request

BTW, I don't mind if things break on the VM ;)

Also, as an update, I have an Arch VM running using KVM/QEMU, under it's default (basic) NAT, with port 22 forwarded to the VM for SSH (the server has an SSH daemon but it runs on a non-standard port so I can forward 22 to the VM and still SSH the server).

I haven't setup any sort of port forwarding for the VM on the modem, so at the moment all you can do from outside my home network is connect via SSH to the server (on its non-standard port).

However, as you mentioned this enables you to do basically anything by using an SSH tunnel, and of course from a CLI prompt on the server you can access anything on the home network :O

---

### Post by Demented ZA on 2011-03-05
Well, depending on your setup and the guest os you are running, a hacker could potentially use your guest os on the virtualmachine to hack your network from a machine behind (virtually behind, but physically on the firewall hardware) your firewall, cuircumventing the need for port forwarding etc.

The rule is not to give an attacker a way in anywhere, as the more open windows there are, the more options he/she has for a greater exploit.

As for CLI vm software, try [VMware]("https://help.ubuntu.com/community/VMware/Server"), or [Virtualbox]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html") and [here]("http://www.ubuntugeek.com/how-to-control-virtual-machines-virtualbox-using-vboxmanage.html").

---

### Post by fela on 2011-03-05
> **Demented ZA said:**
> Well, depending on your setup and the guest os you are running, a hacker could potentially use your guest os on the virtualmachine to hack your network from a machine behind (virtually behind, but physically on the firewall hardware) your firewall, cuircumventing the need for port forwarding etc.

The rule is not to give an attacker a way in anywhere, as the more open windows there are, the more options he/she has for a greater exploit.

As for CLI vm software, try [VMware]("https://help.ubuntu.com/community/VMware/Server"), or [Virtualbox]("http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html") and [here]("http://www.ubuntugeek.com/how-to-control-virtual-machines-virtualbox-using-vboxmanage.html").

If a hacker could do that, wouldn't that represent a different security vulnerability on the network? Ideally, I'd like my network configured so that no one can hack it simply by having access to a machine connected to it (and I don't think anyone can at the moment :D). All my routers have strong passwords for example....(or were you thinking of something totally different?).

I know the rule is not to let anyone in anywhere unnecessary, but I tend to think of it as 'make a compromise between features and security'...

Thanks for the links :)

---

