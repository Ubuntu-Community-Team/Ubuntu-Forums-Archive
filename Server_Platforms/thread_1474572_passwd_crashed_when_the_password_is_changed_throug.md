---
title: "passwd crashed when the password is changed through pam_ldap"
date: 2010-05-06
forum: Server Platforms
---

### Post by minicon on 2010-05-06
I have ubuntu 8.04 LTS, login and change password via LDAP .

When I trying change password via passwd utility password changed in LDAP, but passwd craches.

```
# passwd
Enter login(LDAP) password: 
New password: 
Re-enter new password: 
*** glibc detected *** passwd: free(): invalid pointer: 0x00007f1c056ee600 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f1c05d9408a]
/lib/libc.so.6(cfree+0x8c)[0x7f1c05d97c1c]
/usr/lib/libldap_r-2.4.so.2(ldap_return_request+0x51)[0x7f1c054ccbb1]
/usr/lib/libldap_r-2.4.so.2[0x7f1c054bc5d5]
/usr/lib/libldap_r-2.4.so.2(ldap_result+0x741)[0x7f1c054bd801]
/usr/lib/libldap_r-2.4.so.2(ldap_extended_operation_s+0xfc)[0x7f1c054c09cc]
/lib/security/pam_ldap.so(pam_sm_chauthtok+0xc47)[0x7f1c02e42b87]
/lib/libpam.so.0[0x7f1c064a3961]
/lib/libpam.so.0(pam_chauthtok+0x60)[0x7f1c064a6b60]
passwd[0x403bff]
passwd[0x4035ac]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7f1c05d3e1c4]
passwd(misc_conv+0x219)[0x4024c9]
======= Memory map: ========
00400000-00408000 r-xp 00000000 08:01 90694                              /usr/bin/passwd
00607000-00609000 rw-p 00007000 08:01 90694                              /usr/bin/passwd
00609000-0068f000 rw-p 00609000 00:00 0                                  [heap]
7f1bfc000000-7f1bfc021000 rw-p 7f1bfc000000 00:00 0 
7f1bfc021000-7f1c00000000 ---p 7f1bfc021000 00:00 0 
7f1c02007000-7f1c02014000 r-xp 00000000 08:01 437378                     /lib/libgcc_s.so.1
7f1c02014000-7f1c02214000 ---p 0000d000 08:01 437378                     /lib/libgcc_s.so.1
7f1c02214000-7f1c02215000 rw-p 0000d000 08:01 437378                     /lib/libgcc_s.so.1
7f1c02215000-7f1c02217000 r-xp 00000000 08:01 437427                     /lib/security/pam_umask.so
7f1c02217000-7f1c02416000 ---p 00002000 08:01 437427                     /lib/security/pam_umask.so
7f1c02416000-7f1c02417000 rw-p 00001000 08:01 437427                     /lib/security/pam_umask.so
7f1c02417000-7f1c0241a000 r-xp 00000000 08:01 437407                     /lib/security/pam_limits.so
7f1c0241a000-7f1c02619000 ---p 00003000 08:01 437407                     /lib/security/pam_limits.so
7f1c02619000-7f1c0261a000 rw-p 00002000 08:01 437407                     /lib/security/pam_limits.so
7f1c0261a000-7f1c0261c000 r-xp 00000000 08:01 437412                     /lib/security/pam_mkhomedir.so
7f1c0261c000-7f1c0281b000 ---p 00002000 08:01 437412                     /lib/security/pam_mkhomedir.so
7f1c0281b000-7f1c0281e000 rw-p 00001000 08:01 437412                     /lib/security/pam_mkhomedir.so
7f1c0281e000-7f1c02821000 r-xp 00000000 08:01 434435                     /lib/security/pam_env.so
7f1c02821000-7f1c02a20000 ---p 00003000 08:01 434435                     /lib/security/pam_env.so
7f1c02a20000-7f1c02a21000 rw-p 00002000 08:01 434435                     /lib/security/pam_env.so
7f1c02a21000-7f1c02a23000 r-xp 00000000 08:01 437408                     /lib/security/pam_listfile.so
7f1c02a23000-7f1c02c23000 ---p 00002000 08:01 437408                     /lib/security/pam_listfile.so
7f1c02c23000-7f1c02c24000 rw-p 00002000 08:01 437408                     /lib/security/pam_listfile.so
7f1c02c24000-7f1c02c30000 r-xp 00000000 08:01 437428                     /lib/security/pam_unix.so
7f1c02c30000-7f1c02e2f000 ---p 0000c000 08:01 437428                     /lib/security/pam_unix.so
7f1c02e2f000-7f1c02e30000 rw-p 0000b000 08:01 437428                     /lib/security/pam_unix.so
7f1c02e30000-7f1c02e3c000 rw-p 7f1c02e30000 00:00 0 
7f1c02e3c000-7f1c02e46000 r-xp 00000000 08:01 434460                     /lib/security/pam_ldap.so
7f1c02e46000-7f1c03045000 ---p 0000a000 08:01 434460                     /lib/security/pam_ldap.so
7f1c03045000-7f1c03046000 rw-p 00009000 08:01 434460                     /lib/security/pam_ldap.so
7f1c03046000-7f1c0304a000 r-xp 00000000 08:01 437390                     /lib/libnss_dns-2.7.so
7f1c0304a000-7f1c0324a000 ---p 00004000 08:01 437390                     /lib/libnss_dns-2.7.so
7f1c0324a000-7f1c0324c000 rw-p 00004000 08:01 437390                     /lib/libnss_dns-2.7.so
7f1c0324c000-7f1c0324f000 r-xp 00000000 08:01 434421                     /lib/libgpg-error.so.0.3.0
7f1c0324f000-7f1c0344e000 ---p 00003000 08:01 434421                     /lib/libgpg-error.so.0.3.0
7f1c0344e000-7f1c0344f000 rw-p 00002000 08:01 434421                     /lib/libgpg-error.so.0.3.0
7f1c0344f000-7f1c0349b000 r-xp 00000000 08:01 434420                     /lib/libgcrypt.so.11.2.3
7f1c0349b000-7f1c0369a000 ---p 0004c000 08:01 434420                     /lib/libgcrypt.so.11.2.3
7f1c0369a000-7f1c0369d000 rw-p 0004b000 08:01 434420                     /lib/libgcrypt.so.11.2.3
7f1c0369d000-7f1c036b3000 r-xp 00000000 08:01 90992                      /usr/lib/libz.so.1.2.3.3
7f1c036b3000-7f1c038b3000 ---p 00016000 08:01 90992                      /usr/lib/libz.so.1.2.3.3
7f1c038b3000-7f1c038b4000 rw-p 00016000 08:01 90992                      /usr/lib/libz.so.1.2.3.3
7f1c038b4000-7f1c038c4000 r-xp 00000000 08:01 90991                      /usr/lib/libtasn1.so.3.0.12
7f1c038c4000-7f1c03ac3000 ---p 00010000 08:01 90991                      /usr/lib/libtasn1.so.3.0.12
7f1c03ac3000-7f1c03ac4000 rw-p 0000f000 08:01 90991                      /usr/lib/libtasn1.so.3.0.12
7f1c03ac4000-7f1c03ac6000 r-xp 00000000 08:01 434424                     /lib/libkeyutils-1.2.so
7f1c03ac6000-7f1c03cc5000 ---p 00002000 08:01 434424                     /lib/libkeyutils-1.2.so
7f1c03cc5000-7f1c03cc6000 rw-p 00001000 08:01 434424                     /lib/libkeyutils-1.2.so
7f1c03cc6000-7f1c03ccd000 r-xp 00000000 08:01 409626                     /usr/lib/libkrb5support.so.0.1
7f1c03ccd000-7f1c03ecc000 ---p 00007000 08:01 409626                     /usr/lib/libkrb5support.so.0.1
7f1c03ecc000-7f1c03ecd000 rw-p 00006000 08:01 409626                     /usr/lib/libkrb5support.so.0.1
7f1c03ecd000-7f1c03ef0000 r-xp 00000000 08:01 409623                     /usr/lib/libk5crypto.so.3.1
7f1c03ef0000-7f1c040ef000 ---p 00023000 08:01 409623                     /usr/lib/libk5crypto.so.3.1
7f1c040ef000-7f1c040f1000 rw-p 00022000 08:01 409623                     /usr/lib/libk5crypto.so.3.1
7f1c040f1000-7f1c0416c000 r-xp 00000000 08:01 409606                     /usr/lib/libgnutls.so.13.9.1
7f1c0416c000-7f1c0436c000 ---p 0007b000 08:01 409606                     /usr/lib/libgnutls.so.13.9.1
7f1c0436c000-7f1c04376000 rw-p 0007b000 08:01 409606                     /usr/lib/libgnutls.so.13.9.1
7f1c04376000-7f1c0438c000 r-xp 00000000 08:01 437396                     /lib/libpthread-2.7.so
7f1c0438c000-7f1c0458c000 ---p 00016000 08:01 437396                     /lib/libpthread-2.7.so
7f1c0458c000-7f1c0458e000 rw-p 00016000 08:01 437396                     /lib/libpthread-2.7.so
7f1c0458e000-7f1c04592000 rw-p 7f1c0458e000 00:00 0 
7f1c04592000-7f1c045a4000 r-xp 00000000 08:01 437397                     /lib/libresolv-2.7.so
7f1c045a4000-7f1c047a4000 ---p 00012000 08:01 437397                     /lib/libresolv-2.7.so
7f1c047a4000-7f1c047a6000 rw-p 00012000 08:01 437397                     /lib/libresolv-2.7.so
7f1c047a6000-7f1c047a8000 rw-p 7f1c047a6000 00:00 0 
7f1c047a8000-7f1c047be000 r-xp 00000000 08:01 437388                     /lib/libnsl-2.7.so
7f1c047be000-7f1c049bd000 ---p 00016000 08:01 437388                     /lib/libnsl-2.7.so
7f1c049bd000-7f1c049bf000 rw-p 00015000 08:01 437388                     /lib/libnsl-2.7.so
7f1c049bf000-7f1c049c1000 rw-p 7f1c049bf000 00:00 0 
7f1c049c1000-7f1c049ea000 r-xp 00000000 08:01 409622                     /usr/lib/libgssapi_krb5.so.2.2
7f1c049ea000-7f1c04bea000 ---p 00029000 08:01 409622                     /usr/lib/libgssapi_krb5.so.2.2
7f1c04bea000-7f1c04bec000 rw-p 00029000 08:01 409622                     /usr/lib/libgssapi_krb5.so.2.2
7f1c04bec000-7f1c04bee000 r-xp 00000000 08:01 434411                     /lib/libcom_err.so.2.1
7f1c04bee000-7f1c04ded000 ---p 00002000 08:01 434411                     /lib/libcom_err.so.2.1
7f1c04ded000-7f1c04dee000 rw-p 00001000 08:01 434411                     /lib/libcom_err.so.2.1
7f1c04dee000-7f1c04e82000 r-xp 00000000 08:01 409625                     /usr/lib/libkrb5.so.3.3
7f1c04e82000-7f1c05082000 ---p 00094000 08:01 409625                     /usr/lib/libkrb5.so.3.3
7f1c05082000-7f1c05085000 rw-p 00094000 08:01 409625                     /usr/lib/libkrb5.so.3.3
7f1c05085000-7f1c0509d000 r-xp 00000000 08:01 409610                     /usr/lib/libsasl2.so.2.0.22
7f1c0509d000-7f1c0529d000 ---p 00018000 08:01 409610                     /usr/lib/libsasl2.so.2.0.22
7f1c0529d000-7f1c0529e000 rw-p 00018000 08:01 409610                     /usr/lib/libsasl2.so.2.0.22
7f1c0529e000-7f1c052ac000 r-xp 00000000 08:01 409614                     /usr/lib/liblber-2.4.so.2.0.5
7f1c052ac000-7f1c054ab000 ---p 0000e000 08:01 409614                     /usr/lib/liblber-2.4.so.2.0.5
7f1c054ab000-7f1c054ac000 rw-p 0000d000 08:01 409614                     /usr/lib/liblber-2.4.so.2.0.5
7f1c054ac000-7f1c054ed000 r-xp 00000000 08:01 90163                      /usr/lib/libldap_r-2.4.so.2.0.5
7f1c054ed000-7f1c056ed000 ---p 00041000 08:01 90163                      /usr/lib/libldap_r-2.4.so.2.0.5
7f1c056ed000-7f1c056ef000 rw-p 00041000 08:01 90163                      /usr/lib/libldap_r-2.4.so.2.0.5
7f1c056ef000-7f1c056f1000 rw-p 7f1c056ef000 00:00 0 
7f1c056f1000-7f1c05704000 r-xp 00000000 08:01 434413                     /lib/libnss_ldap-2.7.so
7f1c05704000-7f1c05903000 ---p 00013000 08:01 434413                     /lib/libnss_ldap-2.7.so
7f1c05903000-7f1c05905000 rw-p 00012000 08:01 434413                     /lib/libnss_ldap-2.7.so
7f1c05905000-7f1c05910000 rw-p 7f1c05905000 00:00 0 
7f1c05910000-7f1c0591a000 r-xp 00000000 08:01 437391                     /lib/libnss_files-2.7.so
7f1c0591a000-7f1c05b1a000 ---p 0000a000 08:01 437391                     /lib/libnss_files-2.7.so
7f1c05b1a000-7f1c05b1c000 rw-p 0000a000 08:01 437391                     /lib/libnss_files-2.7.so
7f1c05b1c000-7f1c05b1e000 r-xp 00000000 08:01 437385                     /lib/libdl-2.7.so
7f1c05b1e000-7f1c05d1e000 ---p 00002000 08:01 437385                     /lib/libdl-2.7.so
7f1c05d1e000-7f1c05d20000 rw-p 00002000 08:01 437385                     /lib/libdl-2.7.so
7f1c05d20000-7f1c05e78000 r-xp 00000000 08:01 437382                     /lib/libc-2.7.so
7f1c05e78000-7f1c06078000 ---p 00158000 08:01 437382                     /lib/libc-2.7.so
7f1c06078000-7f1c0607b000 r--p 00158000 08:01 437382                     /lib/libc-2.7.so
7f1c0607b000-7f1c0607d000 rw-p 0015b000 08:01 437382                     /lib/libc-2.7.so
7f1c0607d000-7f1c06082000 rw-p 7f1c0607d000 00:00 0 
7f1c06082000-7f1c0609b000 r-xp 00000000 08:01 434446                     /lib/libselinux.so.1
7f1c0609b000-7f1c0629b000 ---p 00019000 08:01 434446                     /lib/libselinux.so.1
7f1c0629b000-7f1c0629d000 rw-p 00019000 08:01 434446                     /lib/libselinux.so.1
7f1c0629d000-7f1c0629e000 rw-p 7f1c0629d000 00:00 0 
7f1c0629e000-7f1c062a1000 r-xp 00000000 08:01 434399                     /lib/libpam_misc.so.0.81.2
7f1c062a1000-7f1c064a0000 ---p 00003000 08:01 434399                     /lib/libpam_misc.so.0.81.2
7f1c064a0000-7f1c064a1000 rw-p 00002000 08:01 434399                     /lib/libpam_misc.so.0.81.2
7f1c064a1000-7f1c064ab000 r-xp 00000000 08:01 434227                     /lib/libpam.so.0.81.6
7f1c064ab000-7f1c066aa000 ---p 0000a000 08:01 434227                     /lib/libpam.so.0.81.6
7f1c066aa000-7f1c066ab000 rw-p 00009000 08:01 434227                     /lib/libpam.so.0.81.6
7f1c066ab000-7f1c066b4000 r-xp 00000000 08:01 437384                     /lib/libcrypt-2.7.so
7f1c066b4000-7f1c068b3000 ---p 00009000 08:01 437384                     /lib/libcrypt-2.7.so
7f1c068b3000-7f1c068b5000 rw-p 00008000 08:01 437384                     /lib/libcrypt-2.7.so
7f1c068b5000-7f1c068e3000 rw-p 7f1c068b5000 00:00 0 
7f1c068e3000-7f1c06900000 r-xp 00000000 08:01 437379                     /lib/ld-2.7.so
7f1c069c8000-7f1c06a07000 r--p 00000000 08:01 91363                      /usr/lib/locale/ru_RU.utf8/LC_CTYPE
7f1c06a07000-7f1c06a08000 r--p 00000000 08:01 91368                      /usr/lib/locale/ru_RU.utf8/LC_NUMERIC
7f1c06a08000-7f1c06a09000 r--p 00000000 08:01 91371                      /usr/lib/locale/ru_RU.utf8/LC_TIME
7f1c06a09000-7f1c06aea000 r--p 00000000 08:01 91362                      /usr/lib/locale/ru_RU.utf8/LC_COLLATE
7f1c06aea000-7f1c06aeb000 r--p 00000000 08:01 91366                      /usr/lib/locale/ru_RU.utf8/LC_MONETARY
7f1c06aeb000-7f1c06aec000 r--p 00000000 08:01 91372                      /usr/lib/locale/ru_RU.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7f1c06aec000-7f1c06aed000 r--p 00000000 08:01 91369                      /usr/lib/locale/ru_RU.utf8/LC_PAPER
7f1c06aed000-7f1c06aee000 r--p 00000000 08:01 91367                      /usr/lib/locale/ru_RU.utf8/LC_NAME
7f1c06aee000-7f1c06aef000 r--p 00000000 08:01 91361                      /usr/lib/locale/ru_RU.utf8/LC_ADDRESS
7f1c06aef000-7f1c06af6000 r--s 00000000 08:01 90408                      /usr/lib/gconv/gconv-modules.cache
7f1c06af6000-7f1c06afa000 rw-p 7f1c06af6000 00:00 0 
7f1c06afa000-7f1c06afb000 r--p 00000000 08:01 91370                      /usr/lib/locale/ru_RU.utf8/LC_TELEPHONE
7f1c06afb000-7f1c06afc000 r--p 00000000 08:01 91365                      /usr/lib/locale/ru_RU.utf8/LC_MEASUREMENT
7f1c06afc000-7f1c06afd000 r--p 00000000 08:01 91364                      /usr/lib/locale/ru_RU.utf8/LC_IDENTIFICATION
7f1c06afd000-7f1c06b00000 rw-p 7f1c06afd000 00:00 0 
7f1c06b00000-7f1c06b02000 rw-p 0001d000 08:01 437379                     /lib/ld-2.7.so
7fff0eaec000-7fff0eb01000 rw-p 7ffffffea000 00:00 0                      [stack]
7fff0ebfe000-7fff0ebff000 r-xp 7fff0ebfe000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

```My ldap.conf:

```
uri ldap://<ldap_server>
base o=<basedn>
ldap_version 3
scope sub
ssl start_tls
tls_cacertfile /etc/ssl/certs/ca.pem
tls_checkpeer yes
tls_cacertdir /etc/ssl/certs/
binddn uid=<binddn>
bindpw <bindpw>
bind_timelimit 10
timelimit 5
idle_timelimit 300
bind_policy hard_open
pam_lookup_policy yes
pam_password exop
nss_base_passwd o=<base>?sub
nss_base_shadow o=<base>?sub
nss_base_group o=<base>?sub
nss_reconnect_sleeptime 0
nss_reconnect_maxsleeptime 1
nss_reconnect_maxconntries 1
```My /etc/pam.d/common-password:

```
password        sufficient      pam_ldap.so
password        required        pam_unix.so nullok obscure sha512
```

---

