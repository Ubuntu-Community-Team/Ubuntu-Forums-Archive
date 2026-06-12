---
title: "Can anyone help me with an OpenVPN idea?"
date: 2009-04-22
forum: Server Platforms
---

### Post by spynappels on 2009-04-22
Hi Guys,

I'm looking for a little help with a scaleable OpenVPN setup, and the how-tos and tutorials aren't helping me much.

The scenario is this:
I have x number of linux and one or two windows servers in an equal number of different locations
I want them all to connect to an OpenVPN server in an office. They will all only be able to talk to the OpenVPN server, not to each other. I want to connect to the OpenVPN server from a small number of computers that technicians would use to remote administer all the other servers.

Would I use 2 separate OpenVPN servers on one physical machine, one to connect to all the servers and the other to connect all technician machines, with data routed between them? Or is there another option? If one of the servers was compromised, I would not want that to mean that all the servers were compromised.

Can anyone give me an outline of what is possible or even desireable?

Thanks in advance.

---

### Post by kustomjs on 2009-04-22
I would use smoothwall and then install openvpn smoothwall and leave all the computers/servers on a internal ip address.

so when you get connected on openvpn from outside connection you would be connected to your internal network.

by doing this way its more secure.

the reason why I did this way because I was having same issue as you intill I installed openvpn on my smoothwall.

---

### Post by spynappels on 2009-04-23
Hi,
Thanks for your reply, but that would not work because all the servers are in remote locations and the technicians are in different locations. I suppose what I am trying to set up is a virtual WAN, but with some differences.

I could isolate the server nodes from each other by careful setting up of the firewalls but I was just looking for other ideas which might help me create a flexible but secure network.

So any other ideas?

---

### Post by dipeshmehta on 2009-04-24
Hello,

Please check [http://ubuntuforums.org/showthread.php?t=752127](http://ubuntuforums.org/showthread.php?t=752127) - Part 1 would be appropriate in your environment.

for example you may setup server in office as nA/rA and server at remote place as nB/rB, this way remote server is connected to office server via openvpn.  Follow similar setup for other remote servers also.  So that at the end, your office server would have connectivity to all remote servers but remote servers would see only office server.

Hope this helps.

Dipesh

---

