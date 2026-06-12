---
title: "VMware Server installed but won't run."
date: 2007-12-01
forum: Virtualisation
---

### Post by scrawford on 2007-12-01
I'm running Gutsy, and have an apparetnly successful install of VMware server, as reported by the install program. 

When I click the VMware Server console icon, the mouse pointer spins for a few seconds, then disappears, and nothing else happens.

Any suggestions would be helpful.

---

### Post by Cornerville on 2007-12-04
Run it from a terminal. Just type in vmware.  It will likely say "Vmware is installed but not configured correctly.  Run vmware-config.pl"  If it does then run sudo rm /etc/vmware/not_ configured.  This will fix it until you boot the system again, then you will have to do it again.  If you had vmware player installed before, run a search for vmware player and delete all the files you find.  This may correct the problem permanently.

---

### Post by scrawford on 2007-12-11
Running from terminal worked. Will start it from a terminal from now on.

Thanks for the advice.

---

