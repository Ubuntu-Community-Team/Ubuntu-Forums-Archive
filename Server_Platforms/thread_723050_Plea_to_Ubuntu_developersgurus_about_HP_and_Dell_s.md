---
title: "Plea to Ubuntu developers/gurus about HP and Dell storage drivers"
date: 2008-03-13
forum: Server Platforms
---

### Post by Petersonz on 2008-03-13
Attention Ubuntu devs/gurus. HP and Dell are both popular server platforms. Also, both companies routinely update their storage drivers (megaraid_sas and cciss) for Redhat and Suse.

Can someone either post a method of converting these drivers to work with Ubuntu, or compile with Ubuntu kernels?

And/or can the devs please update the kernel for dapper/gutsy/hardy to include the newer versions of these drivers?

I, for one, would rather donate to Ubuntu than pay the blood money to Redhat/Suse just to use Dell/HP's fine servers and have the reliability while keeping Ubuntu under the hood.

Hacking Fedora or CentOS to accept the HP/Dell drivers doesnt seem to appealing either. Having a choice, Id much rather stick with a more community friendly Ubuntu for my server deployments.

Thanks :)

---

### Post by benne on 2008-03-13
Ever heard of openSUSE or CentOS?

Good idea though.

---

### Post by vpsville on 2008-03-13
You could buy the Dells without the raid controllers, and buy 3ware controllers instead.  They are well supported in Debian/Ubuntu.

You might also get a faster server by doing that too ;)

---

### Post by joker535 on 2008-03-14
> **benne said:**
> Ever heard of openSUSE or CentOS?

Good idea though.

Will the SUSE drivers on Hp's site work with opensuse ont he DL380 G3?

---

### Post by Petersonz on 2008-03-14
All good ideas except it means not using Ubuntu server.

As for buying with no RAID controller, does the 3ware SAS controller support the MD1000 disk array? Never tried that combo before.

---

### Post by netlogic on 2008-03-15
> **joker535 said:**
> Will the SUSE drivers on Hp's site work with opensuse ont he DL380 G3?

If it is open source drive, why don't you just compile it?
Also, have you tried their site or mail the support?
So... u want someone who doesn't have your hardware to write, and test the drive without knowing anything about the chipset?

---

### Post by gtdaqua on 2008-03-19
Same problem here. I compiled  the  drivers from source tarball and modified the kernel (using DKMS). But the new compiled kernel did not load! So I had to revert to old kernel (that comes default with Gutsy 64 bit). 

cant current megasas driver 00.00.03.10-rc5 be upgraded to 00.00.03.16 please? It would be awesome if anyone atleast showed how to do it.

---

