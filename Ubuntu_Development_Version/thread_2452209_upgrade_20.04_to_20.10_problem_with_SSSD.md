---
title: "upgrade 20.04 to 20.10 problem with SSSD"
date: 2020-10-18
forum: Ubuntu Development Version
---

### Post by bert.ram.aerts on 2020-10-18
Hi,

Yesterday I upgraded my laptop from Ubuntu 20.04 to Ubuntu 20.10.

In syslog I read:
Oct 17 20:24:30 Dell7577Linux systemd[1]: sssd.service: Scheduled restart job, restart counter is at 4.
Oct 17 20:24:30 Dell7577Linux systemd[1]: Stopped System Security Services Daemon.
Oct 17 20:24:30 Dell7577Linux systemd[1]: Starting System Security Services Daemon...
Oct 17 20:24:30 Dell7577Linux sssd[1070]: SSSD couldn't load the configuration database [2]: No such file or directory.
Oct 17 20:24:30 Dell7577Linux systemd[1]: sssd.service: Main process exited, code=exited, status=4/NOPERMISSION
Oct 17 20:24:30 Dell7577Linux systemd[1]: sssd.service: Failed with result 'exit-code'.
Oct 17 20:24:30 Dell7577Linux systemd[1]: Failed to start System Security Services Daemon.
Oct 17 20:24:30 Dell7577Linux systemd[1]: Dependency failed for SSSD PAM Service responder socket.
Oct 17 20:24:30 Dell7577Linux systemd[1]: Dependency failed for SSSD PAM Service responder private socket.
Oct 17 20:24:30 Dell7577Linux systemd[1]: sssd-pam-priv.socket: Job sssd-pam-priv.socket/start failed with result

Also at boot there are 4 blocks of failing sssd messages about the same issue.

How can I solve this?

Kind regards,

Bert

---

### Post by ActionParsnip on 2020-10-18
Did you add the system to a Windows domain?

---

### Post by Frogs Hair on 2020-10-18
20.10 final has not been released yet. How did you upgrade ?

---

### Post by QIII on 2020-10-18
Moved to Ubuntu Development Version

---

### Post by bert.ram.aerts on 2020-10-18
sudo do-release-upgrade -d

---

### Post by bert.ram.aerts on 2020-10-18
> **ActionParsnip said:**
> Did you add the system to a Windows domain?

I use samba to mount a windows NTFS harddisk from another PC.

---

### Post by bert.ram.aerts on 2020-10-20
SOLVED
# debug with
sudo sssd -d9 -i
# solution
sudo cp /usr/lib/x86_64-linux-gnu/sssd/conf/sssd.conf /etc/sssd/.
sudo chmod 600 /etc/sssd/sssd.conf

---

### Post by P-I H on 2020-10-20
Nice finding.
Works OK, no errors in Logs
Debug after copy
```
p-i@asus-b450-f:~$ sudo sssd -d9 -i
[sudo] password for p-i: 
(2020-10-20 13:25:38:218954): [sssd] [main] (0x0010): pidfile exists at /run/sssd.pid
SSSD is already running
p-i@asus-b450-f:~$ 

```

---

### Post by eldroid-z on 2020-10-23
> **bert.ram.aerts said:**
> SOLVED
# debug with
sudo sssd -d9 -i
# solution
sudo cp /usr/lib/x86_64-linux-gnu/sssd/conf/sssd.conf /etc/sssd/.
sudo chmod 600 /etc/sssd/sssd.conf

Had the same problem after updating to 20.10 today,
Your solution works like a charm, Thank You

---

### Post by Gavin Fowler on 2020-10-23
> **bert.ram.aerts said:**
> SOLVED
# debug with
sudo sssd -d9 -i
# solution
sudo cp /usr/lib/x86_64-linux-gnu/sssd/conf/sssd.conf /etc/sssd/.
sudo chmod 600 /etc/sssd/sssd.conf

I upgraded today from 2.10->20.10 and this worked perfectly for me too - many thanks for posting.

---

