---
title: "Kerberized NFS"
date: 2012-02-13
forum: Server Platforms
---

### Post by oliwei on 2012-02-13
Hi All,
   
  I’m struggling since weeks to get samba winbind and a kerberized nfs mount running. We have a Netapp SAN exporting the nfs share with sec=krb5 and a Linux Client Ubuntu 10.04 Server trying to access the exported share. Accessing the share without krb5 (sec=sys) works fine. The linux machine is joined to an Windows 2008R2 domain and user/group lookups login via ssh etc. work fine.
   
  I have read many articles about using winbind to aquire the Kerberos tickets on login.
   
  What I have done so far is join the linux machine to our AD:
   
  ```
net ads join –U Administrator
```  After this my krb5.keytab file is filled with the following:
   
```
root@ubuntu100432:~# klist -kte
  Keytab name: WRFILE:/etc/krb5.keytab
  KVNO Timestamp         Principal
  ---- ----------------- --------------------------------------------------------
     2 02/13/12 09:34:59 host/ubuntu100432.a.space.corp@A.SPACE.CORP (DES cbc mode with CRC-32)
     2 02/13/12 09:34:59 host/ubuntu100432.a.space.corp@A.SPACE.CORP (DES cbc mode with RSA-MD5)
     2 02/13/12 09:34:59 host/ubuntu100432.a.space.corp@A.SPACE.CORP (ArcFour with HMAC/md5)
     2 02/13/12 09:34:59 host/ubuntu100432@A.SPACE.CORP (DES cbc mode with CRC-32)
     2 02/13/12 09:34:59 host/ubuntu100432@A.SPACE.CORP (DES cbc mode with RSA-MD5)
     2 02/13/12 09:34:59 host/ubuntu100432@A.SPACE.CORP (ArcFour with HMAC/md5)
     2 02/13/12 09:34:59 UBUNTU100432$@A.SPACE.CORP (DES cbc mode with CRC-32)
     2 02/13/12 09:34:59 UBUNTU100432$@A.SPACE.CORP (DES cbc mode with RSA-MD5)
     2 02/13/12 09:34:59 UBUNTU100432$@A.SPACE.CORP (ArcFour with HMAC/md5)

```  Then I add the nfs principal:
   
  ```
net ads keytab add nfs –U Administrator
```  This adds the princ to the keytab file:
   
    ```

 2 02/13/12 09:36:11 nfs/ubuntu100432.a.space.corp@A.SPACE.CORP (DES cbc mode with CRC-32)
     2 02/13/12 09:36:11 nfs/ubuntu100432.a.space.corp@A.SPACE.CORP (DES cbc mode with RSA-MD5)
     2 02/13/12 09:36:11 nfs/ubuntu100432.a.space.corp@A.SPACE.CORP (ArcFour with HMAC/md5)
     2 02/13/12 09:36:11 nfs/ubuntu100432@A.SPACE.CORP (DES cbc mode with CRC-32)
     2 02/13/12 09:36:11 nfs/ubuntu100432@A.SPACE.CORP (DES cbc mode with RSA-MD5)
     2 02/13/12 09:36:11 nfs/ubuntu100432@A.SPACE.CORP (ArcFour with HMAC/md5)

```  I restart the portmap service (this restarts statd idmapd and gssd)
   
  ```
service portmap restart
```  Now when I try to mount the share I always get an access denied:
   
  Looking at /var/log/daemon.log reveals:
   
```
handling krb5 upcall
  Full hostname for 'ds-san-02.a.space.corp' is 'ds-san-02.a.space.corp'
  Full hostname for 'ubuntu100432.a.space.corp' is 'ubuntu100432.a.space.corp'
  Key table entry not found while getting keytab entry for 'root/ubuntu100432.a.space.corp@A.SPACE.CORP'
  Success getting keytab entry for 'nfs/ubuntu100432.a.space.corp@A.SPACE.CORP'
  WARNING: Client not found in Kerberos database while getting initial ticket for principal 'nfs/ubuntu100432.a.space.corp@A.SPACE.CORP' using keytab 'WRFILE:/etc/krb5.keytab'
  ERROR: No credentials found for connection to server ds-san-02.a.space.corp
  doing error downcall
  destroying client clnt13
  destroying client clnt12

```  I checked the host in AD with setspn –L and this lists the following:
   
