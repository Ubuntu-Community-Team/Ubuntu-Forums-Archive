---
title: "stopping &quot;suspended&quot; Virtual Machine in VMWare, grub issues"
date: 2008-09-25
forum: Virtualisation
---

### Post by kellner on 2008-09-25
I followed [this guide]("http://venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/") to virtualize an existing Windows XP Professional installation in Ubuntu Hardy, using vmware server. 

Upon starting the virtual machine, I saw grub appearing and wanted to select Windows XP. However, the cursor did not react within the virtual machine, and Ubuntu booted up instead. This predictably corrupted my Ubuntu installation, but I managed to repair it. 

Foolishly, I tried it again, but on noticing that the cursor again didn't respond in the vm, I quickly suspended the vm. 

Now it's in suspended state, and I would just like to stop it and explore options how to get rid of grub in vmware. But it seems that I can't stop a suspended vm - however, if I continue, it's going to boot up Ubuntu again and corrupt the system ...

Any advice? 

The command I tried was: 

vmware-cmd "/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx" stop

... which returned this error: 

"VMControl error -8: Invalid operation for virtual machine's current state: The requested operation ("stop") could not be completed because it conflicted with the state of the virtual machine ("suspended") at the time the request was received.  This error often occurs because the state of the virtual machine changed before it received the request."

---

### Post by bradmkjr on 2008-09-25
real simple...

delete the state files associated with the vmx. this will erase all knowledge of the partial state. 

[http://www.petri.co.il/virtual_vmware_files_explained.htm](http://www.petri.co.il/virtual_vmware_files_explained.htm)

VMEM – A VMEM file is a backup of the virtual machine’s paging file. It will only appear if the virtual machine is running, or if it has crashed.


Next open up your preferred grub editor and set windows as the default. 

Boot machine inside of VMware Server, windows is already a default, so no worries about getting focus in time.

Brad
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

