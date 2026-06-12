---
title: "Virtualbox VERR_SSM_LOAD_CPUID_MISMATCH error"
date: 2009-06-29
forum: Virtualisation
---

### Post by rmcd on 2009-06-29
I just upgraded from Intrepid to Jaunty. Virtualbox now fails when I try to start my XP virtual machine. I get the error (xxxx is the uuid):

> Unable to restore the virtual machine's saved state from '/home/rmcd/.VirtualBox/Machines/Windows XP/Snapshots/xxxx.sav'. It may be damaged or from an older version of VirtualBox. Please discard the saved state before starting the virtual machine (VERR_SSM_LOAD_CPUID_MISMATCH).

Any suggestions? I would hate to rebuild the machine from scratch but I'm not sure what to do. I have tried using taskset as follows (with c=0, 1, and {0,1}):

sudo taskset -pc 0,1 14629

with 14629 the process id of /usr/lib/virtualbox/VirtualBox . This doesn't change anything.

Suggestions more than welcome. Thanks!

Bob

---

### Post by rmcd on 2009-06-30
Here is a workaround in case anyone else has this problem. 

1. Use File|Export appliance to create a disk based on the latest version of your VM.

2. Use File|Import appliance to create a new VM. 

3. You can now run the new VM since it starts in a powered-off state.

I'm 95% sure there is a simpler way to do this, but I don't know what it is. I hope that others will find helpful either this post or the post telling me I missed a simpler solution :-)

---

