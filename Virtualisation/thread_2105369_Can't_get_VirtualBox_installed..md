---
title: "Can't get VirtualBox installed."
date: 2013-01-15
forum: Virtualisation
---

### Post by DaBungalow on 2013-01-15
I am attempting to install VirtualBox and failing miserably.  I am brand new to Ubuntu (and Linux.  Just started two days ago.) and want to install VirtualBox to run Windows 7; however, I don't know why it isn't working.  I have tried installing it from Oracle's website.  Didn't work.  I tried uninstalling and re-installing.  Didn't work.  The main thing that is getting me is that I don't quite know how to properly install it.  I have followed Oracle's instructions (I think) and when I try to install VirtualBox via the command line, I get this error:

```
Uninstalling modules from DKMS
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.2.6/source ->
                 /usr/src/vboxhost-4.2.6

DKMS: add completed.
Failed to install using DKMS, attempting to install without
Makefile:181: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.
```

Does anybody have any ideas?

---

### Post by leclerc65 on 2013-01-15
Look at the download page carefully, download the appropriate DEB (Precise, 32 bits etc...?).
Then right click on that, choose Open with Gdebi...

---

### Post by DaBungalow on 2013-01-15
> **leclerc65 said:**
> Look at the download page carefully, download the appropriate DEB (Precise, 32 bits etc...?).
Then right click on that, choose Open with Gdebi...

Oops, I am confused about my own question. :oops: I actually did get it installed and it will open; however, if I attempt to create a virtual machine for Windows 7, I "successfully" create the machine, but I can't get the machine to run.  I have tried several tutorials on how to do this but I get an error that VB doesn't have access to USB interface.  I don't even need to access USB as I have an iso on my computer that I wan't to use instead.  Help??? :oops:

---

### Post by Ms. Daisy on 2013-01-15
You need to spend some time with the Virtualbox manual.  VB seems totally intuitive at first glance, but there are a lot of nuances that you need to read about:

[https://www.virtualbox.org/manual/UserManual.html](https://www.virtualbox.org/manual/UserManual.html)

Specifically to create a new VM:
[https://www.virtualbox.org/manual/ch01.html#idp7866992](https://www.virtualbox.org/manual/ch01.html#idp7866992)

---

### Post by leclerc65 on 2013-01-16
You have to add Extension Pack, then install Guest Addition.

---

### Post by MontrealCorp on 2013-01-17
[http://www.youtube.com/watch?v=2_3r5U67Fu4](http://www.youtube.com/watch?v=2_3r5U67Fu4)
it worked for me

---

