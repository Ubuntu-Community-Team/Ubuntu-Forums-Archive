---
title: "Advice for a home virtualization setup"
date: 2010-02-23
forum: Virtualisation
---

### Post by Mandor on 2010-02-23
Hi,

I would like to seek an advice for a virtualisation setup for home. I have one machine (Athlon X2, 4+ GB RAM projected) and I want to install a solid Linux OS, which I will use to run a software RAID array, store my files/backups and run virtual machines. For that use I'm wondering about Ubuntu Server, maybe the next LTS edition. 

Most of the time, I will run one VM with a desktop Linux of my preference for everyday use (so I can be more carefree for breaking it with a bleeding edge distro). I will also need to run some VMWare Win XP machines sometimes, so I basically need VMWare (under extreme inceovenience I might change that to other priduct). So I would like to use a free personal use product. I wonder if VMWare Server will do the job well - how problematic is it for installation and management on kernel updates, how convenient for managing VMs (I suppose it has some kind of management interface ...). I read somewhere that it is availavle in the partner repo, bit did't find anything more.


I know that the best way to understand is to test it, but if someone shares some experience beforehand, it can save me a lot of backups / reinstalling etc.

---

### Post by dehcbad25 on 2010-02-23
if your machine supports hardware virtualization (check on the BIOS) i would suggest that you use Vmware ESXi which is free, and run the server as a virtual machine as well. you will get better performance that way all around for all machines. i use vmware ESXi to run windows 2008R2

---

### Post by Mandor on 2010-02-23
Yeah, but as far as I understood, ECXi can be managed only from a Windows client. I must clear that I don't have other computers at home and everything, both VM server and VM clients will run on the same PC.

I will investigate the option, however.

---

### Post by dehcbad25 on 2010-02-23
the vSphere client is windows only, however they have a CLI for Linux, but I haven't use it at all. Maybe if you don't have a windows client at all then the VMware will not be a good solution unless you are willing to learn the CLI, and it might not be an easy task.
The LTS, still is 2 months away, and after it is release it will take 2 years for an upgrade. I think it is worthy to note that virtualization will change a lot in 2 years, so an LTS platform might not be the best choice. It will make the most robust however, but you will not get all the features as they come out. Do you already have the CPU BTW? an Phenom II would provide better performance thanks to the cache.
You can run vmware server on Ubuntu and during install it gives you the option (role) for virtualization server. That seems to be ytour best choice for now. I usually try to avoid the host OS to increase performance of the virtual machine, but it is also harder to manage.

---

### Post by Mandor on 2010-02-24
I already have the CPU - Athlon X2. Anyway - about performance - I have tried the VMWare Player already and it's fine for me for running VMs, so if the VMWare Server is not slower - it's OK. I prefer to have some management tools. CLI is OK for me, but I don't know if ECXi would provide all options I'm accustomed to.
I also need Linux host in order to assemble my software RAID and also I feel more comfortable with administrating Linux.

My question was more how well integrated are the Ubuntu Server distribution and VMWare Server - as I wrote, I read that there was some collaboration to make it more easily accessible - like putting th VMWare server in 'partner' repo, so it can be managed by apt, easier (or automatic) reconfiguration on kernel upgrade etc.

As for the LTS release - I don't know, but for the host OS, I will not need much more that managing my RAID, hosting filesystems and VMWare server. My everyday distro will be on a VM, where I can run a more bleeding edge OS. For changes in virtualisation - I hope that new versions of VMWare server will be backported, and even if not, as long as it runs, it's fine.

---

### Post by dcstar on 2010-02-26
> **Mandor said:**
> 
........
My question was more how well integrated are the Ubuntu Server distribution and VMWare Server - as I wrote, I read that there was some collaboration to make it more easily accessible - like putting th VMWare server in 'partner' repo, so it can be managed by apt, easier (or automatic) reconfiguration on kernel upgrade etc.
.......

VMware Server is not integrated any more, you simply have to run vmware-config when you ever install a new kernel to get it going again.

I use VMware server 1.0.10 (with the required kernel patch) on my 64-bit 9.04 system and it works fine, the minor issue of new kernels isn't a significant impost for what has turned out to be a pretty stable VM setup over the last few years.

---

