---
title: "Build Gnome-Boxes from source Xubuntu 16.04"
date: 2018-04-03
forum: Virtualisation
---

### Post by b-leigh on 2018-04-03
Hi,

I like Gnome-boxes since it is simple and I do not understand the intricacies of virtualisation etc.

I have the repository version via apt install gnome-boxes (3.18.1)

However, I cannot get access to my USB or computer storage

So I would like to clone the latest (a later?) version from GIT and then build from source (something else I do not understand well)

I have manged to work out that gnome-boxes uses Meson, and followed the instructions on the Meson website, but had lots of problems installing the latest version of Meson and also knowing what to do when building (e.g. in which directory I should build, a new directory, or the one with meson.build) etc, etc.

Obviously I am out of my depth, can anyone give me a simple step by step for this?

Or even to tell me if I should try to install a newer version of Boxes on 16.04

I could wait for 18.04 but I am using boxes for this, and am too impatient :)

---

### Post by DuckHook on 2018-04-03
I don't mean to be discouraging, but if you have difficulties understanding the intricacies of virtualisation, then you most certainly will be even more flustered by any attempt to compile from source. The latter is more technical and obscure than the former. Moreover, if the repo version of *gnome-boxes* does not allow you USB access and shared storage by default, then it is highly unlikely that the compiled version will act differently. These settings are at their defaults for reasons of security and functionality and usually won't change simply by the act of compiling from source.

I am unfamiliar with *gnome-boxes*. Thank you for introducing it to me. It bears noting that *gnome-boxes* is, in fact, a virtual machine that uses *virt* and *kvm*. It just automates the process of setting one up so that you don't have to go through the usual details and rigmarole. However, the graphical control app *virt-manager* is not really that hard to use, and will allow you to map USB ports to your virtual machine. To do so, you will need to install *spice*. Shared storage is a somewhat different matter and involves subsequent installation of client server components that allow shared access to certain files. There is no way around this subsequent requirement irrespective of whether you use *gnome-boxes* or *virt-manager*.

Note that shared file access defeats one of the primary purposes of a VM—that is—the sandboxing of your VM guest so that it cannot affect anything on your host. If you are willing to expose your host to processes in the guest, then the question that naturally arises is: why run a VM? You may have other good reasons for doing so, but you may also want to consider doing away with the VM altogether and just going for simplicity.

---

### Post by b-leigh on 2018-04-04
Thanks Duck Hook
That is a very well written post, thanks for the very helpful advice

I normally install other OS' I wanted to try on another partition and dual boot

Now, I'm mainly using gnome boxes because I am inquisitive and like to try new stuff and have never looked at virtualisation before
I will go back to installing other Os' in another partition I think

But, since I cant leave well alone and since I have pretty much all my files on an external USB drive, I will see if I can get going with boxes then try to find out more about spice and virtual-manager to try and get USB's to show up. I'll start searching, but any starter links to help me in that would be great

Thanks again

---

### Post by Dennis N on 2018-04-04
I have tried Gnome Boxes in the past, and never got the USB to pass through tho the vm. But, since host and the vm have a different IP address, you can network between them to share or transfer files.  

I later used kvm/qemu and virt manager for a virtual machine and that has a lot more settings you can adjust.

---

### Post by kerry_s on 2018-04-04
did you turn the hardware on for the vm? right click vm-> property-> devices (i think)
you have to toggle it on after install.

---

### Post by DuckHook on 2018-04-05
> **b-leigh said:**
> I'm mainly using gnome boxes because I am inquisitive and like to try new stuff and have never looked at virtualisation before…
Your inquisitiveness is admirable. As you can read from other forum members who also posted, we all encourage you to try a VM. Once past the initial learning curve, it's much easier (and safer) than installing in numerous partitions—though there's nothing inherently wrong with that practice either—just more that can go wrong and no ability to roll back to a good snapshot if you mess something up.
> …any starter links to help me in that would be great…
Many people find VirtualBox to be easier than the KVM/QEMU + virt-manager combo. You may wish to give the following a look:
[https://help.ubuntu.com/community/VirtualMachines](https://help.ubuntu.com/community/VirtualMachines)

---

