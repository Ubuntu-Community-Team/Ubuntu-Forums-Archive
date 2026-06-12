---
title: "Macbook Pro: Ubuntu Host and OS X virtual guest?"
date: 2009-04-14
forum: Virtualisation
---

### Post by Aryding on 2009-04-14
So here's my deal.  I have a Macbook Pro and do not want to run OS X natively, but through Virtualbox on Ubuntu.  1) Is this possible?  2) How can I go about and do it since I cannot choose any Mac options in the installation?

Again, this is on a Macbook Pro and I own the rights to a copy of OS X.

---

### Post by pafufta503 on 2009-04-14
this is only currently possible on PowerPC macs.  using mac-on-linux or pearpc.  for intel macs i do not believe it is possible to run OS X as a virtual guest OS.

---

### Post by Peasantoid on 2009-04-14
Probably not. Apple is a bitch.

---

### Post by juancarlospaco on 2009-04-15
I have a running OS X on Qemulator (Qemu+KQemu)

*qemu -M pc -hda /home/juancarlospaco/OSX -soundhw ac97 -m 1024 -cdrom /home/juancarlospaco/10.5.5/10.5.5.iso -net nic,vlan=0 -net user,vlan=0,hostname=OSX  -boot d*

---

### Post by lpsantil on 2009-07-18
> **juancarlospaco said:**
> I have a running OS X on Qemulator (Qemu+KQemu)

*qemu -M pc -hda /home/juancarlospaco/OSX -soundhw ac97 -m 1024 -cdrom /home/juancarlospaco/10.5.5/10.5.5.iso -net nic,vlan=0 -net user,vlan=0,hostname=OSX  -boot d*

Where did you get the iso?  I'm having issues with 10.5.4 retail.

---

### Post by bodhi.zazen on 2009-07-18
I believe it is a violation of the OSX license to run it virtual and I doubt an OSX .iso is legal =)

---

