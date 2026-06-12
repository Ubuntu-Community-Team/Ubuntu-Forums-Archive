---
title: "mount -t vboxfs -- no such type"
date: 2012-09-24
forum: Virtualisation
---

### Post by JKyleOKC on 2012-09-24
Trying to mount a shared folder in vbox 3.2.12, using the example from the vbox help manual (which works corrected in another VM), I get the error message that the mount type is wrong.

After a search of the forum for similar problems I found one that suggested doing "lsmod|grep vbox" to see whether the module had loaded properly. My result was > vboxnetadp              6326  0 
vboxnetflt             15344  0 
vboxdrv               190370  2 vboxnetadp,vboxnetflt
Obviously the module isn't there, nor does a search for it show it anywhere in the VM. I saw no errors when installing the Guest Additions, nor when I created the shared folder in the VM. However the VM is 64-bit while the shared folder is 32-bit. Does this have any effect on creation of the needed module?

And should I try re-installing Guest Additions to see if that fixes things? This is a production system, and I don't want to take chances of causing problems on the host although the 64-bit VM is expendable...

---

### Post by JKyleOKC on 2012-09-24
Another round of troubleshooting revealed that installation of the Guest Additions was failing with a segfault. Perhaps I've not allowed enough disk space for the VM.

In addition, my diagnostic efforts in the previous message reflect the host, not the guest (very senior moment, I fear). While I never saw the errors during my initial attempt to install the guest additions, they're quite clear today. The strange part is that mouse integration and automatic window sizing work despite the failure to install the needed modules. Perhaps it's the 64/32 bit mismatch that's causing the problem.

The specific error message I'm getting when I run the installer script complains about a "-lt" operator at line 360, but it seems perfectly okay. The segfault happens earlier, though, and the script continues on its merry way, finally uninstalling the never-installed additions... 'Tis a puzzlement...

---

### Post by JKyleOKC on 2012-09-25
The "unexpected operator" complaint turned out to be a result of the segfault, which resulted in an undefined script variable being used in the test -- the Oracle programmers obviously failed to anticipate the possibility of that variable being undefined.

The cause of the segfault still isn't clear, but it appears to be happening during an attempt to uncompress the actual "install.sh" script from the ".run" file.

Since the Guest Additions do install properly on other VMs in the same host, all of which are 32-bit, I'm becoming convinced that the problem is due to running a 64-bit VM on a 32-bit host. The great wonder is why it's allowed in the first place, under the circumstances -- or is that just another "failure to anticipate" by the developers?

---

