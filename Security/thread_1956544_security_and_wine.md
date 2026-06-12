---
title: "security and wine"
date: 2012-04-11
forum: Security
---

### Post by mrmedia on 2012-04-11
This is going to get moved so my apologise.  I posted in winehq, and would like to reference that here in case there are some discussions.   [http://forum.winehq.org/viewtopic.php?t=15302](http://forum.winehq.org/viewtopic.php?t=15302)  I am curious as to how to lockdown wine when on Ubuntu.   Thanks

---

### Post by haqking on 2012-04-11
> **mrmedia said:**
> This is going to get moved so my apologise.  I posted in winehq, and would like to reference that here in case there are some discussions.   [http://forum.winehq.org/viewtopic.php?t=15302](http://forum.winehq.org/viewtopic.php?t=15302)  I am curious as to how to lockdown wine when on Ubuntu.   Thanks

Dont use as root and dont open or use potentially or untrusted possible malicious files

Peace

---

### Post by 0011235813 on 2012-04-11
In addition to what haqking said, you should use clamscan to scan the .exe before you ran it, which will weasel out most malware. You can use the *clamscan* syntax in the command line emulator, or you could use virus scanner in the repositories. 

PS: If there was a Linux compatibility layer in Windows, Windows would probably get viruses since it runs the emulator as root by default ):P

---

