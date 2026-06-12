---
title: "Virtualization questions"
date: 2011-12-05
forum: Virtualisation
---

### Post by PommeVerte on 2011-12-05
Hello everyone,

I'll be setting up a server sometime soon and seeing as I'm relatively new to virtualization I was hoping some of you guys could help out with some of my questions.
I'm not expecting anyone to walk me through this but if you could link me to the proper chapters in documentation and such I would be immensely grateful.

Here's the setting:

I'll have one physical machine running ubuntu server. On this machine I would like to virtualize 6-7 machines also running ubuntu server. No graphical interface needed. They're simple LAMP web servers with additional image conversion libraries which may (or may not) chew resources.
Each machine will be identical as far as the installation goes (minus network configuration).
My first issue comes from the fact that I do not know how these machines will have to perform, or what stress they will be under. It may vary from one week to another.
The other issue is that I have to be able to reduce/raise hard disk space for these machines easily.
So my questions are as follow:

1- Is there anyway I can set performance settings for all the virtual machines at once and let the server decide how many resources a server should get depending on it's needs at a given moment. ie: have them share their resources.

2- Is there a way to have all these clients share their installation instead of duplicating them each time.

3- How would I go about making a good system in which I can easily increase hard disk space for each machine if need be. I'm guessing I could probably make another virtual disk and mount that into my clients. But maybe there's a better way.

