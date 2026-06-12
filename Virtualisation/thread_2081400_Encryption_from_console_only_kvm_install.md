---
title: "Encryption from console only kvm install"
date: 2012-11-06
forum: Virtualisation
---

### Post by Nemus on 2012-11-06
So I would say that the console only install for ubuntu is awesome using the serial port, except for one issue. 

When I do a console only install if I put encryption on the hard drive I have to have a vnc console to the box. I would like to be able to set the hard drive encryption password by serial console install in kvm. 

Here is an example command I use to do a no graphics install of a kvm virtual machine. 

virt-install --nographics -n Spoon -r 1024 --os-type=linux --os-variant=debianlenny --disk /opt/kvm/images/Spoon.qcow2,device=disk,bus=virtio,size=24,sparse=true,format=qcow2 -w bridge=br0,model=virtio --noautoconsole --location  [ftp://mirrors.xmission.com/debian/dists/wheezy/main/installer-amd64/](ftp://mirrors.xmission.com/debian/dists/wheezy/main/installer-amd64/) -x "console=ttyS0" 

If I chose to encrypt the hardrive and have specified no graphics from virt-install I cannot enter the passphrase to decrypt the virutal machine. 

I would really like this feature if at all possible. I don't know where else to post this because I think I am the only one in the world that does this.

---

