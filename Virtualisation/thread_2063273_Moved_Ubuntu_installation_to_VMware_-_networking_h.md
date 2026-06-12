---
title: "Moved Ubuntu installation to VMware - networking help requested"
date: 2012-09-26
forum: Virtualisation
---

### Post by Colro on 2012-09-26
Hi all,

I'm not all that experienced with Linux. In the cruel world of IT, my career's been more focused on Windows servers. 

We've got one (very old - 12.08 I think?) Ubuntu installation that's running an OpenVPN server as its only role. Recently I've been virtualizing all of our servers to reduce overhead. 

It went pretty well for the most part. It boots right away with no fuss, and all I had to do was re-configure /etc/network/interfaces to see the new virtual network adapter with is static IP. ALMOST everything is working....

I can connect to the OpenVPN server (as well as SSH and anything else) just fine. However, once a client is connected, it can no longer see the internal network. I can ping any IP on the network and it simply times out. My client is getting assigned an IP on the network just fine, so I'm baffled here. I've tried disabling the firewall. 

I know OpenVPN uses a network bridge, and I (think) I configured it correctly, but has anyone run in to anything similar to this that might have some ideas?

---

### Post by matt_symes on 2012-09-27
Thread moved to virtualization subforum

---

### Post by dcstar on 2012-09-27
> **Colro said:**
> 
.........
I can connect to the OpenVPN server (as well as SSH and anything else) just fine. However, once a client is connected, it can no longer see the internal network. I can ping any IP on the network and it simply times out. My client is getting assigned an IP on the network just fine, so I'm baffled here. I've tried disabling the firewall. 

I know OpenVPN uses a network bridge, and I (think) I configured it correctly, but has anyone run in to anything similar to this that might have some ideas?

VPN connections usually have an option to let a client out of the network or not, since you can connect to the VM then it is not a VM issue, it is a configuration issue of the VPN software you are using.

This is in the assumption that you are using Bridged networking on whatever of the many VMware environments you are actually using.

---

### Post by idlemind324 on 2012-10-02
When you say you changed the configuration in /etc/network/interfaces what exactly did you change. Did you happen to make a backup of the file prior to changing it?

The problem may very well be a setting within OpenVPN or the firewall (probably iptables) especially if when you P2V'd the server it got a new NIC and it wasn't set to whatever interface the old one was (probably eth0).

Just my first thought.

---

