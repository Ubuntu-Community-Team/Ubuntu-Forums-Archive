---
title: "Ubuntu Installer 23.04.2 and Ubuntu 22.04.02 ISO under VMware"
date: 2023-05-02
forum: Virtualisation
---

### Post by stevefxp on 2023-05-02
Hello all,

I have a VMware 8.0U1 server and running several Ubuntu 22.04.2 vms. When I do a new install it asks me to update to 23.04.2 of the installer. When I do this the install stops when its installing the core OS. It just hangs and keeps spinning. If I do not update the installer, and leave it at 23.02.1, then no issues and the install completes. Has anyone seen this behavior under VMware 8?

Thanks,
Steve

---

### Post by MAFoElffen on 2023-05-05
Sounds like something to report to Launchpad as a problem.

I think this might be specific to VMware ESXi 8.0 Update 1, as I don't see anyone reporting problems on metal, nor am I having troubles installing VM Guests under KVM Hosts.

The problems I see on the VMware forum are the people are having crashes on Installing Ubuntu 22.04.2 (for some unknown reason) with less than 2GB of memory allocated for the Guest VM, where as it should be set to at least 4GB, especially for the installation.

Sorry. That was all "I" saw, and found.

---

### Post by stevefxp on 2023-05-06
Its related to ESX 8. I downgraded to 7.03 and it works.

---

### Post by stevefxp on 2023-05-06
Report to Launchpad??

---

### Post by MAFoElffen on 2023-05-07
You could try to report it to Launchpad... But as you have verified, that it is a problem specific to ESXI 8.0 update 1, it is external to Ubuntu and all they could do it try to report it to VMware support... So I don't know that it would go anywhere.

The right thing would be for you to report it directly to VMware, but I see a problem with that also...
> 
                                                                                       If you feel you have found a defect  in a VMware product and you have an active support agreement with us,  you should report that to VMware Support via the normal [Support Request]("https://kb.vmware.com/s/article/2006985?lang=en_US&queryTerm=how+to+file+a+support+request+in+my+vmware") process.
 If you do not have an active support agreement and you want to alert  us to a product defect, please post the issue to the appropriate product  community on the [VMware Technology Network]("https://communities.vmware.com/").
                              
                         


So it seems that if you are paying them for support, you can report it, otherwise report in in their forum.

I guess I'm spoiled. I was one of their beta testers for vSphere, So I had another channel that I had to report through.

Am interested how that goes.

---