```
Registered ServicePrincipalNames for CN=ubuntu100432
  ace,DC=corp:
      NFS/ubuntu100432.a.space.corp
      NFS/ubuntu100432
      HOST/ubuntu100432.a.space.corp
      HOST/UBUNTU100432

```  So there is no principal 'nfs/ubuntu100432.a.space.corp@A.SPACE.CORP'.
   
  Is there something special about Windows 2008 R2?
   
  Regards,
  Oliver

---

### Post by oliwei on 2012-02-14
Ok, I'm making some progress... I guess.

I have now set the upn (userprincipalname) in ad while joining the domain.

net ads join createupn="nfs/ubuntu100432.a.space.corp@A.SPACE.CORP" -U Administrator

This creates the correct upn that gssd is looking for. I have read several howtos and all come to the conclusion that starting with Windows 2008 the kerberos realm has to be omitted in the upn. By doing this I end up where I started gssd can't find the nfs/... principal in the kerberos database (in AD).

When trying to mount a nfs4 export using sec=krb5 I get a segfault:

```
beginning poll
handling krb5 upcall
Full hostname for 'ds-san-02.a.space.corp' is 'ds-san-02.a.space.corp'
Full hostname for 'ubuntu100432.a.space.corp' is 'ubuntu100432.a.space.corp'
Key table entry not found while getting keytab entry for 'root/ubuntu100432.a.space.corp@A.SPACE.CORP'
Success getting keytab entry for 'nfs/ubuntu100432.a.space.corp@A.SPACE.CORP'
Successfully obtained machine credentials for principal 'nfs/ubuntu100432.a.space.corp@A.SPACE.CORP' stored in ccache 'FILE:/tmp/krb5cc_machine_A.SPACE.CORP'
INFO: Credentials in CC 'FILE:/tmp/krb5cc_machine_A.SPACE.CORP' are good until 1329248533
using FILE:/tmp/krb5cc_machine_A.SPACE.CORP as credentials cache for machine creds
using environment variable to select krb5 ccache FILE:/tmp/krb5cc_machine_A.SPACE.CORP
creating context using fsuid 0 (save_uid 0)
creating tcp client for server ds-san-02.a.space.corp
DEBUG: port already set to 2049
creating context with server nfs@ds-san-02.a.space.corp
*** glibc detected *** rpc.gssd: corrupted double-linked list: 0x09d94c10 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b591)[0xb30591]
/lib/tls/i686/cmov/libc.so.6(+0x6b9ea)[0xb309ea]
/lib/tls/i686/cmov/libc.so.6(+0x6dafd)[0xb32afd]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0xab)[0xb3470b]
/usr/lib/libkrb5.so.3(+0x4dc71)[0x619c71]
/usr/lib/libgssapi_krb5.so.2(+0x19933)[0xe83933]
/usr/lib/libgssapi_krb5.so.2(+0x21868)[0xe8b868]
/usr/lib/libgssapi_krb5.so.2(gss_release_cred+0x89)[0xe7a8e9]
/usr/lib/libgssglue.so.1(gss_release_cred+0xbc)[0x3d8d3c]
rpc.gssd[0x804ba5a]
rpc.gssd[0x804ce35]
rpc.gssd[0x804b640]
rpc.gssd[0x804b3d9]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xadbbd6]
rpc.gssd[0x804a671]
======= Memory map: ========
00110000-00120000 r-xp 00000000 08:01 131539     /lib/tls/i686/cmov/libresolv-2.11.1.so
00120000-00121000 r--p 00010000 08:01 131539     /lib/tls/i686/cmov/libresolv-2.11.1.so
00121000-00122000 rw-p 00011000 08:01 131539     /lib/tls/i686/cmov/libresolv-2.11.1.so
00122000-00124000 rw-p 00000000 00:00 0
00124000-0012e000 r-xp 00000000 08:01 131533     /lib/tls/i686/cmov/libnss_files-2.11.1.so
0012e000-0012f000 r--p 00009000 08:01 131533     /lib/tls/i686/cmov/libnss_files-2.11.1.so
0012f000-00130000 rw-p 0000a000 08:01 131533     /lib/tls/i686/cmov/libnss_files-2.11.1.so
0038c000-003ae000 r-xp 00000000 08:01 267512     /usr/lib/libk5crypto.so.3.1
003ae000-003af000 r--p 00021000 08:01 267512     /usr/lib/libk5crypto.so.3.1
003af000-003b0000 rw-p 00022000 08:01 267512     /usr/lib/libk5crypto.so.3.1
003d4000-003db000 r-xp 00000000 08:01 301141     /usr/lib/libgssglue.so.1.0.0
003db000-003dc000 r--p 00006000 08:01 301141     /usr/lib/libgssglue.so.1.0.0
003dc000-003dd000 rw-p 00007000 08:01 301141     /usr/lib/libgssglue.so.1.0.0
0041e000-0041f000 r-xp 00000000 00:00 0          [vdso]
004bf000-004c1000 r-xp 00000000 08:01 130947     /lib/libcom_err.so.2.1
004c1000-004c2000 r--p 00001000 08:01 130947     /lib/libcom_err.so.2.1
004c2000-004c3000 rw-p 00002000 08:01 130947     /lib/libcom_err.so.2.1
00505000-0050b000 r-xp 00000000 08:01 268148     /usr/lib/libkrb5support.so.0.1
0050b000-0050c000 r--p 00005000 08:01 268148     /usr/lib/libkrb5support.so.0.1
0050c000-0050d000 rw-p 00006000 08:01 268148     /usr/lib/libkrb5support.so.0.1
00555000-0056a000 r-xp 00000000 08:01 131538     /lib/tls/i686/cmov/libpthread-2.11.1.so
0056a000-0056b000 r--p 00014000 08:01 131538     /lib/tls/i686/cmov/libpthread-2.11.1.so
0056b000-0056c000 rw-p 00015000 08:01 131538     /lib/tls/i686/cmov/libpthread-2.11.1.so
0056c000-0056e000 rw-p 00000000 00:00 0
00587000-0058b000 r-xp 00000000 08:01 131532     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
0058b000-0058c000 r--p 00004000 08:01 131532     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
0058c000-0058d000 rw-p 00005000 08:01 131532     /lib/tls/i686/cmov/libnss_dns-2.11.1.so
005cc000-00676000 r-xp 00000000 08:01 268128     /usr/lib/libkrb5.so.3.3
00676000-00677000 ---p 000aa000 08:01 268128     /usr/lib/libkrb5.so.3.3
00677000-0067c000 r--p 000aa000 08:01 268128     /usr/lib/libkrb5.so.3.3
0067c000-0067d000 rw-p 000af000 08:01 268128     /usr/lib/libkrb5.so.3.3
006a8000-006aa000 r-xp 00000000 08:01 131737     /lib/libkeyutils-1.2.so
006aa000-006ab000 r--p 00001000 08:01 131737     /lib/libkeyutils-1.2.so
006ab000-006ac000 rw-p 00002000 08:01 131737     /lib/libkeyutils-1.2.so
00712000-0071f000 r-xp 00000000 08:01 301153     /usr/lib/librpcsecgss.so.3.0.0
0071f000-00720000 r--p 0000c000 08:01 301153     /usr/lib/librpcsecgss.so.3.0.0
00720000-00721000 rw-p 0000d000 08:01 301153     /usr/lib/librpcsecgss.so.3.0.0
0094d000-0094f000 r-xp 00000000 08:01 131527     /lib/tls/i686/cmov/libdl-2.11.1.so
0094f000-00950000 r--p 00001000 08:01 131527     /lib/tls/i686/cmov/libdl-2.11.1.so
00950000-00951000 rw-p 00002000 08:01 131527     /lib/tls/i686/cmov/libdl-2.11.1.so
00a9b000-00ab6000 r-xp 00000000 08:01 131252     /lib/ld-2.11.1.so
00ab6000-00ab7000 r--p 0001a000 08:01 131252     /lib/ld-2.11.1.so
00ab7000-00ab8000 rw-p 0001b000 08:01 131252     /lib/ld-2.11.1.so
00ac5000-00c18000 r-xp 00000000 08:01 131524     /lib/tls/i686/cmov/libc-2.11.1.so
00c18000-00c19000 ---p 00153000 08:01 131524     /lib/tls/i686/cmov/libc-2.11.1.so
00c19000-00c1b000 r--p 00153000 08:01 131524     /lib/tls/i686/cmov/libc-2.11.1.so
00c1b000-00c1c000 rw-p 00155000 08:01 131524     /lib/tls/i686/cmov/libc-2.11.1.so
00c1c000-00c1f000 rw-p 00000000 00:00 0
00ccb000-00ce8000 r-xp 00000000 08:01 131007     /lib/libgcc_s.so.1
00ce8000-00ce9000 r--p 0001c000 08:01 131007     /lib/libgcc_s.so.1
00ce9000-00cea000 rw-p 0001d000 08:01 131007     /lib/libgcc_s.so.1
00e6a000-00e97000 r-xp 00000000 08:01 268110     /usr/lib/libgssapi_krb5.so.2.2
00e97000-00e98000 r--p 0002d000 08:01 268110     /usr/lib/libgssapi_krb5.so.2.2
00e98000-00e99000 rw-p 0002e000 08:01 268110     /usr/lib/libgssapi_krb5.so.2.2
08048000-08053000 r-xp 00000000 08:01 301180     /usr/sbin/rpc.gssd
08053000-08054000 r--p 0000a000 08:01 301180     /usr/sbin/rpc.gssd
08054000-08059000 rw-p 0000b000 08:01 301180     /usr/sbin/rpc.gssd
09d91000-09db2000 rw-p 00000000 00:00 0          [heap]
b7600000-b7621000 rw-p 00000000 00:00 0
b7621000-b7700000 ---p 00000000 00:00 0
b77d0000-b77d4000 rw-p 00000000 00:00 0
b77d9000-b77db000 rw-p 00000000 00:00 0
bffd8000-bffed000 rw-p 00000000 00:00 0          [stack]
Aborted

```

