---
title: "rkhunter log analysis"
date: 2008-09-03
forum: Security
---

### Post by niller on 2008-09-03
Hi all

I've just discovered rkhunter and took it for a spin.

I have these issues in the log file, is it something I should be worried about and what have to be done ?

[17:35:59] Performing system configuration file checks
[17:35:59] Info: Starting test name 'system_configs'
[17:35:59]   Checking for SSH configuration file             [ Found ]
[17:35:59] Info: Found SSH configuration file: /etc/ssh/sshd_config
[17:35:59] Info: Rkhunter option ALLOW_SSH_ROOT_USER set to 'no'.
[17:35:59]   Checking if SSH root access is allowed          [ Warning ]
[17:35:59] Warning: The SSH and rkhunter configuration options should be the same:
[17:35:59]          SSH configuration option 'PermitRootLogin': yes
[17:35:59]          Rkhunter configuration option 'ALLOW_SSH_ROOT_USER': no
[17:35:59]   Checking if SSH protocol v1 is allowed          [ Not allowed ]
[17:35:59]   Checking for running syslog daemon              [ Found ]
[17:35:59]   Checking for syslog configuration file          [ Found ]
[17:35:59] Info: Found syslog configuration file: /etc/syslog.conf
[17:36:00]   Checking if syslog remote logging is allowed    [ Not allowed ]
[17:36:00]
[17:36:00] Performing filesystem checks
[17:36:00] Info: Starting test name 'filesystem'
[17:36:00] Info: SCAN_MODE_DEV set to 'THOROUGH'
[17:36:14]   Checking /dev for suspicious file types         [ Warning ]
[17:36:14] Warning: Suspicious files found in /dev:
[17:36:14]          /dev/shm/pulse-shm-2448036307: data
[17:36:14]          /dev/shm/pulse-shm-803441736: data
[17:36:15]   Checking for hidden files and directories       [ Warning ]
[17:36:15] Warning: Hidden directory found: /etc/.java
[17:36:15] Warning: Hidden directory found: /dev/.static
[17:36:15] Warning: Hidden directory found: /dev/.udev
[17:36:15] Warning: Hidden directory found: /dev/.initramfs

Any pointers is highly appreciated as I dont have a clue :-/

Thanks
Niller

---

### Post by rogeriopvl on 2008-09-03
Well, no need to worry about the warnings. But you should change the configuration of your sshd to not allow root login.

To do this just edit the file /etc/ssh/sshd_config, and change the line: "PermitRootLogin: yes" to: "PermitRootLogin: no".

This should get you rid of the SSH warning :)

---

### Post by niller on 2008-09-03
Thanks for reply :-)

But when I'm open the file /etc/ssh/sshd_config the PermitRootLogin or ALLOW_SSH_ROOT_USER entry is not there :-/

I'm currently running Hardy Heron.

---

### Post by rogeriopvl on 2008-09-03
If not, you may add it.

---

### Post by niller on 2008-09-03
Okay :-)

Thanks !!

---

### Post by brian_p on 2008-09-03
> **niller said:**
> Thanks for reply :-)

But when I'm open the file /etc/ssh/sshd_config the PermitRootLogin or ALLOW_SSH_ROOT_USER entry is not there :-/

I'm currently running Hardy Heron.

It should be there but whether it is or not makes no difference with Ubuntu as there is no root account to log into anyway.

---

### Post by ds[de] on 2008-09-03
> **brian_p said:**
> It should be there but whether it is or not makes no difference with Ubuntu as there is no root account to log into anyway.

Hm maybe he enabled the root account?
Or if he enables it later (for some reason) and then forgets about SSHd? It's better to be safe than sorry.


Regards,
ds[de]

---

### Post by brian_p on 2008-09-03
> **'ds[de] said:**
> Hm maybe he enabled the root account?

Then it would make sense to consider altering the default 'yes' to 'no'.

> Or if he enables it later (for some reason) and then forgets about SSHd? It's better to be safe than sorry.

No need for him to be sorry. A login to the root account is no less safe than one into a user account.

---

