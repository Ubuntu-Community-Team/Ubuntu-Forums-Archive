---
title: "VMware won't open. &quot;Kernel headers 3.5.0-27-generic&quot; cannot found &amp; &quot;c header files&quot;."
date: 2013-08-12
forum: Virtualisation
---

### Post by jdawson192 on 2013-08-12
Hey all,

Im hoping someone can help me as Ive tried several different things to get this working and having no luck.

I have managed to install VMware which wouldnt work first time without the command:   sudo rmmod kvm-intel - Unsure why that happened but managed to bypass it.

Now when trying to open vmware I get a box which says "Before you can run VMware player, several modules must be compiled and loaded into the running kernel" then "Kernel headers for version 3.5.0-37-generic were not found. If you installed them in a non-default path you can specify the path below". Ive tried linking the location path to /usr/src/linux-headers-3.5.0-37-generic and /lib/modules/3.5.0-37-generic but each time I get the error message "C header files matching your running kernel were not found".

Ive also tried the following commands after a bit of research but still doesnt work.
   
sudo ln -sf /usr/src/linux-headers-3.5.0-37-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.5.0-37-generic/include/linux/version.h
  

 sudo ln -s /lib/modules/**3.5.0-37-generic**/build/include/generated/utsrelease.h /lib/modules/**3.5.0-37-generic**/build/include/linux/utsrelease.h
 

 sudo ln -s /lib/modules/**3.5.0-37-generic**/build/include/generated/autoconf.h /lib/modules/**3.5.0-37-generic**/build/include/linux/autoconf.h

Can anybody point me in the right direction?

Regards
Jamie

---

### Post by nathan-b on 2013-08-12
Have you installed the kernel-headers package and build-essential?

[https://communities.vmware.com/thread/444027?start=0&tstart=0](https://communities.vmware.com/thread/444027?start=0&tstart=0)

---

### Post by jdawson192 on 2013-08-12
With the command:
```
sudo apt-get install linux-headers-3.5.0-37-generic build-essential

```

I get the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.5.0-37-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Still no luck.

Jamie

---

### Post by SlugSlug on 2013-08-12
Is it the latest version of vmware?

---

### Post by jdawson192 on 2013-08-12
Yes :)

---

### Post by Cheesemill on 2013-08-12
Which VMware product is this, Workstation or Player?

Can you tell us what version of Ubuntu you are using and what version of VMware please.

---

### Post by jdawson192 on 2013-08-12
> **Cheesemill said:**
> Which VMware product is this, Workstation or Player?

Can you tell us what version of Ubuntu you are using and what version of VMware please.

VMware Player. Ubuntu 12.04LTS. VMware-Player-2.5.5-328052.x86_64. Just noticed I messed up the title of this thread. Apologies for that, was half asleep at the time!

Jamie

---

### Post by Cheesemill on 2013-08-12
*Thread moved to **Virtualisation**.*

You're trying to use an ancient version of VMware Player, latest is 5.0.2.

Download it from here and just run the .bundle file, it should install without any issues.

[https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0)

Edit - You'll probably need to uninstall your current version first.

---

### Post by jdawson192 on 2013-08-12
> **Cheesemill said:**
> *Thread moved to **Virtualisation**.*

You're trying to use an ancient version of VMware Player, latest is 5.0.2.

Download it from here and just run the .bundle file, it should install without any issues.

[https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0](https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0)

Edit - You'll probably need to uninstall your current version first.

Ha, thank you! Not sure how I managed that! But, I'm sorry to say I'm still getting the same message when trying to launch after installation. Any ideas? Thanks for your time and patience by the way.

EDIT: It is this time asking for "3.5.0-37-generic".

Jamie

---

### Post by jdawson192 on 2013-08-14
Sorry to bump, but has anyone got any ideas?

Jamie

---

### Post by RichardET on 2013-08-18
Here is a similar thread with a solution?
[http://www.kubuntuforums.net/showthread.php?58594-Problem-updating-VMware-Kernel-Module-after-upgrade](http://www.kubuntuforums.net/showthread.php?58594-Problem-updating-VMware-Kernel-Module-after-upgrade)

---

