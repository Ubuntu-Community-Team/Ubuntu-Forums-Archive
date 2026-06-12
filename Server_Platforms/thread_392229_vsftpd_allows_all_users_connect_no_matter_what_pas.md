---
title: "vsftpd allows all users connect no matter what password they use"
date: 2007-03-24
forum: Server Platforms
---

### Post by -=pug=- on 2007-03-24
I think I have an unusual problem if anyone here wants to try and help me...

Anyone with a valid shell account can login with any password they choose, or with no password at all if they like. I've checked and double checked both my vsftpd.conf and pam.d configs but I can't see anything unusual in either, I just don't know what I'm missing :(

anon users are blocked, and non shell accounts can't login, but anyone with the correct username can login no matter what password they use.

vsftpd.conf file.....
> 
listen=YES
listen_ipv6=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=002
anon_upload_enable=NO
anon_mkdir_write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=share
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
ls_recurse_enable=YES
userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO
hide_ids=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


/etc/pam.d/vsftpd....
> 
# Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session

#@include common-auth
auth    required        pam_shells.so


/etc/pam.d/common-account....
> 
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account required        pam_unix.so


/etc/pam.d/common-session
> 
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session required        pam_unix.so
session optional        pam_foreground.so


Any help appreciated :)

[EDIT] Forgot to say I'm using ubunto 6.06 server with long term support.

---

### Post by Mr. C. on 2007-03-24
How and where are your local users passwords set?  Your pam configuration will look in the system default location (/etc/shadow, and not /etc/passwd).

Also, these make no sense with anonymous users disable:
chown_uploads=YES
chown_username=share


MrC

---

### Post by -=pug=- on 2007-03-24
> **Mr. C. said:**
> How and where are your local users passwords set?  Your pam configuration will look in the system default location (/etc/shadow, and not /etc/passwd).
Everything is set to defaults so system users passwords are stored in /etc/shadow.

I know they are not related, but it might be worth saying that password authentication for ssh logins work just fine, which is what makes me think it's some pam sillyness.
> Also, these make no sense with anonymous users disable:
chown_uploads=YES
chown_username=share


MrC
idd I was doing some testing on anon users and forgot to remove those lines, thanks for pointing it out :)

---

### Post by Mr. C. on 2007-03-24
I don't think the vsftpd setup is at fault - you can check this by reverting to a stock vsftpd.conf, with the single change of setting local_enable=YES, and restarting vsftpd.

Your pam files look fine.  Have you changed anything pam or login related?  Have you changed: /etc/ftpusers, or any files referenced by the pam modules?

I keep thinking something is wrong with your passwd and/or shadow files.  Do you have any accounts that have no passwords?

You might want to run the vsftpd daemon under strace via command line (disable background mode).  This will give you the results of which system calls and libraries are being used, perhaps helping you narrow the problem area.

MrC

---

### Post by -=pug=- on 2007-03-25
> **Mr. C. said:**
> I don't think the vsftpd setup is at fault - you can check this by reverting to a stock vsftpd.conf, with the single change of setting local_enable=YES, and restarting vsftpd.
OK tried that, installed vsftpd on another box, and just copied and pasted the default config file from there no joy.

> Your pam files look fine.  Have you changed anything pam or login related?  Have you changed: /etc/ftpusers, or any files referenced by the pam modules?
I haven't touched pam, to tell the truth I'm afraid of it :D haven't touched /etc/ftpusers either and all that's in there is the usual accounts root, daemon, bin etc. I did make changes to /etc/vsftpd.chroot_list, and /etc/vsftpd.user_list but only to add the users I wanted to each.

> I keep thinking something is wrong with your passwd and/or shadow files.  Do you have any accounts that have no passwords?
I can promise you passwd and shadow files are as they should be, the password field in /etc/passwd is blank, and only users that should have a login have entries in the password field in /etc/shadow. I'd paste both in to proove it, but considering all you need to know is the usernames I use to gain access to my ftp server it's probably not such a good idea ;)

> You might want to run the vsftpd daemon under strace via command line (disable listen mode).  This will give you the results of which system calls and libraries are being used, perhaps helping you narrow the problem area.

