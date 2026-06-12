---
title: "Question: KVM networking setup"
date: 2014-02-28
forum: Virtualisation
---

### Post by viijay2 on 2014-02-28
Hello community,

I have some questions on how to make my network setup work right from the start.

At the moment I am running VMWare and wanted to switch to a KVM based virtualisation platform. My choice is a Ubuntu server 13.10 which was easy to setup. So far KVM runs properly. But now the tricky part. My network situation. In VMWare it is something like this:

VMWare Networks:
Internal (physical NIC 1 bound)
- PFSense firewall
- a couple of other server

DMZ (no physical NIC bound)
- PFSense firewall
- a couple of other servers

WAN (physical NIC 2 bound)
- PFSense firewall only (IP through dhcp - cable provider)


My question is how to set this up within KVM?
What I figured so far - and I have used the virt-manager (VMM) for this - is that the internal interface of PFSense has to be setup up as "Host device eth0: macvtap" with source mode "Bridge". That way I was able to connect to the web interface of the firewall from my client which was in the same network like the Internal NIC of the firewall.

But how do I setup the DMZ for this? I am wondering if there is a way (like I understood in VMWare) not to use a physical interface.

WAN I suppose I have to choose eth1 from the server and set to passthrough?

At the end the firewall should be the main component taking care of all traffic on all the networks and the "host" should be just a simple client on the internal network at best.

Thanks for any insight, ideas or suggestions on how to accomplish a scenario like this.

VJ

---

