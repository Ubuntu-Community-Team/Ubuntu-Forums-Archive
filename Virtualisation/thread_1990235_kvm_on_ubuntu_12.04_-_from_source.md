---
title: "kvm on ubuntu 12.04 - from source"
date: 2012-05-29
forum: Virtualisation
---

### Post by essential1 on 2012-05-29
hi all,

i am trying to install kvm from source on ubuntu 12.04. i have already managed it using apt-get, but want to try to modify it. 

i followed the guide [here]("http://www.linux-kvm.org/page/HOWTO1"), after downloading and extracting [this]("http://sourceforge.net/projects/kvm/files/"). then i moved into that folder and did the following:

./configure --prefix=/usr/local/kvm 

make 

sudo make install 

sudo /sbin/modprobe kvm-intel

this passed without any problem. 
then i create a vm using :

/usr/local/kvm/bin/qemu-img create -f qcow2 vdisk.img 10G  

sudo /usr/local/kvm/bin/qemu-system-x86_64 -hda vdisk.img -cdrom /home/mus/downloads/ubuntu.iso \     -boot d

however the command

virsh -c qemu:///system list

does not show that a kvm virtual machine is running, so i suspect it is only running in qemu. i have followed the instructions on the official guide to the letter. can anybody suggest what i might be doing wrong please?

---

### Post by essential1 on 2012-05-30
this problem has been solved, the command mentioned works through virsh - however the create and run calls to the virtual machines run directly throught kvm-qemu and not through virsh. therefore virsh has no idea about them. 

the kvm appears to therefore be doing its job as expected.

---

