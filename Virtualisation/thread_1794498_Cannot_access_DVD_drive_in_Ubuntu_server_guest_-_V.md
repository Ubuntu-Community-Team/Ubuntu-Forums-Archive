---
title: "Cannot access DVD drive in Ubuntu server guest - Virtualbox"
date: 2011-07-01
forum: Virtualisation
---

### Post by roundhay on 2011-07-01
I have a Ubuntu server guest running in Virtualbox which is installed on a Ubuntu server host.

I have set up the virtual machine using the following commands, an all works well

```
VBoxManage createvm --name "TMdesk" --register
VBoxManage modifyvm "TMdesk" --memory 512 --acpi on --boot1 dvd --nic1 bridged --bridgeadapter1 eth0
VBoxManage createhd --filename TMdesk.vdi --size 15000
VBoxManage storagectl "TMdesk" --name "IDE Controller" --add ide
VBoxManage storageattach "TMdesk" --storagectl "IDE Controller" --port 0 --device 0 --type hdd --medium TMdesk.vdi
VBoxManage storageattach "TMdesk" --storagectl "IDE Controller" --port 1 --device 0 --type dvddrive --medium /home/user/isos/
```

I have the networking is OK and I can SSH into the virtual machine and can access the Virtual box gui of the host over my network by forwarding X

I want to be able to use the DVD drive of the host machine in the guest but I cannot get this to work.

**Problem 1**
After following the set up procedure above the ubuntu-10.04.2-server-i386.iso is attached to the DVD drive of the guest, my first question is how can I remove the iso image from the host DVD drive? 

**Problem 2**
How do you install guestadditions on a server? I have found a lot of guides explaining how to do this on a guest ubuntu desktop machine but can't find anything explaining how to so it via the command line?

**Workaround**
By forwarding the virtualbox gui of the host machine using X I managed to delete the host drive with the iso image attached and added a new one which I attached VBoxGuestAdditions.iso and managed to install the guest additions........
....but I have still not been able to managed to add the host DVD drive to the guest system

Any help would be greatly appreciated

I managed to work around this by forwarding virtualbox gui and deleting the drive and adding a new one

---

