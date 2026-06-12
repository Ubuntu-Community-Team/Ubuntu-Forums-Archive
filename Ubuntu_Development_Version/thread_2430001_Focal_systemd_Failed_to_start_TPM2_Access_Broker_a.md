---
title: "Focal: systemd: Failed to start TPM2 Access Broker and Resource Management Daemon."
date: 2019-10-26
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-10-26
That error is now flooding the log.
To understand what is going on: [https://www.reddit.com/r/linuxquestions/comments/dhinl0/what_is_tpm2abrmdservice_and_why_does_it_try_fail/](https://www.reddit.com/r/linuxquestions/comments/dhinl0/what_is_tpm2abrmdservice_and_why_does_it_try_fail/)

So checking my hardware:

oem@oem-desktop:~$ ls /dev | grep tpm0   ===> nothing found

so disabling that flooding service

oem@oem-desktop:~$ sudo systemctl disable tpm2-abrmd.service
[sudo] password for oem: 
Synchronizing state of tpm2-abrmd.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install disable tpm2-abrmd
Removed /etc/systemd/system/multi-user.target.wants/tpm2-abrmd.service.

This is a systemd fault: it should check first if the hardware is able to run that service instead of enabling it everywhere :mad:

[https://github.com/tpm2-software/tpm2-tss/issues/1541](https://github.com/tpm2-software/tpm2-tss/issues/1541)

---

