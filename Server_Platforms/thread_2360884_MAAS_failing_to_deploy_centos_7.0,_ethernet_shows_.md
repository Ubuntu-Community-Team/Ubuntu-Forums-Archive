---
title: "MAAS failing to deploy centos 7.0, ethernet shows down"
date: 2017-05-09
forum: Server Platforms
---

### Post by bigtexun on 2017-05-09
I'm running MAAS [COLOR=#333333][FONT=Ubuntu]Version 2.1.3+bzr5573-0ubuntu1 (16.04.1).  I'm deploying to an HP Proliant DL360 G7 for my testing.  Eventually I will go into production with a mix of 5 year old HP proliant 360's and 380's of the G7 vintage, as well as a much larger stack of more contemporary SuperMicro systems.  Obviously I'm just getting started working with MAAS, and I'm using one node to test against until I'm ready to go into production with a larger stack.

The setup was smooth, and after a couple of false starts, the main issues blocking success with Ubuntu were network configuration related.  Deploying Ubuntu using the stock distributions is a thing of beauty!  Everything works flawlessly out of the box.  The only areas I had issues with was when I was trying to deploy into multiple subnets, and when I was using some machines out of the e-waste pile that were proliant G6 vintage. Once I simplified the network design, and moved to more current and supported hardware things started clicking right along. 

Once I had my network design established, I did a fresh install of ubuntu 16.04.1 with MAAS.  I then confirmed that the Ubuntu images installed successfully every time  onto Centos.

I'm using the stock configuration, with the stock Centos images (7.0 and 6.6).  These are the images already "supported" in the UI, all I have to do is check the box on the image page to cause them to be loaded into the local repository.

When I try Centos 6.6, deployment is successful. 

Centos 7.0 appears to think the interface enp3s0f0 is down...  This is the eth0 inteface under Centos 6.6.  Obviously if the ethernet seems to be down, DHCP is probably not going to work, and the install process will grind to a halt.  Of course this also means that there is no visible syslog messages appearing on the MAAS server.

The interface is not down, it is the same physical node that works fine under all other install images.  To eliminate random set-up flaws I am using the same node for all image testing, and it is working great for every OS except centos7.

If the Centos 7 image missing a working ethernet configuration?  Or is this a network driver issue?


[/FONT][/COLOR]

---

### Post by bigtexun on 2017-05-10
Ok, I found the problem...  Centos 7 defaults to all interfaces disabled.  You must manually enable an interface during the install (or after first boot) if you want a network.  Of course in MAAS, first boot is when the deployment scripts pull the rest of the installation over the network, including the ssh key so that you can log in over the network the first time.  And in that scenario, you have no way to log in at the console until after you have logged in over the network (which is impossible).  

This is a "working as designed" issue for Centos 7.  It is #2 in the Centos 7 FAQ.

I'm assuming that someone put code in MAAS to turn on the network for a Centos 7 deployment (as why would they include centos 7 as something directly supported in the default MAAS install?).  But centos 7 doesn't use the normal "eth0" name for the first disabled interface, rather it uses a hardware name that is probably different for every ethernet chipset/driver...  So unless the script is written to find the names of all possible ethernet interfaces and turn them all on, it will probably only work for the machine the script was tested on, and few others.

I knew that eventually I was going to have to dig into the MAAS deployment scripts and make them my own, but that will make deploying massive numbers of MAAS systems a larger pain in the neck, I would much rather leave them at a stock configuration.   I don't think I have the time to wait for Ubuntu to fix MAAS...

---