MrC

Thanks for the tip I'll give it a try and report back.

---

### Post by -=pug=- on 2007-03-25
> **Mr. C. said:**
> You might want to run the vsftpd daemon under strace via command line (disable listen mode).  This will give you the results of which system calls and libraries are being used, perhaps helping you narrow the problem area.

MrC
Sweet jebus I haven't used strace before, so I didn't know the output would be so... uummm detailed :) most of it is illegable to me anyway, but running from the cli with standalone disabled only returns an error that it's not configured to run in standalone mode, and to run it from /etc/init.d. Before it exits the only libs that return errors are /etc/ld.so.nohwcap, and /etc/ld.so.preload output for both below...
> 
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac1000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=10078, ...}) = 0
mmap(NULL, 10078, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libncurses.so.5", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\372\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=373480, ...}) = 0

Tried running it from /etc/init.d too with the exact same results but without the exit error this time, and the only additional errors were from missing locale files which shouldn't cause any problems afaik anyway. If you like I can paste the entire output in here, i'm just a bit hesetant cos it's so bloody long and I don't want to drive people away screaming when they read this thread :)

---

### Post by Mr. C. on 2007-03-25
I'm not sure what to tell you.  I can't help you debug without data (vs. interpretation).

I'd be very wealthy if I had dollar for every student or otherwise that promised me they didn't change this or that, or that everything was correct (and yet their setup still fails).

If you're going to go it alone, I'd suggest you need to start learning how the authentication system works, and how to debug.

Sorry,
MrC

---

### Post by -=pug=- on 2007-03-25
> **Mr. C. said:**
> I'm not sure what to tell you.  I can't help you debug without data (vs. interpretation).

I'd be very wealthy if I had dollar for every student or otherwise that promised me they didn't change this or that, or that everything was correct (and yet their setup still fails).

If you're going to go it alone, I'd suggest you need to start learning how the authentication system works, and how to debug.

Sorry,
MrC
Fair enough then, I've edited the actual usernames and real names if that's OK, but here's everything....

