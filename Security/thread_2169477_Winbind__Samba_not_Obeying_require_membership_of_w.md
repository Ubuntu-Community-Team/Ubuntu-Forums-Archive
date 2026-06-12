---
title: "Winbind / Samba not Obeying require_membership_of when ActiveDirectory &quot;User must cha"
date: 2013-08-22
forum: Security
---

### Post by jason18 on 2013-08-22
Okay, so I have an Active Directory server running on Windows Server 2012 Standard
I have configured Samba/Kerberos/Winbind to bind to the DC properly.
I am able to login with my Active Directory users
When I use the 'require_membership_of' option in pam.d/common-auth for winbind.so using the SID of the group I want to restrict access to, it works like a charm.
There is a drawback to using this it seems. When I go into my AD server and check the box marked "User must change password at next logon" then that user, regardless of being apart of the required group, is granted access on my ubuntu client.
Has anyone ever experienced this before? Would anyone know of a fix?


When I first install winbind and samba I run this command with a ReadOnly account:
/usr/bin/net ads join -U ${join_user}%${join_pass}


My files are listed below


**Common-Account:**
```
account [success=2 new_authtok_reqd=done default=ignore] pam_unix.so 
account [success=1 new_authtok_reqd=done default=ignore] pam_winbind.so 
account requisite pam_deny.so
account required pam_permit.so
```




**Common-Auth:**
```
auth [success=2 default=ignore] pam_unix.so nullok_secure
auth [success=1 default=ignore] pam_winbind.so require_membership_of=S-1-5-21-5555555-5555555-5555555-5555 krb5_auth krb5_ccache_type=FILE cached_login use_first_pass
auth requisite pam_deny.so
auth required pam_permit.so
auth optional pam_mount.so 
auth optional pam_cap.so 
```


**Common-Password:**
```
password [success=2 default=ignore] pam_unix.so obscure sha512
password [success=1 default=ignore] pam_winbind.so
password requisite pam_deny.so
password required pam_permit.so
password optional pam_gnome_keyring.so
``` 


**Common-Session:**
```
session [default=1] pam_permit.so
session requisite pam_deny.so
session required pam_permit.so
session optional  pam_umask.so
session required pam_unix.so
session required  pam_mkhomedir.so umask=0022 skel=/etc/skel 
session optional pam_winbind.so 
session optional pam_mount.so 
session optional pam_xdg_support.so 
session optional pam_ck_connector.so nox11
```


**Common-Session-NonInteractive:**
```
session [default=1] pam_permit.so
session requisite pam_deny.so
session required pam_permit.so
session optional  pam_umask.so
session required pam_unix.so 
session optional pam_winbind.so 
session optional pam_xdg_support.so 
```


**/etc/krb5.conf**
```
[logging]
default = FILE:/var/log/krb5.log
[libdefaults]
default_realm = IN.MYCOMPANY.COM
kdc_timesync = 1
ccache_type = 4
forwardable = true
proxiable = true
[realms]
IN.MYCOMPANY.COM = {
kdc = in.mycompany.com
admin_server = in.mycompany.com
default_domain = in.mycompany.com
}
[domain_realm]
.in.mycompany.com = in.mycompany.com
in.mycompany.com = in.mycompany.com
```




**/etc/nsswitch.conf**
```
passwd:         files compat ldap winbind
group:          files compat ldap winbind
shadow:         files compat ldap winbind
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
```


**/etc/samba/smb.conf:**
```
[global]
   workgroup = inCOMPANY
   server string = %h server (Samba, Ubuntu)
   netbios name = %h
   dns proxy = no
   realm = IN.MYCOMPANY.COM
   local master = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   wtmp directory = /var/log
   utmp = yes
   utmp directory = /var/run
   security = ADS
   client ntlmv2 auth = yes
   ntlm auth = no
   guest account = nobody
   restrict anonymous = 2
   idmap backend = tdb
   idmap uid = 10000000-30000000
   idmap gid = 10000000-30000000
   idmap config inIS:backend = rid
   idmap config inIS:range = 100000-999999
   template shell = /bin/bash
   template homedir = /home/%D/%U
   winbind separator = +
   winbind use default domain = yes
   winbind offline logon = true
   winbind enum users = yes
   winbind enum groups = yes
   winbind refresh tickets = true
   winbind cache time = 60
   allow trusted domains = yes
   smb ports = 445
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   password server = in.mycompany.com
   client use spnego = yes
   encrypt passwords = no
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   map untrusted to domain = Yes
   usershare allow guests = yes
   load printers = no
```

---

### Post by jason18 on 2013-08-26
Is there something wrong with my pam stack??

---

