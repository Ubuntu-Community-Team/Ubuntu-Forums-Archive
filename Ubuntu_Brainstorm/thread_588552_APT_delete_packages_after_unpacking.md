---
title: "APT delete packages after unpacking"
date: 2007-10-23
forum: Ubuntu Brainstorm
---

### Post by Megatog615 on 2007-10-23
For users with low disk space, it would be nice to have apt delete the downloaded package after the unpacking stage. This would help reduce the chance of running out of disk space during package installation.

---

### Post by smartboyathome on 2007-10-23
> **Megatog615 said:**
> For users with low disk space, it would be nice to have apt delete the downloaded package after the unpacking stage. This would help reduce the chance of running out of disk space during package installation.

Maybe have it as an option? I would like to keep my packages on my system in case I need them.

---

### Post by Megatog615 on 2007-10-23
You're right.

Since this would only cater to advanced users anyway(I run Ubuntu on a rather specialized environment with limited disk space), an option with apt, like --delete-after-unpack or something.

---

### Post by bikeboy on 2007-10-23
sudo apt-get clean or apt-get autoclean are already available to do this. Perhaps it could be included as part of the low disk space rescue system that was implemented in Gutsy.

From man apt-get:
> 
clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

---

### Post by Megatog615 on 2007-10-24
I don't think you understand. What I thought of is that it deletes the package right after it is unpacked in the install process.

---

### Post by bikeboy on 2007-10-24
Yeah, so the low disk space rescue thing (can't remember the name in the end) could automatically run the approapriate one of those commands when need. If you're using a small partition, this could be straight after package install.

---

### Post by Megatog615 on 2007-10-24
Here's what I mean:```
Selecting previously deselected package randompackage.
(Reading database ... ###### files and directories currently installed.)
Unpacking randompackage (from .../randompackage_version_i386.deb) ...
Deleting unpacked package archive for randompackage (randompackage_version_i386.deb) ...
Setting up randompackage (version) ...
```

---

### Post by Martje_001 on 2007-10-25
Aaah.. that's a very good idea!
+1 from me!

---

### Post by LaserJock on 2007-10-25
Seems like this would only be useful if you also downloaded the .debs one at a time. Otherwise you still have the disk space usage of having all the .debs downloaded before even unpacking the first one. Honestly though, I'd think people would be better served by doing a custom installation maybe via Ubuntu Server. If you are **that** low on disk space you are going to have a lot of problems. Packages themselves are usually pretty small.

-LaserJock

---

### Post by shad0w_walker on 2007-10-25
Maybe something along the lines of modifying apt-get/synaptic/whichever to check the disk space free after installing packages. If the system has less than a preset/user definable amount of disk space then it will automatically delete the oldest package files first.

---

