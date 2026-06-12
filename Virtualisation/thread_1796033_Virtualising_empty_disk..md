---
title: "Virtualising empty disk."
date: 2011-07-03
forum: Virtualisation
---

### Post by Northernen on 2011-07-03
Hello.

Being quite new to Linux, I wanted to create a virtual empty disk, so that I would be able to toy around with various disk utilities on it.

Is this possible, and if so, how? If not with VMWare player, with which application?

---

### Post by CharlesA on 2011-07-04
You can just create a virtual hard drive the same way you create one when you are going to install something on it. Just don't install anything on it. ;)

---

### Post by Northernen on 2011-07-04
> **CharlesA said:**
> You can just create a virtual hard drive the same way you create one when you are going to install something on it. Just don't install anything on it. ;)

I did try that, but the virtual partition is not recognised by fdisk.

---

### Post by psusi on 2011-07-04
> **Northernen said:**
> I did try that, but the virtual partition is not recognised by fdisk.

Can you be a little more specific?

---

### Post by Northernen on 2011-07-04
> **psusi said:**
> Can you be a little more specific?

I power on the virtual machine. By now I would have thought it would be listed with "fdisk -l". It doesn't.

Have I misunderstood something?

Edit: The virtual partition was given /dev/scd0 from the installation, not sdX/hdX. Not quite certain of whether this factors in or not.

---

### Post by CharlesA on 2011-07-04
Are you sure you've created a virtual hard disk and attached it to the VM?

I think scd0 is the cdrom drive..

---

### Post by Northernen on 2011-07-04
> **CharlesA said:**
> Are you sure you've created a virtual hard disk and attached it to the VM?

I think scd0 is the cdrom drive..

I certainly think so. I've gone through the wizard (VMware player) with allocating memory, hard disk usage and so forth. After that I click "play virtual machine", and I get the boot process stating "Operating system not found" on the screen.

How can I validate that it is in fact attached?

---

### Post by in-dust-rial on 2011-07-04
hey,
i think its a known issue I stumbled upon a month ago.
the problem seems to be, that there is no partition table available yet.
(so some distributions can not be installed easily and the issue was discussed somewhere at virtual box support)

load live-cd run gparted and create a partition table.
then try to run fdisc.

good luck

---

### Post by psusi on 2011-07-05
Yes, it sounds like you did not configure the virtual disk.

---

### Post by Northernen on 2011-07-05
> **psusi said:**
> Yes, it sounds like you did not configure the virtual disk.

Sooo... how do I do this?

---

### Post by in-dust-rial on 2011-07-05
dude, did you try?
[HTML]
gparted
device
create partition table?[/HTML]

good luck

---

### Post by Northernen on 2011-07-08
> **in-dust-rial said:**
> dude, did you try?
[HTML]
gparted
device
create partition table?[/HTML]good luck

I did, and now I give up.

Thanks for all the help.

---

### Post by CharlesA on 2011-07-08
If you can't get it working in VMware, perhaps try VBox.

---

