---
title: "installing guest to a logical volume?"
date: 2012-05-13
forum: Virtualisation
---

### Post by ClientAlive on 2012-05-13
I'm having a heck of a time finding info on the beginning part of installing a kvm guest to a logical volume. I see lot's of info that starts after the logical volume is created (and whatever else has to be done with it) but not on setting up the lvm for this application:

~ how many logical volumes to create for a single guest (is it more than one?)
~ where to mount it/ them
~ how to mount them (fstab?)
~ if fstab, then what is the exact options/ syntax to use?

Can anyone help?

thanks in advance.

---

### Post by ClientAlive on 2012-05-13
sorry,

I got it sorted out. Thx.

Turns out that part of the process/ steps in virt-manager involves choosing a logical volume to install to. I'm not sure whether one is able to create the logical volume in that step/ using virt-manager. What I did was to create a logical volume with the lvm command for it:

```

lvcreate -L 35000 -n devsys system

```

This creates a logical volume of 35000 MB, named devsys on the volume group named system.

After that I could fire up virt-manager; and, in the step for it, choose to use it to install to (the parts in that step with virt-manager are pretty straightforward).

------------------------------------------------------------

Aside:

For me, there were two big questions I was confused about:

(1) I knew that a typical operating system installation uses more than one partition (at least two - one for swap and another for the sytem). I wasn't sure whether I needed to (a) find a way to partition the logical volume or if it were possible to do so during the installation; or (b) create more than one logical volume for a single guest (one to correspond to each partition for that guest).


What I learned: I'm not sure the technical details of how it works, but the installation is able to create partitions in the logical volume. It seems to have something to do with the fact that a logical volume is a "block device" and is treated like it's a hard drive in an of itsels  --I think.

(2) I knew that stuff has to be mounted to use it (partitions, file systems, whatever). I wasn't sure if I needed to modify fstab so that the logical volume would be mounted when I fire up the computer.

What I learned:

lvm takes care of itself. There is no need to modify anything (least of all fstab). If you run:

```

sudo lvdisplay

```

after you create the new logical volume, and you see it listed, it will be available every time you fire up the computer - it just works on it's own somehow

--------------------------------------------------------

hth



Jake

---

