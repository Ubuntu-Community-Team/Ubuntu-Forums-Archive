---
title: "Key Topics for KVM Virtualization Presentation?"
date: 2014-03-26
forum: Virtualisation
---

### Post by TheFu on 2014-03-26
Volunteered to present on virtualization at a few metro area technology meetings in the next few weeks.  I've been presenting on Virtualbox the last 3 yrs around the world (mostly on desktop tuning), but this is my first time attempting to do anything for KVM.  IMHO, KVM is a better all-around solution now, beating out VirtualBox, Xen, ESX/i, .... especially where servers are involved, but the desktop works well too.

The audience will be varied from college CS students to IT professionals who are expert at running other VM technologies the last 8 yrs in large scale environments (1,000+ physical servers).

I plan to keep this beginner level, small-biz related and want it to be hands-on, so the attendees can follow along on their Linux laptops to get a plain server up with 1 or 2 server VMs.

90 minutes is the time limit. I think 60 minutes will be necessary for the hands-on stuff, so that doesn't leave much time for virtualization background.

So, what are the key, don't miss, things you would want included in a *KVM VMs for Dummies* talk?

Lastly - I'm planning to use the **14.04 Server Beta** for this. Grabbed a nightly (tested) build a few days ago and everything seemed to work as expected on my chromebook (yes, a $200 chromebook C720 CAN run KVM and it isn't slow).  Will be using a Core i5 laptop for the presentation.

Current slide titles are:

[LIST=1]
[*]Running VMs w/ KVM + virt-manager
[*]Abstract
[*]About Me
[*]Company Marketing Slide  <--- marking guy mandated.
[*]About You   <--- ask audience how they currently use VMs
[*]100 Ways   <--- more than 1 way to do this
[*]KVM <--- name, key parts of KVM, stability
[*]LibVirt <--- manage almost any virtualization hypervisor
[*]Goals for Tonight  <--- hostOS config, 1+ clientOS installs
[*]Virtualization Overview  <--- generic hypervisor slide
[*]The Setup
[*]Requirements  <--- VT-x/AMD-v
[*]Performance Considerations
[*]Install a few packages  <--- only 5 
[*]Linux Bridging  <--- interfaces file changes
[*]No Guest Additions!
[*]Live Demo / VM Setup  <--- ssh-keys, then virt-manager
[*]Private Cloud for You
[*]Requirements for a Cloud
[*]Goodnight
[/LIST]

Feels like I'm missing something really important.

Here is the [Running VMs w/ KVM + virt-manager ]("http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html")presentation.  Would really appreciate comments prior to April 10th 2014.

---

