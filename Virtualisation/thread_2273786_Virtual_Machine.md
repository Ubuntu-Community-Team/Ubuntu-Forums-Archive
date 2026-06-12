---
title: "Virtual Machine"
date: 2015-04-15
forum: Virtualisation
---

### Post by cameron24 on 2015-04-15
Hi,
I'm pretty new, and I'm trying to learn the ups and downs of Linux systems. I want to use a virtual machine as a learning tool, and I have already downloaded the machine itself. However, I still need to put an OS on it, and I was wondering the best way to download Ubuntu onto a virtual machine from the internet.
Thanks!

---

### Post by howefield on 2015-04-15
Thread moved to the "*Virtualisation*" forum.

---

### Post by ajgreeny on 2015-04-15
I am not sure what you mean when you say you have downloaded a virtual machine and then say that you want to put an OS on it.

Do you really mean you downloaded a virtual machine, ie an OS, or are you talking of the virtualisation software to run it, such as vmware or virtualbox?

---

### Post by cameron24 on 2015-04-15
I downloaded VirtualBox software, and it let me set up a machine (it will even let me power on said machine), but of course, it won't run without an OS. So my question is, how do I go about downloading Ubuntu for a virtual machine?

---

### Post by sammiev on 2015-04-15
> **cameron24 said:**
> I downloaded VirtualBox software, and it let me set up a machine (it will even let me power on said machine), but of course, it won't run without an OS. So my question is, how do I go about downloading Ubuntu for a virtual machine?

If I am reading you correctly, down load the ISO and selected the ISO from the menu within VB - create or add new OS.

---

### Post by cameron24 on 2015-04-15
Where/how do I download the ISO? How exactly does that work? Will it save like a zipped file that I can access in my file manager etc?

---

### Post by sammiev on 2015-04-15
Depends on the Ubuntu flavor you want to download. If it's Ubuntu 14.04.2 then it's [here]("http://releases.ubuntu.com/14.04/").

Usually it get saved in the Downloads folder. Then you point your VM to the folder that contains your ISO ( Ubuntu 14.04.2 ) and it will install the ISO into the VM.

---

### Post by TheFu on 2015-04-16
There are lots of youtube videos with how-to guides for this.
Think of the VM as a real computer. You have to setup the HW to be seen by the guestOS - i.e. the VM.
That means you will need to install the OSes you want into the VM.  Like all Linux distros, Ubuntu has free downloads available as ISO files.  An ISO file is really just a CDROM/DVD image, but you can tell the newly created VM to boot off this ISO using the DVD/CDROM device in the VM.  That will launch the installer automatically.  Just remember, your real hardware has little to do with what the VM is presented.

Practice making a VM or three. Get comfortable with the different settings. Search for performance guides or you could end up creating a VM that runs slowly.

Distrowatch.com has links to many different Linux versions from the official sites.  Go look around a little. Different distros have different uses. For online banking, I use tinycorePlus. For servers, I use Ubuntu Server. Find which distros work for you. 99% are free and open source - F/LOSS. A few ask for payment, and about 5 demand payment.

There is a caution.  Avoid GUIs that require 3D accelerated graphics to work. This has caused issues in the past for virtualized machine performance.

There are specific settings and techniques to make life easier depending on the hypervisor selected. Which did you choose to run? You'll get better answers to your questions if you always state that -  there are about 5 real, viable, good, choices in hypervisors.  For running desktops-on-desktops, virtualbox is probably the most popular. It is free for non-commercial use.  If you load the guest additions, be certain to read the license agreement carefully. KVM is good for server-on-server and remote desktop-on-server situations. I migrated from virtualbox, Xen, ESXi, to KVM in 2010-11 for a number of reasons. Stability chief among those reasons, but the supporting organization philosophy matters to me as well.

Oh - a common question is when the Ubuntu/Linux installer asks to wipe the entire drive - go ahead and say yes.  Inside a VM, it only sees the virtual disk that you created as a VDI file, not the real hard drive.  Start out with a 15G VDI file, assuming you are using virtualbox.  15G for storage is enough for most VMs, certainly enough to get the feel when just starting out.  Creating a VM is not a big commitment - takes just 15 minutes to create and install most distros.  Don't like it? wipe it completely.

You'll get comfortable doing this the more you practice, just like with most things.

---

### Post by cameron24 on 2015-04-17
Thanks! This was a big help.

---

### Post by fidel5 on 2015-05-03
Here you have a step-by-step guide on how to create a virtual machine and then install Ubuntu inside of it: [http://oracle-virtualbox.com/install-ubuntu-on-virtualbox/](http://oracle-virtualbox.com/install-ubuntu-on-virtualbox/)

---

### Post by TheFu on 2015-05-03
> **fidel5 said:**
> Here you have a step-by-step guide on how to create a virtual machine and then install Ubuntu inside of it: [http://oracle-virtualbox.com/install-ubuntu-on-virtualbox/](http://oracle-virtualbox.com/install-ubuntu-on-virtualbox/)

I've blogged about settings to make virtualbox as fast as possible:
* [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)  At the bottom of that article with the settings and the "why", is this screen-by-screen 
* [http://blog.jdpfu.com/ALE/ALE-NW/Ubuntu-12.04-x32-install.pdf](http://blog.jdpfu.com/ALE/ALE-NW/Ubuntu-12.04-x32-install.pdf) how-to. It isn't  current, but things don't really change much.  I created this for an Atlanta-PC meeting presentation.  This information has been presented at LUGs and conferences on 3 continents. Even got through it in 5 minutes at YAPC once. ;)

---

### Post by fidel5 on 2015-05-04
Tnx man, useful stuff. LOL at Ubuntu being slow at Core i7, 6GB of RAM

---

### Post by QIII on 2015-05-04
> **fidel5 said:**
> LOL at Ubuntu being slow at Core i7, 6GB of RAM

It is?

---

### Post by TheFu on 2015-05-04
> **QIII said:**
> It is?

It was, with the wrong (default) Vbox settings.  Took 20 min to see a login screen after a fresh Ubuntu desktop install. That was about 18 months ago, methinks.  That is why I've been recommending people do not enable 2D/3D support initially. For some laptops, it makes for extremely slow results. Also, for people running VMs remotely, it doesn't make sense.  There is little downside to doing this from what I can see. The first impression isn't of an extremely slow system. If everything is going well, at the next reboot - after guess additions have been installed, they can enable 2D/3D support to see how it works.

OTOH, I haven't touched vbox at all in over a year. For my needs, KVM fits better.

---

### Post by QIII on 2015-05-04
Ah.  Must not have noticed that one.

Still, that would be Virtualbox rather than Ubuntu, it seems.

---

### Post by TheFu on 2015-05-04
> **QIII said:**
> Ah.  Must not have noticed that one.

Still, that would be Virtualbox rather than Ubuntu, it seems.

It was an LTS desktop release with Unity and 3D accel HW required.  It sucked for VMs. Canonical assumes most people are running desktops on real hardware, but that just isn't the way that most people new to Linux do it. They run it in a VM (Player or vbox) under Windows as the hostOS.  The users don't care who's fault it is, they just know it took 20 to see a login prompt.

Vbox worked fine with all releases before that. 

This was at an installfest with about 30 systems and 45 people at a local tech university.  I'd provided detailed instructions for setting up vbox, but the guy with the Core i7 didn't follow them. I wasn't using vbox daily myself by then - had switched to KVM for almost everything.

---

