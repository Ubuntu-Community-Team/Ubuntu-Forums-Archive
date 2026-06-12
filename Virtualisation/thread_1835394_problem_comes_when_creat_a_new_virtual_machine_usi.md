---
title: "problem comes when creat a new virtual machine using libvirt"
date: 2011-08-29
forum: Virtualisation
---

### Post by xueliangfei on 2011-08-29
when i creat the new machine using code ```
sudo virt-install  - - connect qemu:///system  -n winxp  -r  512  - -vnc
-f  windowsxpsp3.qcow2   -s  12   -c  windowsxpsp3.iso   - -accelebrate  
- - noautoconsole
```

then i connect to the new virt machine to complete the install 
```
virt-viewer –c qemu:///system  web_devel
```
but  i   get the problem of below
[IMG]http://fmn.rrimg.com/fmn047/20110829/1925/p_large_C3lx_0c49000880085c70.jpg[/IMG]

who can help me to solve the problem ? thanks in advance!!
welcome all the possible solutions!!

---

### Post by bodhi.zazen on 2011-08-29
Try using the full path to your qcow and iso

---

### Post by xueliangfei on 2011-08-29
> **bodhi.zazen said:**
> Try using the full path to your qcow and iso
 
At first, thanks.
i hava done it by using the full path , but  the problem still comes.
so , what can i do next? 
any reply will be welcomed

---

### Post by xueliangfei on 2011-08-29
[IMG]http://fmn.rrfmn.com/fmn048/20110830/1045/p_large_Shb3_4a440007aeb15c41.jpg[/IMG]> **bodhi.zazen said:**
> Try using the full path to your qcow and iso
 
[B][SIZE=4][COLOR=red]this is the new picture of the virtual machine . the installation will be stop here   how can i solve it 
???[/COLOR][/SIZE][/B]

---

### Post by bodhi.zazen on 2011-08-29
Well, could be a bad iso for all I know.

You will need to simplify that command.

Try to boot the iso with kvm

```
kvm -m 512 -cdrom windows.iso -boot d
```

---

### Post by xueliangfei on 2011-08-30
> **bodhi.zazen said:**
> Well, could be a bad iso for all I know.
 
You will need to simplify that command.
 
Try to boot the iso with kvm
 
```
kvm -m 512 -cdrom windows.iso -boot d
```
 
 
thanks  very much    \problem has been solved.:guitar:

---

