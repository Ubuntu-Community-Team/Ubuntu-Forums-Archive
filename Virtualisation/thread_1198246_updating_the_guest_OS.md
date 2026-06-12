---
title: "updating the guest OS"
date: 2009-06-27
forum: Virtualisation
---

### Post by cjv8888 on 2009-06-27
I have successfully installed Win2000 in VirtualBox. 
Just wondering:

1. Should I install all the Windows Updates and turn on the automatic updates.  
2. Install firewall and antivirus program?
3. Defragment, antivirus and antispyware scan the guest OS?  :P

---

### Post by dcstar on 2009-06-27
> **cjv8888 said:**
> I have successfully installed Win2000 in VirtualBox. 
Just wondering:

1. Should I install all the Windows Updates and turn on the automatic updates.  
2. Install firewall and antivirus program?
3. Defragment, antivirus and antispyware scan the guest OS?  :P

Yes, it doesn't really matter if you run a security deficient (P)OS on a real machine or a VM, it is still vulnerable.

---

### Post by binbash on 2009-06-28
Install updates but skip the firewall + antivirus if you are not gonna use windows to store an important file.firewall + antivirus will make the virtual OS slower a lot.

---

### Post by bodhi.zazen on 2009-06-28
You should treat your virtual windows as you would a physical installation. To be honest, I suggest you install all updates, install all the software you need, then take a snapshot or back up the virtual disk.

---

