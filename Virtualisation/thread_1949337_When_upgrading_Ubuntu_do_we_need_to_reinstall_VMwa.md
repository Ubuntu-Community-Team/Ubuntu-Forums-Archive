---
title: "When upgrading Ubuntu do we need to reinstall VMware tools?"
date: 2012-03-30
forum: Virtualisation
---

### Post by dharmavir on 2012-03-30
Hello All,

I am using Ubuntu on VMware vSphere Hypervisor™ (ESXi) 5.0, now when I update Ubuntu core (Kernel) do I need to re-install these VMware tools? Are they built for specific or get compiled for specific kernel? Because when we install them we have to build them from source using "make install" and they look for Kernel version/path. 

So if I am upgrading Ubuntu distribution from 11.10 to 12.04 beta2 or from 12.04 beta1 to beta2 where Kernel file get updated do I need to re-install VMware tools?

VMware tools claims to improve network and some other performances and I have measured them by benchmark so they are worth installing initially but I am not sure whether I need to make install them every time I do an Distribution upgrade or not? Because doing it on 20 nodes will be hectic job.

Another question: After dist-upgrade, when I try adding any new package using apt-get it gives me following message as advice:
--------------------------------------------------------------
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-17 libjpeg-progs
  linux-headers-3.2.0-17-generic libjpeg-turbo-progs
Use 'apt-get autoremove' to remove them.
--------------------------------------------------------------

I am sorry, I might sound like novice but it is better to ask experts here rather than messing up with all the setups. I am afraid that all the software installed earlier using make install will work as they might have dependencies with old version of kernel or linux headers?

Please advice.
Thanks in Advance.

---

### Post by dharmavir on 2012-03-30
I know that this could be generic question instead of falling into Virtualization category but I thought of adding it here as there was VMware involved and I thought might get some important comments from VMware+Ubuntu experts.

---

### Post by dharmavir on 2012-03-30
Can somebody please reply to this question? Admins if required please move it to some different category if I have made mistake by putting it inside Virtualization category.

Thanks.

---

### Post by 2F4U on 2012-03-30
You don't need to re-install, but you need to reconfigure on every kernel update:

[http://ubuntuforums.org/showthread.php?t=1133427](http://ubuntuforums.org/showthread.php?t=1133427)

---

### Post by dcstar on 2012-03-31
> **dharmavir said:**
> Hello All,

I am using Ubuntu on VMware vSphere Hypervisor&#8482; (ESXi) 5.0, now when I update Ubuntu core (Kernel) do I need to re-install these VMware tools?
.........

When installing the current Linux VMware Tools you are asked if you want to install the "Auto Kernel Modules" feature, AFAIK that is supposed to update things whenever you install a new kernel.

---

### Post by dharmavir on 2012-03-31
Alright - Thanks everyone. I think I am understanding things now.

Now question I am having is:
There are 2 choices an individual have as an ubuntu server admin:
1) open-vm-tools
2) vmware distributed tools along with ESXi 5.0

Which one is good to go with?

---

### Post by dcstar on 2012-04-01
> **dharmavir said:**
> 
Now question I am having is:
There are 2 choices an individual have as an ubuntu server admin:
1) open-vm-tools
2) vmware distributed tools along with ESXi 5.0

Which one is good to go with?

[LIST=1]
[*]Do **not** change the topic of threads, start a new thread when you have a different question.
[*]Always use the VMware product.
[/LIST]

---

### Post by dharmavir on 2012-04-02
> **dcstar said:**
> [LIST=1]
[*]Do **not** change the topic of threads, start a new thread when you have a different question.
[*]Always use the VMware product.
[/LIST]

Thanks David, I understood but I think I was lazy to start off new topic this time or just didn't wanted to bother everyone with my questions...

I was feeling like I am having too many questions at the start itself but I think it is natural for any new learner.

I will take care of it in future and here I am assuming that installing vmware original tools makes more sense rather than going with packages available as open-vm-tools.

Regards,
Dharmavirsinh Jhala

---

