---
title: "rootkit? or false positive?"
date: 2004-11-03
forum: Server Platforms
---

### Post by AsteriskNix on 2004-11-03
installed chkrootkit from Universe today and ran it. This is a 1 week old install, and my only packages are from the Ubuntu+Universe. Here is my output...

Checking `lkm'... You have    14 process hidden for readdir command
You have    14 process hidden for ps command
Warning: Possible LKM Trojan installed

 ^^^^
  
I did some googling on this topic and I saw things from "Sky is falling, disconnect now!!@@!11one" posts to 

"your distro may be running apps that does this on purpose.

I would like to know if anyone knows the scoop on this, or if I may actually have a hacked ps binary.

Thanks in advance

*nix

---

### Post by jdodson on 2004-11-04
do you have any services running(SSH, Telnet, FTP, etc), if you dont then i wouldnt worry about it too much as the deault ubuntu install has no ports open.

---

### Post by Seti on 2004-11-06
Yeah, getting the LKM false-alarm seems to be pretty common; LOTS of us get it, and its a pretty safe assumption that it is usually a false positive. LinuxKernelModule. I have been told that it is caused by using the newer 2.6 kernels, although I'm not entirely sure what causes it exactly. Something about processes starting and stopping during the check. But yeah, a nice comprehensive info page on the subject would be nice.

---

