---
title: "Do you think maintaining a separate machine solely for PFsense is an overkill ?"
date: 2020-01-22
forum: Ubuntu, Linux and OS Chat
---

### Post by linuxyogi on 2020-01-22
Do you maintain a separate machine solely for firewall like PFsense, IPcop etc? I don't. I just enable ufw on my Linux box and rely on my router's firewall.

---

### Post by crip720 on 2020-01-22
For most home users a simple setup is probably more than they need.  The paranoid and banking/business admins need everything they can get their hands on.

---

### Post by linuxyogi on 2020-01-23
Thanks for the reply.
I was interested to know what [**TheFu**]("https://ubuntuforums.org/member.php?u=1037685") thinks about this but he doesn't allow PMs so cant contact him.

---

### Post by kevdog on 2020-01-23
Hmm -- I'm a home setup guy -- and to answer your question I have pfsense running virtualized within a hypervisor.  So I guess this is kind of a mixed case with your scenario with having a separate machine solely for pfsense but also having pfsense run on hardware where there are other VMs running on the same hardware.

Anyway to answer your questions about pfsense -- it would just depend.  How many servers are you running at home?  If there are only a few then probably what you are doing is fine. 
Does your home network require network separation with the creation of VLANs to keep one IoT devices separate from the main devices? (Probably can't do with your setup)
Do you want to control at the router level so that all devices are using DOH rather than configuring this at the individual device level? (Probably can't do with your setup)
Do you need more restrictive firewall rules on your network as a whole than just the firewall you have on your machine?

I'm not criticizing your setup at all, since it's very similar to my own setup that I ran for years -- which worked well.  As time passed and probably because of boredom however I ventured into setting up a more "enterprise-like" network which my first step was adding a comprehensive router into the mix rather than a home grade Linksys/Netgate/D-Link or one provided by your ISP.  I took a lot of time however how to learn how to set everything up -- and unfortunately your time probably means something.  In the end however I'm really happy with the results and there is probably no way I'd go back to home-level networking stuff again.  The knowledge you have acquired in setting up iptables/ufw however is transferrable to the router level since its generally the same concept.  In building my own router from scratch however, I thought it kind of a waste to dedicate and i5/32Gb of RAM strictly to a router (which probably doesn't need these requirements).  I decided to virtualize my pfsense installation so I could run additional VMs on the same machine -- which pro or con forced me to learn about virtualization/hypervisors/etc -- yet another concept I wasn't extremely familiar with.  With big corporate networks with a lot of connected devices I'm aware its frowned up to virtualize router software however for home use where there are less than 10 users, my needs haven't overwhelmed the setup.

---

### Post by linuxyogi on 2020-01-23
> **kevdog said:**
> 
Anyway to answer your questions about pfsense -- it would just depend.  How many servers are you running at home?  If there are only a few then probably what you are doing is fine. 
Does your home network require network separation with the creation of VLANs to keep one IoT devices separate from the main devices? (Probably can't do with your setup)
Do you want to control at the router level so that all devices are using DOH rather than configuring this at the individual device level? (Probably can't do with your setup)
Do you need more restrictive firewall rules on your network as a whole than just the firewall you have on your machine?


I am running absolutely no servers at home. 
No IoT devices.
My ufw rules are
```
# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

```
Also I checked my router at grc.com and it passed the test.

We will be moving to a new home soon. I will definitely consider PFsense then.
Thanks a lot for the reply.

---

### Post by kevdog on 2020-01-23
If you are not running any servers or don't have any specific needs then your setup is probably fine. Just depends if you if have the budget and desire to push your knowledge to learn new things.  I'm not saying these two reasons always justifies the decision.  Good luck with whatever setup your using, at least you're asking questions.

---

