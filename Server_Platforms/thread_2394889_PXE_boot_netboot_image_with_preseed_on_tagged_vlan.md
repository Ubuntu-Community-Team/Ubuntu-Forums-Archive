---
title: "PXE boot netboot image with preseed on tagged vlan"
date: 2018-06-23
forum: Server Platforms
---

### Post by justleen on 2018-06-23
Hello All!

I'm looking to better understand the installation proccess of ubuntu.
Im trying to automate server deployement via PXE.  Im using the netboot image and a squashfs image to boot. The problem lies in the preseed file, which is hosted on machine with a seperated tagged vlan.
At this moment, when I boot, the first question the installer comes up with, is the network config wizard. This wizard fails on DHCP / Manual config since it's trying to get an IP in the wrong vlan.
Weird thing: The setup wizard only sometimes (seemingly random) asks for a tagged vlan ID, but most of the times it doesn't and keeps falling back to DHCP autodiscovery/manual config without VLAN.

Since I want automated deployment, I really dont want a network config wizard during install.

I have tried passing vlan arguments to the PXE kernel parameters, without success (this affects the PXE boot networking, not the installer networking).
My next approach was to customize the squashfs image to have a vlan interface defined, but the network settings inside the squashfs image dont seems to effect the installer network.
I got a lab setup working, but the lab is on a flat, single /24 network without vlans.

An extra complication is that we already have a full fledged infrastructure based on Redhat and I am forced to re-use components like the existing dhcp/tftp server and the hosts that server kickstart/preseed file - and offcourse the existing network layout.
Having a rogue proof-of-concept MAAS server inside our production network would cause all kinds of havoc.
By using the existing tftp server and adding ubuntu with squashfs seemed like the way go to integrate as much as possible with the current infra.


TL;DR: My preseed file is on a different tagged vlan. 
How can I preconfigure a tagged vlan during an automated deploy via pxe/squash so the installer knows which vlan the preseed file resides?
Should the squashfs image be configured for tagged vlan or should PXE still handle this part?

Any help would be much appreciated!

---

