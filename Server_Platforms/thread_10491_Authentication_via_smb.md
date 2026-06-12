---
title: "Authentication via smb"
date: 2005-01-08
forum: Server Platforms
---

### Post by szz on 2005-01-08
I would like to use Ubuntu linux in a school, where students authenticate themselves via smb. Under an other distribution (UHU-Linux) I had **pam_smb_auth.so** for this purpose, but I can't find anything. Can you help me?

Thank you
SzZ

---

### Post by jdong on 2005-01-08
IT should be in libpam-smbpass.

---

### Post by szz on 2005-01-09
I can find only **pam_smbpass.so** in the mentioned package, but I suppose that in this case the samba database must be on the same machine as the user wants to log on:
"pluggable authentication module for SMB password database".

My need would be a possibility to authenticate against an *smb password database of an other (network) machine.* (This works for UHU-Linux, so I suppose this must be possible for UBUNTU, too.)

---

### Post by nocturn on 2005-01-12
[QUOTE=szz]I can find only **pam_smbpass.so** in the mentioned package, but I suppose that in this case the samba database must be on the same machine as the user wants to log on:
"pluggable authentication module for SMB password database".

My need would be a possibility to authenticate against an *smb password database of an other (network) machine.* (This works for UHU-Linux, so I suppose this must be possible for UBUNTU, too.)[/QUOTE]

I am not sure, but I think it can authenticat against a remote server.
If the server is running Active Directory (W2K, XP), check out google for this, it uses a combination of LDAP (Directory service) and Kerberos.
I believe you can connect to AD with nsswitch LDAP and libpam-krb5.

---

### Post by szz on 2005-01-19
[QUOTE=nocturn]I am not sure, but I think it can authenticat against a remote server.
If the server is running Active Directory (W2K, XP), check out google for this, it uses a combination of LDAP (Directory service) and Kerberos.
I believe you can connect to AD with nsswitch LDAP and libpam-krb5.[/QUOTE]
 Sorry, it's not clear. What should I write into the /etc/pam.d/??which_file?? instead of this:

auth    sufficient      /lib/security/pam_smb_auth.so use_first_pass nolocal

?

Thank you:
SzZ

---

### Post by nocturn on 2005-01-19
[QUOTE=szz]Sorry, it's not clear. What should I write into the /etc/pam.d/??which_file?? instead of this:

auth    sufficient      /lib/security/pam_smb_auth.so use_first_pass nolocal

?

Thank you:
SzZ[/QUOTE]

It depends on what authentication your windows server uses (NTLM, Kerberos).

---

### Post by szz on 2005-01-20
[QUOTE=nocturn]It depends on what authentication your windows server uses (NTLM, Kerberos).[/QUOTE]

Fortunately, it's not a windows server. 
Its a Fedora linux, running smb authentication, this way:

>cat system-auth
#%PAM-1.0
auth        required      /lib/security/$ISA/pam_env.so
auth        sufficient    /lib/security/$ISA/pam_unix.so likeauth nullok
auth        sufficient    /lib/security/$ISA/pam_smb_auth.so use_first_pass nolocal
auth        required      /lib/security/$ISA/pam_deny.so
 
account     sufficient    /lib/security/$ISA/pam_succeed_if.so uid < 100
account     required      /lib/security/$ISA/pam_unix.so
 
password    requisite     /lib/security/$ISA/pam_cracklib.so retry=3
password    sufficient    /lib/security/$ISA/pam_unix.so nullok use_authtok md5 shadow
password    required      /lib/security/$ISA/pam_deny.so
 
session     required      /lib/security/$ISA/pam_limits.so
session     required      /lib/security/$ISA/pam_unix.so

---

### Post by nocturn on 2005-01-20
[QUOTE=szz]Fortunately, it's not a windows server. 
Its a Fedora linux, running smb authentication, this way:

>cat system-auth
#%PAM-1.0
auth        required      /lib/security/$ISA/pam_env.so
auth        sufficient    /lib/security/$ISA/pam_unix.so likeauth nullok
auth        sufficient    /lib/security/$ISA/pam_smb_auth.so use_first_pass nolocal
auth        required      /lib/security/$ISA/pam_deny.so
 
account     sufficient    /lib/security/$ISA/pam_succeed_if.so uid < 100
account     required      /lib/security/$ISA/pam_unix.so
 
password    requisite     /lib/security/$ISA/pam_cracklib.so retry=3
password    sufficient    /lib/security/$ISA/pam_unix.so nullok use_authtok md5 shadow
password    required      /lib/security/$ISA/pam_deny.so
 
session     required      /lib/security/$ISA/pam_limits.so
session     required      /lib/security/$ISA/pam_unix.so[/QUOTE]


Just mimic it on Ubuntu (maybe pam_smb has a config file you need to edit).
Replace $ISA with a full path though.

---

### Post by szz on 2005-01-21
It's not so simple just to mimic it, because there is no pam_smb_auth.so in Ubuntu (only pam_smbpass.so, but it is used to other purpose: authentication on a local computer).

---

### Post by szz on 2005-02-06
This problem is still not solved. Can you help me?

---

### Post by nocturn on 2005-02-07
[QUOTE=szz]This problem is still not solved. Can you help me?[/QUOTE]

Can you check what package on the server owns  pam_smb_auth.so.

I believe the right command is:
rpm -qf /pathtopam_smb_auth.so

---

### Post by nocturn on 2005-02-07
I  googled for this, the package on Debian you require is:
libpam-smb

[https://www.redhat.com/archives/pam-list/2003-January/msg00048.html](https://www.redhat.com/archives/pam-list/2003-January/msg00048.html)
Solution (Debian)

   apt-get install libpam-smb, then edit /etc/pam_smb.conf as in Solaris
   step 9. Edit any config files in /etc/pam.d you want to be SMB-aware,
   changing
  auth  required    pam_unix.so

   to
  auth  sufficient  pam_unix.so
  auth  required    pam_smb_auth.so

---

### Post by atom on 2005-04-29
[QUOTE=nocturn]apt-get install libpam-smb[/QUOTE]
this will not work in ubuntu. debian's last package for libpam-smb is in stable and is using v. 1.1.6. i did not try that package personally, but it may work.

i got it working by downloading and compiling [pam_smb]("http://www.csn.ul.ie/~airlied/pam_smb/") by hand. you will need libpam0g-dev and build-essential installed to compiled it. just a simple
```
./configure --prefix=/usr
make
make install
```that set it up somewhat. 

/etc/pam_smb.conf gets:   DOMAIN,PDC,BDC

mine
```
BOKONET,ENTI,ENTI
```
/etc/pam.d/common-auth needs to look like this:
```
auth       sufficient   pam_unix.so nullok_secure
auth       sufficient   pam_smb_auth.so use_first_pass nolocal
```

you **need** to run the daemon /usr/sbin/pamsmbd in order for the module to work.

more information, and generic distribution info in the **[INSTALL]("http://cvs.sourceforge.net/cgi-bin/viewcvs.cgi/pamsmb/pam_smb/INSTALL?rev=HEAD&content-type=text/vnd.viewcvs-markup")** file

---