output from strace.....
```

execve("/etc/init.d/vsftpd", ["/etc/init.d/vsftpd", "start"], [/* 23 vars */]) = 0
uname({sys="Linux", node="chimp", ...}) = 0
brk(0)                                  = 0x5c7000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac1000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=10078, ...}) = 0
mmap(NULL, 10078, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libncurses.so.5", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\372\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=373480, ...}) = 0
mmap(NULL, 1423696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaabc2000
mprotect(0x2aaaaac0f000, 1108304, PROT_NONE) = 0
mmap(0x2aaaaad0f000, 57344, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4d000) = 0x2aaaaad0f000
mmap(0x2aaaaad1d000, 2384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaaad1d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libdl.so.2", O_RDONLY)       = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\17\0\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0644, st_size=10056, ...}) = 0
mmap(NULL, 1056664, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaad1e000
mprotect(0x2aaaaad20000, 1048472, PROT_NONE) = 0
mmap(0x2aaaaae1f000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x2aaaaae1f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\305\1\0"..., 640) = 640
fstat(3, {st_mode=S_IFREG|0755, st_size=1267512, ...}) = 0
mmap(NULL, 2327016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2aaaaae20000
mprotect(0x2aaaaaf3d000, 1159656, PROT_NONE) = 0
mmap(0x2aaaab03d000, 94208, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11d000) = 0x2aaaab03d000
mmap(0x2aaaab054000, 16872, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2aaaab054000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab059000
arch_prctl(ARCH_SET_FS, 0x2aaaab0596d0) = 0
munmap(0x2aaaaaac4000, 10078)           = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
open("/dev/tty", O_RDWR|O_NONBLOCK)     = 3
close(3)                                = 0
brk(0)                                  = 0x5c7000
brk(0x5c8000)                           = 0x5c8000
open("/usr/lib/locale/locale-archive", O_RDONLY) = -1 ENOENT (No such file or directory)
brk(0x5c9000)                           = 0x5c9000
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2586, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac4000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2586
brk(0x5ca000)                           = 0x5ca000
brk(0x5cb000)                           = 0x5cb000
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x2aaaaaac4000, 4096)            = 0
open("/usr/lib/locale/en_IE.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_IDENTIFICATION", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=347, ...}) = 0
mmap(NULL, 347, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac4000
close(3)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
brk(0x5cc000)                           = 0x5cc000
open("/usr/lib/gconv/gconv-modules", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=45568, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaaaac5000
read(3, "# GNU libc iconv configuration.\n"..., 4096) = 4096
brk(0x5cd000)                           = 0x5cd000
brk(0x5ce000)                           = 0x5ce000
read(3, "lias\tJS//\t\t\tJUS_I.B1.002//\nalias"..., 4096) = 4096
brk(0x5cf000)                           = 0x5cf000
brk(0x5d0000)                           = 0x5d0000
brk(0x5d1000)                           = 0x5d1000
read(3, "ule\tINTERNAL\t\tISO-8859-3//\t\tISO8"..., 4096) = 4096
brk(0x5d2000)                           = 0x5d2000
brk(0x5d3000)                           = 0x5d3000
brk(0x5d4000)                           = 0x5d4000
read(3, "lias\tISO-IR-199//\t\tISO-8859-14//"..., 4096) = 4096
brk(0x5d5000)                           = 0x5d5000
brk(0x5d6000)                           = 0x5d6000
brk(0x5d7000)                           = 0x5d7000
read(3, "\t\tto\t\t\tmodule\t\tcost\nalias\tCSEBCD"..., 4096) = 4096
brk(0x5d8000)                           = 0x5d8000
brk(0x5d9000)                           = 0x5d9000
brk(0x5da000)                           = 0x5da000
read(3, "ule\t\tcost\nalias\tCP284//\t\t\tIBM284"..., 4096) = 4096
brk(0x5db000)                           = 0x5db000
brk(0x5dc000)                           = 0x5dc000
brk(0x5dd000)                           = 0x5dd000
brk(0x5de000)                           = 0x5de000
read(3, "lias\tCP864//\t\t\tIBM864//\nalias\t86"..., 4096) = 4096
brk(0x5df000)                           = 0x5df000
brk(0x5e0000)                           = 0x5e0000
brk(0x5e1000)                           = 0x5e1000
read(3, "module\tIBM937//\t\tINTERNAL\t\tIBM93"..., 4096) = 4096
brk(0x5e2000)                           = 0x5e2000
brk(0x5e3000)                           = 0x5e3000
brk(0x5e4000)                           = 0x5e4000
brk(0x5e5000)                           = 0x5e5000
read(3, "\tEUC-JP//\nalias\tUJIS//\t\t\tEUC-JP/"..., 4096) = 4096
brk(0x5e6000)                           = 0x5e6000
brk(0x5e7000)                           = 0x5e7000
brk(0x5e8000)                           = 0x5e8000
read(3, "module\t\tcost\nalias\tISO-IR-143//\t"..., 4096) = 4096
brk(0x5e9000)                           = 0x5e9000
brk(0x5ea000)                           = 0x5ea000
brk(0x5eb000)                           = 0x5eb000
read(3, "-BOX//\nmodule\tISO_10367-BOX//\t\tI"..., 4096) = 4096
brk(0x5ec000)                           = 0x5ec000
brk(0x5ed000)                           = 0x5ed000
brk(0x5ee000)                           = 0x5ee000
read(3, "module\tINTERNAL\t\tEUC-JISX0213//\t"..., 4096) = 512
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x2aaaaaac5000, 4096)            = 0
brk(0x5ef000)                           = 0x5ef000
brk(0x5f0000)                           = 0x5f0000
open("/usr/lib/locale/en_IE.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_MEASUREMENT", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac5000
close(3)                                = 0
brk(0x5f1000)                           = 0x5f1000
open("/usr/lib/locale/en_IE.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_TELEPHONE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=50, ...}) = 0
mmap(NULL, 50, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac6000
close(3)                                = 0
brk(0x5f2000)                           = 0x5f2000
brk(0x5f3000)                           = 0x5f3000
open("/usr/lib/locale/en_IE.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_ADDRESS", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=127, ...}) = 0
mmap(NULL, 127, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac7000
close(3)                                = 0
open("/usr/lib/locale/en_IE.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_NAME", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=62, ...}) = 0
mmap(NULL, 62, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac8000
close(3)                                = 0
brk(0x5f4000)                           = 0x5f4000
open("/usr/lib/locale/en_IE.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_PAPER", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaac9000
close(3)                                = 0
open("/usr/lib/locale/en_IE.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_MESSAGES", O_RDONLY) = 3
fstat(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(3)                                = 0
open("/usr/lib/locale/en_IE.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=52, ...}) = 0
mmap(NULL, 52, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaaca000
close(3)                                = 0
brk(0x5f5000)                           = 0x5f5000
brk(0x5f6000)                           = 0x5f6000
open("/usr/lib/locale/en_IE.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_MONETARY", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=294, ...}) = 0
mmap(NULL, 294, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaacb000
close(3)                                = 0
open("/usr/lib/locale/en_IE.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_COLLATE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=880086, ...}) = 0
mmap(NULL, 880086, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaacc000
close(3)                                = 0
brk(0x5f7000)                           = 0x5f7000
open("/usr/lib/locale/en_IE.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_TIME", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2451, ...}) = 0
mmap(NULL, 2451, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaba3000
close(3)                                = 0
brk(0x5f8000)                           = 0x5f8000
open("/usr/lib/locale/en_IE.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaaaba4000
close(3)                                = 0
brk(0x5f9000)                           = 0x5f9000
open("/usr/lib/locale/en_IE.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_IE.utf8/LC_CTYPE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=208464, ...}) = 0
mmap(NULL, 208464, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2aaaab05a000
close(3)                                = 0
brk(0x5fa000)                           = 0x5fa000
getuid()                                = 0
getgid()                                = 0
geteuid()                               = 0
getegid()                               = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x5fb000)                           = 0x5fb000
open("/etc/mtab", O_RDONLY)             = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=330, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab08d000
read(3, "/dev/hda1 / ext3 rw,errors=remou"..., 4096) = 330
close(3)                                = 0
munmap(0x2aaaab08d000, 4096)            = 0
open("/proc/meminfo", O_RDONLY)         = 3
fstat(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2aaaab08d000
read(3, "MemTotal:       962648 kB\nMemFre"..., 1024) = 604
close(3)                                = 0
munmap(0x2aaaab08d000, 4096)            = 0
brk(0x5fc000)                           = 0x5fc000
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigaction(SIGQUIT, {SIG_IGN}, {SIG_DFL}, 8) = 0
uname({sys="Linux", node="chimp", ...}) = 0
brk(0x5fd000)                           = 0x5fd000
brk(0x5fe000)                           = 0x5fe000
stat("/home/timky", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
getpid()                                = 7313
brk(0x5ff000)                           = 0x5ff000
getppid()                               = 7312
brk(0x600000)                           = 0x600000
getpgrp()                               = 7312
rt_sigaction(SIGCHLD, {0x436740, [], SA_RESTORER, 0x2aaaaae4f1b0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
open("/etc/init.d/vsftpd", O_RDONLY)    = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, 0x7fffffa84690) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "#!/bin/sh\n# /etc/init.d/vsftpd\n#"..., 80) = 80
lseek(3, 0, SEEK_SET)                   = 0
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
dup2(3, 255)                            = 255
close(3)                                = 0
fcntl(255, F_SETFD, FD_CLOEXEC)         = 0
fcntl(255, F_GETFL)                     = 0x8000 (flags O_RDONLY|O_LARGEFILE)
fstat(255, {st_mode=S_IFREG|0755, st_size=1208, ...}) = 0
lseek(255, 0, SEEK_CUR)                 = 0
brk(0x601000)                           = 0x601000
brk(0x602000)                           = 0x602000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "#!/bin/sh\n# /etc/init.d/vsftpd\n#"..., 1208) = 1208
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
brk(0x603000)                           = 0x603000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat("/etc/vsftpd.conf", {st_mode=S_IFREG|0755, st_size=5772, ...}) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/local/sbin/egrep", 0x7fffffa838a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/bin/egrep", 0x7fffffa838a0) = -1 ENOENT (No such file or directory)
stat("/usr/sbin/egrep", 0x7fffffa838a0) = -1 ENOENT (No such file or directory)
stat("/usr/bin/egrep", 0x7fffffa838a0)  = -1 ENOENT (No such file or directory)
stat("/sbin/egrep", 0x7fffffa838a0)     = -1 ENOENT (No such file or directory)
stat("/bin/egrep", {st_mode=S_IFREG|0755, st_size=33, ...}) = 0
stat("/bin/egrep", {st_mode=S_IFREG|0755, st_size=33, ...}) = 0
brk(0x604000)                           = 0x604000
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -906, SEEK_CUR)              = 302
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x2aaaab059760) = 7314
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, NULL) = 7314
wait4(-1, 0x7fffffa83694, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn(0xffffffffffffffff)        = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {0x4350a0, [], SA_RESTORER, 0x2aaaaae4f1b0}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {0x4350a0, [], SA_RESTORER, 0x2aaaaae4f1b0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
exit_group(0)

```
I also went through the log files today to see every sudo command run since the box was installed, and the only other file that was edited appart from the vsftpd ones was /etc/shells and that was just so /bin/true could be added to allow people without full shell access have ftp access.

