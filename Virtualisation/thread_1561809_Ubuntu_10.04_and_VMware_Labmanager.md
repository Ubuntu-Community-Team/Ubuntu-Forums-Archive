---
title: "Ubuntu 10.04 and VMware Labmanager?"
date: 2010-08-26
forum: Virtualisation
---

### Post by elowe on 2010-08-26
Hello all.

We have a VMware Labmanager environment for our software development and I am doing some testing of Ubuntu templates for deployment.  

I have set up Ubuntu (32 and 64bit versions) 9.04, 9.10, and 10.04 VM templates and they all have VMware Tools installed, with the exception of the vmci module in 10.04.  I have also built Redhat and SuSE templates in the Labmanager environment and users have been able to deploy working VMs from these templates.

However, the ubuntu VM templates don't automatically configure themselves with a proper hostname.  In Labmanager, I blank out the hostname of the VM template.  When I start up a new SuSE or Redhat VM from the template, it automatically gives the deployed VM a generated hostname ie. Config8124VM0.  The VM hostname is inserted into the /etc/hosts file and it recognizes itself as that hostname on bootup and DNS is also updated to reflect the new VM name.

However, if I delete the hostname from the /etc/hosts and /etc/hostname file in the Ubuntu template, the VMs deployed from the template will have no hostname (just localhost).  

Anyone have any experience with Ubuntu and Labmanager?  

Why would SuSE and Redhat work, but not any of the Ubuntu versions I have tried?

Thanks in advance.

---

### Post by irishshagua on 2011-11-09
Thread Bump.
I'm having the same issues (only have a 10.04 template) as stated in this post and was wondering if there had been any updates/solutions suggested for this?

The deployed machines work correctly (ie network connection works) once the ipaddress has been updated (manually) to the dynamically assigned ip from vCenter LabManager but as the deployment is supposed to be an automated process, this is a bit of a problem... :confused:


Any responses on the issue would be greatly appreciated.

Regards,
Brian

---

