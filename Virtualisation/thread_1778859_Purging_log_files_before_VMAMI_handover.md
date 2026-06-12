---
title: "Purging log files before VM/AMI handover"
date: 2011-06-09
forum: Virtualisation
---

### Post by wspoonr on 2011-06-09
We need to sanitise VMs and AMIs before snapshotting and handing over to clients. The log files are one area of concern. The following command is appealing as it should just purge all of the files in /var/log/, but is it dangerous - e.g. making the system unstable in any way?

   sudo find /var/log/ -type f -exec cat /dev/null > {} \;

Does Ubuntu (and 'good' Ubuntu packages) keep log files containing sensitive info anywhere other than /var/log (and /home)?

---

