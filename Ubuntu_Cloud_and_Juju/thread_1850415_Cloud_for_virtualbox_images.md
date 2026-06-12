---
title: "Cloud for virtualbox images?"
date: 2011-09-26
forum: Ubuntu Cloud and Juju
---

### Post by camelinahat on 2011-09-26
Hi Folks,

I currently have a workstation which is used as a host for a number of virtualbox images. There will be new images to be added to the load and to ensure I have maximum uptime and best load distribution I was thinking of using a 2nd, identical workstation to take some of the load. My thought was that if one of the systems required additional updates etc to the host machine then the load could be transferred to the 2nd machine while updates etc took place. 

My question is, is this possible? Can virtualbox appliances be loaded as images in a cloud? Would I need to have one image to act as a virtual box host, and then in turn have the images running within that?

I'll be honest, I'm not entirely up-to-scratch on clouds, and their uses. Perhaps they're not designed to have multiple small resources shared between a few larger ones but rather one large resource shared between multiple smaller ones.

I'd appreciate any help which can point me in the right direction or if even what I want to do is possible/advisable. 

Matt

---

### Post by SecretCode on 2011-09-26
After reading your post a couple of times I'm not sure if you are referring to "cloud" as remote server sites hosted by someone else (which is what I would say the main usage is) - or hot-swappable capability between local servers.

I assume it's the latter, because running a vm across a remote connection would be pretty bad. And you do mean live running vms not just backups?

How many vms are we talking about and how many users / connected devices? How are the vms accessed - by IP address? by host name? some other way?

Is the second workstation in the same place? Could it share storage - either with the vm images on a SAN, or in the most basic case by moving a hard drive?

In principle there is nothing wrong with what you are suggesting.

---

### Post by camelinahat on 2011-09-27
> **SecretCode said:**
> After reading your post a couple of times I'm not sure if you are referring to "cloud" as remote server sites hosted by someone else (which is what I would say the main usage is) - or hot-swappable capability between local servers.

I assume it's the latter, because running a vm across a remote connection would be pretty bad. And you do mean live running vms not just backups?

How many vms are we talking about and how many users / connected devices? How are the vms accessed - by IP address? by host name? some other way?

Is the second workstation in the same place? Could it share storage - either with the vm images on a SAN, or in the most basic case by moving a hard drive?

In principle there is nothing wrong with what you are suggesting.

For 'cloud' it was to host a private cloud between two workstations physically located and connected on an internal network.

We'll use a rough estimate of 8 virtual machine images, probably won't be quite that many but just to be on the safe side. Some virtual machine images have a public IP and are accessed via dns, some have a private non routable IP. The vlan setup and configuration isn't a problem and is already done. I just wanted to know if setting up a private cloud between two machines would give me the redundancy between them to spread the load (potentially dynamically depending on needs) between the two machines (ie 4 images on each workstation). The imagines do not have heavy loads, only accessed by 4 or 5 individuals, and some will make connections out of the network with a couple megs of snmp traffic an hour.

Idealy rather than having two separate machines locked into the 4 images I put on each, I'd like to have one 'cloud' to administer the 8 images. So if one workstation failed the images could run, albeit a little slower, on one workstation until another could be added to help offset the load. (Same if I wanted to run system updates to one of the workstations, transfer the load to one temporarily to allow updates to complete etc).

I'm not sure on how it needs to be accomplished however. Do I have one cloud image which runs virtualbox with the 8 appliances? Can the virtualbox appliances be converted to cloud images to manage that way?

Or is my best bet to forgo a cloud configuration and find an alternative solution for sharing (such as via a SAN) the virtualbox images between the two workstations?

---

### Post by SecretCode on 2011-09-27
Beyond my expertise, but I think VirtualBox has, or will have in an imminent version, the ability to move a running vm from one box to another. I suggest asking at forums.virtualbox.org. 

Since each vm has its own IP address and will keep it whichever host it moves to, I don't see a problem with routing ... but you'll need to be careful. After updating a host, you'll need a test phase to ensure your vms are still fine ... and this might need a different IP address. Unless the services can withstand downtime.

I'm not seeing this as a "cloud or not" question, just a standard network-design-for-availability question. A cloud service has to deal with this kind of thing, but having it doesn't make a cloud - for example, I'm not seeing that you need rapid, automated provisioning.

---

### Post by camelinahat on 2011-09-27
> **SecretCode said:**
> for example, I'm not seeing that you need rapid, automated provisioning.

That is correct. I'm not looking for these type of services from a cloud, but more so the multiple host systems acting as 1 large host system handling the virtual machines. I know in essence a cloud setup does that as well. Multiple images managed between multiple hosts via one controller. But as indicated I'm not very experienced with setup or using a cloud so wasn't sure if converting the virtualbox appliances to cloud images and loading them would be an appropriate option or if it would be overkill for what I want to accomplish.

At this point I think my best bet will be to use multipe hosts and a NAS of some sort to store the image files and manage loads manually. Thanks for the feedback SecretCode.

---