Is this a bug in gssd?

---

### Post by oliwei on 2012-02-14
I have now redone the ad join and now I get the following error. I can't find anyhting helpful on the net. :(

rpcsec_gss: gss_init_sec_context: (major) Invalid token was supplied - (minor) Unknown error

---

### Post by oliwei on 2012-02-15
Dear All,

I finally have it working. The holy grail. :)

I had to change my /etc/krb5.conf. I added/changed the following 3 lines.

```
default_tgs_enctypes = des-cbc-crc aes256-cts-hmac-sha1-96 arcfour-hmac
default_tkt_enctypes = des-cbc-crc aes256-cts-hmac-sha1-96 arcfour-hmac
allow_weak_crypto = 1
```

I rejoined the machine to the domain:

```
net ads join createupn=nfs/ubuntu100432.a.space.corp -U Administrator
```

created the nfs service principal (I'm not 100% sure if it is any longer needed since rpc.gssd checks for root and host principal)

```
net ads keytab add nfs -U Administrator
```

finally mount the nfs export:

mount -t nfs4 -o sec=krb5 ds-san-02:/vol/nfsv4test_krb5 /mnt/nfsv4test_krb5

I will write a complete howto soon.

---

### Post by nanog on 2012-03-11
please write up your how to. i've been meaning to do this on my nfs shares. i've just been lazy since they are behind a firewall and restricted to specific ips and users.

---

### Post by oliwei on 2012-06-25
Hi,

today I have some time to test the setup again and probably write a howto. Currently I'm stuck on getting Ubuntu 10.04 to work with NFSv4 krb5 again.

Regards,
Oli

---

### Post by oliwei on 2012-06-25
Hi,

okay I have it working under Ubuntu 12.04 using winbind and a 2008 R2 Domain.

Benefits of this setup:

- no NFS 16 groups limit 
- higher security, without a valid TGT exports can't be accessed***

*** This setup doesn't prevent a root user to su. If a user is already logged in on a system a root user can still su to that particular user and steal his kerberos cache ***

First install winbind:

```
apt-get install winbind
```edit /etc/samba/smb.conf:

```

[global]
        netbios name = ubuntu1204x8664
        realm = LINUX.COM
        workgroup = LINUX
        security = ADS
        encrypt passwords = yes
        password server = *
        idmap config * : backend = tdb
        idmap config * : range = 1-50
        idmap config A : backend = ad
        idmap config A : schema_mode = rfc2307
        idmap config A : range = 51-99999999
        winbind nss info = rfc2307
        winbind enum users = no
        winbind enum groups = no
        winbind offline logon = yes
        preferred master = no
        winbind nested groups = Yes
        winbind use default domain = Yes
        max log size = 50
        log file = /var/log/samba/log.%m
        log level = 3
        allow trusted domains = No
        client use spnego = Yes
        kerberos method = secrets and keytab
        dedicated keytab file = /etc/krb5.keytab
        winbind refresh tickets = true
        name resolve order = lmhosts host

```edit /etc/krb5.conf:

```

[libdefaults]
        ticket_lifetime = 24000
        default_realm = LINUX.COM
        dns_lookup_realm = false
        dns_lookup_kdc = false
        default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_keytab_name = FILE:/etc/krb5.keytab

[realms]
        LINUX.COM = {
        kdc = dc1.linux.com:88
        kdc = dc2.linux.com:88
        admin_server = dc1.linux.com:749
        admin_server = dc2.linux.com:749
        kpasswd_server = dc1.linux.com:464
        kpasswd_server = dc2.linux.com:464
        kpasswd_protocol = SET_CHANGE
        default_domain = linux.com
        }

[domain_realm]
        *.linux.com = LINUX.COM
        .linux.com = LINUX.COM
        linux.com = LINUX.COM

[logging]
        default = FILE:/var/krb5/kdc.log
        kdc = FILE:/var/krb5/kdc.log

[appdefaults]

```to automatically request a kerberos ticket on user login, edit /etc/security/pam_winbind.conf:

```
#
# pam_winbind configuration file
#
# /etc/security/pam_winbind.conf
#

[global]

# turn on debugging
;debug = no

# request a cached login if possible
# (needs "winbind offline logon = yes" in smb.conf)
cached_login = yes

# authenticate using kerberos
krb5_auth = yes

# when using kerberos, request a "FILE" krb5 credential cache type
# (leave empty to just do krb5 authentication but not have a ticket
# afterwards)
krb5_ccache_type = FILE

# make successful authentication dependend on membership of one SID
# (can also take a name)
;require_membership_of =

```Now join the machine to the domain:

```
net ads join createupn=nfs/ubuntu1204x8664.a.space.corp -U Administrator
```Check if the machine is successfully joined to the domain and that you can lookup users:

```
root@ubuntu1204x8664:~# wbinfo -t
checking the trust secret for domain LINUX via RPC calls succeeded

``````
root@ubuntu1204x8664:~# id someuser
uid=10000(someuser) gid=10000(domain users) groups=10000(domain users)

Modify PAM to use winbind:

[CODE]/usr/sbin/pam-auth-update winbind
```

Login as the user and check for valid TGT:

```
someuser@ubuntu1204x8664:/$ klist
Ticket cache: FILE:/tmp/krb5cc_10000_oe3133
Default principal: someuser@LINUX.COM

Valid starting     Expires            Service principal
25/06/12 16:53:05  25/06/12 23:33:05  krbtgt/LINUX.COM@LINUX.COM

```Create a nfs service principal:

```
net ads keytab add nfs -U Administrator
```Verify that the nfs principal is in your keytab file:

```
root@ubuntu1004x8664:~# klist -kte
Keytab name: WRFILE:/etc/krb5.keytab
KVNO Timestamp         Principal
---- ----------------- --------------------------------------------------------
   2 06/25/12 13:06:33 host/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 13:06:33 host/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 13:06:33 host/ubuntu1004x8664.linux.com@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 11:40:19 host/ubuntu1004x8664@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 11:40:19 host/ubuntu1004x8664@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 11:40:19 host/ubuntu1004x8664@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 13:06:33 UBUNTU1004X8664$@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 13:06:33 UBUNTU1004X8664$@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 13:06:33 UBUNTU1004X8664$@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 11:40:19 nfs/ubuntu100432.linux.com/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 11:40:19 nfs/ubuntu100432.linux.com/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 11:40:19 nfs/ubuntu100432.linux.com/ubuntu1004x8664.linux.com@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 11:40:19 nfs/ubuntu100432.linux.com/ubuntu1004x8664@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 11:40:19 nfs/ubuntu100432.linux.com/ubuntu1004x8664@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 11:40:19 nfs/ubuntu100432.linux.com/ubuntu1004x8664@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 15:59:58 nfs/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 15:59:58 nfs/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 15:59:58 nfs/ubuntu1004x8664.linux.com@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 11:41:49 nfs/ubuntu1004x8664@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 11:41:49 nfs/ubuntu1004x8664@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 11:41:49 nfs/ubuntu1004x8664@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 13:06:33 host/UBUNTU1004X8664@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 13:06:33 host/UBUNTU1004X8664@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 13:06:33 host/UBUNTU1004X8664@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 13:06:33 nfs/ubuntu1004x8664.linux.com/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 13:06:33 nfs/ubuntu1004x8664.linux.com/ubuntu1004x8664.linux.com@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 13:06:33 nfs/ubuntu1004x8664.linux.com/ubuntu1004x8664.linux.com@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 13:06:33 nfs/ubuntu1004x8664.linux.com/UBUNTU1004X8664@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 13:06:33 nfs/ubuntu1004x8664.linux.com/UBUNTU1004X8664@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 13:06:33 nfs/ubuntu1004x8664.linux.com/UBUNTU1004X8664@LINUX.COM (ArcFour with HMAC/md5)
   2 06/25/12 15:59:58 nfs/UBUNTU1004X8664@LINUX.COM (DES cbc mode with CRC-32)
   2 06/25/12 15:59:58 nfs/UBUNTU1004X8664@LINUX.COM (DES cbc mode with RSA-MD5)
   2 06/25/12 15:59:58 nfs/UBUNTU1004X8664@LINUX.COM (ArcFour with HMAC/md5)

```edit /etc/idmapd.conf:

```

[General]

Verbosity = 1
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
Domain = linux.com

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

```Domain has to be the same as on your nfs server!!!

Now you are ready to mount a kerberized nfs export:

```
mount -t nfs4 -o sec=krb5 netapp01:/vol/nfsv4test_krb5 /mnt/nfsv4test_krb5
```The export is  now mounted:

```
root@ubuntu1204x8664:/# ls -al /mnt/
total 16
drwxr-xr-x  4 root      root         4096 Jun 25 16:58 .
drwxr-xr-x 23 root      root         4096 Jun 22 10:09 ..
drwxr-xr-x  2 root      root         4096 Apr 27 17:54 hgfs
drwxrwx---  6 someuser domain users 4096 Jun 25 11:03 nfsv4test_krb5

```Only user someuser and members of the "domain users" group can access the directory. And they can only access the directory if the have a valid TGT.

Regards,
Oli

---

### Post by lamoureux on 2013-06-19
Hello,


Sorry to send a message on an Ubuntu forum despite I'm using Debian Squeeze, but I'm totally disapointed.


I try to configure NFSv4 + Kerberos + Active Directory since several days without any success.


Here is my configuration :

[LIST]
[*]One Active Directory server under MS Server 2008 R2, which provide a DOMAIN.LOC directory
[*]One linux NFS Server under Debian Squeeze, named nfsserver
[*]One linux NFS Client under Debian Squeeze, named nfsclient
[/LIST]


Here are all the steps I performed.


[FONT=arial black]On Linux Server (nfsserver)[/FONT]


[U]Package installation
[/U]
[LIST]
[*]nfs-common
[*]nfs-kernel-server
[*]winbind
[/LIST]


[U]Package configuration
[/U]
/etc/samba/smb.conf
```

[global]
netbios name = nfsserver
interfaces = 192.168.1.0/24 192.168.10.0/24 127.0.0.1/32
bind interfaces only = yes
workgroup = DOMAIN
realm = DOMAIN.LOC
server string = Server %h
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 100
log level = 3
syslog = 0
security     = ADS
local master = no
domain master = no
prefered master = no
idmap backend = tdb
idmap uid = 10000-49999
idmap gid = 10000-49999
idmap config DOMAIN : backend  = rid
idmap config DOMAIN : range    = 10000-49999
idmap config DOMAIN : base_rid = 0
winbind enum users = yes
winbind enum groups = yes
winbind offline logon = yes
winbind nested groups = yes
winbind refresh tickets = yes
winbind use default domain = yes
encrypt passwords = yes
password server = 192.168.1.11 192.168.1.14
client use spnego = Yes
kerberos method = secrets and keytab
dedicated keytab file = /etc/krb5.keytab
winbind refresh tickets = true
template shell = /bin/bash
template homedir  = /DOMAIN/%U
name resolve order = lmhosts host

```


/etc/krb5.conf
```

[libdefaults]
        ticket_lifetime = 24000
        default_realm = DOMAIN.LOC
        dns_lookup_realm = false
        dns_lookup_kdc = false
        default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_keytab_name = FILE:/etc/krb5.keytab


[realms]
        DOMAIN.LOC = {
        kdc = dc1.domain.loc:88
        kdc = dc2.domain.loc:88
        admin_server = dc1.domain.loc:749
        admin_server = dc2.domain.loc:749
        kpasswd_server = dc1.domain.loc:464
        kpasswd_server = dc2.domain.loc:464
        kpasswd_protocol = SET_CHANGE
        default_domain = domain.loc
        }


[domain_realm]
        *.domain.loc = DOMAIN.LOC
        .domain.loc = DOMAIN.LOC
        domain.loc = DOMAIN.LOC
 
[logging]
        default = FILE:/var/krb5/kdc.log
        kdc = FILE:/var/krb5/kdc.log

```


To automatically get a kerberos ticket, Winbind is configured in /etc/pam.d/common-auth :
```

auth    [success=3 default=ignore]      pam_unix.so
auth    [success=1 default=ignore]      pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login use_first_pass
auth    requisite                       pam_deny.so
auth    optional                        pam_mount.so
auth    required                        pam_group.so
auth    required                        pam_permit.so

```


/etc/idmapd.conf
```

[General]


Verbosity = 3
Pipefs-Directory = /var/lib/nfs/rpc_pipefs
Domain = domain.loc


[Mapping]


Nobody-User = nobody
Nobody-Group = nogroup

```


/etc/default/nfs-common
```

NEED_STATD=yes
STATDOPTS=
NEED_IDMAPD=yes
NEED_GSSD=yes
RPCGSSDOPTS="-vvv"

```


/etc/default/nfs-kernel-server
```

RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS="--manage-gids"
NEED_SVCGSSD=yes
RPCSVCGSSDOPTS=" -vvv "
RPCNFSDOPTS=

```


Join machine to the domain
```

> net ads join createupn=nfs/nfsserver.domain.loc -U Administrator
Using short domain name -- DOMAIN
Joined 'NFSSERVER' to realm 'domain.loc'

```


Check :
```

> wbinfo -t
checking the trust secret for domain DOMAIN via RPC calls succeeded


> id toto
uid=10000(toto) gid=10000(domain users) groups=10000(domain users)

```


Login with a domain user :
```

> klist
Ticket cache: FILE:/tmp/krb5cc_11147
Default principal: toto@DOMAIN.LOC


Valid starting     Expires            Service principal
06/19/13 16:13:44  06/20/13 02:13:44  krbtgt/DOMAIN.LOC@DOMAIN.LOC
        renew until 06/26/13 16:13:44
06/19/13 16:13:44  06/20/13 02:13:44  NFSSERVER$@DOMAIN.LOC
        renew until 06/26/13 16:13:44
06/19/13 16:13:44  06/20/13 02:13:44  NFSSERVER@DOMAIN.LOC
        renew until 06/26/13 16:13:44

```


Login back with root and create a nfs service principal:
```
> net ads keytab add nfs -U Administrator
```


/etc/exports
```

/srv/nfs4        gss/krb5(rw,sync,fsid=0,crossmnt,no_subtree_check)
/srv/nfs4/share  gss/krb5(rw,sync,no_subtree_check)

```


Restart NFS Service
```

> /etc/init.d/nfs-common restart
> /etc/init.d/nfs-kernel-server restart

```


View nfs exports 
```

> exportfs
/srv/nfs4            gss/krb5
/srv/nfs4/share        gss/krb5

```



[FONT=arial black]On Linux Client (nfsclient)[/FONT]


_Package installation_

[LIST]
[*]nfs-common
[*]winbind
[/LIST]

_Package configuration_
Exactly the same configuration than nfsserver except the nfs-kernel-server and exports parts which is empty.


[FONT=arial black]Mounting the FS[/FONT]


Now I try to mount my nfs volume :
```

> mount -t nfs4 -o sec=krb5 nfsserver:/share /mnt -vvv
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "nfsserver:/share"
mount: node:  "/mnt"
mount: types: "nfs4"
mount: opts:  "sec=krb5"
mount: external mount: argv[0] = "/sbin/mount.nfs4"
mount: external mount: argv[1] = "nfsserver:/share"
mount: external mount: argv[2] = "/mnt"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,sec=krb5"
mount.nfs4: timeout set for Wed Jun 19 16:31:01 2013
mount.nfs4: trying text-based options 'sec=krb5,addr=192.168.1.140,clientaddr=192.168.10.63'
mount.nfs4: mount(2): Permission denied
mount.nfs4: access denied by server while mounting nfsserver:/share

```


And in syslog of nfsclient I have:
```

Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: New client: 59
Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: Opened /var/lib/nfs/rpc_pipefs/nfs/clnt59/idmap
Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: New client: 5a
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: handling gssd upcall (/var/lib/nfs/rpc_pipefs/nfs/clnt59)
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: handle_gssd_upcall: 'mech=krb5 uid=0 '
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: handling krb5 upcall (/var/lib/nfs/rpc_pipefs/nfs/clnt59)
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: process_krb5_upcall: service is '<null>'
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: Full hostname for 'nfsserver.domain.loc' is 'nfsserver.domain.loc'
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: Full hostname for 'nfsclient.domain.loc' is 'nfsclient.domain.loc'
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: Key table entry not found while getting keytab entry for 'root/nfsclient.domain.loc@DOMAIN.LOC'
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: Success getting keytab entry for 'nfs/nfsclient.domain.loc@DOMAIN.LOC'
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: WARNING: Client not found in Kerberos database while getting initial ticket for principal 'nfs/nfsclient.domain.loc@DOMAIN.LOC' using keytab 'WRFILE:/etc/krb5.keytab'
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: ERROR: No credentials found for connection to server nfsserver.domain.loc
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: doing error downcall
Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: Stale client: 5a
Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: #011-> closed /var/lib/nfs/rpc_pipefs/nfs/clnt5a/idmap
Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: Stale client: 59
Jun 19 16:33:13 vm-pxe rpc.idmapd[4839]: #011-> closed /var/lib/nfs/rpc_pipefs/nfs/clnt59/idmap
Jun 19 16:33:13 vm-pxe rpc.gssd[4843]: destroying client /var/lib/nfs/rpc_pipefs/nfs/clnt59

```

I don't know what to do more... If you have an advice or a good idea, please help me :)

Thierry.

---

### Post by michael41 on 2013-08-31
Hi, 

I just wanted to confirm that oliweis method also worked for me with Windows 2012 Server and ubuntu 12.04LTS. 
Keep in mind that your AD has to be set to support these weak encryption types, too.

Set 
**“[B]Network security: Configure encryption types allowed for Kerberos” Policy in "Computer **[/B]**Configuration\ Windows Settings\ Security Settings\ Local Policies\ Security Options " **to also use the weaker encryption types, as Samba 3 does not support aes encryption as far as I read. 

I also managed to get native unix logins working with sssd, see 
[https://fedorahosted.org/sssd/wiki/Configuring%20sssd%20to%20authenticate%20with%20a%20Windows%202008%20Domain%20Server](https://fedorahosted.org/sssd/wiki/Configuring%20sssd%20to%20authenticate%20with%20a%20Windows%202008%20Domain%20Server)
(you have to install identity management for unix, see [http://technet.microsoft.com/en-us/library/cc731178.aspx](http://technet.microsoft.com/en-us/library/cc731178.aspx) and modify your AD users accordingly).

---

