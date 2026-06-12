---
title: "virtual box error"
date: 2015-12-16
forum: Virtualisation
---

### Post by cmcanulty on 2015-12-16
I get an error on trying to install vb 5.0 not sure how to proceed, see screenshot

[ATTACH=CONFIG]266182[/ATTACH]

---

### Post by slickymaster on 2015-12-16
Did you remove everything related to the previous VirtualBox version?

You won't lose the VMs if that is your concern.

---

### Post by cmcanulty on 2015-12-16
No I didn't remove anything as I want to keep my windows 7 virtual machine, how do I remove only the other things in virtual box?

---

### Post by slickymaster on 2015-12-16
By default virtual machines are stored in an own directory```
~/Virtual Box VMs/<Name of VM>/
```See [this]("https://www.virtualbox.org/manual/ch10.html#vboxconfigdata"). So backup this folder.

In a terminal window```
sudo apt-get remove --purge virtualbox-4.*
```

---

### Post by cmcanulty on 2015-12-16
wow that is scary I never had to purge it before. So if I backup "VirtualBox VMs" then purge and install the new version then how do I get my windows 7 VB without a new install? I show  54GB in that folder is why I ask though it is just windows 7 with virtually no files so why is it so huge?

---

### Post by SeijiSensei on 2015-12-16
First, if you're using a package called virtualbox-4.3, you must be using the Oracle repositories as described at virtualbox.org.  Is that correct?

As for purging, it might have to do with the major version change from 4 to 5.  I followed the same procedure when I upgraded to 5.x a few weeks back.

After you install the new version, your VM should appear in the manager application just like before.  If for some reason it doesn't, you can use Machine > Add in the manager app to add the VM manually.

---

### Post by cmcanulty on 2015-12-16
I always try to thank the helpers at the end but was still responding. So thank you everyone.

---

