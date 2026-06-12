---
title: "VMWare in virtual terminals"
date: 2008-05-14
forum: Virtualisation
---

### Post by adam35413 on 2008-05-14
I have a very aggravating issue that I would love help with.  How do you send Ctrl+Alt+F# using code to running VMs in VMWare Workstation when you are inside the virtual terminals that are locked to the VMs without corrupting the keyboard/mouse locks?  
Example:  I start two VMs, and by using python's virtkey library, switch to the first VM's virtual terminal (9 in this case).  Everything is perfect at this point.  My python program then switches to the second VM's virtual terminal fine.  I then use ```
os.system("vmrun suspend pathToVMXfile soft") 
``` to stop the first VM.  At this point the terminals get hosed.  If I try to switch back to virtual terminal 7, I usually just see black.  After I kill the second VM manually, I end up seeing the workstation error that says that vmware failed to acquire the lock for the keyboard or mouse.  

I know that when you switch to a VM's virtual terminal by hitting Ctrl+Alt+F#, VMWare does some magic and ends up leaving X server in terminal 7.  

If the description above got confusing, I apologize.  Bottom line: I want to switch between VMware virtual terminals in Ubuntu with a program.  If some one knows of a better approach, I am all ears.  Again, I would love any help at all.  Thanks.

---

