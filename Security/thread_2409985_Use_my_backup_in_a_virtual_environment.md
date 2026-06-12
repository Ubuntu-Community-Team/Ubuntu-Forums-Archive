---
title: "Use my backup in a virtual environment"
date: 2019-01-09
forum: Security
---

### Post by luxocrypto on 2019-01-09
Hi, just switched from W10 to Ubuntu and loving it. Just a small question: I want to backup my (physical) Ubuntu and move it to a Virtualbox VM. However, the backup is 22 GB. How do I do that? My problem is in Virtualbox I can create the new VM, but I cannot access the backup files. I can select a "Local folder", however, that is the VM's local folder, it's not my physical machine's local folder. I also tried the Virtual box settings > Storage, but I can't figure it out...

---

### Post by &amp;KyT$0P# on 2019-01-09
How did you create the backup?

---

### Post by luxocrypto on 2019-01-09
The default backup program 'Backups' aka "Deja Dup."

---

### Post by SeijiSensei on 2019-01-09
You can access files and directories on the host machine by using the "Shared Folders" feature in VirtualBox.  You need to install the "Extension Pack" to do this.  

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

See [https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by luxocrypto on 2019-01-25
That worked. Thank you very much, SeijiSensei !

---

