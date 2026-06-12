---
title: "QEMU won't start using Qemulator"
date: 2008-04-28
forum: Virtualisation
---

### Post by samexner on 2008-04-28
I'm using Ubuntu Hardy x86-64, and I'm trying to get Mandriva 2007 to run in a x86-64 QEMU vm using Qemulator. When I try to start the VM, I get this output at the terminal:
> qemu called with command: qemu-system-x86_64 -M pc -smp 2 -m 2048 -kernel-kqemu -hda /home/sam/pclos64/myhdd.img -cdrom /home/sam/Desktop/boot.iso -net nic,vlan=0 -net user,vlan=0,hostname=emu -smb /home/sam/pclos64 -monitor pty -boot d
started qemu with pid: 6615
timeout!

While this happens, the qemulator window grays out, then the color is restored within a few seconds, and I get a window that says > Qemu exited with Error Message:

Anyone know how to fix this?

Thanks,
--Sam Exner

---

### Post by agent8131 on 2008-04-29
I'm still new to Qemulator and I haven't seen this problem but I'd suggest trying to reduce some of the options.  Perhaps removing the smb and monitor options might help.  Another thing to try would be copying the command into a terminal and running it to see if you get a more helpful error message.

---

