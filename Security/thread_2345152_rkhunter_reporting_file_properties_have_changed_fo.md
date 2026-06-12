---
title: "rkhunter reporting file properties have changed for /bin/bash"
date: 2016-12-01
forum: Security
---

### Post by preske87 on 2016-12-01
Good Morning,

I am running an Ubuntu based root server for a week now, one of the first actions was to install rkhunter. Now this morning I got this report:

```

Warning: Checking for prerequisites               [ Warning ]
         Unable to find 'lsattr' command - all file immutable-bit checks will be skipped.
Warning: The file properties have changed:
         File: /bin/bash
         Current file modification time: 1480536254 (30-Nov-2016 21:04:14)
         Stored file modification time : 1480273481 (27-Nov-2016 20:04:41)
Warning: Found enabled xinetd service: /etc/xinetd.d/ftp_psa
Warning: Found enabled xinetd service: /etc/xinetd.d/poppassd_psa
Warning: No output found from the lsmod command or the /proc/modules file:
         /proc/modules output:
         lsmod output:
Warning: The SSH and rkhunter configuration options should be the same:
         SSH configuration option 'PermitRootLogin': yes
         Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
Warning: Suspicious file types found in /dev:
         /dev/.udev/rules.d/root.rules: ASCII text
Warning: Hidden directory found: /dev/.udev: directory

```

the section about changed /bin/bash is confusing me, especially as neither /var/log/apt/history.log nor /var/log/aptitude show any record or change.

Further, when looking into the directory, I already see it being changed yet again:


```

root@h2634426:/bin# ll | grep bash
-rwxr-xr-x  1 root root 1021112 Dez  1 06:42 **bash***
lrwxrwxrwx  1 root root       4 Okt  7  2014 r**bash** -> **bash***

```

---

