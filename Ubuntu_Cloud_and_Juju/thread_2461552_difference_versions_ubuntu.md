---
title: "difference versions ubuntu"
date: 2021-05-03
forum: Ubuntu Cloud and Juju
---

### Post by pcfreak492 on 2021-05-03
Hi I have a question about two images of ubuntu sometimes someone knows what the difference is between bionic-server-cloudimg-amd64 and the ubuntu-18.04.4-server-amd64

---

### Post by blackbird34 on 2021-05-03
I'd say the first is for deploying on cloud instances, whereas the second would be for deploying on your own physical hardware on your own premises.

---

### Post by MAFoElffen on 2021-06-10
> **blackbird34 said:**
> I'd say the first is for deploying on cloud instances, whereas the second would be for deploying on your own physical hardware on your own premises.
Sort of needed expanded on...

Ubuntu's Cloud Images are vanilla pre-installed server images that already have cloud-init installed. Good as a template. They have been custom engineered to be optimized/certified cloud images.

I think the second image you referred to is the full server installation media, which would install to where you wanted. Physical metal, virtual, cloud, etc. You you would have to install, configure and tune that yourself. Doing that on your own, they are not automatically "certified" as optimized by Canonical for cloud computing. Just because an OS is approved and certified for, does not mean the user involved configured it well for the environment, right? (Lot's of variables.)

It's like when you pick Docker Containers. Some have more bells and whistles pre-attached as a starting point and/or need less investment to get to where you want to be. And some applications for commercial use, if they are going to provide their support, require that they be run on certified server images.

I hope this answered your question.

---

### Post by TheFu on 2021-06-10
The cloud images don't prompt to setup users or passwords, IME.  That makes them suitable for enterprise deployments where the installed image can be mounted pre-login to setup ssh keys.  Normally, that would be automated by the cloud service provider.  This sort of image isn't for regular people wanting to try out Ubuntu Server who aren't great at modifying system files from outside the environment.

---

