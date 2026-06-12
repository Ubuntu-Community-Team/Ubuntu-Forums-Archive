---
title: "Questions about the best way to bullet proof an xp install in virtualbox"
date: 2014-06-20
forum: Virtualisation
---

### Post by therrera1550 on 2014-06-20
Hi list,

I would like to move my small home business laptops (workstations) away from Windows.  I setup a test system on an older Dell laptop (Inspiron 1150) and put Lubuntu 14.04 on it and XP in virtualbox.  It is functioning well and want to install our main application that we depend on based on ACT! 11.0 which is a Windows app.  After getting this test workstation setup I would like to take an image of it that can be used to restore it intact should the OS or application files get damaged.

Is there a standard way of doing this?  For example is there an application like "ghost" or other imaging software that could save the image to an external drive to be used to restore the virtual OS back?  I am thinking also if the XP VM got infected with a virus or other malware, I could wipe it and restore from image, then put back my latest backup of our database and be back in business.  One way to prevent infection will be to make sure that we don't run with admin rights.  I chose to run it under Linux to help insulate ourselves from infections out there especially in light of the fact that XP is no longer supported, formally.

Any thoughts on this?

Thanks for the help,

Tony

---

### Post by SeijiSensei on 2014-06-20
You can take a "snapshot" of a virtual machine once you have configured it to your liking.  See [http://www.virtualbox.org/manual/ch01.html#snapshots](http://www.virtualbox.org/manual/ch01.html#snapshots) for details.

---

### Post by oldfred on 2014-06-21
Someday you may want a Linux app.

Alternatives to ACT!, not all Linux compatible.
[http://alternativeto.net/software/act/](http://alternativeto.net/software/act/)

---

### Post by therrera1550 on 2014-06-22
Thanks for the replies.  I will take a snapshot of the setup once I get it configured with the apps I need.  Is the snapshot a physical file that I can back up so I can restore it should my pc hard drive fail or otherwise get corrupted and require a re-install?

I looked into the page you sent me on Act! alternatives.  Thanks for that and I will start checking these out.  One of the primary reasons we like to use Act! is because of its synchronization feature.  Our workstations can all contain the same data so we don't have to have separate databases on each machine.  Its a compromise between having a server based database and individual ones.

Thanks.

Tony

---

### Post by SeijiSensei on 2014-06-23
The size of the snapshots depends on the total amount of storage in use by the VM so they can be quite large.  Mine are over 25 GB.

---

### Post by therrera1550 on 2014-06-25
Thanks for the replies.  I consider my questions answered and the issue resolved.

Tony

---

