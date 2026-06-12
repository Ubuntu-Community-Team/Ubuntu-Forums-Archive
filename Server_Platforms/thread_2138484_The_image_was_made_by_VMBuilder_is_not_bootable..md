---
title: "The image was made by VMBuilder is not bootable."
date: 2013-04-24
forum: Server Platforms
---

### Post by annahita on 2013-04-24
I made one image with below command 
[COLOR=#000000][FONT=Times New Roman]sudo  vmbuilder qemu  ubuntu --verbose --dest /home/anahita --suite precise  --flavour virtual --arch i386 -o --libvirt qemu:///system  --hostname VM   --user ubuntu --name user --pass ubuntu  --rootpass ubuntu  --part=/home/anahita/vmbuilder.partition --ssh-key ~/.ssh/id_rsa.pub  --addpkg hping3 --addpkg libc6 --addpkg libpcap0.8 --addpkg tcl8.4  --addpkg nmap[/FONT][/COLOR]

the image has been created successful but when I want to upload image.qcow2 in my cloud platform, I see the massage no bootable device and it does not come up. 
Can anybody help me?

---

