---
title: "Open Source Cloud. Where to start?!"
date: 2013-07-18
forum: Virtualisation
---

### Post by CrimsonEclipse on 2013-07-18
I've been given 6 rack servers and would like to make an open source cloud with them. 
Nothing fancy, just something where a few friends and I could make several VM's, and experiment with virtual networks and storage. 

My main problem is where to begin. I have researched a few guides, all seem a bit different and a tad overwhelming. 

The idea is to use Open Stack but do I use the UBUNU 13 and the JUJU or use the downloads on Open Stack, or MAAS, or a number of other tools that are starting to make my head spin. 

I would like a how-to to get the NOVA, KEYSTONE, GLANCE, etc servers running. I am also trying to get a feel on what components require specific resources. Some may be CPU intensive while others might need network bandwidth. 

I just need direction, and ANY help would be greatly appreciated. 


I would happily post pics and updates of the full rig if I can get this to work. 

Hardware includes HP 360's 380's and Dell 1950's.

---

### Post by lukeiamyourfather on 2013-07-18
If you haven't seen this yet, check it out.

[https://help.ubuntu.com/12.04/serverguide/ubuntucloud.html](https://help.ubuntu.com/12.04/serverguide/ubuntucloud.html)

---

### Post by CrimsonEclipse on 2013-07-19
Haven't seen it yet. This will help, thanks!

---

### Post by bmullan2 on 2013-07-30
if you are an Ubuntu user (I assume you are) then you might want to check out the combination of Ubuntu's Metal as a Service (MAAS) and the devops tool - JuJu.

Both can be found on this web page:  [https://juju.ubuntu.com/](https://juju.ubuntu.com/)

You can use MAAS to deploy ubuntu to bare metal machines
Then
You can use JuJu to deploy OpenStack very easily to those machines.   Here is a great YouTube video by an Ubuntu engineer that shows you how its done:   [http://www.youtube.com/watch?v=mspwQfoYQks](http://www.youtube.com/watch?v=mspwQfoYQks)

JuJu now also has a very nice GUI (JuJu-GUI) 

Once you have OpenStack deployed you can then continue to use JuJu to deploy any of the awesome application recipes (in JuJu they are called "Charms") and you can see all of them here:   [https://jujucharms.com/](https://jujucharms.com/)

There is probably anything application server-wise you could think of in the Charm Store

Search on YouTube for other JuJu and MAAS videos or search on Ubuntu.Com

You will have a little learning to do with both MAAS and JuJu ... but FAR less than deploying OpenStack (Nova, Glance, Horizon, etc servers) all separately.

---

### Post by CrimsonEclipse on 2013-08-13
Thanks Bmullan2!

I have briefly scanned juju but didn't have time to properly research it. 

Promised pic. 

Still need to prep the hardware a bit. 

[IMG]http://i.imgur.com/x1nesSm.jpg[/IMG]

Also had to upgrade the wheels. Those cheapie blue ones can't take the 400lb load without flattening.

---

### Post by Montassar_Billeh_HAZGUI on 2013-08-14
Hello,
I have axactly the same idea :)
Where can I find a cheap servers like that?

---

### Post by TheFu on 2013-08-15
If you want to learn OpenStack, you have a steep learning curve.  Lots of moving parts and changes happen constantly.  Start with DevStack on a single system to learn how things fit together.  Also, there are OpenStack groups in many metro areas - mine has 3.  I've never run it, but my business partner is in the middle of a 1,000+ physical server deployment now and he talks about all the ways that it sucks constantly.  The virtual networking is reeking havoc with the corporate networking folks.  They need to merge VLANs in 4 datacenters each at least 500mi apart.  They use puppet for management - that is a completely different headache, but the "recommended solution" by high-powered consultants. Cough.  I'm going an Ansible deployment now instead at a different location.  Puppet to make money consulting, ansible to get things done. Salt is another option for management.  Management is the hard part of clouds.

If you just want an easy way to manage 50 VMs, then **KVM** and **virt-manager** completely rock. Both are in the repos and just as easy to use as VirtualBox.  Virt-manager works over ssh (non-root) and lets you control multiple physical VM hosts. If you have a SAN, you can live-migrate VMs between the physical servers too.

OTOH, I've never looked at juju. Might completely rock.

Which gen are the HPs?  Without VT-x, you are screwed. I doubt any of them support VT-d, so PCI passthru isn't possible.

Found myself with a small Core i7 box recently - probably should play with this "cloud" IaaS stuff myself.

---

### Post by CrimsonEclipse on 2013-08-22
The HP's are G5

Got lucky with someone upgrading. I'm pretty sure that they have VT capability. 

My biggest problem right now is getting time to sit down and get things running.

---

