---
title: "Create virtual routers with multipass?"
date: 2023-03-17
forum: Virtualisation
---

### Post by rrlangly2 on 2023-03-17
Hi,

I have two Ubuntu 20.04 instances running in multipass. I would like to make each one of these a router for a LAN, and then have a network segment in between each router. I will then later add VM's to each LAN.

lan1 <--> r1 <--> r2 <--> lan2

Can anyone tell me what needs to be done to make this happen? Am I on the right path by making two Ubuntu instances for the routers?

---

### Post by DuckHook on 2023-03-17
I would recommend a different strategy altogether, using what I think are the proper tools for the job.

Install pfsense or opnsense in just one VM. These are pure router distros. That's what they are built to be and they excel at what they do. From within their user interface, you can define as many sub&#8209;LANs as you want. If creating separate vlans for your VMs (you don't tell us if these will all be on one physical machine so I'm assuming that they are) then pf/opn/sense can be configured to segment your network efficiently.

Using a full Ubuntu server instance as a router is doable, but it's rather like killing a fly with a blunderbuss.

If you want to avoid VMs altogether, then in LXD you can set up two containers to do the same job. You can also set up as many vlans as you want, although I'm not seeing what the point would be in your case. You won't be able to use pf/opn/sense in LXD though.

Last but not least, why Multipass? I always worry about layering on purportedly ease&#8209;of&#8209;use add&#8209;ons to my VMs. Each added bell and whistle increases attack surface which negates one of the most important benefits of VMs in the first place.

---

### Post by rrlangly2 on 2023-03-17
Thanks for getting back.

I'm creating a closed network on my machine to do some testing using an app on each end and require this setup so I can test just the app layer protocol from end-to-end going through these two NAT'd routers. I'm not creating any virtual LAN's. I think pfsense or opnsense would be overkill. I just want routed ip's for my lab env.

The reason I was using multipass is because it seems pretty simple to setup VM's on each end and install my app. It's just the network part I'm trying to simulate by having it routed through virtual routers.

I definitely want to run things as light-weight as possible with a routed network.

---

### Post by DuckHook on 2023-03-17
Then two VMs running pf/opn/sense.

You will still need a vlan between the two routers but that's easy to setup.

I don't doubt that Multipass makes things ***look*** simple, but these sorts of app&#8209;ons actually ***add*** complexity to make things appear simpler. It's your call. I don't see how it impacts what you are trying to do one way or the other.

---

### Post by MAFoElffen on 2023-03-18
+1 with DuckHook.

I do a lot of testing in KVM. I use pfSense and OpenWRT appliances in my Virtual networks. There is a lot I can do, easier with those two type of appliances, to replicate real word networking scenarios.

Easier to make change in that than manually setting routes and having to keep track of individual rules that were set. I mean it's possible, doable and it works, but it more work. Lots easier to use the right toolset.

---

