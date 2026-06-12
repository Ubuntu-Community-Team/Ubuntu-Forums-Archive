---
title: "How to use Shared Folders in Virtal Box?"
date: 2011-11-19
forum: Virtualisation
---

### Post by marer13 on 2011-11-19
Hello everyone,

I'm new to Virtual Box and virtualisation. I have installed Virtual Box and Windows as virtual. 

I have defined a Shared Folder like this:

/home/marer13/Documents/Dokumenty/Adobe/Courses

And when I start WIndows, I don't see the access to the shared folder anywhere.

Please help.

---

### Post by CharlesA on 2011-11-19
Make sure you have the guest additions installed.

You should be able to browse out to the share from Windows Explorer.

---

### Post by marer13 on 2011-11-19
Do you mean:

virtualbox-ose-guest-dkms


?

---

### Post by CharlesA on 2011-11-19
> **marer13 said:**
> Do you mean:

virtualbox-ose-guest-dkms


?
No. You install them from within virtualbox itself.

---

### Post by marer13 on 2011-11-19
How?

---

### Post by azmyth on 2011-11-19
You need to download the Vboxguestadditions_4.1.6.iso and install them. You'll need to chose the iso under your CD and then run the auto install once you start the guest. You'll need the guest additions version to match your vbox version.

---

### Post by CharlesA on 2011-11-19
> **marer13 said:**
> How?
Start the VM and then go to the devices menu and select install guest additions.

---

### Post by marer13 on 2011-11-19
I've downloaded the iso.

Now, how do I install it within Virtual Box? Shall I burn it onto a cd and then run Windows guest os from this cd?

---

### Post by azmyth on 2011-11-19
I just set the CD to the iso under the storage options within the guest listed in virtualbox. Guess you could burn it and install but it's a waste of cd.

---

### Post by marer13 on 2011-11-20
It worked!


Thank you.

---

