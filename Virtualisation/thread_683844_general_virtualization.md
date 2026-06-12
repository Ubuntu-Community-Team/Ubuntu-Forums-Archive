---
title: "general virtualization ?"
date: 2008-01-31
forum: Virtualisation
---

### Post by roofninja on 2008-01-31
Ok, my head hurts.  I have been reading LOTs of threads on and about virtualization.  I have narrowed my chose down to VirtualBox or VMWare.  What I don't understand is what to use.  What is a guest OS?  Do I have to have a copy of XP to install or can I download an ISO or Image?  If I want to setup a Fedora do I just install from CD or do can I get an Image for one?  As you can see I don't know much but I am trying to understand it.  This is not question of who is better but I just don't understand it.  Thanks for any help.

---

### Post by fjgaude on 2008-01-31
Okay, you install the virtual software, then you use either an ISO or the actual OS install disk to install what is called the guest.

When you start to install you are asked what kind of OS is it to be: Win, Linux, then what version of it, like 2000, XP, Vista, or Ubuntu, Fedora, etc.

It's pretty easy to get started. To get all the features of the virtual host, you will have to do a few more things, but that comes after you are there with something to work with.

Let us know if you have further questions.

---

### Post by roofninja on 2008-01-31
What is the difference between VMPlayer and VMServer?  Do I have to have VMServer to run VMPlayer?  Is VirtualBox the same way?  Where do I find these guest OS's?

---

### Post by fjgaude on 2008-01-31
VMplayer only plays guests that have been created by something like VMware Server, both are free.

You can install VMware Server from your Ubuntu repository by using apt-get or Synaptic.

```
sudo apt-get install vmware-server
```

Or you can download the binary from vmware.com and follow instructions re installing. I did this for the last year, as the repositories were being updated from Fesity to Gutsy.

You can get Virtual Box from the repositories:

```
sudo apt-get install virtualbox-ose
```

I used to use this but gave it up in favor of vmware server.

The clients (guests), the OS that you install into the virtual machine, has to come from your disk or from an ISO you might own.

Let us know how you are doing.

---

### Post by roofninja on 2008-01-31
Thanks fjgaude for making it clear to me.  I will be trying this out over the weekend when I have more time to devote to trouble shooting and installing.

---

