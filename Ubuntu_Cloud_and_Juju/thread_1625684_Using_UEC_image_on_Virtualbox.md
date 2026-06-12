---
title: "Using UEC image on Virtualbox"
date: 2010-11-19
forum: Ubuntu Cloud and Juju
---

### Post by rainbowsheep on 2010-11-19
Hi,

Anyone know if it's possible to use an UEC image in Virtualbox?

I'm using the Ubuntu-provided AMIs on EC2, but would like to have a local version of the AMI running on my local Virtualbox.

Any ideas?

Thanks,
Joe

---

### Post by marrusl on 2010-11-19
I'm not sure about VirtualBox, but you can run your images offline with KVM:

[https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud](https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud)

Regards,
Mark

---

### Post by rainbowsheep on 2010-11-19
> **marrusl said:**
> I'm not sure about VirtualBox, but you can run your images offline with KVM:

[https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud](https://help.ubuntu.com/community/UEC/Images#Run%20Images%20locally%20without%20a%20Cloud)

Regards,
Mark

Hm, thanks.  I'm using Vagrant ([http://vagrantup.com/](http://vagrantup.com/)) which uses Virtualbox.  I'm trying to get a Vagrant+chef setup that matches what the Amazon AMI would look like.

---

