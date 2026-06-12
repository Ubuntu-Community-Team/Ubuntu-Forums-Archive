---
title: "[SOLVED] VMware Workstation 6.0.4-93057 on Ubuntu 8.04 problem"
date: 2008-06-08
forum: Virtualisation
---

### Post by bmwman on 2008-06-08
I just installed Vmware Worksation 6.0.4-93057. Everything went smooth and without any problems compiling. Configuration completed with no probems as well. But when I try to start its telling me :

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

WTF. I ran it few times and everytime completes fine but it still shows as not configured.

Has anyone fixed that yet?

---

### Post by bmwman on 2008-06-08
Same thing  VMware Workstation 6.0.3 build-80004. I just reverted to the old version but I get the same error. Instalation completes fine after changing #include &#8220;asm/bitops.h&#8221; to: #include &#8220;linux/bitops.h&#8221; but when I start the vmware it's saying that is not properly configured. Is there a problem with the 2.6.24-18 kernel?

---

### Post by fjgaude on 2008-06-08
I don't know about Workstation but Server works fine with 2.6.24-18, as it did with -17.

---

### Post by bmwman on 2008-06-08
Does the VMware server has all the features like VMware Workstation. I'm mosty using cloning or importing physical drives as virtual. If I can get the same options I might switch. I've tried in the past but have never been able to make the VMware server to work so I always used Workstation. And i have VMware workstation in Windows and I use the same virtual machines in Ubuntu.

---

### Post by fjgaude on 2008-06-08
My only experience is with Server (and sometime back, with VBox)... I know that some VMs created with Workstation don't work with Server. I do think Server handles drives and the like, and certainly makes VMs... that's its strength.

From what I've read vmware server 1.0.6 installs in Hardy without any patches.

Maybe others with more knowledge will respond to your questions.

---

### Post by bmwman on 2008-06-12
I removed everything and after few updates few days later everything installed fine. Dunno what the problem was :)

---

### Post by bewolf on 2008-07-02
thks i have solve the same problem :)

---

### Post by dxxvi on 2008-08-09
> **bewolf said:**
> thks i have solve the same problem :)

How did you solve your problem? I'm facing that problem now and don't know what to do.

---

