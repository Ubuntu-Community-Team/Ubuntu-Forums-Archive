---
title: "Installing virtualbox"
date: 2017-09-29
forum: Virtualisation
---

### Post by RobGoss on 2017-09-29
Hello everyone's I was wondering what's the best method to install virtualbox in Ubuntu 16.04

I installed it from the Ubuntu Repository but from what I been reading there's something extra I needed to install as well

I also want to use virtualbox in full screen for demo purposes

Thanks so much for any help with this matter

---

### Post by slickymaster on 2017-09-29
You'll have to install Virtual Box Guest Additions

See this thread: [How to install VirtualBox Guest Additions for Ubuntu 16.04]("https://askubuntu.com/questions/792832/how-to-install-virtualbox-guest-additions-for-ubuntu-16-04#792833")

---

### Post by RobGoss on 2017-09-29
Thanks Slickmaster for the help I will look at that link

---

### Post by SeijiSensei on 2017-09-29
I prefer to use Oracle's own repository for VirtualBox.  See these instructions: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by RobGoss on 2017-09-29
> **SeijiSensei said:**
> I prefer to use Oracle's own repository for VirtualBox.  See these instructions: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

Yes that makes a lot of since I will do just that....Thanks so much

---

### Post by oldos2er on 2017-09-29
Thread moved to Virtualisation.

---

### Post by TheFu on 2017-10-01
I've never used virtualbox on a Linux host, but we just had an installfest here and installed mostly Ubuntu-Mate 16.04 on mainly Windows systems running Virtualbox from the Oracle download location.  Many of the defaults are less than optimal and make no sense with what we know today.  It is a shame they still don't default to 128MB of video RAM and pre-allocated storage.  I saw terrible performance on new Core i7 machines **with** SSDs until we wiped the VM and started over.  At least virtualbox supports virtio for networking, finally.  I didn't see any virtio for disks, which is a shame, even with the e1000 (Intel PRO/1000) virtual hardware being the default.  There are a number of other performance settings we had to change too.

Of course, getting the guest additions installed is pretty important for a desktop, but not so much for a server VM.  Just be certain to read the different license that comes with using the guest additions. It isn't F/LOSS.

<soapbox>
Whenever I see folks using virtualbox on a Linux host instead of KVM + libvirt + virt-manager, I always wonder why?  The graphics support with SPICE through virt-manager is pretty impressive.  Plus Intel is working on shared direct hardware access to the GPU for all guests, which should provide 90% native GPU speeds for VMs too.  Saw a demo about 6 months ago at an Intel F/LOSS conference.  They called it intel gvt-g.  KVM is extremely fast, stable, enterprise-grade virtualization.</soapbox>

It used to be that virtualbox was the least offensive of the desktop-on-desktop VM solutions.  It hasn't been that way since SPICE was included - by - default with virt-manager a few yrs ago.  I find that anything which removes Oracle stuff from my systems is a win, but that is a personal issue, I suppose.

---

### Post by RobGoss on 2017-10-01
This is also my first time using VM I normally use a live desktop for every installation, but I been working on a new project that will require installation very frequently so VM might be a good option

---

