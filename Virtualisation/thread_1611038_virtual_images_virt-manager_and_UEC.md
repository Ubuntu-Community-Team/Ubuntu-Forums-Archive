---
title: "virtual images virt-manager and UEC"
date: 2010-11-01
forum: Virtualisation
---

### Post by wcorey on 2010-11-01
I am hoping this is a simple question and has a simple answer. Last summer I took the RedHat certification course in RHEV, RedHat's enterprise virtualiztion solution.

I talked about the UEC and Amazon notion of kernel plus ramdisk plus image and the instructor told me that was old technology and existed only as a throwback to Zen days. He did not elaborate more on it. However, RHEV, which is a really slick wrapper around KVM abstracts out the physical files in use but I did notice when you create a VM with virt-manager, for instance, you merely get a blahblah.img file. 

What's nice about these VM's, much like VMware's way more involved file structure, is if you add a package or program to it, after you restart the image that package/program is still there. This is pretty slick.

If you run an EMI, or AMI for that matter, built out of ram disk image, kernel image and another img file, you can add packages and programs all day long but once you terminate that image all your deltas are gone.

Seems to me the advantage of the EMI (or AMI) is you can fire off multiple copies of it simultaneously or via RightScale or SCALR etc. If you start a KVM image it is a single image with only one invocation allowed.

My question is this. Would someone explain the nuances of those components and if and how they allow for the particular run time behavior of both flavors, EMI vs qem-kvm img file?


In other words virsh or virt-manager will take all the parameters and create a single .img file that can be fired up and updated in place and grown (by way of programs or packages) and these persist. However only one instance of this image can be fired up at any given time, so if you have, for instance, 5 JBoss servers that cooperate, these would be 5 .img files on disk.

On the other hand you create a JBoss EMI (or AMI). It is comprised of 3 files, a kernel, a rdimage, and a xxx.img, these get bundled together to form a runnable EMI/AMI and you can issue a run-instance on it specifying you want n instances started. However, if during it's run it installs a package or upgrades itself, once it stops it reverts as the [E|A]MI is not persistable. I think cloud-init is supposed to change all that or some of that. But the question is was the RH instructor correct that the rdimage/kernel image and xxx.img relics of Xen days and is the single xxx.img of virsh or virt-manager the 'new' way to create an image etc. I hope my question is clear.

Thanks,
Walt

---

### Post by eblume on 2010-11-01
Hi wcorey,

My understanding of the qemu system is that you can specify at 'launch' of a vm (either by using qemu with or without kvm acceleration, or as automatically started by libvirtd) to have the deltas generated during virtualization sent to a different disk image, leaving your initial disk image clean. I do not know how to do this as it has never fit my usage scenario, but I would be VERY surprised to learn that this quite basic and long-supported paradigm wasn't included in the kvm/qemu/libvirtd environment.

At the very least, I know that qcow2 images support a snapshot system that should effectively create this scenario. Again, I don't know how to set it up, sorry. I would look at the documentation for libvirtd and qemu (don't bother looking at the kvm documentation, this is outside the scope of kvm. That is to say, kvm itself wouldn't support this, but rather whatever virtualization environment kvm spawns will.)

---

### Post by wcorey on 2010-11-01
Yes, you can snapshot them. I know this because RHEV supports both snapshots and templates. A snapshot allows you to test a change and roll it back if it doesn't do what you intended. A template is way more fascinating and perhaps what is meant by 'clone' in virt-manager/virsh land. As I stared out saying that if you wanted 5 separate instances running you had to create 5 images. Well, snapshot makes that easier in that you can have a base image and use that as the template from which you base 'child' images. Again, Redhat did not go into what things looked like on disk as in the environment you create you create an ISO store and an Image store. We never saw the contents of that store. But templates were neat.

If someone can explain the purpose of the vmlinuz image, the rdimage and the main image that, together, create the [A|E]MI -> ami or emi and why they aren't necessary in cloud land and why they are, if they are, required in a paravirtualized environment I suspect we'd all appreciate the knowledge.

And welcome eblume, e as in Ed? I see you recently joined, is this your first Ubuntu?

---

