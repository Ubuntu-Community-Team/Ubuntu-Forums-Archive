---
title: "IP Addressing Question"
date: 2013-03-27
forum: Virtualisation
---

### Post by throese on 2013-03-27
I was at a friend's house last night and my VMs had the IP address of 10.0.0.1 and 10.0.2.1 (or something similar), what causes them and how do you fix the issue?

---

### Post by prodigy_ on 2013-03-27
Eh? I suppose you connected a device to your friend's network (wi-fi or wired) and got a 10.0.x.x IP address [assigned](http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol). If yes, there's nothing wrong with that.

So could you explain what exactly went wrong?

---

### Post by throese on 2013-03-27
I have 2 VMs. Windows XP and ubuntu server 12.04. I have openssh-server installed and tried to use putty to access the server, but it didn't register for some reason.

---

### Post by prodigy_ on 2013-03-28
Can you ping your Ubuntu server? At least by IP? If not, something is wrong with your network configuration. Check the [official guide](https://help.ubuntu.com/12.04/serverguide/networking.html). Note that both machines should be in the same IP subnet to be able to communicate with each other directly.

If you can ping the server, then what error message do you get in putty?

---

### Post by hartz on 2013-03-28
What network mode do you use? For each VM under "Attached To" you can select NAT, Bridged Adapter, Inetrnal Network, or Host Only Network.  There is also two other settings, Not Attached and Generic Mode.

Typically you will only get an address assigned by the external network DHCP server if using Bridge mode, but Wifi does not play with Bridge Mode so this is not what you are using.

NAT mode uses a point-to-point connection internally and all VMs van have the same IP on NAT mode because it is actually isolated.  VirtualBox handles these connections internally as if behind a NAT proxy.  VirtualBox provides the IP addresses for NAT'ed hosts so these are not affected by any external DHCP server. 

Host-Only networking allows the Host and Guests on the same virtual network to talk to one another as if plugged into a single switch.  This does not touch the host's external networking (unless you set up IP routing in the host operating system).  Internal networking provides an isolated network where guests can talk to one another and there is no access to the Host.

Generic Mode depends on some extra plugins, eg for secure tunnels.  No Connection presents a virtual network card with no connction to anything.

If an external DHCP server assigned an address to your VMs then I assume that those VMs are on a Bridge interface and you use a wired connection.  TO provide more information I realy need a better explanation of the problem:

> I was at a friend's house last night and my VMs had the IP address of 10.0.0.1 and 10.0.2.1 (or something similar), what causes them and how do you fix the issue? 

> I have 2 VMs. Windows XP and ubuntu server 12.04. I have openssh-server installed and tried to use putty to access the server, but it didn't register for some reason. 

Where were you running the Putty client?  On the Host or another computer on the network?  Or were you trying to access one VM from the other?

How did the "It didn't register" problem present itself - please give actual error messages, symptoms, etc.  Connection time out or rejected?  Failed Login?  Failed Public/Private Key login?  Failed host name resolution?  Is this the first time you tried to use Putty in this way or does it normally work but not at thr friend's house?  Or is this a new setup?

Note: Old versions of Putty, particularly Putty on MS Windows, can not talk to new versions of SSH.

---

### Post by throese on 2013-04-01
I realized that I needed to switch it to "Bridged" instead of "NAT" and it seems to be working for now. =)

---

### Post by dcstar on 2013-04-07
> **throese said:**
> I realized that I needed to switch it to "Bridged" instead of "NAT" and **it seems to be working** for now. =)

If the problem is SOLVED then mark the thread.

---

