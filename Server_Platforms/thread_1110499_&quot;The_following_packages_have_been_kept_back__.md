---
title: "&quot;The following packages have been kept back:   linux-image-virtual&quot;"
date: 2009-03-29
forum: Server Platforms
---

### Post by zigx on 2009-03-29
Hi all,

I was wondering why that package is held back when i do apt-get update; apt-get upgrade 

any ideas? thank you!

---

### Post by doogy2004 on 2009-03-29
From my experience apt does this with certain packages.  I would call it a feature because it warns you in advance of certain changes, such as kernel updates.  Kernel updates require a reboot to take affect and if you have anything that uses kernel specific modules such as VMware it reminds you that you will need to rebuild the modules after the kernel has been upgraded.

To fix this you can run the following:
```
sudo apt-get dist-upgrade
```

---

### Post by zigx on 2009-03-29
> **doogy2004 said:**
> From my experience apt does this with certain packages.  I would call it a feature because it warns you in advance of certain changes, such as kernel updates.  Kernel updates require a reboot to take affect and if you have anything that uses kernel specific modules such as VMware it reminds you that you will need to rebuild the modules after the kernel has been upgraded.

To fix this you can run the following:
```
sudo apt-get dist-upgrade
```

i happen to be using KVM with JeOS... is there anyway to tell what the consequences might be before actually doing this?

---

### Post by doogy2004 on 2009-03-29
I'm not sure, since those pieces of software are installed using apt they may be ok or they may rebuild their own modules automagically.  Or you may have to do a dpkg-reconfigure on those packages that stop working or do not work correctly after the kernel upgrade.

---

### Post by Vegan on 2009-03-30
> **zigx said:**
> Hi all,

I was wondering why that package is held back when i do apt-get update; apt-get upgrade 

any ideas? thank you!

Try running

```
sudo apt-get install linux-server
```

---

### Post by netztier on 2009-03-30
> **Vegan said:**
> Try running

```
sudo apt-get install linux-server
```

Well if the OP actually runs *JeOS in a VM* (and if this message actually comes froma VM guest), installing the normal full-blown server kernel would not necessarily be a wise decision, would it?

He should rather stick with the kernel image that is optimised for running as VM guests.  **linux-image-virtual** is the meta-package for the latest VM-optimized kernel image:

```
user@server:~$ sudo apt-cache search linux-image
...
linux-image-2.6.27-3-rt - Linux kernel image for version 2.6.27 on Ingo Molnar's full real time preemption patch (2.6.26.5-rt9)
linux-image-rt - Rt Linux kernel image
linux-image - Generic Linux kernel image.
linux-image-2.6.27-11-generic - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-11-server - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-11-virtual - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-7-generic - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-7-server - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-7-virtual - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-9-generic - Linux kernel image for version 2.6.27 on x86/x86_64
linux-image-2.6.27-9-server - Linux kernel image for version 2.6.27 on x86/x86_64
[COLOR="Red"]linux-image-2.6.27-9-virtual - Linux kernel image for version 2.6.27 on x86/x86_64[/COLOR]
linux-image-generic - Generic Linux kernel image
linux-image-server - Linux kernel image on Server Equipment.
[COLOR="Red"]linux-image-virtual - Linux kernel image for virtual machines[/COLOR]
```

If however this is about running JeOS as VM host, why yes, you might be right.

regards

Marc

---

### Post by Cheesemill on 2009-03-30
If you do a 
```
sudo aptitude update && sudo aptitude safe-upgrade
```
then it will install any kernel updates.

Cheesemill

---

### Post by BkkBonanza on 2009-03-30
apt-get will hold back packages when there is a conflict in dependencies. so you will have to try and trace down where the conflict is and decide what to do about it. 

You might try,

sudo apt-get check

to update your cache and check for broken dependencies. Probably not recommended but you can ignore holds with --ignore-hold

and running apt-get with --simulate will show you what it will do without actually doing it.

---

### Post by kyng on 2010-05-07
If I try to upgrade via terminal, some packages a held pack. But when Update manager pops up, they can be installed. Why is that?

---

### Post by rich97 on 2010-09-08
For anyone else looking at this thread, this is what worked for me:

sudo apt-get dist-upgrade

It then says some packages have been held back, simply install them manually, in my case it was ubuntu-desktop:

sudo apt-get install ubuntu-desktop

As someone suggested earlier there was a package conflict, it asked me if I wanted to remove the old and install the new and suggested some other packages to go along with the new ubuntu-desktop. Which I did. All good now! :)

---

### Post by Gaba_p on 2011-02-09
Last suggestion worked for me (installing manually).
I was having 'kde-standard' package held back after a dist-upgrade.

Cheers

---

### Post by andyvy on 2012-02-29
> **rich97 said:**
> For anyone else looking at this thread, this is what worked for me:

sudo apt-get dist-upgrade

It then says some packages have been held back, simply install them manually, in my case it was ubuntu-desktop:

sudo apt-get install ubuntu-desktop

As someone suggested earlier there was a package conflict, it asked me if I wanted to remove the old and install the new and suggested some other packages to go along with the new ubuntu-desktop. Which I did. All good now! :)

This worked, cheers.

---

