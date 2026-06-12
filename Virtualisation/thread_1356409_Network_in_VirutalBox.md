---
title: "Network in VirutalBox?"
date: 2009-12-16
forum: Virtualisation
---

### Post by researcher123 on 2009-12-16
Hello everybody
I am looking after 7 computer laboratories each consisting of 30 computers in LAN. I want to install italc master  on its Teacher terminal(One per laboratory) and italc client on Student terminal(29 per laboratory). To test how this  will be useful for students I am using VirtualBox. I did the following basic work (Do let me know if I am going right :o)

1.I have created one Ubuntu Virtual machine named **Ubuntu-italc-master**.I want to make it my server.
2.I have created 29 Ubuntu virtual machines by names **client-1, client-2 ...client29** etc.These will be client machines (student terminals)
Now my question is 
[COLOR="DarkRed"]1.How to create virtual network from 29  virtual client PCs? 
2.Is it necessary  to have a separate virtual hard disk for each Virtual client & Virtual Server machine? 
3. I know little bit of a tool available here [http://clonezilla.org/](http://clonezilla.org/). Kindly advice.
4.Can I transfer this whole setup and configurations to actual physical lab once the virtual test is over? How?[/COLOR]

Hope all experts here will be cooperative in their usual spirits of Virtualization.
Thanks.:P

---

### Post by lukeiamyourfather on 2009-12-16
VirtualBox can export the entire virtual machine as an "appliance" which can then be used on other machines with VirtualBox . I think its in the File menu, something like Export Appliance but I don't have it in front of me to check. Cheers!

---

### Post by researcher123 on 2009-12-16
Thanks Lukeiamyourfather.  Any advice on whats to be done for virtual networking?

---

### Post by egravede on 2009-12-16
Are you trying to network Ubuntu clients through virtual machines?

---

### Post by memilanuk on 2009-12-16
Unless something has changed in Virtualbox recently, you still need a dedicated virtual hdd for each virtual machine; you can't 'share' in that you have client1 and client2 both boot and run concurrently off the same virtual hdd any more than you would have two physical PCs boot and run from the same disk.

You can select the network adapter for the clients to all point to the internal network ('intnet').  They will all be connected to one another via a virtual switch, and they will be completely sandboxed (in terms of networking) from the outside world.  If you need to be able to run a packet sniffer or something of that sort, change the network adapter to a 'host-only' configuration. If you need external network access to the Internet (for say, upgrades/updates or other services) you can configur your 'server' machine so it has two NICs - the first one connected to the outside network and configured as 'eth0' inside the server VM, and the second one connected to the internal network and configured as 'eth1' inside the server VM.  Then set up your stuff like dnsmasq (takes care of local name resolution, DNS caching, and DHCP all in one simple package), etc. on your server and configure it to act as a gateway/router for your network.  

HTH,

Monte

---

### Post by researcher123 on 2009-12-17
> **egravede said:**
> Are you trying to network Ubuntu clients through virtual machines?


Yes . I am trying to network with virtual machines and virtual server.

---

### Post by researcher123 on 2009-12-17
Ok. Let me try and report the success about this

---

### Post by researcher123 on 2009-12-19
But after I did this work I do not know what type of network should it be. I mean to say' what connection type'? I should be able to view all the clients just as they are visible in Windows network once I log into the host.How can this happen?

---

### Post by memilanuk on 2009-12-19
okay... from the sounds of your original post, you had one master server guest VM running on your host, and you'd installed iTalk on that guest server.  You'd also created 29 guest 'clients' that were all supposed to be on the same LAN as the server.  

What I said before - have all the machines use an 'internal network' connection, which should automagically have them all wired together on one virtual LAN.  If you have one machine (the server guest) acting as a dhcp server also for the internal network, then they should all have IP addresses.  If not, you'll have to establish static IP addresses for all thirty and manually create an /etc/hosts file with ip <-> name mappings for all thirty machines, and cut-n-paste from one to the next (assuming you have the guest additions working on all of them).  An interim would be to set up dnsmasq, which can act as a simple dhcp server and then provide name resolution based on the leases its given out, or based on its master /etc/hosts file.  Any way you slice it, your machines need to be able to reach each other on the internal network... and they all need ip addresses.  Once you think you have that set up, I'd suggest opening a terminal or console window, and trying 'ping -c3 italc-server' or 'ping -c3 client-27' to make sure that it works as expected.  Once you have that... I imagine you'll have much more luck with the machines 'seeing' each other in the GUI network stuff.

If on the other hand, you are wondering why you can't 'see' each of the guests on the host machines network... its because the host isn't by default attached to the same network as all the client VMs and the server VM.  If you use a bridged connection instead of an internal network, each of the VMs would have access to the physical external network... but it'd be 30 machines competing for the use of your *one* physical connection, so I'd imagine that could get ugly (and slow) quickly.

HTH,

Monte

---

### Post by researcher123 on 2010-03-19
yes. that way it worked. thanks.:D

---

