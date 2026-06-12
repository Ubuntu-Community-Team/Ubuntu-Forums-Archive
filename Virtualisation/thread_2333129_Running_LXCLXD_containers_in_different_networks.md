---
title: "Running LXC/LXD containers in different networks"
date: 2016-08-07
forum: Virtualisation
---

### Post by rolandcg on 2016-08-07
Hi,
I have a server with 16.04 up and running. I used lxd to create a container environment, where I bridged my network.
Everything is running smoothly.

Now I want to create different containers, which belong to 3 projects.
I would like to separate these projects, they should be running in 3 different networks, two containers in every subnet should have a loadbalancer and a jumhost, they should have two network interfaces, one facing to the projects internal network, one facing the default network, that is the one my servernode is using.

How can this be archieved? Would I have to set up the project-internal network manually or can I configure multiple networks with LXC / LXD?

Kind regards,

---

### Post by MAFoElffen on 2016-08-08
I could be a smart-Alec and say you can do anything you want ... and that would be somewhat accurate, within your own abilities.

What is your understanding of networking and virtual networking?

Ask yourself, what is your network segments? What are your broadacst domains? Why do you have the segmentation in the first place? That will give you and idea on what needs to be where, and your topology (in virt, that may be just logical).

Next, on topology, do you need your segments on different NID's, or can diffrent vlan ID's be enough to do what you need to do?Presently from your first post, you siad you have a bridge (br0) so I knwo you have 2 NIC's(right?) I host, what also has lxbr0. Than br0.

To rout, you coulld between or elsewhere, you can do that via a virt router aplliance or through one (or more) of the vm guests.

Tell me a little mpre about the above question and I can be a little less general.

---

