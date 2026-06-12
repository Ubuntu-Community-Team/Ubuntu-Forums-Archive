---
title: "samba-ad-dc package and sudo rights"
date: 2024-11-04
forum: Server Platforms
---

### Post by sahulkko on 2024-11-04
Hi,
Upgraded to latest:
samba-ad-dc/noble,noble,now 2:4.19.5+dfsg-4ubuntu9
Now I am not able to password auth a sudo group member if it is also a domain user while nsswitch.conf is configured with winbind.

In auth.log I get:
pam_krb5(sudo:auth): authentication failure; logname=DOMAIN\user uid=xxxxxx euid=0 tty=/dev/pts/2 ruser=DOMAIN\user rhost=
pam_unix(sudo:auth): conversation failed
pam_unix(sudo:auth): auth could not identify password for [DOMAIN\user]

in log.DOMAINwb:
auth/gensec/gensec_start.c:844(gensec_start_mech)
  Starting GENSEC mechanism gse_krb5
source3/librpc/crypto/gse_krb5.c:425(fill_mem_keytab_from_system_keytab)
  source3/librpc/crypto/gse_krb5.c:425: krb5_kt_start_seq_get failed (Permission denied) 

**No file read access for winbindd for system keytab/etc/krb5.keytab**



There is no winbind or samba user and I have presumed that samba-ad-dc is run by root that has rw access to that file. One could add group access to keytab if one would know who is running winbindd sub process of reading keytab into cache.

This only happens in AD-DC system. All other servers happily do password auth for sudo.

Atol

---

### Post by sahulkko on 2024-11-04
I can add that there are no apparmor DENIED cases.

---

### Post by sahulkko on 2024-11-04
ps -aux shows:
root        5101  0.0  0.3 169692 63488 ?        Ss   13:22   0:01 /usr/sbin/winbindd -D --option=server role check:inhibit=yes --foreground
While in LOG:
[COLOR=#000000]source3/librpc/crypto/gse_krb5.c:425: krb5_kt_start_seq_get failed (Permission denied)
and ls- -l shows:
[/COLOR]-rw------- 1 root root 6917 Nov  1 16:32 /etc/krb5.keytab[COLOR=#000000]

[/COLOR]

---

### Post by sahulkko on 2024-11-04
The right asnwer is:
chmod 0640 on /etc/krb5.keytab to:
-rw-r----- 1 root root 6917 Nov  1 16:32 /etc/krb5.keytab

and logins work!

---

