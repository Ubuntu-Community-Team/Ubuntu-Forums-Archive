---
title: "[SOLVED] Can't uninstall VMware workstation that was installed via a &amp;quot;.bundle&amp;quot; file"
date: 2008-10-11
forum: Virtualisation
---

### Post by akelsall on 2008-10-11
I downloaded a trial version of VMWare Workstation 6.5. I didn't see a tar or gz file, so I downloaded a ".bundle" file. At first I didn't know what to do with it, but then I read the contents of the file and discovered it was a shell script. Here are the first few lines of the file:

#!/usr/bin/env bash
#
# VMware Installer Launcher
#
# This is the executable stub to check if the VMware Installer Service
# is installed and if so, launch it.  If it is not installed, the
# attached payload is extracted, the VMIS is installed, and the VMIS
# is launched to install the bundle as normal.

So, I ran it by entering "sudo ./vmware.bundle" and it installed with no problem. Now, I want to uninstall it (as I found out that VMWare Server is FREE), but I can't find it at all under Add/Remove. In Synaptic, only three things show up (VMMouse input driver, VMWare display driver, and mouse device autodetection tool). Is there a good way to completely remove a program install in this manner (i.e. a program installed via a .bundle file)? I see a lot of vmware files under /usr/bin that I "could" delete manually, but I'd rather do a clean uninstall. 

Thanks,

Andy

---

### Post by kogos on 2008-10-11
It's pretty easy to uninstall .bundle files actually... 

Just type in terminal: sudo ./VMware.bundle -uninstall

Of course, instead of "VMware.bundle" you will put your installation file name. 

Let me know if it worked Andy.

---

### Post by aiyeou on 2008-10-12
> **akelsall said:**
> I downloaded a trial version of VMWare Workstation 6.5. I didn't see a tar or gz file, so I downloaded a ".bundle" file. At first I didn't know what to do with it, 
.
.
So, I ran it by entering "sudo ./vmware.bundle" and it installed with no problem. 

Just a quick FYI that I had to use ```
sudo sh VMware-Workstation-6.5.0-118166.i386.bundle
```

since ```
sudo ./VMware-Workstation-6.5.0-118166.i386.bundle
``` did not run it.

Thanks

---

### Post by akelsall on 2008-10-13
Well, I had too much free time on my hands and wanted to get the vmware server software loaded, so I went the "brute force" way before reading the posts here (i.e. I located all the directories with vmware data in them) and deleted everything I could find). After that, I was able to install the vmware server edition. 

I'll keep the tips the two of you provided handy for next time though. Thanks for the help!

Andy

---

### Post by itsdaveperdue on 2008-10-20
> **aiyeou said:**
> Just a quick FYI that I had to use ```
sudo sh VMware-Workstation-6.5.0-118166.i386.bundle
```

since ```
sudo ./VMware-Workstation-6.5.0-118166.i386.bundle
``` did not run it.

Thanks


My guess is that you didn't assign the execute permission to the file before trying to run it; that's why you needed to run sh to call the file.

Just something to keep in mind next time this happens to you.

---

### Post by anarki13 on 2009-08-30
> **kogos said:**
> It's pretty easy to uninstall .bundle files actually... 

Just type in terminal: sudo ./VMware.bundle -uninstall

Of course, instead of "VMware.bundle" you will put your installation file name. 

Let me know if it worked Andy.

Thanks muchly!

drove me nuts looking for the .pl file described on other threads, then i took note its Workstation and not Server. thanks again!

---

### Post by amwnog on 2010-06-24
> **kogos said:**
> It's pretty easy to uninstall .bundle files actually... 

Just type in terminal: sudo ./VMware.bundle -uninstall

Of course, instead of "VMware.bundle" you will put your installation file name. 

Let me know if it worked Andy.

I followed your instruction to remove VMware.bundle, but error:

 uninstall is not an installed product avaliable product are: vmware-workstation

---

### Post by sarahstrong on 2010-07-03
amwnog: I got the same error.

The correct option was "-u vmware-workstation" for me. Run "<my VMware-Workstation bundle> -h" and read the help file to find out if the command has changed in your version.

---

### Post by NitroBooster on 2010-07-03
sudo ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle -u vmware-workstation

---

### Post by wiss on 2010-10-10
works fine,

txh.

---

### Post by -=Daemon=- on 2010-10-16
> **NitroBooster said:**
> sudo ./VMware-Workstation-Full-7.1.0-261024.x86_64.bundle -u vmware-workstation

Possoble other metode too
sudo vmware-installer --uninstall-product vmware-workstation

---

### Post by Ayazen on 2011-06-01
sudo vmware-installer --uninstall-product vmware-workstation

This one worked for me thanks!

---

