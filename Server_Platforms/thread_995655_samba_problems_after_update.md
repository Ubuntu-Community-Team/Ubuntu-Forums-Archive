---
title: "samba problems after update"
date: 2008-11-28
forum: Server Platforms
---

### Post by wydensaas on 2008-11-28
Hy

Two days ago I have made an update of my Ubuntu 8.04 Server Editon. Than, yesterday I counldn't log me in. I doens't give me an error. Than I have looked up the following command in the inernet: apt-get remove libpam-smbpass

After this, I was able to log me in, but my samba doesn't function now!

For example, when I want to change the password of an user, it gives the following massage back:

```
smbpasswd ANYUSER
No builtin nor plugin backend for admin found
PANIC (pid 7508): pdb_get_methods_reload: failed to get pdb methods for backend admin

BACKTRACE: 7 stack frames:
 #0 smbpasswd(log_stack_trace+0x2d) [0x812a75d]
 #1 smbpasswd(smb_panic+0x5d) [0x812a88d]
 #2 smbpasswd [0x80e0dde]
 #3 smbpasswd(initialize_password_db+0xe) [0x80e0e2e]
 #4 smbpasswd(main+0x5db) [0x808617b]
 #5 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c77450]
 #6 smbpasswd [0x80856a1]
smb_panic(): calling panic action [/usr/share/samba/panic-action 7508]
smb_panic(): action returned status 0
Aborted

```

The I have tried to 'apt-get remove samba' and then 'apt-get install samba'. But it doenst work?

Can somebody help me?

Tank you.

Wyden

---

### Post by cariboo on 2008-11-28
Using apt-get remove program doesn't remove the configuration files. If you want completely remove a service and all its configuration files, use apt-get purge package. When having problems mounting a share check the log files. They are located in /var/log/samba. They should give you and indication of what is going wrong.

Jim

---

