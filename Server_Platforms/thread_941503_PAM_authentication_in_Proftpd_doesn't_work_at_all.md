---
title: "PAM authentication in Proftpd doesn't work at all"
date: 2008-10-08
forum: Server Platforms
---

### Post by Hark on 2008-10-08
I try to let ProFTPD on Ubuntu Hardy work with PAM authentication (and PAM uses my LDAP server). However it looks like ProFTPD doesn't use PAM at all. I cannot see anything about PAM in the (trace) log files. What am I doing wrong? Here is my proftpd.conf:

```

TraceLog /var/log/proftpd/trace.log
Trace pam:10            # trace.log stays empty with this setting...

Include /etc/proftpd/modules.conf
UseIPv6				off
ServerName			"Debian"
ServerType			standalone
DeferWelcome			on
UseReverseDNS                   off
IdentLookups                    off
DisplayConnect                  /etc/ftpwelcome
MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on
TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200
ListOptions                	"-l"
DenyFilter			\*.*/
DefaultRoot			~
Port				21
PassivePorts                  49152 65534
MaxInstances			30
Umask				022  022
AllowOverwrite			on
AuthPAM				on
AuthOrder			mod_auth_pam.c # also tried mod_auth_pam.c* and *mod_auth_pam.c, that also doesn't work (I don't know what the * means b.t.w.)
TransferLog /var/log/proftpd/xferlog
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

```

I'm expecting at least some PAM info in /var/log/proftpd/trace.log with this configuration, but it stays completely empty.

In proftpd.log I only get errors like these:

```
Oct 08 13:15:12 webserver proftpd[20275] webserver.domain.nl (1.2.3.4[1.2.3.4]): FTP session opened.
Oct 08 13:15:12 webserver proftpd[20275] webserver.domain.nl(1.2.3.4[1.2.3.4]): no such user 'test'
Oct 08 13:15:12 webserver proftpd[20275] webserver.domain.nl(1.2.3.4[1.2.3.4]): USER test: no such user found from 1.2.3.4 [1.2.3.4] to 1.2.3.4:21
Oct 08 13:15:12 webserver proftpd[20275] webserver.domain.nl(1.2.3.4[1.2.3.4]): FTP session closed.
```

Of course the user test is in LDAP and PAM can find it. Only ProFTPD cannot.

---

### Post by Hark on 2008-10-09
I finally figured out that the ftp user can log in when I add it to /etc/passwd. The password is then checked with PAM (LDAP). But of course I don't want to add all users to /etc/passwd, since they are already in LDAP with their id, homedir etc.
Is this possible? Of course I can use proftpd-ldap, but I would really like to use pam.

---

### Post by Hark on 2008-10-10
Ok, I now read somewhere that PAM cannot provide some information like homedir. Apparently proftpd cannot use nss like the os can.

I have now configured proftpd so it uses LDAP directly, that works ok. But I have configured PAM in way that it does some additional checks on a user. I can write these rules in a filter in the proptpd LDAPDoAuth setting, but is it possible to use PAM authentication in combination with LDAP for proftpd?

I have tried to set LDAPDoAuth to off (so it has to fall back to PAM for authentication), but when I do that the proftpd child segfaults when a user tries to connect.

---

### Post by Hark on 2008-10-13
I finally managed to get proftpd work with PAM/NSS. The only thing that I needed to add to proftpd.conf was
```
PersistentPasswd              off
```

All other directives (that sometimes caused segfaults) were not necessary, I just commented out AuthOrder, AuthPAM, AuthPAMConfig etc. and didn't have to use ldap.conf.

Thanks for your help...

---

### Post by tonymaro on 2009-03-08
No, thank YOU for the help - but I'd really rather use the LDAP settings myself so I could auth against a specific OU and only those people get access...

But I'm having the same segfaults you were.

---

