---
title: "Samba + PAM error in syslog"
date: 2007-11-08
forum: Server Platforms
---

### Post by xianthax on 2007-11-08
hi all, i've had a x86 AMD drapper server install running for a little over a year now authenticating against a windows server 2003 domain controller, works great, its used as a file + print server + sftp server and have several VM's running inside of it for the few windows apps that require a windows server, all pretty much all without a hitch......however there is one nagging issue....

i've been trying to figure out this error which pops up every 5min (its a cron process), it appears in the syslog and auth.log files and i'm unsure what it is as it does not appear to effect operation of the server is any way...here is the error....

<code>
Nov  8 11:20:01 CSM-SERVER1 CRON[21293]: PAM unable to dlopen(/lib/security/pam_windbind.so)
Nov  8 11:20:01 CSM-SERVER1 CRON[21293]: PAM [dlerror: /lib/security/pam_windbind.so: cannot open shared object file: No such file or directory]
Nov  8 11:20:01 CSM-SERVER1 CRON[21293]: PAM adding faulty module: /lib/security/pam_windbind.so
Nov  8 11:20:01 CSM-SERVER1 CRON[21292]: PAM unable to dlopen(/lib/security/pam_windbind.so)
Nov  8 11:20:01 CSM-SERVER1 CRON[21292]: PAM [dlerror: /lib/security/pam_windbind.so: cannot open shared object file: No such file or directory]
Nov  8 11:20:01 CSM-SERVER1 CRON[21292]: PAM adding faulty module: /lib/security/pam_windbind.so
</code>

i'm using winbind to auth against the AD server and pam_windbind.so is in fact in the location listed in the error.

anyone seen this before or have a recommend direction to look for a solution?

thanks!

~x

---

### Post by Nerd_bloke on 2008-04-24
There is a typo in the module name you are using, should be "pam_winbind.so" without the "d" in the middle.

---

