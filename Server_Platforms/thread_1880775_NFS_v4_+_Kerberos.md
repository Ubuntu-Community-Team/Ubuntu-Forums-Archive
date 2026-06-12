---
title: "NFS v4 + Kerberos"
date: 2011-11-14
forum: Server Platforms
---

### Post by oliwei on 2011-11-14
Hi All,

I'm currently trying to get Ubuntu 10.04 working with NFSv4 kerberos. The Ubuntu box is joined to an AD 2008 R2 domain using winbind. I have followed various guides and forum posts to get it working but I'm always stuck with an error when mounting the nfs v4 share. BTW. NFS Server is a NetApp SAN. Mounting NFSv4 without kerberos works fine.

I have successfully created the nfs upn on the 2008 R2 server using:

```
net ads keytab add nfs -U Administrator
```on the Server I can lookup the UPNsfine:

```
Registered ServicePrincipalNames for CN=ubuntutest,OU=New Computers,DC=a,DC=space,DC=corp:
        NFS/ubuntutest.a.space.corp
        NFS/ubuntutest
        HOST/ubuntutest.a.space.corp
        HOST/UBUNTUTEST

```after that I run kinit on the Ubuntu client:

```
root@ubuntutest:~# kinit -k nfs/ubuntutest.a.space.corp@A.SPACE.CORP
root@ubuntutest:~# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: nfs/ubuntutest.a.space.corp@A.SPACE.CORP

Valid starting     Expires            Service principal
11/14/11 13:24:23  11/14/11 20:04:23  krbtgt/A.SPACE.CORP@A.SPACE.CORP
```but the mounting fails:

```
mount -vvvv -t nfs4 -o sec=krb5,rw,acl ds-san-02:/vol/nfsv4test_krb5 /nfsv4test_krb5
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "ds-san-02:/vol/nfsv4test_krb5"
mount: node:  "/nfsv4test_krb5"
mount: types: "nfs4"
mount: opts:  "sec=krb5,rw,acl"
mount: external mount: argv[0] = "/sbin/mount.nfs4"
mount: external mount: argv[1] = "ds-san-02:/vol/nfsv4test_krb5"
mount: external mount: argv[2] = "/nfsv4test_krb5"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,sec=krb5,acl"
mount.nfs4: timeout set for Mon Nov 14 13:26:50 2011
mount.nfs4: text-based options: 'sec=krb5,acl,clientaddr=172.28.19.55,addr=172.28.4.101'
mount.nfs4: mount(2): Permission denied
mount.nfs4: access denied by server while mounting ds-san-02:/vol/nfsv4test_krb5

```Looking at the logs just gives me this error:

```
Nov 14 13:25:32 ubuntutest winbindd[920]: [2011/11/14 13:25:32,  0] libads/sasl.c:819(ads_sasl_spnego_bind)
Nov 14 13:25:32 ubuntutest winbindd[920]:   kinit succeeded but ads_sasl_spnego_krb5_bind failed: Unspecified GSS failure.  Minor code may provide more information : Cannot find KDC for requested realm
```Googling for the error doesn't show anything helpful.

Any hints are appreciated.

---

### Post by oliwei on 2011-11-14
Ok, now I have a different error:

rpcsec_gss: gss_init_sec_context: (major) Unspecified GSS failure.  Minor code may provide more information - (minor) Server not found in Kerberos database

I will have to check more logfiles to see what hostname is send to the KDC.

---

