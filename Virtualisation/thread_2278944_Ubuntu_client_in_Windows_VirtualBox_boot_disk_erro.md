---
title: "Ubuntu client in Windows VirtualBox: boot disk error after upgrade"
date: 2015-05-20
forum: Virtualisation
---

### Post by AussieGuy on 2015-05-20
Hello,

I'm running Kubuntu 14.04 as a client in VirtualBox 4.3.12, the host system being Windows 7 Enterprise 64bit.  I've just upgraded Ubuntu, and now it won't boot:

```
ALERT!  /dev/disk/by-uuid/<long string> does not exist.  Dropping to a shell!
```

And then I get a BusyBox shell with (initramfs) prompt.  I'm completely lost and confused here: I've never seen this error before, and I'm totally bamboozled.  I understand that in not virtualized Ubuntu, I could boot with a rescue CD and mount the correct disk.  Can I do the same thing here?  Or is there a "backdoor" into linux from Windows which will enable me to sort out the issue?

Many thanks for your help!

cheers,
-A.

---

### Post by bashiergui on 2015-05-24
Revert to the most recent snapshot prior to upgrade, but since you're asking you probably didn't take any. Snapshots and cloning are two awesome "undo" features that don't exist in bare metal installations. Take advantage of them. 

Did you back up your data somewhere before upgrading?

---

### Post by SeijiSensei on 2015-05-24
Foillowing on bashiergui's suggestion, if you rebuild the virtual machine, make a backup copy of the VM file and store it in a safe place.  That way you'll always have a known good copy you can boot from if things go awry.  The machine files are stored in /home/username/VirtualBox VMs/.

---

### Post by AussieGuy on 2015-05-24
Drat!  Yes, all my work is backed up (on DropBox, but I'm about to switch to OwnCloud), and no, I hadn't made any backup snapshots.  However - once bitten, twice shy, eh?  So what I'll do is start again from scratch - most of my applications (maths science ones generally) were overdue for an upgrade anyway.  And I'll upgrade VirtualBox as well.  Dammit!

Thanks very much for your replies!
-A.

---

### Post by AussieGuy on 2015-05-24
Would you believe it - I installed a brand-new Ubuntu, ran 'sudo apt-get update; sudo apt-get upgrade', installed some of the virtualbox guest additions, and whaddya know?  The NEW machine doesn't boot!  Back to initramfs and busybox again!  So I guess upgrading is the killer.  Sigh... back to square one.

---

### Post by SeijiSensei on 2015-05-25
Did you select either "Logical Volume Management (LVM)" or full-disk encryption during installation?  From the original error it looks like you chose LVM. Do not choose either of those, but simply accept the default and let Ubuntu install itself into the whole virtual drive. Those options require a separate /boot partition; I don't know how that would be handled in a VB virtual machine.

I also don't understand why the developers think offering LVM makes sense on anything other than servers.  It's an advanced method of disk management that the vast majority of users do not need.  Both these options are causing [other problems]("http://ubuntuforums.org/showthread.php?t=2278674") as well.

---

### Post by AussieGuy on 2015-05-25
Thanks for that, but in fact I selected none of the options, but simply let Ubuntu install itself onto the drive.

-A.

---

### Post by bashiergui on 2015-05-25
What is the configuration of the VM- how much RAM did you give it, hard drive space, cores?

---

### Post by AussieGuy on 2015-05-25
4096Mb RAM, 203 GB disk space - I allocated a fixed disk space before I started.  My machine has 8GB RAM and a 500GB HDD.  There should be problems actually running Ubuntu - it's just getting it to behave nicely with VirtualBox. And in fact I'm not quite sure which guest additions to install: the ones from the Ubuntu repositories, or the ones available at the VirtualBox website.

---

### Post by SeijiSensei on 2015-05-25
I always use the method described on the [Linux downloads page]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") at virtualbox.org to install VB.  Add the repository to your system as described there, and you will always have the most recent release.  It will be updated via apt the same way the rest of the Ubuntu software is.  Then install the Extension Pack from the [Downloads]("https://www.virtualbox.org/wiki/Downloads") page.

---

