---
title: "Optimal way to create KVM guests?"
date: 2013-09-22
forum: Virtualisation
---

### Post by KillerKelvUK on 2013-09-22
I've recently stood up KVM on my home server and have been playing around trying to find the optimal way to create an Ubuntu Server guest.  I've used virt-manager (gui) and vmbuilder (cli) and can create vm's fine with either/both but I'd like the guests to meet the following requirements...


[LIST]
[*]Storage must use my LVM configured as a storage pool on virsh.
[*]The guest kernel must be the "virtual" variant and not the "generic" variant.
[*]Unattended install.
[*]All locale and keyboard configurations accurate for my needs (en_GB).
[*]Smallest guest install footprint possible.
[/LIST]

I've had varying results trying to achieve the above, for example...


[LIST]
[*]vmbuilder pros
[LIST]
[*]Fast guest creation (network speed dependant)
[*]Can specify installation parameters in .vmbuilder.cfg to make creation nearly completely unattended.
[*]The required 3.2.0-53-virtual kernel is installed.
[*]Unattended for the most part.
[/LIST]

[*]vmbuilder cons
[LIST]
[*]bug prevents the creation directly into an LVM, so far I can only create a .qcow2 image file which I then need to convert into raw format afterwards to put it on my LVM.
[*]Whilst I can configure the locale for the guest in the .vmbuilder.cfg file I can't find a way to preset the keyboard so need to complete a 'dpkg-reconfigure keyboard-configuration' on first login.
[*]bug prevents a scripted firstlogin process to correct the keyboard and other settings.  (Unless root account login is enabled and used for first login.)
[*]bug prevents using an iso file locally as the install source.
[/LIST]
[/LIST]


[LIST]
[*]virt-manager pros
[LIST]
[*]Used a kickstart file to create an unattended installation.
[*]Created the guest directly within my LVM storage pool.
[*]All necessary locale and keyboard configurations correct as per the kickstart config.
[/LIST]

[*]virt-manager cons
[LIST]
[*]I can't find a way to force the install to use a "virtual" kernel so "generic" kernel is installed and I have to change this manually post install.
[*]Not the fastest installation, certainly can live with it but was very noticeable in comparison with vmbuilder.
[/LIST]
[/LIST]

Has anyone come up with any other approaches to this or can you help resolve some of the points I have listed as my "cons" against each tool above?

Thanks,

K

---

### Post by TheFu on 2013-09-24
Have you considered using a cloning technique, instead of a full install?
To safely clone, just the MAC and hostname need to be modified, rihgt?

---

### Post by CharlesA on 2013-09-24
> **TheFu said:**
> Have you considered using a cloning technique, instead of a full install?
To safely clone, just the MAC and hostname need to be modified, rihgt?

I've always had it give me a new MAC when I cloned a VM. Of course, that was back when I was using VBox, so I'm not sure if it is the same thing with KVM, but other than that, you just need to change /etc/hostname and /etc/hosts then reboot/restart networking.

---

### Post by KillerKelvUK on 2013-09-25
Thanks good suggestion, I've just tried this using virt-manager and it would seem this handles the unique mac assignment per clone which just leaves what you 2 have called out plus the IP config. Seems like a good compromise to the issues I'd documented.

---

### Post by TheFu on 2013-09-25
> **KillerKelvUK said:**
> Thanks good suggestion, I've just tried this using virt-manager and it would seem this handles the unique mac assignment per clone which just leaves what you 2 have called out plus the IP config. Seems like a good compromise to the issues I'd documented.

After cloning, then I'd point my ansible server at the box and reconfigure as desired for the specific tasks.  Just brought up a new KVM host (ok, KVM isn't installed on it yet) and I'm building on my default server settings, tasks and configs to make a new KVM server set of tasks.  Shouldn't take too long to have a 100% reproducible "bring a new KVM host up" playbook (they call them that in the Ansible world).  Best of all, it will work every time by starting from a box with reasonable disk config and ssh server, that's it.

---

### Post by KillerKelvUK on 2013-09-26
Just been to school with "ansible"...had to google/wiki it!  Very good :-)

---

### Post by TheFu on 2013-09-26
Ansible is the easiest of the CM tools that I've found. Most of us work through a period of scripting, before we discover that we've been reinventing the wheel.

Of course, Ansible isn't perfect. Chef, puppet, rexify, saltstack are other F/LOSS options ... each has a place for different needs.  I've read that ansible isn't as mature in cloud deployments as some of the others We avoid cloud stuff due to security concerns, but for people with cloud-centric deployments with less stringent security needs, another tool might be a better choice ... or be prepared to write a bunch of modules.

If you learn by watching videos, the Ansible group put out a new one last month that is a great overview. Sometimes wrapping our mind about some of the complexities isn't easy. It will help any lurkers with 15 min.

---

### Post by KillerKelvUK on 2013-09-26
Will look out for the vid and take a closer look but from a quick skim on their site the conf mgt front-end looks pretty similar to WebVirtMgr which I gave a test run the other month...too basic for my likes but Ansible may be worth the time.

---

### Post by TheFu on 2013-09-27
> **KillerKelvUK said:**
> Will look out for the vid and take a closer look but from a quick skim on their site the conf mgt front-end looks pretty similar to WebVirtMgr which I gave a test run the other month...too basic for my likes but Ansible may be worth the time.

I dn't know anything about WebVirtMgr - seems like an attempt to make virt-manager a webapp.   Ansible doesn't have anything to do with something like virt-manager. Completely different uses.  I use either virt-manager or virsh to start/stop machines.  The remote connection is over ssh, so if I have a virt-manager capable client with me (it is a GUI), I'll use that with key-auth.  I've never needed to setup a VM when I was outside the trusted LAN, however.  

Using a web server for VM management just seems non-secure and wrong to me, but I can see how others might desire control from a web server. Securing something with ssh is 2nd nature to me.  Securing something with a web server ... well, I always assume a web service can AND will be hacked.

Perhaps WebVirtMgr is different, but cpanel, WebMin, phpMyAdmin and other web-front-ends have all been hacked.

---

### Post by CharlesA on 2013-09-27
> **TheFu said:**
> 
Perhaps WebVirtMgr is different, but cpanel, WebMin, phpMyAdmin and other web-front-ends have all been hacked.

You can limit that by only allowing certain IP addresses access to the control panel, but imho adding extra stuff for convenience will almost always add extra attack surface.

It's the convenience vs security thing.

---

### Post by KillerKelvUK on 2013-10-01
WebVirt is pretty limited in features, no where near compares to full blown virt-manager.  Understand its a security risk and need to weigh up the balance of security vs. convenience but I've yet to find a web frontend thats a good mix of light-weight and just enough features to be worth the hassle and for those with concerns, the risk.  That said the dev on WebVirt seems to be pretty much working, I hit a bug on the install and posted it on git, quick response and a couple of weeks later a fix was rolled in properly.

---

