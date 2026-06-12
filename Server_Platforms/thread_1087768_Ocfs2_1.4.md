---
title: "Ocfs2 1.4"
date: 2009-03-05
forum: Server Platforms
---

### Post by 3bit on 2009-03-05
Hello Ubuntuers,

is there any possibility to install OCFS2 version 1.4 in Ubuntu?

Sure I could compile it myself and be happy, but every kernel update would give me nightmares. 

If somebody has it packaged and an installation repository would be extremly good.

All advices are welcome.

---

### Post by Brazen on 2009-03-05
Even if somebody did have OCFS packaged in a third-party repository, you would be relying on them to keep it updated for each new kernel.  If you update your kernel and there is no matching OCFS2 build in the other repo, then that partition will be unusuable unless you boot into your previous kernel.  This could get messy and could cause unexpected boot failures on a server that runs unattended.

So my point is, I would stick with the OCFS that comes with Ubuntu.  If I just had to have OCFS2 version 1.4, then there are two other options - 1) switch to Debian which has OCFS2 1.4.1 in the stable branch, or 2) stay with Ubuntu and use DKMS to automatically rebuild the OCFS2 kernel module anytime there is a kernel upgrade.

Information on DKMS can be found in this pdf: [http://linux.dell.com/dkms/dkms-ols2004.pdf](http://linux.dell.com/dkms/dkms-ols2004.pdf)
It's full of information on how dkms works, but the important part starts on page 13 about setting up the dkms.conf file for the modules source.

---

