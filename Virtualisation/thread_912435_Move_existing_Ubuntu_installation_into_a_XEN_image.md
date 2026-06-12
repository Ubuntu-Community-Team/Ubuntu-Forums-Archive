---
title: "Move existing Ubuntu installation into a XEN image"
date: 2008-09-06
forum: Virtualisation
---

### Post by eldaria on 2008-09-06
Hey all.

Not sure if anyone has done this.
Basically I have a server that is running Ubuntu 6.06 Server.
And I would like to go over to do virtualization with xen.

The server is currently serving mine and some friends web pages, as well as e-mail, and some other stuff.
So to minimize down time I was thinking of just migrate the whole existing installation into a xen image.
And then run it virtualized, while slowly migrating the various services of to other xen images.

The reason I want to do this is that I don't have any spare hardware powerful enough laying around that I use to migrate onto.
Server is running 64bit and it is the only hardware I have that can do it, my other pc's are all 32bit cpu in them.

So anyone have an idea of how I could go about doing this?

Regards.
Brian.

---

### Post by grantek on 2008-09-09
Yeah, I've done this for a Debian server, I think the only problems I had were finding a precompiled debian kernel that worked as a xen guest, so I just used an Ubuntu kernel :)

It's basically just like creating a new Xen domu, but you restore a full backup of the physical server onto the storage for the Xen domain. You need to have the domu's kernel file and initrd copied onto the dom0's filesystem, but if you're running Ubuntu on Ubuntu it's just a matter of having the same kernel package installed on both systems :)

Other gotchas I can think of:
- If your server runs a desktop/X environment, check your xorg.conf for any hardware-specific stuff, or driver entries for physical cards.
- If you're performing a filesystem backup (copying all the files across to the Xen server, as opposed to imaging the disk and dumping the image somewhere on the xen server), you'll need to check your /etc/fstab and fix it to suit the new environment. 
- check /etc/udev/rules.d for any "persistent-net.rules" entries, which contain mappings for physical network devices to "ethX" device names. If you're just giving the domu a single virtual network interface, and want it to be "eth0", just delete all of the stored entries.

---

### Post by eldaria on 2008-09-10
Ok excellent thanks, I will give it a try this weekend.

---

