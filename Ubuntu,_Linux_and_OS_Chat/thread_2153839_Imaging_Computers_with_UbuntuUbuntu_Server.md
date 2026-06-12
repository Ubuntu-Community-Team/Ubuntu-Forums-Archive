---
title: "Imaging Computers with Ubuntu/Ubuntu Server"
date: 2013-06-12
forum: Ubuntu, Linux and OS Chat
---

### Post by XgeorgeX on 2013-06-12
I work for a software company that sells whole systems with our software. So when a customer buys our software they get anywhere from 5 to 50 servers/workstations, that run windows as the OS. In our production process we have Windows Deployment Services handling system images. So we have a base image with OS, tweaks, and software for all of our platforms. I really really really hate windows deployment services and I have been looking for a replacement for a while. WDS is used a replacement for an imaging suite that stopped supporting windows OS's after XP so it forced us to move along. I have tried Acronis and Ghost which worked but the licensing is where things start to get expensive. I am trying to find all zero cost options before I hammer on our sales department about adding the imaging costs into our systems costs. 

 So does anyone know of a Linux equivalent to Windows Deployment Services? Essentially what I'm looking for is software that runs on Linux that allows you to capture an image of a computer and deploy that image over the network to multiple clients. How it currently works in WDS is the clients that are going to get an image installed PXE boot to the WDS server, you select what image you want to install, and the image deploys over the network. To capture an image is kind of the same actions but with a lot more details and actions. This type of a flow with a network deployment of the image is a must and it has to be able to capture/deploy both Windows server OS's and Windows workstation OS's. Handling the Windows Server OS's is where I have been finding some issues with imaging software. So any suggestions for a service that could do this running on a Linux server would be greatly appreciated. I had someone a long time ago evaluate CloneZilla, however they said it wouldn't work for what we wanted it for. I'm going to revisit that since I don't really know why it wouldn't have worked but I'm hoping for other suggestions as well. I heard Cobbler might work so that's another application I'll look into.

---

### Post by mips on 2013-06-12
Have a look at FOG & Clonezilla SE

---

### Post by Cheesemill on 2013-06-13
+1 for FOG.

I use it at work to automatically re-image all of our workstations every night as well as deploying machines that are going to be sent off site.

[http://www.fogproject.org/](http://www.fogproject.org/)

---

### Post by lykwydchykyn on 2013-06-13
I've used G4L in the past; I think the techs that took over imaging after me quit using it because whole-disk imaging created problems with duplicate SIDs or something.  Either that, or they just didn't want a Linux-based solution :D.

---

### Post by Cheesemill on 2013-06-13
> **lykwydchykyn said:**
> I think the techs that took over imaging after me quit using it because whole-disk imaging created problems with duplicate SIDs or something.

This issue doesn't exist if you do things properly and run sysprep on the machine before shutting it down for imaging, a new random SID will be created for each machine that's created from the image on first boot.

---

### Post by mips on 2013-06-13
> **lykwydchykyn said:**
> I've used G4L in the past; I think the techs that took over imaging after me quit using it because whole-disk imaging created problems with duplicate SIDs or something.  Either that, or they just didn't want a Linux-based solution :D.

They probably did not know what they were doing I suspect.

---

### Post by lykwydchykyn on 2013-06-13
> **mips said:**
> They probably did not know what they were doing I suspect.

Naw, they're smart guys; they just don't get warm fuzzies from Linux like I do.  That, and I think using WDS or whatever it is let them do some customizing that whole-disk imaging (regardless of platform) couldn't do.  Looks like FOG can do some of that, though.

---

### Post by ppv on 2013-06-13
> **Cheesemill said:**
> +1 for FOG.

I use it at work to automatically re-image all of our workstations every night as well as deploying machines that are going to be sent off site.

[http://www.fogproject.org/](http://www.fogproject.org/)

If you don't mind, would you tell what would be a use case where ALL workstations would be reimaged EVERY night...like why do you do so.

---

### Post by XgeorgeX on 2013-06-13
Thanks for the responses. WDS does a have a cool way of imaging where it isn't taking a whole disk image but I will essentially run a windows install then use sys prep to get everything up and running to match the system you captured from. So you don't hit the SID issue because windows installs like normal. The original imaging software we were using like 7 years ago took a direct HD image and it had an option to update the SID during a phase kind of like sys prep after the image was deployed, but we found a bug where it wasn't actually updating the SID after deploying the image. We had a very large customer blow up and blame the SID for it, which lead to a long debate to weather SID's actually matter in a windows domain environment. We found, after getting some high level MS people involved, SIDS don't matter until you have a "large domain". This customer has thousands of users and computers so yep they hit an issue with the SIDs not being unique from out imaging process. We also didn't find what "large domains" really meant which was kind of lame but the end conclusion was that customer had a large enough domain to make the SID actually matter. 

I'll take a look at FOG, CloneZilla, and G4L to see how they work. I get psyched on getting Linux stuff wherever I can so if I can replace WDS with something using Linux and it works better that would be fantastic.

---

### Post by Cheesemill on 2013-06-13
> **ppv said:**
> If you don't mind, would you tell what would be a use case where ALL workstations would be reimaged EVERY night...like why do you do so.

A few reasons.

First of all, all of the Windows and software updates are applied to the machine we use to take the images from. Re-imaging the machines is often much quicker than than applying the updates locally, especially with large updates and service packs.

It guarantees that ***all*** of the workstations on the network are in a consistent, virus free state. Even if something nasty does slip through it won't be there for long.

No matter how many times you tell them you always get users who insist on saving documents onto the local drive instead of the network shares like they're supposed to. Wiping the drive every night is the quickest way to break this bad habit :)

---

### Post by ppv on 2013-06-16
> [COLOR=#000000]Wiping the drive every night is the quickest way to break this bad habit[/COLOR]
Lol.

and thanks for the reply : )

---

