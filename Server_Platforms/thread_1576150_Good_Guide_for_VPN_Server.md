---
title: "Good Guide for VPN Server"
date: 2010-09-16
forum: Server Platforms
---

### Post by mattlach on 2010-09-16
Hey all,

I did some googling on the subject and didn't come up with much.  There were a couple of guides to set up VPN for masquerading so that local machines can reach the outside network via the VPN, but I want to do the opposite.

I want users windows boxes to be able to access their SAMBA shares and printer on the local network from anywhere on the internet.

Any suggestions?

My original plan was to use SSHFS for this, and just access them from anywhere directly, but it turns out that the SSHFS implementations, while they work great on linux, are not so hot on Windows.   Both Winfuse and Expandrive have some serious limitations.

Thanks,
Matt

---

### Post by samosamo on 2010-09-16
I'd like to help but what exactly is the "opposite" of masquerading to you?  And why aren't the 100 tutorials on google good enough for this?  Are you the first person ever to need a VPN?

---

### Post by mattlach on 2010-09-17
> **samosamo said:**
> I'd like to help but what exactly is the "opposite" of masquerading to you?  And why aren't the 100 tutorials on google good enough for this?  Are you the first person ever to need a VPN?

I must admit that I don't quite know the VPN terminology yet, so my statement about masquerading may be incorrect.

From the descriptions I read it looks like the guides I have read are for setting up a remote VPN for local computers to connect to, like a typical proxy.

My goal is to have remote computers connect to a local VPN in order to access the local network.

I followed a guide a found after I posted this last night and right now I am a little stuck.  It appears to be establishing a tunnel to my server, but once connected I don't have any access to either local or remote hosts.

---

### Post by Grenage on 2010-09-17
> **mattlach said:**
> My goal is to have remote computers connect to a local VPN in order to access the local network.

You want a client VPN solution, the two main types are client and site.

An easy way to go about this would be a dedicated system such as PFSense for the server, and the Shrewsoft client for the remote PCs.  All free, all quite user friendly, all GUI.

> **mattlach said:**
> I followed a guide a found after I posted this last night and right now I am a little stuck. It appears to be establishing a tunnel to my server, but once connected I don't have any access to either local or remote hosts.

It could be a simple name resolution problem, can you ping remote machines by IP address?  Bear in mind, unless they have a route back to you (the VPN endpoint is the default gw, etc) - it probably won't work that well.

---

### Post by kgatan on 2010-09-18
the most easy way to setup vpn imo is to use openvpn-as.
Downxload it from openvpn site as deb package and install

Its a simplified version of the openvpn package that lets you set up vpn with a simple script.

If you have problems you can even find video tutorials on youtube by searching openvpn-as.

---

