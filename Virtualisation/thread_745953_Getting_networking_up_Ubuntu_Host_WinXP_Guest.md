---
title: "Getting networking up Ubuntu Host WinXP Guest"
date: 2008-04-05
forum: Virtualisation
---

### Post by fireman71 on 2008-04-05
I recently decided to try out a little virtualization with VMWare and have run into a problem.

Current setup is ubuntu 7.10 as the host with vmware server installed from the repository and windows xp home as the guest with networking set to bridged.

The install of both vmware and windows xp went without errors and windows can connect to the internet.

My problem is that nothing on my network can connect to a share on the guest windows xp virtual machine and the virtual machine cannot connect to anything on the local network but receives an IP address from a Linksys router via DHCP and can surf the web just fine. Meaning I cannot see any of the local windows shares on my local lan, my son's shared music folder, my windows xp shared external harddrive nor shared internal IDE data drive, etc. I cannot connect to anything by either samba share name nor ip address on the local lan.

My local lan uses the ip range of 192.168.1.1-255 and according to ipconfig in windows the virtual machine is being assigned an address of 192.168.1.106 or .107 almost all the time from the linksys router. In ubuntu, ifconfig shows ip address on eth0 as 192.168.1.100, vmnet1 shows 172.16.141.1 and vmnet8 gets 172.16.35.1.

I haven't found anything in the forums that seems to relate to my problems nor has google turned up anything that I think might be applicable.

What am I missing?

I am thinking that the problem is the network interfaces being assigned different numbers, but I cannot find any way to change them so that the vmnet interfaces get assigned local lan ip addresses on the host. The guest seems to be getting assigned a dhcp ip address perfectly fine though.

Many thanks in advance!:confused:

LATEST UPDATE ON THIS PROBLEM:

I installed a copy of Ubuntu 7.10 as a guest on the VMWare server. Straight after the installation I was able to ssh into my Ubuntu Host without a problem. So, this seems to eliminate the IP address as the cause of the problem and throw it back into windows or something related to the install of windows in the VMWare server.

Has anyone had a similar problem or is there some special step for installing windows into VMWare that I missed?

Thanks again.

---

### Post by VitaLiNux on 2008-04-05
Hey, Friend!

Give a try to this, [http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/]("http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/")
This might be helpful for you. It worked for me Try it, then! Come and tell us how it worked out.

---

### Post by fireman71 on 2008-04-06
nope still no luck. Thank you for the suggestion though.

I am going to completely remove vmware and the virtual machines I had made and start all over from scratch and see how it goes.

---

