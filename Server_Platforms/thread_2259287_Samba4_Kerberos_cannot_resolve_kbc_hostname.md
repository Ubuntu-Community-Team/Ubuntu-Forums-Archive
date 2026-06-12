---
title: "Samba4 Kerberos cannot resolve kbc hostname"
date: 2015-01-03
forum: Server Platforms
---

### Post by robert-x7ykxjdf on 2015-01-03
Hi,

i am really depressed at this moment. I set up an domain controller using samba4 and an raspberry pi. 

I can join the domain and everything works BUT kerberos has some strange problems resolving my raspberry hostname.

First of all some information:

Raspberry pi is DHCP Server and DNS-Server (BIND9).

First of all the configurations:

```

/usr/local/samba/etc/smb.conf

# Global parameters
[global]
        workgroup = FAMILY
        realm = FAMILY.RAPSBERRY.LOCAL
        netbios name = RASP
        server role = active directory domain controller
        server services = s3fs, rpc, nbt, wrepl, ldap, cldap, kdc, drepl, winbind, ntp_signd, kcc, dnsupdate
        allow dns updates = nonsecure and secure


[netlogon]
        path = /usr/local/samba/var/locks/sysvol/family.rapsberry.local/scripts
        read only = No


[sysvol]
        path = /usr/local/samba/var/locks/sysvol
        read only = No



```

As i said: Samba is working with this configuration. I can join the domain with an WIN 7 Client.

I don't post the bind9 configs but what i can do is post results of following DNS queries:

```
# host -t SRV _ldap._tcp.family.rapsberry.local. localhost; host -t SRV _kerberos._tcp.family.rapsberry.local. localhost
Using domain server:
Name: localhost
Address: 127.0.0.1#53
Aliases:


_ldap._tcp.family.rapsberry.local has SRV record 0 100 389 rasp.family.rapsberry.local.
Using domain server:
Name: localhost
Address: 127.0.0.1#53
Aliases:


_kerberos._tcp.family.rapsberry.local has SRV record 0 100 88 rasp.family.rapsberry.local.

```
Everything seems to be set up nice.

During Domain creation samba4 provides an krb5.conf file:

```
/etc/krb5.conf (provided by samba4)

[libdefaults]
        default_realm = FAMILY.RAPSBERRY.LOCAL
        dns_lookup_realm = false
        dns_lookup_kdc = true

```

This results in:

```
# KRB5_TRACE=/dev/stdout kinit Administrator@FAMILY.RAPSBERRY.LOCAL
[6195] 1420299460.392810: Getting initial credentials for Administrator@FAMILY.RAPSBERRY.LOCAL
[6195] 1420299460.399120: Sending request (208 bytes) to FAMILY.RAPSBERRY.LOCAL
[6195] 1420299460.492736: Resolving hostname rasp.family.rapsberry.local.
[6195] 1420299465.503209: Resolving hostname rasp.family.rapsberry.local.
kinit: Cannot contact any KDC for realm 'FAMILY.RAPSBERRY.LOCAL' while getting initial credentials

```

Strange thing is that BIND9/named did resolve the hostname  rasp.family.rapsberry.local. properly:

```
# cat /var/log/named/queries.log 
[...]
03-Jan-2015 16:23:34.068 client 192.168.178.89#61685 (rasp.family.rapsberry.local): query: rasp.family.rapsberry.local IN A + (192.168.178.222)
```

Whatever, when i use the following krb5.conf (bypassing hostname resolution) everything works:

```
/etc/krb5.conf (bypassing resolution)

[libdefaults]
 default_realm = FAMILY.RAPSBERRY.LOCAL
 dns_lookup_realm = false
 dns_lookup_kdc = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 verify_ap_req_nofail = false


[realms]
 FAMILY.RAPSBERRY.LOCAL = {
 kdc = 192.168.178.222
 admin_server = 192.168.178.222
 default_domain = FAMILY.RAPSBERRY.LOCAL
}


[domain_realm]
 .family.rapsberry.local = FAMILY.RAPSBERRY.LOCAL
 family.rapsberry.local = FAMILY.RAPSBERRY.LOCAL

```

i get the following results:

```
# kinit Administrator@FAMILY.RAPSBERRY.LOCAL
Password for Administrator@FAMILY.RAPSBERRY.LOCAL:
Warning: Your password will expire in 41 days on Sat Feb 14 15:29:32 2015

```

So of course this time kinit did not try to resolve the hostname, but this is no solution for me since Windows Clients of course resolve hostnames.

My last attempt was doing

```
strace kinit Administrator@FAMILY.RAPSBERRY.LOCAL
```

but i cannot see any hints here:

