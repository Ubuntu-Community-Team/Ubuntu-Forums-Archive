---
title: "Available boot options in Ubuntu (/server)"
date: 2010-06-02
forum: Server Platforms
---

### Post by pepijn on 2010-06-02
Hi there!

I recently had some trouble getting my ubuntu lamp server to boot, because the CIFS folders couldn't mount.(because of a change of ipaddress - my bet). It caused the system to hang after the error message, saying /var/folder couldn't mount. Ctrl-D / -C / esc / q didn't do anything.

The problem was that i was unable to ssh into the machine, because apparently the ssh server would load after the cifs mount. I fixed it (changing ipaddress in /etc/fstab) by using the server cd Rescue option, but was wondering what other (build in)options there are to rescue a broken system. Without having to pull out the cd.

For example: A friend told me that RHEL has a keyboard shortcut that let's you answer YES or NO to every step in the boot process. This would've been a big help. Because you'd just choose 'no' for whatever is failing.

Is there a build in utility that I missed?
Are there other keyboard shortcuts?
Is there a way to change the order of init.d stuff, so that ssh starts before anything else?

I realize this is a broad question, but any helpful answers are appreciated.

---

### Post by pepijn on 2010-06-11
Anyone? ):P

---

### Post by lisati on 2010-06-11
Moved to "Server Platforms"

---

