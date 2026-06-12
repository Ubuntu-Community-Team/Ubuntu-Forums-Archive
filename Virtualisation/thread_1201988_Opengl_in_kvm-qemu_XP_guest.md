---
title: "Opengl in kvm-qemu XP guest"
date: 2009-07-01
forum: Virtualisation
---

### Post by MasterPoulos89 on 2009-07-01
I know VMGL enables opengl in a Linux guest vm but I need opengl for a windows guest so I can install wined3d to use directx.

Virtual box can easily enable opengl for any os so it should be possible for kvm-qemu to do it too.

So all I need is opengl in XP guest using kvm-qemu. Does anyone know how to do so. If so please help.

---

### Post by MasterPoulos89 on 2009-07-02
Now I'm not even sure if opengl is the problem cause I tried it in virtualbox with opengl enabled and got the same problem.

I think wined3d is at a stage where it should at least tell me direct 3d is enabled on the guest so I still thing I must be doing something wrong.

Does anyone know??

---

### Post by MasterPoulos89 on 2009-07-02
OK........I see the new version of Virtualbox(3.0) has default direct3d support I believe using wined3d.

I believe if opengl could be enabled in kvm-qemu then wined3d would work as it does for virtualbox. But I don't think kvm-qemu supports opengl for windows yet.

I think vmgl works with kvm for linux guest, so I would assume its not much harder for windows guest.

Does anyone know if it is possible??

---

