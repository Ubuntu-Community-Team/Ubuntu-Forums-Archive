---
title: "Intrepid - VMWare Server 2.0 Pageload error (stopped working)"
date: 2009-01-29
forum: Virtualisation
---

### Post by nderic77 on 2009-01-29
After installing updates yesterday (28 January), my VMWare Server is suddenly not working. I get the following error from Firefox when I attempt to access [https://127.0.0.1:8333/ui/#:](https://127.0.0.1:8333/ui/#:)

Firefox can't establish a connection to the server at 127.0.0.1:8333

I get a similar error when I attempt to boot a VM directly from the desktop link. Any idea how to fix this? Many thanks in advance.

nb: I am trying to boot an XP VM.

---

### Post by Cato2 on 2009-01-29
This thread looks similar:  [http://ubuntuforums.org/showthread.php?t=946973](http://ubuntuforums.org/showthread.php?t=946973)

The last post suggests that if you have had a kernel upgrade just recently (check your dpkg log in /var/log), you may need to reconfigure VMware to handle this.  This might explain why it's only failed after recent updates.  However, do try the other suggestions first.

---

### Post by nderic77 on 2009-01-29
> **Cato2 said:**
> This thread looks similar:  [http://ubuntuforums.org/showthread.php?t=946973](http://ubuntuforums.org/showthread.php?t=946973)

The last post suggests that if you have had a kernel upgrade just recently (check your dpkg log in /var/log), you may need to reconfigure VMware to handle this.  This might explain why it's only failed after recent updates.  However, do try the other suggestions first.

Thank you for the heads-up. I re-compiled using the perl script, and am back in business.

---

