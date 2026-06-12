---
title: "Tips : Virtualbox 3 and above command line tips"
date: 2011-04-26
forum: Virtualisation
---

### Post by hawk2010 on 2011-04-26
Hi All,

I have found below during my research into the command line interaction between Virtualbox which were time saving and hopefully informative for all those admins out there. I think the shortcuts below will save time and effort in searching for commands. During my days I had to test out each one since the manuals were not up to date on Virtualbox website.

VBoxManage setproperty hdfolder /vms/vms/vdifiles

VBoxManage createvm -name "avserver" --basefolder /vms/vms -register
VBoxManage modifyvm "avserver" --memory "512"
VBoxManage modifyvm "avserver" --acpi on
VBoxManage modifyvm "avserver" --boot1 dvd 
VBoxManage modifyvm "avserver" --nic1 bridged --bridgeadapter1 eth0
VBoxManage createhd --filename avserver --size 61440 --format VDI --variant Standard --register
VBoxManage storagectl "avserver" --name "IDE Controller" --add ide
VBoxManage storageattach "avserver" --storagectl "IDE Controller" --port 0 --device 0 --type hdd --medium avserver.vdi
VBoxManage storageattach "avserver" --storagectl "IDE Controller" --port 1 --device 0 --type dvddrive --medium /to/iso
VBoxManage modifyvm "avserver" --vrdp on --vrdpport 3339 --vrdpaddress 192.168.2.220 --vrdpauthtype external

Unregister and Delete the VM
---------------------------------
VBoxManage unregistervm "avserver" --delete


Starting VM with VRDP enabled
---------------------------------
VBoxHeadless --startvm "avserver" --vrdp=config


Stopping VM
---------------------------------
VBoxManage controlvm "avserver" poweroff/resume/pause


VBoxManage showvminfo "avserver"

---

### Post by howefield on 2011-04-27
Thread moved to the "*Virtualization*" forum.

---

### Post by falko on 2011-04-27
Thanks a lot! :)

Here are some commands cor VirtualBox 4.0: [http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server](http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.0-on-a-headless-ubuntu-10.10-server)

---

