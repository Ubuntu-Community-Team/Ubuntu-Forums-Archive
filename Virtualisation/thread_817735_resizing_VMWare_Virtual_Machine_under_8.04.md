---
title: "resizing VMWare Virtual Machine under 8.04"
date: 2008-06-03
forum: Virtualisation
---

### Post by bluewhale on 2008-06-03
Hi.  I've been googling this for about a week. I would like to increase the size of a couple of VM's I have running on Ubuntu 8.04 and 7.10. All of the VM's are versions of Windows: we're experimenting with Ubuntu and VMWare to see if we can slowly start moving the company to Linux while still offering the 'ease of use' that Windows/Office provides. ( no snickering please  :-\"   ) 

None of the threads I've read actually match my test VM's. either the commands are incorrect, the references to choices on the screen are off, etc. It seems I need to change the physical parameters of the VM then go into that VM and change the size by using Qparted or something similar. 

One additional Q I add in is that we experimented by setting one VM up with 4 2GB files, another has one 8GB vmdk file, etc. 

Does anyone have a URL they like to refer noobs to regarding resizing VM Clients? ( doing so from VM Workstation and also the free server )

---

### Post by fjgaude on 2008-06-04
Seems like maybe you haven't checked the View/Autofix box items in vmware console menu?

I assume you have intalled the VMware Tools?

---

### Post by bluewhale on 2008-06-04
View/Autofit pertains to the size of the screen. I'm trying to change the size of the default 8 GB partition for this VM. 

Or did I miss a step?

---

### Post by fjgaude on 2008-06-04
I believe that once, during the console setup for the VM, you select the size of vm file you can't change it. You can delete it and start over... without having to install VMware again.

---

### Post by bluewhale on 2008-06-04
No, I'm certain it is doable. There are multiple ways to accomplish this from the threads I've read. But I have not been able to get it to work where hundreds before me have, thus my request. ](*,)

Thanks anyway.

---

### Post by bluewhale on 2008-06-05
Bump

---

### Post by fjgaude on 2008-06-05
Maybe one way is to simply copy the vm to another directory, create a big virtual file with the console, one that is big enough for your needs, then copy back the vm to this newly created virtual.

Look at this thread:

[http://ubuntuforums.org/showthread.php?t=818711](http://ubuntuforums.org/showthread.php?t=818711)

Help is on its way.

---

