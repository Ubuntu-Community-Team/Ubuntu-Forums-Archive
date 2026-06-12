---
title: "Windows Server 2008 in Linux KVM Hanging"
date: 2012-12-07
forum: Virtualisation
---

### Post by expphoto on 2012-12-07
I've been working on getting a Windows Server 2008 KVM in my linux box running Ubuntu Server 12.04. I've got virt-install and virt-manager installed, got the install up and running via

virt-install --connect qemu:///system -n winsvr2008 -r 1024 --vcpus=1 --disk path=/home/pwnd/vm/2008.img,size=30 -c /home/pwnd/en_windows_server_2008_with_sp2_x86_dvd_342333.iso --graphics vnc,listen=192.168.1.127 --noautoconsole --os-type=windows --os-variant=win2k8 --network=bridge:virbr0 --hvm -v
and

virsh vncdisplay winsvr2008

I can connect and view, but upon starting, I get hung up on please wait right after clicking Install. Any ideas?

---

