---
title: "Is there a way to use a virtual machine type thing to boot form existing partitions?"
date: 2012-05-07
forum: Virtualisation
---

### Post by Jynks on 2012-05-07
Is there a way to use a virtual machine type thing to boot form existing partitions?

I run a tripple boot mac. Win7, Lion and Ubuntu. I mainly use ubuntu and for those times like when  I wish to use the other partitions I find it a little annoying to fully boot into them.

I thought it would be a trivial matter to simply use virtualbox or something like that to select the windows7 or Mac partition and just boot them.. but apparently not.

Dose anyone know how I would go about this? I would like to be able to boot into these partitions normally, but also simply load virtual box in ubuntu and load them as well in a window.

Any ideas?

---

### Post by Bucky Ball on 2012-05-07
A virtual machine is installed inside the host operating system.

For instance:

* Install Ubuntu if that is the one you use most (Host);
* Install Virtualbox or something like it;
* Install Lion and Win *inside* Ubuntu as virtual machines (Guests).

There is no way I know of to run existing partitions as virtual machines as they are not virtual machines, they are actual installs on physical partitions of a physical hard drive. Have a good read about what virtual machines are, how they work and what they do. ;)

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)
[https://www.virtualbox.org/manual/ch01.html#gui-createvm](https://www.virtualbox.org/manual/ch01.html#gui-createvm)

You'll need plenty of RAM but if you have that you're good to go (the RAM must be shared between host and guests but you choose; if you have 6Gb RAM then you might want to allocate 2Gb to each OS).

---

### Post by Jynks on 2012-05-07
> **Bucky Ball said:**
> A virtual machine is installed inside the host operating system.

For instance:

* Install Ubuntu if that is the one you use most;
* Install Virtualbox or something like it;
* Install Lion and Win *inside* Ubuntu as virtual machines.

Have a good read about what virtual machines are, how they work and what they do. ;)

yeah I realise that.. I am asking if there is a way to boot a partition as if it was a virtual drive.

Just like I said above. I have full triple boot computer, is there a way to boot these partitions in a window in something like virtualbox or other application.

---

### Post by Bucky Ball on 2012-05-07
Read my last post again. I edited it. But here:

[http://www.softpanorama.org/VM/conversion_of_harddrive_partition_into_virtual.shtml](http://www.softpanorama.org/VM/conversion_of_harddrive_partition_into_virtual.shtml)

[http://stackoverflow.com/questions/24864/virtualbox-from-an-existing-partition](http://stackoverflow.com/questions/24864/virtualbox-from-an-existing-partition)

Seems there is a way for Windows at least. This looks like it might work if Lion is the host:

[http://download.parallels.com/desktop/v4/docs/en/Parallels_Desktop_Users_Guide/22185.htm](http://download.parallels.com/desktop/v4/docs/en/Parallels_Desktop_Users_Guide/22185.htm)

---

### Post by Jynks on 2012-05-07
dude. your not listening to me. I get it what your saying.. I understand what a virtual machine is that has NOTHING to do with what I am asking...

All I am asking is

***IS* there a way to load OS from an existing bootable partition inside a window *"like"* the way a virtual machine works?**

- EDIT - 
 I see your edits now.. this is a possible option.. but not one I wish to use.. It is basically a conversion process. I wish to leve the original partitions unmodified.

---

### Post by Bucky Ball on 2012-05-07
I provided links for that in my last post. Happy googling and good luck with it. ;)

---

### Post by dcstar on 2012-05-08
> **Jynks said:**
> Is there a way to use a virtual machine type thing to boot form existing partitions?
.........


It is basically solid-gold insanity to use a VM to directly access physical (non VM) partitions.

When an desktop OS runs it assumes that it has total control over all hardware resources. You cannot have one OS (the base OS) running that assumes that it has exclusive control of a storage device and then run a VM that has access to **the same device at the same time** also assuming total, sole control.

Good VM systems take care of this issue by having separate VM storage resources or taking the hardware storage resource away from the base OS on a permanent basis. Bad VM systems allow users to kludge things that allow all sorts of potential problems by allowing this sort of access.

---