---

### Post by Mr. C. on 2007-03-25
This should not be commented out : 

> #@include common-auth

in /etc/pam.d/vsftpd.  Otherwise, account authentication is bypassed.  This is why authentication is required for ssh, but not vsftpd.

Remove your encrypted passwords from your /etc/shadow posting; that data is far more sensitive than the user names.  In fact, delete all of it.

MrC

---

### Post by -=pug=- on 2007-03-25
\o/ Thanks very much, I don't know how many times I looked at that and didn't see that line commented out. I feel a little stupid now, but at least it's working. All that's left is to figure out who did it (though I've an idea), and why I didn't see that the file was actually edited, though that's probably down to my own blindness again.

[EDIT] Though now that I look at the top post, I notice I didn't even paste in the contents of common-auth so it musn't have even registered with me, sometimes I wonder how my brain works, or that it works at all :)

---

### Post by Mr. C. on 2007-03-25
I didn't notice it right away either.  Once I saw your passwd and shadow files, and they were correct, I knew where the problem had to be.  Authentication for vsftpd, and there was only one place that was happening in your setup.

Since you'd mentioned you didn't touch pam, I didn't consider it as the possibility at first.  Someone changed it.  Now go have that talk with one of your users who has root access!

Since you've posted your encrypted passwords, you should require users to change them ASAP.  Consider them compromised.  Although it is not likely they will be cracked using that data, the entire point of /etc/shadow was to hide encrypted passwords so that brute force attacks were not as easy.

Cheers,
MrC

---

### Post by -=pug=- on 2007-03-26
Don't know if you're interested to know what happened or not, but I finally figured it out. There are only 2 other people with root on the box, and one of them was trying to figure out why users without shell access weren't able to login, he edited /etc/pam.d/vsftpd at about the same time I added /bin/true to /etc/shells, saw it was working figured he'd fixed it and then promptly forgot all about it.

The reason I didn't see anyone edited the pam.d config was because I stupidly piped my username into a grep when searching the log files for sudo, I didn't think anyone else was even looking at the box for anything other than ftp let alone editing files on it. Just goes to show you can't be too careful even with a tiny private little ftp server I guess.

All passwords are changed now, thanks for the advice they were all once off random throw away passwords anyway but better safe than sorry as I'm slowly starting to learn :)

Finally thanks again for the help it really is greatly appreciated, I have a lot of respect for people who donate their time to help others in a community spirited manner, and I'm not so sure a lot of people give the likes of yorself the respect and gratitude deserved.

---

### Post by Mr. C. on 2007-03-26
Thanks for the update.  The good news is that you were able to identify the cause, and the now-shamed guilty party.  This is a text-book example of why security audit trails are important.

Nice work.
MrC

---