4- How much ram/etc. Should my physical server keep to run all of these (ie: so I don't attribute too much to the virtual machines)

Thanks a lot for your help. I think KVM is default for ubuntu but if you think there's a better option for my needs let me know.

---

### Post by coldraven on 2011-12-05
This is not my field but I do keep up with the news, Openstack seems to be the in thing.
Also Landscape for all your admin needs, but I think you have to pay for that
[https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

---

### Post by CharlesA on 2011-12-05
I use VirtualBox instead of KVM, since that's what I am used to, but generally - VM software will allocate resources when the VM is started instead of allocating them dynamically. 

Give each guest more disk space then you think you'd need. I have a Ubuntu server install in a VM with 8GB of HDD space and 512MB of RAM.

I try to give the host at least 25% of total memory, so if I have 8GB of RAM, I would try to allow the host to have 2GB of memory for it to use.

---

### Post by PommeVerte on 2011-12-08
> **coldraven said:**
> This is not my field but I do keep up with the news, Openstack seems to be the in thing.
Also Landscape for all your admin needs, but I think you have to pay for that
[https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC)

Thanks, actually looks spot on. Though considering I only have one physical server at the moment, wouldn't this be relatively heavy? Compared to simply running KVM for instance?

---

### Post by PommeVerte on 2011-12-08
> **CharlesA said:**
> I use VirtualBox instead of KVM, since that's what I am used to, but generally - VM software will allocate resources when the VM is started instead of allocating them dynamically. 

Give each guest more disk space then you think you'd need. I have a Ubuntu server install in a VM with 8GB of HDD space and 512MB of RAM.

I try to give the host at least 25% of total memory, so if I have 8GB of RAM, I would try to allow the host to have 2GB of memory for it to use.

Thanks! Unfortunately I can't give the guests more hard disk than they need because that can change weekly and go anywhere from 10gigs to 500gigs of added space. (I might be exaggerating a bit but that's the main idea). So I really need a system that is maintainable relatively easily.

I'll keep the 25% resources in mind.

---

### Post by mountainman1 on 2011-12-12
CPU:as processor speeds boost, and as twin and also quad core grow to be much more and much more eye-catching price-wise, you'll want to look at receiving a rapid CPU for the pc.
Memory: A further notable thought when operating VMs is their memory use.
Disk: We require to generate positive that we've got sufficient disk area on our host device to host the many virtual disks of our visitor devices and One particular with the significant bottlenecks of making use of VMs may be the disk I/O, in particular on high-capacity VMs
Network: Despite the fact that not immediately linked towards the VM functioning functionality, in manufacturing environments exactly where Virtual Server will probably be made use of plus the visitor devices will in fact be manufacturing servers, network interface cards (or NICs) are really essential.

---

### Post by CharlesA on 2011-12-12
If you are serious about doing virtualization, you would want at least a quad core with a boatload of memory and drive space.

If you aren't always looking into KVM, you might want to consider it.

---

### Post by JKyleOKC on 2011-12-13
> **CharlesA said:**
> If you are serious about doing virtualization, you would want at least a quad core with a boatload of memory and drive space.That depends to a significant degree on just how you want to use virtualization.

I consider the absolute minimum for operation of a single VM to be dual-core CPU and 2 GB of RAM. Disk capacity depends on the number of VMs you want to create, and the size of the files they will be working with. I normally create each primary virtual disk as 30 GB, which is adequate for my needs, and while I have a number of VMs on this system, hardly ever have more than one active at a time (the others lie dormant, in saved state). Thus a dual-core CPU and 3 GB of RAM, plus a 500-GB hard drive, is plenty for my needs.

However if one plans to have a dozen or more VMs all running at the same time, then much more capable CPUs and lots more RAM would be needed. In such a situation, the rule is "too much isn't nearly enough" so get all that you can afford.

As they taught me at Fort Sill back when training me as an artillery observer nearly 60 years ago, "It all depends on the situation, sir!"

---

### Post by CharlesA on 2011-12-13
> **JKyleOKC said:**
> That depends to a significant degree on just how you want to use virtualization.

That's true. I've been running 3 VMs on a dual core box and it's been dog slow at times. As a rule, I try to give each VM a core and at least 512MB of memory (usually a GB).

---

### Post by JKyleOKC on 2011-12-13
Yep, I've occasionally run two at the same time on this box and the loss of speed is noticeable. That's one reason I avoid doing so as much as possible. Another reason is that I have the same VDI file assigned to several VMs as the slave HD, and having it opened simultaneously by different VMs causes data loss from it. It's not even supposed to be possible, but I found (by accident) that it can be done if one of the VMs is dormant when the other is booted, and then the first one made active again. Internal buffering of the directory data is what caused the data loss. I'm careful not to open both at the same time, any more; if I need to transfer a file from one to the other, I use a shared host folder and have only one VM active at a time.

I've also learned the hard way that vbox caches its writes to the VDI file for an amazing amount of time. It doesn't affect operation usually, and can be mystifying. One of my homebrew programs would apparently freeze (totally, neither mouse nor keyboard would respond inside the VM but operation outside the VM was normal) after writing a few thousand lines of data to an output file. It would thaw, though, after a full minute or so. I finally found that by forcing buffer flushes after every hundred lines or so, the freeze can be prevented.

---

### Post by CharlesA on 2011-12-13
That sounds like a nasty thing to deal with. :(

---

### Post by Dangertux on 2011-12-13
> **PommeVerte said:**
> Hello everyone,

I'll be setting up a server sometime soon and seeing as I'm relatively new to virtualization I was hoping some of you guys could help out with some of my questions.
I'm not expecting anyone to walk me through this but if you could link me to the proper chapters in documentation and such I would be immensely grateful.

Here's the setting:

I'll have one physical machine running ubuntu server. On this machine I would like to virtualize 6-7 machines also running ubuntu server. No graphical interface needed. They're simple LAMP web servers with additional image conversion libraries which may (or may not) chew resources.
Each machine will be identical as far as the installation goes (minus network configuration).
My first issue comes from the fact that I do not know how these machines will have to perform, or what stress they will be under. It may vary from one week to another.
The other issue is that I have to be able to reduce/raise hard disk space for these machines easily.
So my questions are as follow:

1- Is there anyway I can set performance settings for all the virtual machines at once and let the server decide how many resources a server should get depending on it's needs at a given moment. ie: have them share their resources.

2- Is there a way to have all these clients share their installation instead of duplicating them each time.

3- How would I go about making a good system in which I can easily increase hard disk space for each machine if need be. I'm guessing I could probably make another virtual disk and mount that into my clients. But maybe there's a better way.

4- How much ram/etc. Should my physical server keep to run all of these (ie: so I don't attribute too much to the virtual machines)

Thanks a lot for your help. I think KVM is default for ubuntu but if you think there's a better option for my needs let me know.


1 - Yes it's called ballooning, depending on the hypervisor you choose it will be an option when you create the VM (Xen manages this well)

2 - Yes you can create a new instance from a base installation image with most (if not all) popular hypervisor technologies (consult the documentation for whichever you choose)

3 - You will have to change the images each time you want them to have more space, or allow them to balloon disk usage as well (this is usually not recommended) and just add additional physical storage.

4 - The hypervisor itself doesn't need that much memory, I've seen systems which dozens of instances running the hypervisor with only 2 GB or so of ram. The guest instance is what will need access to resources. The hypervisor itself only performs basic functions.

I like Xen, or KVM. KVM is a little more friendly with Ubuntu, however Xen has slightly better performance in my opinion. It's a preference thing though.

---

### Post by JKyleOKC on 2011-12-13
> **CharlesA said:**
> That sounds like a nasty thing to deal with. :(It definitely was. Fortunately, that virtual drive is an archive of past work, so the data loss was nearly so catastrophic as it would have been had current projects been lost. I'm glad to have learned the lesson at such low cost!

---

