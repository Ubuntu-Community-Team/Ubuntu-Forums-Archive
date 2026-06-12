---
title: "Using OVS  to demultiplex traffic to VMs based on VLAN tags (and not rip them off)"
date: 2016-04-14
forum: Virtualisation
---

### Post by ksengal on 2016-04-14
[FONT=Arial]Hi, [/FONT]

[FONT=Arial]Is there a way to, using OVS(OpenV Switch) on Ubuntu, demultiplex vlanned traffic to multiple virtual guess based on vlans WITHOUT remove the vlan tags? [/FONT]

[FONT=Arial]Mind someone point me in the right direction (e.g., a web link, example)? [/FONT]
[FONT=Arial]My googling skills are failing me. [/FONT]

[FONT=Arial]Most links (like [/FONT]http://openvswitch.org/support/config-cookbooks/vlan-configuration-cookbook/) give instructions where the OVS bridge will rip off the vlan tags. But I'm trying to preserve them.

Thanks for any pointers.

---

### Post by MAFoElffen on 2016-04-16
I'm just getting more into virtual networking now, so not an expert by any means... but maybe I could give you some ideas to research(?) or someone else can jump in to help. I learn by doing...

What you are asking about, Re: [Overview on Virtual Switching Technologies and Linux Bridge]("http://events.linuxfoundation.org/sites/events/files/slides/LinuxConJapan2014_makita_0.pdf")

On vlan, I looked into OpenVswitch, then saw that Ubuntu had their own vlan package, info here:  [Ubuntu Wiki VLan]("https://wiki.ubuntu.com/vlan")
More on VLan: [Linux Journal: VLans on Linux]("http://www.linuxjournal.com/article/7268"), [Linux Foundation: VLan]("http://www.linuxfoundation.org/collaborate/workgroups/networking/vlan").

During some recent Linux Recert's, I had to do them on rhel branch, so had to learn systemd. Later, while I was testing dev versions of Ubuntu, I played wioth that more. Part of systemd is brctl: [Set Up the Bridge]("http://www.tldp.org/HOWTO/BRIDGE-STP-HOWTO/set-up-the-bridge.html")

After playing with that, someone on the Server Section mentioned MACVLan, and their comments got me curious about learning more about that: [Some notes on MACVlan/MACVtap]("http://backreference.org/2014/03/20/some-notes-on-macvlanmacvtap/")
More on MACVLan: [MACVlans and Virtual Ethernets]("http://www.pocketnix.org/posts/Linux%20Networking:%20MAC%20VLANs%20and%20Virtual%20Ethernets"), [Mulitple Eth Addresses over single NIC]("http://www.bertera.it/index.php/2011/10/04/howto-configure-multiple-mac-address-over-a-single-ethernet-interface/"), [systemd-networkd-macvlan]("https://major.io/2015/10/26/systemd-networkd-and-macvlan-interfaces/"), [LXC MacVlan Networking]("https://www.flockport.com/lxc-macvlan-networking/"), [Configuring Macvlan and Ipvlan Linux Networking]("http://networkstatic.net/configuring-macvlan-ipvlan-linux-networking/")

I hope those articles can give you some ideas. They got me trying different things to see how each works. As for OpenVswitch... idk, I think I just moved on to other things and lost interest in that specifically. There were other ways. As I go back to document my skills, at least in networking: I keep thinking that network device functionality themselves are all built into and encapsulated into an OS itself (Linux Win, etc...). Reminds me that a stand-alone bridge, switch or router can all be done within a machine internally, and sometimes do not need any more additional pieces or software to do that... but learning how to do that might entail a lot of CLI commands to get there. Sometimes the additional packages are just adding a simpler access method to configure the same.

---