```
# strace kinit Administrator
execve("/usr/bin/kinit", ["kinit", "Administrator"], [/* 17 vars */]) = 0
brk(0)                                  = 0x1ae6000
uname({sys="Linux", node="rasp", ...})  = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f37000
access("/etc/ld.so.preload", R_OK)      = 0
open("/etc/ld.so.preload", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=44, ...}) = 0
mmap2(NULL, 44, PROT_READ|PROT_WRITE, MAP_PRIVATE, 3, 0) = 0xb6f36000
close(3)                                = 0
open("/usr/lib/arm-linux-gnueabihf/libcofi_rpi.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\270\4\0\0004\0\0\0"..., 512) = 512
lseek(3, 7276, SEEK_SET)                = 7276
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1080) = 1080
lseek(3, 7001, SEEK_SET)                = 7001
read(3, "A.\0\0\0aeabi\0\1$\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 47) = 47
fstat64(3, {st_mode=S_IFREG|0755, st_size=10170, ...}) = 0
mmap2(NULL, 39740, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6f0b000
mprotect(0xb6f0d000, 28672, PROT_NONE)  = 0
mmap2(0xb6f14000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6f14000
close(3)                                = 0
munmap(0xb6f36000, 44)                  = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59797, ...}) = 0
mmap2(NULL, 59797, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6efc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkadm5srv_mit.so.8", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0004T\0\0004\0\0\0"..., 512) = 512
lseek(3, 91460, SEEK_SET)               = 91460
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 91132, SEEK_SET)               = 91132
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=92580, ...}) = 0
mmap2(NULL, 165308, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6ed3000
mprotect(0xb6ee8000, 32768, PROT_NONE)  = 0
mmap2(0xb6ef0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xb6ef0000
mmap2(0xb6ef2000, 38332, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6ef2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkdb5.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\3245\0\0004\0\0\0"..., 512) = 512
lseek(3, 54324, SEEK_SET)               = 54324
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 54004, SEEK_SET)               = 54004
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=55444, ...}) = 0
mmap2(NULL, 86824, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6ebd000
mprotect(0xb6eca000, 28672, PROT_NONE)  = 0
mmap2(0xb6ed1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc) = 0xb6ed1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libgssrpc.so.4", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\354@\0\0004\0\0\0"..., 512) = 512
lseek(3, 91692, SEEK_SET)               = 91692
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 91368, SEEK_SET)               = 91368
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=92812, ...}) = 0
mmap2(NULL, 124460, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e9e000
mprotect(0xb6eb4000, 28672, PROT_NONE)  = 0
mmap2(0xb6ebb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xb6ebb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libgssapi_krb5.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\20s\0\0004\0\0\0"..., 512) = 512
lseek(3, 195920, SEEK_SET)              = 195920
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 195592, SEEK_SET)              = 195592
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=197040, ...}) = 0
mmap2(NULL, 228724, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e66000
mprotect(0xb6e94000, 32768, PROT_NONE)  = 0
mmap2(0xb6e9c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2e) = 0xb6e9c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkrb5.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\340\24\1\0004\0\0\0"..., 512) = 512
lseek(3, 679596, SEEK_SET)              = 679596
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 679264, SEEK_SET)              = 679264
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=680756, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f36000
mmap2(NULL, 712416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6db8000
mprotect(0xb6e59000, 28672, PROT_NONE)  = 0
mmap2(0xb6e60000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa0) = 0xb6e60000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libk5crypto.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\374-\0\0004\0\0\0"..., 512) = 512
lseek(3, 156464, SEEK_SET)              = 156464
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 156140, SEEK_SET)              = 156140
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=157584, ...}) = 0
mmap2(NULL, 192612, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d88000
mprotect(0xb6dad000, 32768, PROT_NONE)  = 0
mmap2(0xb6db5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x25) = 0xb6db5000
mmap2(0xb6db7000, 100, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6db7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libcom_err.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\234\17\0\0004\0\0\0"..., 512) = 512
lseek(3, 8712, SEEK_SET)                = 8712
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1080) = 1080
lseek(3, 8408, SEEK_SET)                = 8408
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=9792, ...}) = 0
mmap2(NULL, 41228, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d7d000
mprotect(0xb6d7f000, 28672, PROT_NONE)  = 0
mmap2(0xb6d86000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6d86000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkrb5support.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\304\32\0\0004\0\0\0"..., 512) = 512
lseek(3, 25248, SEEK_SET)               = 25248
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 24920, SEEK_SET)               = 24920
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=26368, ...}) = 0
mmap2(NULL, 57832, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d6e000
mprotect(0xb6d74000, 28672, PROT_NONE)  = 0
mmap2(0xb6d7b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5) = 0xb6d7b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libkeyutils.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\314\16\0\0004\0\0\0"..., 512) = 512
lseek(3, 8536, SEEK_SET)                = 8536
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1080) = 1080
lseek(3, 8196, SEEK_SET)                = 8196
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=9616, ...}) = 0
mmap2(NULL, 40968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d63000
mprotect(0xb6d65000, 28672, PROT_NONE)  = 0
mmap2(0xb6d6c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6d6c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libresolv.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0D$\0\0004\0\0\0"..., 512) = 512
lseek(3, 70328, SEEK_SET)               = 70328
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1200) = 1200
lseek(3, 69980, SEEK_SET)               = 69980
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=71528, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f35000
mmap2(NULL, 79772, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d4f000
mmap2(0xb6d5f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10) = 0xb6d5f000
mmap2(0xb6d61000, 6044, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6d61000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0(\t\0\0004\0\0\0"..., 512) = 512
lseek(3, 8652, SEEK_SET)                = 8652
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 8320, SEEK_SET)                = 8320
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=9812, ...}) = 0
mmap2(NULL, 41136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d44000
mprotect(0xb6d46000, 28672, PROT_NONE)  = 0
mmap2(0xb6d4d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6d4d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\230y\1\0004\0\0\0"..., 512) = 512
lseek(3, 1198880, SEEK_SET)             = 1198880
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1360) = 1360
lseek(3, 1198444, SEEK_SET)             = 1198444
read(3, "A.\0\0\0aeabi\0\1$\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 47) = 47
fstat64(3, {st_mode=S_IFREG|0755, st_size=1200240, ...}) = 0
mmap2(NULL, 1242408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6c14000
mprotect(0xb6d37000, 28672, PROT_NONE)  = 0
mmap2(0xb6d3e000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x122) = 0xb6d3e000
mmap2(0xb6d41000, 9512, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6d41000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libgcc_s.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0P\364\0\0004\0\0\0"..., 512) = 512
lseek(3, 129288, SEEK_SET)              = 129288
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 128956, SEEK_SET)              = 128956
read(3, "A2\0\0\0aeabi\0\1(\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 51) = 51
fstat64(3, {st_mode=S_IFREG|0644, st_size=130448, ...}) = 0
mmap2(NULL, 161780, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6bec000
mprotect(0xb6c0c000, 28672, PROT_NONE)  = 0
mmap2(0xb6c13000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f) = 0xb6c13000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\274V\0\0004\0\0\0"..., 512) = 512
lseek(3, 82712, SEEK_SET)               = 82712
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1400) = 1400
lseek(3, 82308, SEEK_SET)               = 82308
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0755, st_size=116462, ...}) = 0
mmap2(NULL, 123412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6bcd000
mprotect(0xb6be1000, 28672, PROT_NONE)  = 0
mmap2(0xb6be8000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb6be8000
mmap2(0xb6bea000, 4628, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6bea000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f34000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f33000
set_tls(0xb6f334c0, 0xb6f33bb8, 0xb6f3b048, 0xb6f334c0, 0xb6f3b048) = 0
mprotect(0xb6be8000, 4096, PROT_READ)   = 0
mprotect(0xb6d3e000, 8192, PROT_READ)   = 0
mprotect(0xb6d4d000, 4096, PROT_READ)   = 0
mprotect(0xb6d5f000, 4096, PROT_READ)   = 0
mprotect(0xb6d6c000, 4096, PROT_READ)   = 0
mprotect(0xb6d7b000, 4096, PROT_READ)   = 0
mprotect(0xb6d86000, 4096, PROT_READ)   = 0
mprotect(0xb6db5000, 4096, PROT_READ)   = 0
mprotect(0xb6e60000, 20480, PROT_READ)  = 0
mprotect(0xb6e9c000, 4096, PROT_READ)   = 0
mprotect(0xb6ebb000, 4096, PROT_READ)   = 0
mprotect(0xb6ed1000, 4096, PROT_READ)   = 0
mprotect(0xb6ef0000, 4096, PROT_READ)   = 0
mprotect(0x13000, 4096, PROT_READ)      = 0
mprotect(0xb6f3a000, 4096, PROT_READ)   = 0
munmap(0xb6efc000, 59797)               = 0
set_tid_address(0xb6f33068)             = 6210
set_robust_list(0xb6f33070, 0xc)        = 0
futex(0xbed5d838, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, b6be9000) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xb6bd220c, [], SA_SIGINFO|0x4000000}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb6bd20b4, [], SA_RESTART|SA_SIGINFO|0x4000000}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
brk(0)                                  = 0x1ae6000
brk(0x1b07000)                          = 0x1b07000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=1534656, ...}) = 0
mmap2(NULL, 1534656, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6a56000
close(3)                                = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(2, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
futex(0xb6d7c15c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb6d7c144, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb6e65b10, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb6e65d4c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
gettimeofday({1420299769, 734542}, NULL) = 0
stat64("/etc/krb5.conf", {st_mode=S_IFREG|0644, st_size=103, ...}) = 0
open("/etc/krb5.conf", O_RDONLY)        = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=103, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f32000
read(3, "[libdefaults]\n\tdefault_realm = F"..., 4096) = 103
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6f32000, 4096)                = 0
gettimeofday({1420299769, 746495}, NULL) = 0
stat64("/usr/etc/krb5.conf", 0xbed5b460) = -1 ENOENT (No such file or directory)
gettimeofday({1420299769, 748999}, NULL) = 0
gettimeofday({1420299769, 750260}, NULL) = 0
open("/dev/urandom", O_RDONLY)          = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 9), ...}) = 0
read(3, "\231\336\226\26l5k6\343\5\236k\230^\31\27\266\16\355\246\220W\27\177x\207\276\321\5?d\201"..., 64) = 64
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 9), ...}) = 0
read(3, "\340\232\354\204\366\215{\31\216\302\264o\303\324fx\3679P^\2045\346N\267^\371G\252\206\23\225"..., 64) = 64
close(3)                                = 0
futex(0xb6db61d8, FUTEX_WAKE_PRIVATE, 2147483647) = 0
gettimeofday({1420299769, 765521}, NULL) = 0
gettimeofday({1420299769, 766695}, NULL) = 0
gettimeofday({1420299769, 768022}, NULL) = 0
gettimeofday({1420299769, 769054}, NULL) = 0
gettimeofday({1420299769, 770218}, NULL) = 0
gettimeofday({1420299769, 771202}, NULL) = 0
gettimeofday({1420299769, 772861}, NULL) = 0
gettimeofday({1420299769, 774083}, NULL) = 0
gettimeofday({1420299769, 774607}, NULL) = 0
gettimeofday({1420299769, 775645}, NULL) = 0
getuid32()                              = 0
gettimeofday({1420299769, 778794}, NULL) = 0
gettimeofday({1420299769, 779985}, NULL) = 0
gettimeofday({1420299769, 780970}, NULL) = 0
gettimeofday({1420299769, 782174}, NULL) = 0
gettimeofday({1420299769, 783087}, NULL) = 0
gettimeofday({1420299769, 783534}, NULL) = 0
gettimeofday({1420299769, 785187}, NULL) = 0
gettimeofday({1420299769, 786316}, NULL) = 0
gettimeofday({1420299769, 786781}, NULL) = 0
gettimeofday({1420299769, 787877}, NULL) = 0
gettimeofday({1420299769, 789006}, NULL) = 0
gettimeofday({1420299769, 790322}, NULL) = 0
gettimeofday({1420299769, 790775}, NULL) = 0
stat64("/usr/lib/arm-linux-gnueabihf/krb5/plugins/preauth/pkinit.so", 0xbed5c168) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f32000
read(3, "# Locale name alias data base.\n#"..., 1024) = 1024
read(3, " entries are case independent.\n\n"..., 1024) = 1024
read(3, "eucKR\nko_KR\t\tko_KR.eucKR\nlithuan"..., 1024) = 522
read(3, "", 1024)                       = 0
close(3)                                = 0
munmap(0xb6f32000, 4096)                = 0
open("/usr/share/locale/en_GB.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB/LC_MESSAGES/libc.mo", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=1474, ...}) = 0
mmap2(NULL, 1474, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6f32000
close(3)                                = 0
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB.UTF-8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB.utf8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
gettimeofday({1420299769, 827793}, NULL) = 0
gettimeofday({1420299769, 828939}, NULL) = 0
gettimeofday({1420299769, 829879}, NULL) = 0
gettimeofday({1420299769, 831484}, NULL) = 0
open("/etc/localtime", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\10\0\0\0\10\0\0\0\0"..., 4096) = 2309
_llseek(3, -28, [2281], SEEK_CUR)       = 0
read(3, "\nCET-1CEST,M3.5.0,M10.5.0/3\n", 4096) = 28
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
gettimeofday({1420299769, 844968}, NULL) = 0
open("/usr/lib/arm-linux-gnueabihf/krb5/plugins/libkrb5", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
gettimeofday({1420299769, 849605}, NULL) = 0
gettimeofday({1420299769, 850172}, NULL) = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "domain family.rapsberry.local\nse"..., 4096) = 87
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "domain family.rapsberry.local\nse"..., 4096) = 87
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
gettimeofday({1420299769, 869502}, NULL) = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, 16) = 0
gettimeofday({1420299769, 873429}, NULL) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
send(3, "\300\325\1\0\0\1\0\0\0\0\0\0\t_kerberos\4_udp\6FAMI"..., 55, MSG_NOSIGNAL) = 55
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\300\325\205\200\0\1\0\1\0\1\0\1\t_kerberos\4_udp\6FAMI"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, [16]) = 132
close(3)                                = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "domain family.rapsberry.local\nse"..., 4096) = 87
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
gettimeofday({1420299769, 938032}, NULL) = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, 16) = 0
gettimeofday({1420299769, 940729}, NULL) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
send(3, "\360~\1\0\0\1\0\0\0\0\0\0\t_kerberos\4_tcp\6FAMI"..., 55, MSG_NOSIGNAL) = 55
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\360~\205\200\0\1\0\1\0\1\0\1\t_kerberos\4_tcp\6FAMI"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, [16]) = 132
close(3)                                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 3
bind(3, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, pid=6210, groups=00000000}, [12]) = 0
gettimeofday({1420299769, 996499}, NULL) = 0
sendto(3, "\24\0\0\0\26\0\1\3\371\r\250T\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"D\0\0\0\24\0\2\0\371\r\250TB\30\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 148
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\371\r\250TB\30\0\0\0\0\0\0\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59797, ...}) = 0
mmap2(NULL, 59797, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6efc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\324\31\0\0004\0\0\0"..., 512) = 512
lseek(3, 41532, SEEK_SET)               = 41532
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 41192, SEEK_SET)               = 41192
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=42692, ...}) = 0
mmap2(NULL, 74492, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6a43000
mprotect(0xb6a4d000, 28672, PROT_NONE)  = 0
mmap2(0xb6a54000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xb6a54000
close(3)                                = 0
mprotect(0xb6a54000, 4096, PROT_READ)   = 0
munmap(0xb6efc000, 59797)               = 0
open("/etc/host.conf", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=9, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "multi on\n", 1024)             = 9
read(3, "", 1024)                       = 0
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
futex(0xb6d42824, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/etc/hosts", O_RDONLY|O_CLOEXEC)  = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
fstat64(3, {st_mode=S_IFREG|0644, st_size=261, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
read(3, "127.0.0.1\tlocalhost localhost.lo"..., 4096) = 261
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6f0a000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59797, ...}) = 0
mmap2(NULL, 59797, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6efc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_mdns4_minimal.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\354\7\0\0004\0\0\0"..., 512) = 512
lseek(3, 5964, SEEK_SET)                = 5964
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1040) = 1040
lseek(3, 5692, SEEK_SET)                = 5692
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=7004, ...}) = 0
mmap2(NULL, 38464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6a39000
mprotect(0xb6a3b000, 28672, PROT_NONE)  = 0
mmap2(0xb6a42000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6a42000
close(3)                                = 0
munmap(0xb6efc000, 59797)               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
connect(3, {sa_family=AF_FILE, path="/var/run/avahi-daemon/socket"}, 110) = 0
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f0a000
_llseek(3, 0, 0xbed5b920, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "RESOLVE-HOSTNAME-IPV4 rasp.famil"..., 51) = 51
read(3, ^C <unfinished ...>
root@rasp:/home/pi# strace kinit Administrator@FAMILY.RAPSBERRY.LOCAL
execve("/usr/bin/kinit", ["kinit", "Administrator@FAMILY.RAPSBERRY.L"...], [/* 17 vars */]) = 0
brk(0)                                  = 0x747000
uname({sys="Linux", node="rasp", ...})  = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6f00000
access("/etc/ld.so.preload", R_OK)      = 0
open("/etc/ld.so.preload", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=44, ...}) = 0
mmap2(NULL, 44, PROT_READ|PROT_WRITE, MAP_PRIVATE, 3, 0) = 0xb6eff000
close(3)                                = 0
open("/usr/lib/arm-linux-gnueabihf/libcofi_rpi.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\270\4\0\0004\0\0\0"..., 512) = 512
lseek(3, 7276, SEEK_SET)                = 7276
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1080) = 1080
lseek(3, 7001, SEEK_SET)                = 7001
read(3, "A.\0\0\0aeabi\0\1$\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 47) = 47
fstat64(3, {st_mode=S_IFREG|0755, st_size=10170, ...}) = 0
mmap2(NULL, 39740, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6ed4000
mprotect(0xb6ed6000, 28672, PROT_NONE)  = 0
mmap2(0xb6edd000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6edd000
close(3)                                = 0
munmap(0xb6eff000, 44)                  = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59797, ...}) = 0
mmap2(NULL, 59797, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6ec5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkadm5srv_mit.so.8", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0004T\0\0004\0\0\0"..., 512) = 512
lseek(3, 91460, SEEK_SET)               = 91460
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 91132, SEEK_SET)               = 91132
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=92580, ...}) = 0
mmap2(NULL, 165308, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e9c000
mprotect(0xb6eb1000, 32768, PROT_NONE)  = 0
mmap2(0xb6eb9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xb6eb9000
mmap2(0xb6ebb000, 38332, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6ebb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkdb5.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\3245\0\0004\0\0\0"..., 512) = 512
lseek(3, 54324, SEEK_SET)               = 54324
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 54004, SEEK_SET)               = 54004
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=55444, ...}) = 0
mmap2(NULL, 86824, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e86000
mprotect(0xb6e93000, 28672, PROT_NONE)  = 0
mmap2(0xb6e9a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc) = 0xb6e9a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libgssrpc.so.4", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\354@\0\0004\0\0\0"..., 512) = 512
lseek(3, 91692, SEEK_SET)               = 91692
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 91368, SEEK_SET)               = 91368
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=92812, ...}) = 0
mmap2(NULL, 124460, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e67000
mprotect(0xb6e7d000, 28672, PROT_NONE)  = 0
mmap2(0xb6e84000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xb6e84000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libgssapi_krb5.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\20s\0\0004\0\0\0"..., 512) = 512
lseek(3, 195920, SEEK_SET)              = 195920
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 195592, SEEK_SET)              = 195592
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=197040, ...}) = 0
mmap2(NULL, 228724, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e2f000
mprotect(0xb6e5d000, 32768, PROT_NONE)  = 0
mmap2(0xb6e65000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2e) = 0xb6e65000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkrb5.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\340\24\1\0004\0\0\0"..., 512) = 512
lseek(3, 679596, SEEK_SET)              = 679596
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 679264, SEEK_SET)              = 679264
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=680756, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6eff000
mmap2(NULL, 712416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d81000
mprotect(0xb6e22000, 28672, PROT_NONE)  = 0
mmap2(0xb6e29000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa0) = 0xb6e29000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libk5crypto.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\374-\0\0004\0\0\0"..., 512) = 512
lseek(3, 156464, SEEK_SET)              = 156464
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 156140, SEEK_SET)              = 156140
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=157584, ...}) = 0
mmap2(NULL, 192612, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d51000
mprotect(0xb6d76000, 32768, PROT_NONE)  = 0
mmap2(0xb6d7e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x25) = 0xb6d7e000
mmap2(0xb6d80000, 100, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6d80000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libcom_err.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\234\17\0\0004\0\0\0"..., 512) = 512
lseek(3, 8712, SEEK_SET)                = 8712
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1080) = 1080
lseek(3, 8408, SEEK_SET)                = 8408
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=9792, ...}) = 0
mmap2(NULL, 41228, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d46000
mprotect(0xb6d48000, 28672, PROT_NONE)  = 0
mmap2(0xb6d4f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6d4f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/arm-linux-gnueabihf/libkrb5support.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\304\32\0\0004\0\0\0"..., 512) = 512
lseek(3, 25248, SEEK_SET)               = 25248
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1120) = 1120
lseek(3, 24920, SEEK_SET)               = 24920
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=26368, ...}) = 0
mmap2(NULL, 57832, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d37000
mprotect(0xb6d3d000, 28672, PROT_NONE)  = 0
mmap2(0xb6d44000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5) = 0xb6d44000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libkeyutils.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\314\16\0\0004\0\0\0"..., 512) = 512
lseek(3, 8536, SEEK_SET)                = 8536
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1080) = 1080
lseek(3, 8196, SEEK_SET)                = 8196
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=9616, ...}) = 0
mmap2(NULL, 40968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d2c000
mprotect(0xb6d2e000, 28672, PROT_NONE)  = 0
mmap2(0xb6d35000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6d35000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libresolv.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0D$\0\0004\0\0\0"..., 512) = 512
lseek(3, 70328, SEEK_SET)               = 70328
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1200) = 1200
lseek(3, 69980, SEEK_SET)               = 69980
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=71528, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6efe000
mmap2(NULL, 79772, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d18000
mmap2(0xb6d28000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10) = 0xb6d28000
mmap2(0xb6d2a000, 6044, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6d2a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0(\t\0\0004\0\0\0"..., 512) = 512
lseek(3, 8652, SEEK_SET)                = 8652
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 8320, SEEK_SET)                = 8320
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=9812, ...}) = 0
mmap2(NULL, 41136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6d0d000
mprotect(0xb6d0f000, 28672, PROT_NONE)  = 0
mmap2(0xb6d16000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6d16000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\230y\1\0004\0\0\0"..., 512) = 512
lseek(3, 1198880, SEEK_SET)             = 1198880
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1360) = 1360
lseek(3, 1198444, SEEK_SET)             = 1198444
read(3, "A.\0\0\0aeabi\0\1$\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 47) = 47
fstat64(3, {st_mode=S_IFREG|0755, st_size=1200240, ...}) = 0
mmap2(NULL, 1242408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6bdd000
mprotect(0xb6d00000, 28672, PROT_NONE)  = 0
mmap2(0xb6d07000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x122) = 0xb6d07000
mmap2(0xb6d0a000, 9512, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6d0a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libgcc_s.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0P\364\0\0004\0\0\0"..., 512) = 512
lseek(3, 129288, SEEK_SET)              = 129288
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 128956, SEEK_SET)              = 128956
read(3, "A2\0\0\0aeabi\0\1(\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 51) = 51
fstat64(3, {st_mode=S_IFREG|0644, st_size=130448, ...}) = 0
mmap2(NULL, 161780, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6bb5000
mprotect(0xb6bd5000, 28672, PROT_NONE)  = 0
mmap2(0xb6bdc000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f) = 0xb6bdc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\274V\0\0004\0\0\0"..., 512) = 512
lseek(3, 82712, SEEK_SET)               = 82712
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1400) = 1400
lseek(3, 82308, SEEK_SET)               = 82308
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0755, st_size=116462, ...}) = 0
mmap2(NULL, 123412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6b96000
mprotect(0xb6baa000, 28672, PROT_NONE)  = 0
mmap2(0xb6bb1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb6bb1000
mmap2(0xb6bb3000, 4628, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6bb3000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6efd000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6efc000
set_tls(0xb6efc4c0, 0xb6efcbb8, 0xb6f04048, 0xb6efc4c0, 0xb6f04048) = 0
mprotect(0xb6bb1000, 4096, PROT_READ)   = 0
mprotect(0xb6d07000, 8192, PROT_READ)   = 0
mprotect(0xb6d16000, 4096, PROT_READ)   = 0
mprotect(0xb6d28000, 4096, PROT_READ)   = 0
mprotect(0xb6d35000, 4096, PROT_READ)   = 0
mprotect(0xb6d44000, 4096, PROT_READ)   = 0
mprotect(0xb6d4f000, 4096, PROT_READ)   = 0
mprotect(0xb6d7e000, 4096, PROT_READ)   = 0
mprotect(0xb6e29000, 20480, PROT_READ)  = 0
mprotect(0xb6e65000, 4096, PROT_READ)   = 0
mprotect(0xb6e84000, 4096, PROT_READ)   = 0
mprotect(0xb6e9a000, 4096, PROT_READ)   = 0
mprotect(0xb6eb9000, 4096, PROT_READ)   = 0
mprotect(0x13000, 4096, PROT_READ)      = 0
mprotect(0xb6f03000, 4096, PROT_READ)   = 0
munmap(0xb6ec5000, 59797)               = 0
set_tid_address(0xb6efc068)             = 6212
set_robust_list(0xb6efc070, 0xc)        = 0
futex(0xbef73818, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, b6bb2000) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xb6b9b20c, [], SA_SIGINFO|0x4000000}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb6b9b0b4, [], SA_RESTART|SA_SIGINFO|0x4000000}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
brk(0)                                  = 0x747000
brk(0x768000)                           = 0x768000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=1534656, ...}) = 0
mmap2(NULL, 1534656, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6a1f000
close(3)                                = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(2, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
futex(0xb6d4515c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb6d45144, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb6e2eb10, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb6e2ed4c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
gettimeofday({1420299777, 115922}, NULL) = 0
stat64("/etc/krb5.conf", {st_mode=S_IFREG|0644, st_size=103, ...}) = 0
open("/etc/krb5.conf", O_RDONLY)        = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=103, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6efb000
read(3, "[libdefaults]\n\tdefault_realm = F"..., 4096) = 103
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6efb000, 4096)                = 0
gettimeofday({1420299777, 128746}, NULL) = 0
stat64("/usr/etc/krb5.conf", 0xbef71440) = -1 ENOENT (No such file or directory)
gettimeofday({1420299777, 131179}, NULL) = 0
gettimeofday({1420299777, 132408}, NULL) = 0
open("/dev/urandom", O_RDONLY)          = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 9), ...}) = 0
read(3, "e)\222\25j2\177\177\21\252 8s\v 5{\r\16\rS\264\206h \243\355\36)h\0\334"..., 64) = 64
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFCHR|0666, st_rdev=makedev(1, 9), ...}) = 0
read(3, "\364\215\324\316Y\373Hw\nw`\366\26b\3544\27G\231*^\271:>\201\266\v*6\7@\303"..., 64) = 64
close(3)                                = 0
futex(0xb6d7f1d8, FUTEX_WAKE_PRIVATE, 2147483647) = 0
gettimeofday({1420299777, 147599}, NULL) = 0
gettimeofday({1420299777, 148700}, NULL) = 0
gettimeofday({1420299777, 149170}, NULL) = 0
gettimeofday({1420299777, 150323}, NULL) = 0
gettimeofday({1420299777, 151339}, NULL) = 0
gettimeofday({1420299777, 152472}, NULL) = 0
gettimeofday({1420299777, 152948}, NULL) = 0
gettimeofday({1420299777, 153892}, NULL) = 0
gettimeofday({1420299777, 155082}, NULL) = 0
getuid32()                              = 0
gettimeofday({1420299777, 158878}, NULL) = 0
gettimeofday({1420299777, 159345}, NULL) = 0
gettimeofday({1420299777, 160485}, NULL) = 0
gettimeofday({1420299777, 161404}, NULL) = 0
gettimeofday({1420299777, 161868}, NULL) = 0
gettimeofday({1420299777, 162988}, NULL) = 0
gettimeofday({1420299777, 163916}, NULL) = 0
gettimeofday({1420299777, 165044}, NULL) = 0
gettimeofday({1420299777, 165513}, NULL) = 0
gettimeofday({1420299777, 166413}, NULL) = 0
gettimeofday({1420299777, 167794}, NULL) = 0
gettimeofday({1420299777, 169045}, NULL) = 0
gettimeofday({1420299777, 170180}, NULL) = 0
stat64("/usr/lib/arm-linux-gnueabihf/krb5/plugins/preauth/pkinit.so", 0xbef72148) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6efb000
read(3, "# Locale name alias data base.\n#"..., 1024) = 1024
read(3, " entries are case independent.\n\n"..., 1024) = 1024
read(3, "eucKR\nko_KR\t\tko_KR.eucKR\nlithuan"..., 1024) = 522
read(3, "", 1024)                       = 0
close(3)                                = 0
munmap(0xb6efb000, 4096)                = 0
open("/usr/share/locale/en_GB.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB/LC_MESSAGES/libc.mo", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=1474, ...}) = 0
mmap2(NULL, 1474, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6efb000
close(3)                                = 0
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB.UTF-8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB.utf8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_GB/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/mit-krb5.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
gettimeofday({1420299777, 205101}, NULL) = 0
gettimeofday({1420299777, 206107}, NULL) = 0
gettimeofday({1420299777, 206999}, NULL) = 0
gettimeofday({1420299777, 208730}, NULL) = 0
open("/etc/localtime", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\10\0\0\0\10\0\0\0\0"..., 4096) = 2309
_llseek(3, -28, [2281], SEEK_CUR)       = 0
read(3, "\nCET-1CEST,M3.5.0,M10.5.0/3\n", 4096) = 28
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
gettimeofday({1420299777, 221684}, NULL) = 0
open("/usr/lib/arm-linux-gnueabihf/krb5/plugins/libkrb5", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
gettimeofday({1420299777, 225818}, NULL) = 0
gettimeofday({1420299777, 227173}, NULL) = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "domain family.rapsberry.local\nse"..., 4096) = 87
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "domain family.rapsberry.local\nse"..., 4096) = 87
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
gettimeofday({1420299777, 245675}, NULL) = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, 16) = 0
gettimeofday({1420299777, 250460}, NULL) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
send(3, "\357\326\1\0\0\1\0\0\0\0\0\0\t_kerberos\4_udp\6FAMI"..., 55, MSG_NOSIGNAL) = 55
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "\357\326\205\200\0\1\0\1\0\1\0\1\t_kerberos\4_udp\6FAMI"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, [16]) = 132
close(3)                                = 0
open("/etc/resolv.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "domain family.rapsberry.local\nse"..., 4096) = 87
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
gettimeofday({1420299777, 314212}, NULL) = 0
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, 16) = 0
gettimeofday({1420299777, 316982}, NULL) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
send(3, "S\241\1\0\0\1\0\0\0\0\0\0\t_kerberos\4_tcp\6FAMI"..., 55, MSG_NOSIGNAL) = 55
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
recvfrom(3, "S\241\205\200\0\1\0\1\0\1\0\1\t_kerberos\4_tcp\6FAMI"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("192.168.178.222")}, [16]) = 132
close(3)                                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 3
bind(3, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, pid=6212, groups=00000000}, [12]) = 0
gettimeofday({1420299777, 373221}, NULL) = 0
sendto(3, "\24\0\0\0\26\0\1\3\1\16\250T\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"D\0\0\0\24\0\2\0\1\16\250TD\30\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 148
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\1\16\250TD\30\0\0\0\0\0\0\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59797, ...}) = 0
mmap2(NULL, 59797, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6ec5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/arm-linux-gnueabihf/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\324\31\0\0004\0\0\0"..., 512) = 512
lseek(3, 41532, SEEK_SET)               = 41532
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1160) = 1160
lseek(3, 41192, SEEK_SET)               = 41192
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=42692, ...}) = 0
mmap2(NULL, 74492, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6a0c000
mprotect(0xb6a16000, 28672, PROT_NONE)  = 0
mmap2(0xb6a1d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xb6a1d000
close(3)                                = 0
mprotect(0xb6a1d000, 4096, PROT_READ)   = 0
munmap(0xb6ec5000, 59797)               = 0
open("/etc/host.conf", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=9, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "multi on\n", 1024)             = 9
read(3, "", 1024)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
futex(0xb6d0b824, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/etc/hosts", O_RDONLY|O_CLOEXEC)  = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
fstat64(3, {st_mode=S_IFREG|0644, st_size=261, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "127.0.0.1\tlocalhost localhost.lo"..., 4096) = 261
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=59797, ...}) = 0
mmap2(NULL, 59797, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6ec5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libnss_mdns4_minimal.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0(\0\1\0\0\0\354\7\0\0004\0\0\0"..., 512) = 512
lseek(3, 5964, SEEK_SET)                = 5964
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 1040) = 1040
lseek(3, 5692, SEEK_SET)                = 5692
read(3, "A0\0\0\0aeabi\0\1&\0\0\0\0056\0\6\6\10\1\t\1\n\2\22\4\24\1\25"..., 49) = 49
fstat64(3, {st_mode=S_IFREG|0644, st_size=7004, ...}) = 0
mmap2(NULL, 38464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6a02000
mprotect(0xb6a04000, 28672, PROT_NONE)  = 0
mmap2(0xb6a0b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6a0b000
close(3)                                = 0
munmap(0xb6ec5000, 59797)               = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
connect(3, {sa_family=AF_FILE, path="/var/run/avahi-daemon/socket"}, 110) = 0
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
_llseek(3, 0, 0xbef71900, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "RESOLVE-HOSTNAME-IPV4 rasp.famil"..., 51) = 51
read(3, "-15 Timeout reached\n", 4096)  = 20
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
socket(PF_NETLINK, SOCK_RAW, 0)         = 3
bind(3, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, pid=6212, groups=00000000}, [12]) = 0
gettimeofday({1420299782, 477292}, NULL) = 0
sendto(3, "\24\0\0\0\26\0\1\3\6\16\250T\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"D\0\0\0\24\0\2\0\6\16\250TD\30\0\0\2\10\200\376\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 148
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\6\16\250TD\30\0\0\0\0\0\0\1\0\0\0\10\0\1\0\177\0\0\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
stat64("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=87, ...}) = 0
open("/etc/hosts", O_RDONLY|O_CLOEXEC)  = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=261, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
read(3, "127.0.0.1\tlocalhost localhost.lo"..., 4096) = 261
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
connect(3, {sa_family=AF_FILE, path="/var/run/avahi-daemon/socket"}, 110) = 0
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ed3000
_llseek(3, 0, 0xbef71900, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "RESOLVE-HOSTNAME-IPV4 rasp.famil"..., 51) = 51
read(3, "-15 Timeout reached\n", 4096)  = 20
close(3)                                = 0
munmap(0xb6ed3000, 4096)                = 0
gettimeofday({1420299787, 508384}, NULL) = 0
gettimeofday({1420299787, 508656}, NULL) = 0
write(2, "kinit: Cannot contact any KDC fo"..., 65kinit: Cannot contact any KDC for realm 'FAMILY.RAPSBERRY.LOCAL' ) = 65
write(2, "while getting initial credential"..., 33while getting initial credentials) = 33
write(2, "\n", 1
)                       = 1
exit_group(1)                           = ?

```

ANY! suggestion is highly appreciated! :( thanks in advance

---

