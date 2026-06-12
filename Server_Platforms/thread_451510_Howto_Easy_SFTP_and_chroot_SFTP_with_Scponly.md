---
title: "Howto: Easy SFTP and chroot SFTP with Scponly"
date: 2007-05-22
forum: Server Platforms
---

### Post by ruibernardo on 2007-05-22
Hi everyone,

I was getting some problems to get scponly installed. I've searched through the forum, but didn't found any solution. Now I got it working, so I'm posting how I got Scponly installed and working.

Scponly for transferring files securely with ssh, but the user doesn't have a shell, so he only can transfer files. He cannot execute anything in the server. 

There are 2 shells, one normal (scponly), that allows users to transfer files and see all the system files, but can't execute anything. The other one is scponlyc, the chroot version (the user is locked inside his home folder). Now here we go.

Install the scponly package in the server machine:

```
sudo apt-get install scponly
```[B] Normal SFTP
[/B]
Change the shell of the user:

```
sudo chsh -s /usr/bin/scponly username
```Test it from the remote machine:

```
sftp username@server
```Painless 8-)

**Chroot/Jail SFTP:**

Reconfigure the scponly package so that scponlyc (the chroot version) is activated:

```
sudo dpkg-reconfigure -plow scponly
```Answer "Yes". Now setup the chroot scponly user using the setup_chroot script included to do it. It can't be an existing user, and don't create him with adduser. He will be created by the setup_chroot script:

```
cd /usr/share/doc/scponly/setup_chroot
sudo gunzip setup_chroot.sh.gz
sudo chmod +x setup_chroot.sh
sudo ./setup_chroot.sh

```To make this simpler, lets accept the default answers (scponly for username and home folder). At the end, create the password of scponly user.

Scponlyc has a "bug" and don't work out of the box ([https://lists.ccs.neu.edu/pipermail/scponly/2006-December/001692.html](https://lists.ccs.neu.edu/pipermail/scponly/2006-December/001692.html)). The message is about FreeBSD, but it happens in Linux/Ubuntu too, at least with me. You have to create /dev/null in scponly chroot home folder. Thanks [to revertex]("http://ubuntuforums.org/showpost.php?p=2765654&postcount=2"), the right way to do this is:

```
sudo -i
cd /home/scponly

mkdir /home/scponly/dev 
mknod -m 666 /home/scponly/dev/null c 1 3

exit

```Now test it from the remote computer:

```
sftp scponly@server
```If you login, it worked. You only can upload files to the "incoming" folder. You can't leave scponly chroot jail, and you cannot execute anything from the server system.:D

[From cypher35]("http://ubuntuforums.org/showpost.php?p=3368113&postcount=18"): This is very useful, because, by default, only the "incoming" folder of the home folder is writeable by the user. To make the "incoming" folder the default one for the uploads in the chroot/jail, edit the file /etc/passwd and change the home folder of the user(s), and add two slashes ("[COLOR=Red]**//**[/COLOR]") and the "incoming" directory name (in the following example, the "incoming" folder is named "default"):

```
 sftpguest:x:1001:1001::/home/sftpguest[COLOR=Red]**//**[COLOR=Black]default[/COLOR][/COLOR]:/usr/sbin/scponlyc
```This was [suggested by revertex]("http://ubuntuforums.org/showpost.php?p=2796472&postcount=4"):

To provide access to files that are outside the scponly homedir root jail, bind mount option should be handy.

As example, supose you have a dir /mnt/stuff and want to provide access to a chrooted scponly user.


Code:
```
mkdir /home/scponly/stuff

mount -o bind /mnt/stuff /home/scponly/stuff

```and to make this permanent, edit your /etc/fstab and add something like

Code:

```
 /mnt/stuff   /home/scponly/stuff   none   rw,bind   0 0
```change [FONT=System]rw,bind[/FONT] to [FONT=System]ro,bind[/FONT] to read only access.

Tested in Ubuntu Feisty 7.04. I think it works on other versions with no or few changes.

I Hope this works for you to.

** Edit 1**, *June 8th, 2007. Reason: added revertex suggestion for binding dir from outside chroot dir;*
**Edit 2**, *September 16th. Reason: added cypher35 tip to set the default directory/folder for a user;*

---

### Post by revertex on 2007-06-02
Thank you a ton, i've spend a lot of time trying to figure why scponly connection close unexpected when logged.

Very nice tutorial, pretty clear and well writen, surelly deserves a place in ubuntu wiki.

i was close, but dunno why this do not worked

```
mkdir /home/scponly/dev 
mknod -m 666 /home/scponly/dev/null c 1 3
```

---

### Post by ruibernardo on 2007-06-06
Your welcome, revertex. And thank you for your suggestion for creating de /dev/null device as it should. Edited and corrected :)

---

### Post by revertex on 2007-06-06
Another tip that may sould be useful,is to mount another dir inside scponly homedir.
 
Supose you want to provide access to files that are outside the scponly homedir root jail, bind mount option should be handy.

As example, supose you have a dir /mnt/stuff and want to provide access to a chrooted scponly user.


```
mkdir /home/scponly/stuff

mount -o bind /mnt/stuff /home/scponly/stuff

``` ( jtc point me that ro option is useless here, only have use in /etc/fstab , thank you for enlightenment )

and to make this permanent, edit your /etc/fstab and add something like

```
/mnt/stuff   /home/scponly/stuff   none   rw,bind   0 0
```change rw,bind to ro,bind to read only access

Cheers!

---

### Post by jtc on 2007-06-06
Are you sure 

```
mount -o ro,bind ...
```

behave exactly the way you think it does?

---

### Post by revertex on 2007-06-07
Ops! sorry, my bad, ro does nothing as mount option, only works in /etc/fstab.

Thank's to point me my mistake. (i mean ignorance)

---

### Post by ruibernardo on 2007-06-08
> **revertex said:**
> Another tip that may sould be useful,is to mount another dir inside scponly homedir.
 
Supose you want to provide access to files that are outside the scponly homedir root jail, bind mount option should be handy.

As example, supose you have a dir /mnt/stuff and want to provide access to a chrooted scponly user.


```
mkdir /home/scponly/stuff

mount -o bind /mnt/stuff /home/scponly/stuff

``` ( jtc point me that ro option is useless here, only have use in /etc/fstab , thank you for enlightenment )

and to make this permanent, edit your /etc/fstab and add something like

```
/mnt/stuff   /home/scponly/stuff   none   rw,bind   0 0
```change rw,bind to ro,bind to read only access

Cheers!
Edited and added. Thank you both.

---

### Post by dwstevens on 2007-07-03
I was wondering if anyone could take a look at my situtation here. I'm having a bit of trouble getting the chroot setup for sftp users. Our situation is a little complicated, as you'll see below. I've followed the directions to the letter here, including the setup of /dev/null, and just can't get sftp to connect. It authenticates fine, but when it goes to setup the sftp-server it exits and shows connection closed.  I've even compiled the groups.c hack, with no luck. Any help would be greatly appreciated.

Here is dev/null in the scponly4 home directory:

root@XXXXX:/home2/scponly4# ll dev/null 
crw-rw-rw- 1 root root 1, 3 2007-07-03 11:27 dev/null

Here is the directory structure created buy setup_chroot.sh:

root@XXXXX:/home2/scponly4# tree
.
|-- bin
|   |-- chgrp
|   |-- chmod
|   |-- chown
|   |-- echo
|   |-- ln
|   |-- ls
|   |-- mkdir
|   |-- mv
|   |-- pwd
|   |-- rm
|   `-- rmdir
|-- dev
|   `-- null
|-- etc
|   `-- passwd
|-- incoming
|-- lib
|   |-- ld.so
|   |-- libacl.so.1
|   |-- libattr.so.1
|   |-- libc.so.6
|   |-- libcom_err.so.2
|   |-- libcrypt.so.1
|   |-- libdl.so.2
|   |-- libnsl.so.1
|   |-- libnss_compat-2.5.so
|   |-- libnss_compat.so.2
|   |-- libpam.so.0
|   |-- libpam_misc.so.0
|   |-- libpopt.so.0
|   |-- libpthread.so.0
|   |-- libresolv.so.2
|   |-- librt.so.1
|   |-- libselinux.so.1
|   |-- libsepol.so.1
|   `-- libutil.so.1
`-- usr
    |-- bin
    |   |-- groups
    |   |-- id
    |   |-- passwd
    |   |-- rsync
    |   `-- scp
    `-- lib
        |-- libcrypto.so.0.9.8
        |-- libgssapi_krb5.so.2
        |-- libk5crypto.so.3
        |-- libkrb5.so.3
        |-- libkrb5support.so.0
        |-- libz.so.1
        `-- sftp-server

8 directories, 44 files

Here is the /etc/passwd entry for scponly4 user:

scponly4:x:5004:5004::/home2/scponly4:/usr/sbin/scponlyc

Here is the auth log 

Jul  3 11:31:02 XXXX sshd[27302]: Accepted password for scponly4 from 10.42.84.103 port 49805 ssh2
Jul  3 11:31:02 XXXX sshd[27306]: subsystem request for sftp
Jul  3 11:31:02 XXXX scponly[27307]: running: /usr/lib/sftp-server (username: scponly4(5004), IP/port: 10.42.84.103 49805 22)
Jul  3 11:31:02 XXXX scponly[27307]: failed: /usr/lib/sftp-server with error No such file or directory(2) (username: scponly4(5004), IP/port: 10.42.84.103 49805 22)

Here's the kernel:

2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

Here's the ubuntu release from /etc/issue:

Ubuntu 7.04


I can't figure out what sftp-server can't find.  Any help would be appreciated. We are using PAM_LDAP to authenticate against an LDAP server, and our main home directory on each server is mounted over NFS. However that's why there is a /home2 directory that is local. Here is our pam conf just in case:

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    sufficient      pam_ldap.so 
auth    required        pam_unix.so nullok_secure use_first_pass

root@XXXX:/etc/pam.d# more system-auth 
#%PAM-1.0
# This file is auto-generated.
# User changes will be destroyed the next time authconfig is run.
auth        required      /lib/security/$ISA/pam_env.so
auth        sufficient    /lib/security/$ISA/pam_unix.so likeauth nullok
auth        sufficient    /lib/security/$ISA/pam_ldap.so use_first_pass
auth        required      /lib/security/$ISA/pam_deny.so

account     required      /lib/security/$ISA/pam_unix.so broken_shadow
account     sufficient    /lib/security/$ISA/pam_succeed_if.so uid < 100 quiet
account     [default=bad success=ok user_unknown=ignore] /lib/security/$ISA/pam_ldap.so
account     required      /lib/security/$ISA/pam_permit.so

password    requisite     /lib/security/$ISA/pam_cracklib.so retry=3
password    sufficient    /lib/security/$ISA/pam_unix.so nullok use_authtok md5 shadow
password    sufficient    /lib/security/$ISA/pam_ldap.so use_authtok
password    required      /lib/security/$ISA/pam_deny.so

session     required      /lib/security/$ISA/pam_limits.so
session     required      /lib/security/$ISA/pam_unix.so
session     optional      /lib/security/$ISA/pam_ldap.so

Thanks,

David

---

### Post by revertex on 2007-07-03
dumb question, is /etc/ssh/sshd_config  properly configured?

maybe you you forgot to set "AllowUsers scponly4" in /etc/ssh/sshd_config

---

### Post by dwstevens on 2007-07-03
> **revertex said:**
> dumb question, is /etc/ssh/sshd_config  properly configured?

maybe you you forgot to set "AllowUsers scponly4" in /etc/ssh/sshd_config

Thanks, I just checked, and it's set to use PAM, I am able to log in with sftp, ssh, scp with other users, but none that are chrooted.

root@XXXX:/etc/ssh# more sshd_config 
# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes

---

### Post by ruibernardo on 2007-07-04
Hi dwstevens, please check the FAQ page of the scponly web page to have more log details of what is happening to the connection.

[http://sublimation.org/scponly/wiki/index.php/FAQ#How_do_I_turn_on_logging.3F](http://sublimation.org/scponly/wiki/index.php/FAQ#How_do_I_turn_on_logging.3F)


This might help you (and us  here if you post the resulting log) to find what might be the problem.

---

### Post by govindaraju on 2007-07-12
I also have similar issues for using sftp on 64 bit AMD linux AS 4.0 with chrooted scponlyc.

Here is the setup:

[root@sgcsglxsft03 tmp]#  grep scponly /etc/passwd
scponly:x:89:12365::/home/scponly/./incoming:/usr/local/sbin/scponlyc

It can correctly expand test* to the two files present inside the incoming directly.  But while transferring it has a file not found (2) error.

Any help is greatly appreciated.

Thanks a lot in advance,
REgards
Govinda

Here is the error log (strace at the end). 

[root@sgcsglxsft03 ~]# scp -v scponly@localhost:test* .
Executing: program /usr/bin/ssh host localhost, user scponly, command scp -v -f test*
OpenSSH_3.9p1, OpenSSL 0.9.7a Feb 19 2003
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type 1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_3.9p1
debug1: match: OpenSSH_3.9p1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_3.9p1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: publickey
debug1: Offering public key: /root/.ssh/id_rsa
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
scponly@localhost's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending command: scp -v -f test*
scponly[18238]: chrooted binary in place, will chroot()
debug1: client_input_channel_req: channel 0 rtype exit-signal reply 0
scponly[18238]: 3 arguments in total.
scponly[18238]:         arg 0 is scponlyc
scponly[18238]:         arg 1 is -c
scponly[18238]:         arg 2 is scp -v -f test*
scponly[18238]: opened log at LOG_AUTHPRIV, opts 0x00000029
scponly[18238]: retrieved home directory of "/home/scponly/./incoming" for user "scponly"
scponly[18238]: chrooting to dir: "/home/scponly/./incoming"
scponly[18238]: chdiring to dir: "/"
scponly[18238]: setting uid to 89
scponly[18238]: processing request: "scp -v -f test*"
scponly[18238]: Unable to find "LOG_SFTP" in the environment
scponly[18238]: Found "USER" and setting it to "scponly"
scponly[18238]: Unable to find "SFTP_UMASK" in the environment
scponly[18238]: Unable to find "SFTP_PERMIT_CHMOD" in the environment
scponly[18238]: Unable to find "SFTP_PERMIT_CHOWN" in the environment
scponly[18238]: Unable to find "SFTP_LOG_LEVEL" in the environment
scponly[18238]: Unable to find "SFTP_LOG_FACILITY" in the environment
scponly[18238]: Environment contains "USER=scponly"
scponly[18238]: running: /usr/bin/scp -v -f test-download-file-incoming test123.txt (username: scponly(89), IP/port: ::ffff:127.0.0.1 53622 22)
scponly[18238]: failed: /usr/bin/scp -v -f test-download-file-incoming test123.txt with error No such file or directory(2) (username: scponly(89), IP/port: ::ffff:127.0.0.1 53622 22)
*** glibc detected *** free(): invalid pointer: 0x0000000000504640 ***
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.0 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status -1

---------------------------
[root@sgcsglxsft03 tmp]# strace -o /var/tmp/scponly.trace.out4 -f -ff -p 4949
Process 4949 attached - interrupt to quit
Process 22951 attached
Process 22952 attached
Process 22952 detached
Process 22955 attached
Process 22956 attached
Process 22956 detached
Process 22951 suspended
Process 22951 resumed
Process 22955 detached
Process 22951 detached
Process 4949 detached
-----------------------

close(61)                               = -1 EBADF (Bad file descriptor)
close(62)                               = -1 EBADF (Bad file descriptor)
close(63)                               = -1 EBADF (Bad file descriptor)
chdir("/home/scponly/./incoming")       = 0
stat(".ssh/rc", 0x7fbfffd4a0)           = -1 ENOENT (No such file or directory)
stat("/etc/ssh/sshrc", 0x7fbfffd4a0)    = -1 ENOENT (No such file or directory)
rt_sigaction(SIGPIPE, NULL, {SIG_IGN}, 8) = 0
rt_sigaction(SIGPIPE, {SIG_DFL}, NULL, 8) = 0
execve("/usr/local/sbin/scponlyc", ["scponlyc", "-c", "scp -v -f test*"], [/* 8 vars */]) = 0
uname({sys="Linux", node="sgcsglxsft03", ...}) = 0
brk(0)                                  = 0x506000
fcntl(0, F_GETFD)                       = 0
fcntl(1, F_GETFD)                       = 0
fcntl(2, F_GETFD)                       = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95556000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=45278, ...}) = 0
mmap(NULL, 45278, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2a95557000
close(3)                                = 0
open("/lib64/tls/libc.so.6", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\304"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1493409, ...}) = 0
mmap(0x3172f00000, 2310088, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3172f00000
mprotect(0x317302b000, 1085384, PROT_NONE) = 0
mmap(0x317312b000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12b000) = 0x317312b000
mmap(0x3173130000, 16328, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x3173130000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95563000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95564000
mprotect(0x317312b000, 8192, PROT_READ) = 0
arch_prctl(ARCH_SET_FS, 0x2a95563b00)   = 0
munmap(0x2a95557000, 45278)             = 0
brk(0)                                  = 0x506000
brk(0x527000)                           = 0x527000
open("/usr/local/etc/scponly/debuglevel", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95557000
read(3, "4\n", 4096)                    = 2
close(3)                                = 0
munmap(0x2a95557000, 4096)              = 0
socket(PF_FILE, SOCK_DGRAM, 0)          = 3
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
connect(3, {sa_family=AF_FILE, path="/dev/log"}, 16) = 0
open("/etc/localtime", O_RDONLY)        = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95557000
read(4, "TZif\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\10\0\0\0\10"..., 4096) = 171
close(4)                                = 0
munmap(0x2a95557000, 4096)              = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
getpid()                                = 22956
writev(2, [{"scponly[22956]: chrooted binary "..., 55}, {"\n", 1}], 2) = 56
sendto(3, "<86>Jul 12 16:39:20 scponly[2295"..., 75, MSG_NOSIGNAL, NULL, 0)     = 75
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: 3 arguments in t"..., 37}, {"\n", 1}], 2)     = 38
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 57, MSG_NOSIGNAL, NULL, 0)       = 57
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: \targ 0 is scponl"..., 34}, {"\n", 1}], 2)       = 35
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 54, MSG_NOSIGNAL, NULL, 0)                              = 54
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: \targ 1 is -c", 28}, {"\n", 1}], 2) = 29
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 48, MSG_NOSIGNAL, NULL, 0)  = 48
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: \targ 2 is scp -v"..., 41}, {"\n", 1}], 2) = 42
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 61, MSG_NOSIGNAL, NULL, 0)     = 61
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: opened log at LO"..., 59}, {"\n", 1}], 2) = 60
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 79, MSG_NOSIGNAL, NULL, 0)     = 79
getuid()       = 89
getuid()                              = 89
socket(PF_FILE, SOCK_STREAM, 0) = 4
fcntl(4, F_GETFL) = 0x2 (flags O_RDWR)
fcntl(4, F_SETFL, O_RDWR|O_NONBLOCK)     = 0
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = 0
poll([{fd=4, events=POLLOUT|POLLERR|POLLHUP, revents=POLLOUT}], 1, 5000) = 1
sendto(4, "\2\0\0\0\v\0\0\0\7\0\0\0passwd\0\0", 20, MSG_NOSIGNAL, NULL, 0) = 20
poll([{fd=4, events=POLLIN|POLLERR|POLLHUP, revents=POLLIN|POLLERR|POLLHUP}], 1, 5000) = 1
recvmsg(4, {msg_name(0)=NULL, msg_iov(1)=[{"passwd\0", 7}], msg_controllen=24, {cmsg_len=20, cmsg_level=SOL_SOCKET, cmsg_type=
SCM_RIGHTS, {5}}, msg_flags=0}, 0) = 7
fstat(5, {st_mode=S_IFREG|0600, st_size=217016, ...}) = 0
pread(5, "\1\0\0\0h\0\0\0J\0\0\0\1\0\0\0U\314\225F\0\0\0\0\323\0"..., 104, 0) = 104
mmap(NULL, 217016, PROT_READ, MAP_SHARED, 5, 0) = 0x2a95565000
close(5)                                = 0
close(4)                                = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: retrieved home d"..., 89}, {"\n", 1}], 2) = 90
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 109, MSG_NOSIGNAL, NULL, 0)     = 109
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[22956]: chrooting to dir"..., 60}, {"\n", 1}], 2)     = 61
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 80, MSG_NOSIGNAL, NULL, 0)       = 80
chroot("/home/scponly/./incoming") = 0
stat("/etc/localtime", 0x7fbfffe720) = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)                              = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: chdiring to dir:"..., 36}, {"\n", 1}], 2) = 37
sendto(3, "<87>Jul 12 16:39:20 scponly[2295"..., 56, MSG_NOSIGNAL, NULL, 0)     = 56
chdir("/")       = 0
getuid()                              = 89
open("/etc/localtime", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)     = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: setting uid to 8"..., 33}, {"\n", 1}], 2)       = 34
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 53, MSG_NOSIGNAL, NULL, 0)  = 53
getuid()                                = 89
setresuid(-1, 89, -1)                   = 0
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: processing reque"..., 54}], 1) = 54
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 74, MSG_NOSIGNAL, NULL, 0)  = 74
open(".", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
getdents64(4, /* 4 entries */, 4096)    = 128
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Unable to find \""..., 60}, {"\n", 1}], 2) = 61
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 80, MSG_NOSIGNAL, NULL, 0)  = 80
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Found \"USER\" and"..., 56}, {"\n", 1}], 2) = 57
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 76, MSG_NOSIGNAL, NULL, 0)  = 76
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Unable to find \""..., 62}, {"\n", 1}], 2) = 63
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 82, MSG_NOSIGNAL, NULL, 0)  = 82
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Unable to find \""..., 69}, {"\n", 1}], 2) = 70
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 89, MSG_NOSIGNAL, NULL, 0)  = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Unable to find \""..., 69}, {"\n", 1}], 2) = 70
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 89, MSG_NOSIGNAL, NULL, 0)  = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Unable to find \""..., 66}, {"\n", 1}], 2) = 67
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 86, MSG_NOSIGNAL, NULL, 0)  = 86
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Unable to find \""..., 69}, {"\n", 1}], 2) = 70
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 89, MSG_NOSIGNAL, NULL, 0)  = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: Environment cont"..., 51}, {"\n", 1}], 2) = 52
sendto(3, "<87>Jul 12 08:39:20 scponly[2295"..., 71, MSG_NOSIGNAL, NULL, 0)  = 71
getuid()                                = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: running: /usr/bi"..., 143}, {"\n", 1}], 2) = 144
sendto(3, "<86>Jul 12 08:39:20 scponly[2295"..., 163, MSG_NOSIGNAL, NULL, 0)  = 163
execve("/usr/bin/scp", ["/usr/bin/scp", "-v", "-f", "test-download-file-incoming", "test123.txt"], [/* 1 var */]) = -1 ENOENT
(No such file or directory)
getuid()                                = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[22956]: failed: /usr/bin"..., 182}, {"\n", 1}], 2) = 183
sendto(3, "<83>Jul 12 08:39:20 scponly[2295"..., 202, MSG_NOSIGNAL, NULL, 0)  = 202
open("/dev/tty", O_RDWR|O_NONBLOCK|O_NOCTTY) = -1 ENOENT (No such file or directory)
writev(2, [{"*** glibc detected *** ", 23}, {"free(): invalid pointer", 23}, {": 0x", 4}, {"0000000000504640", 16}, {" ***\n",
 5}], 5) = 71
rt_sigprocmask(SIG_UNBLOCK, [ABRT], NULL, 8) = 0
tgkill(22956, 22956, SIGABRT) = 0
--- SIGABRT (Aborted) @ 0 (0) ---

---

### Post by ruibernardo on 2007-07-12
Hi govinaraju,

> **govindaraju said:**
> 
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)


ENOENT indicates that some file or directory wasn't found. Apparently your /etc/localtime is missing inside the /home/scponly folder. Copy the one of your system:

```
sudo cp /etc/localtime /home/scponly/etc/
```

---

### Post by govindaraju on 2007-07-12
Thank you for your reply epimeteo!

I copied the /etc/localtime to the jailed /etc (/home/scponly/etc).  It did not say the error messages for the file not found for /etc/localtime any more.  That means, the chrooted directory structure worked.  But still I am not able to copy the files successfully using scp.

When I do scp scponly@localhost:/test* .  I can see the command getting translated to scp -f test* on the server side passed into scponlyc shell
----------
scponly[14983]: chrooted binary in place, will chroot()
scponly[14983]: 3 arguments in total.
scponly[14983]:         arg 0 is scponlyc
scponly[14983]:         arg 1 is -c
scponly[14983]:         arg 2 is scp -v -f /test*
---------
It can expand to the files list available on the server even (seen from the strace output).
--------
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: processing request: "scp -v -f /test*"
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Unable to find "LOG_SFTP" in the environment
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Found "USER" and setting it to "scponly"
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Unable to find "SFTP_UMASK" in the environment
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Unable to find "SFTP_PERMIT_CHMOD" in the environment
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Unable to find "SFTP_PERMIT_CHOWN" in the environment
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Unable to find "SFTP_LOG_LEVEL" in the environment
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Unable to find "SFTP_LOG_FACILITY" in the environment
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: Environment contains "USER=scponly"
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: running: /usr/bin/scp -v -f /test-download-file-incoming /test123.txt (username: scponly(89), IP/port: ::ffff:127.0.0.1 32911 22)
----------------
It is only when running the last step running "/usr/bin/scp -v -f /test-download-file-incoming /test123.txt" it fails using the scponlyc.  When the same is run using scponly shell (not the chrooted binary) it continued and copied the file.  Here the statement where it fails.
---------
Jul 13 00:31:51 sgcsglxsft03 scponly[14983]: failed: /usr/bin/scp -v -f /test-download-file-incoming /test123.txt with error No such file or directory(2) (username: scponly(89), IP/port: ::ffff:127.0.0.1 32911 22)
----------
I am not sure what the error refers too.  Whether it refers to the scp binary itself or parameter files.  
Here is how the scponlyc binary was compiled on Redhat AS 4.0 64 bit AMD.
-------
[root@sgcsglxsft03 ~]# more /home/chandrag/scponly-4.6/compile-scponlyc.sh
./configure     --enable-sftp-logging-compat \
                --enable-chrooted-binary \
                --enable-scp-compat \
                --enable-rsync-compat \
                --disable-chroot-checkdir \
                --with-sftp-server=/usr/libexec/openssh/sftp-server
make
make install
---------------
I have been trying all these with the /dev/null created under the chrooted directory as per this site.  (Than you all for that key info!)
I have tried with nscd running as well as without running nscd, both are not working.
Tried adding the root userid on /home/scponly/etc/passwd too.  Groups is present under /home/scponly/bin.

Here is the result of my chroot test for scp:
[root@sgcsglxsft03 ~]# chroot /home/scponly /usr/bin/scp
unknown user 0
[root@sgcsglxsft03 ~]# echo $?
255
[root@sgcsglxsft03 ~]#
[root@sgcsglxsft03 ~]# more /home/scponly/etc/passwd
root:x:0:0:root:/root:/bin/bash
chandrag:x:12159:12159::/home/chandrag/:/usr/local/sbin/scponlyc
scponly:x:12364:12365::/home/scponly:/usr/local/sbin/scponlyc


If you can find anything that can be tried, please let me know.  Thanks a lot in advance.
Govinda
Here is the revised strace output file after copying /etc/localtime (for reference).
-------------
close(61)                               = -1 EBADF (Bad file descriptor)
close(62)                               = -1 EBADF (Bad file descriptor)
close(63)                               = -1 EBADF (Bad file descriptor)
chdir("/home/scponly/./incoming")       = 0
stat(".ssh/rc", 0x7fbfffd4a0)           = -1 ENOENT (No such file or directory)
stat("/etc/ssh/sshrc", 0x7fbfffd4a0)    = -1 ENOENT (No such file or directory)
rt_sigaction(SIGPIPE, NULL, {SIG_IGN}, 8) = 0
rt_sigaction(SIGPIPE, {SIG_DFL}, NULL, 8) = 0
execve("/usr/local/sbin/scponlyc", ["scponlyc", "-c", "scp -v -f /test*"], [/* 8 vars */]) = 0
uname({sys="Linux", node="sgcsglxsft03", ...}) = 0
brk(0)                                  = 0x506000
fcntl(0, F_GETFD)                       = 0
fcntl(1, F_GETFD)                       = 0
fcntl(2, F_GETFD)                       = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95556000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=45278, ...}) = 0
mmap(NULL, 45278, PROT_READ, MAP_PRIVATE, 3, 0) = 0x2a95557000
close(3)                                = 0
open("/lib64/tls/libc.so.6", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\304"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1493409, ...}) = 0
mmap(0x3172f00000, 2310088, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3172f00000
mprotect(0x317302b000, 1085384, PROT_NONE) = 0
mmap(0x317312b000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12b000) = 0x317312b000
mmap(0x3173130000, 16328, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x3173130000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95563000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95564000
mprotect(0x317312b000, 8192, PROT_READ) = 0
arch_prctl(ARCH_SET_FS, 0x2a95563b00)   = 0
munmap(0x2a95557000, 45278)             = 0
brk(0)                                  = 0x506000
brk(0x527000)                           = 0x527000
open("/usr/local/etc/scponly/debuglevel", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95557000
read(3, "4\n", 4096)                    = 2
close(3)                                = 0
munmap(0x2a95557000, 4096)              = 0
socket(PF_FILE, SOCK_DGRAM, 0)          = 3
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
connect(3, {sa_family=AF_FILE, path="/dev/log"}, 16) = 0
open("/etc/localtime", O_RDONLY)        = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95557000
read(4, "TZif\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\10\0\0\0\10"..., 4096) = 171
close(4)                                = 0
munmap(0x2a95557000, 4096)              = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
getpid()                                = 14983
writev(2, [{"scponly[14983]: chrooted binary "..., 55}, {"\n", 1}], 2) = 56
sendto(3, "<86>Jul 13 08:31:51 scponly[1498"..., 75, MSG_NOSIGNAL, NULL, 0)     = 75
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: 3 arguments in t"..., 37}, {"\n", 1}], 2)     = 38
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 57, MSG_NOSIGNAL, NULL, 0)       = 57
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: \targ 0 is scponl"..., 34}, {"\n", 1}], 2)       = 35
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 54, MSG_NOSIGNAL, NULL, 0)                              = 54
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: \targ 1 is -c", 28}, {"\n", 1}], 2) = 29
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 48, MSG_NOSIGNAL, NULL, 0)  = 48
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: \targ 2 is scp -v"..., 42}, {"\n", 1}], 2) = 43
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 62, MSG_NOSIGNAL, NULL, 0)     = 62
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: opened log at LO"..., 59}, {"\n", 1}], 2) = 60
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 79, MSG_NOSIGNAL, NULL, 0)     = 79
getuid()       = 89
getuid()                              = 89
socket(PF_FILE, SOCK_STREAM, 0) = 4
fcntl(4, F_GETFL) = 0x2 (flags O_RDWR)
fcntl(4, F_SETFL, O_RDWR|O_NONBLOCK)     = 0
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110)       = -1 ENOENT (No such file or directory)
close(4) = 0
socket(PF_FILE, SOCK_STREAM, 0)  = 4
fcntl(4, F_GETFL)                       = 0x2 (flags O_RDWR)
fcntl(4, F_SETFL, O_RDWR|O_NONBLOCK)    = 0
connect(4, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=1658, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95557000
read(4, "#\n# /etc/nsswitch.conf\n#\n# An ex"..., 4096) = 1658
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x2a95557000, 4096)              = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=45278, ...}) = 0
mmap(NULL, 45278, PROT_READ, MAP_PRIVATE, 4, 0) = 0x2a95557000
close(4)                                = 0
open("/lib64/libnss_files.so.2", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\"\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0755, st_size=56902, ...}) = 0
mmap(NULL, 1094952, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x2a95565000
mprotect(0x2a9556f000, 1053992, PROT_NONE) = 0
mmap(0x2a9566f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xa000) = 0x2a9566f000
close(4)                                = 0
munmap(0x2a95557000, 45278)             = 0
open("/etc/passwd", O_RDONLY)           = 4
fcntl(4, F_GETFD)                       = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=1717, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2a95557000
read(4, "root:x:0:0:root:/root:/bin/bash\n"..., 4096) = 1717
close(4)                                = 0
munmap(0x2a95557000, 4096)              = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: retrieved home d"..., 89}, {"\n", 1}], 2) = 90
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 109, MSG_NOSIGNAL, NULL, 0)     = 109
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=171, ...}) = 0
writev(2, [{"scponly[14983]: chrooting to dir"..., 60}, {"\n", 1}], 2)     = 61
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 80, MSG_NOSIGNAL, NULL, 0)       = 80
chroot("/home/scponly/./incoming") = 0
stat("/etc/localtime", 0x7fbfffe720) = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)     = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)                              = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: chdiring to dir:"..., 36}, {"\n", 1}], 2) = 37
sendto(3, "<87>Jul 13 08:31:51 scponly[1498"..., 56, MSG_NOSIGNAL, NULL, 0)     = 56
chdir("/")       = 0
getuid()                              = 89
open("/etc/localtime", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)     = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: setting uid to 8"..., 33}, {"\n", 1}], 2) = 34
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 53, MSG_NOSIGNAL, NULL, 0)  = 53
getuid()                                = 89
setresuid(-1, 89, -1)                   = 0
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: processing reque"..., 55}], 1) = 55
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 75, MSG_NOSIGNAL, NULL, 0)  = 75
open("/", O_RDONLY|O_NONBLOCK|O_DIRECTORY) = 4
fstat(4, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
getdents64(4, /* 4 entries */, 4096)    = 128
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Unable to find \""..., 60}, {"\n", 1}], 2) = 61
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 80, MSG_NOSIGNAL, NULL, 0)  = 80
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Found \"USER\" and"..., 56}, {"\n", 1}], 2) = 57
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 76, MSG_NOSIGNAL, NULL, 0)  = 76
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Unable to find \""..., 62}, {"\n", 1}], 2) = 63
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 82, MSG_NOSIGNAL, NULL, 0)  = 82
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Unable to find \""..., 69}, {"\n", 1}], 2) = 70
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 89, MSG_NOSIGNAL, NULL, 0)  = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Unable to find \""..., 69}, {"\n", 1}], 2) = 70
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 89, MSG_NOSIGNAL, NULL, 0)  = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Unable to find \""..., 66}, {"\n", 1}], 2) = 67
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 86, MSG_NOSIGNAL, NULL, 0)  = 86
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Unable to find \""..., 69}, {"\n", 1}], 2) = 70
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 89, MSG_NOSIGNAL, NULL, 0)  = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: Environment cont"..., 51}, {"\n", 1}], 2) = 52
sendto(3, "<87>Jul 13 00:31:51 scponly[1498"..., 71, MSG_NOSIGNAL, NULL, 0)  = 71
getuid()                                = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: running: /usr/bi"..., 145}, {"\n", 1}], 2) = 146
sendto(3, "<86>Jul 13 00:31:51 scponly[1498"..., 165, MSG_NOSIGNAL, NULL, 0)  = 165
execve("/usr/bin/scp", ["/usr/bin/scp", "-v", "-f", "/test-download-file-incoming", "/test123.txt"], [/* 1 var */]) = -1 ENOE
NT (No such file or directory)
getuid()                                = 89
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/localtime", O_RDONLY)        = -1 ENOENT (No such file or directory)
writev(2, [{"scponly[14983]: failed: /usr/bin"..., 184}, {"\n", 1}], 2) = 185
sendto(3, "<83>Jul 13 00:31:51 scponly[1498"..., 204, MSG_NOSIGNAL, NULL, 0)  = 204
open("/dev/tty", O_RDWR|O_NONBLOCK|O_NOCTTY) = -1 ENOENT (No such file or directory)
writev(2, [{"*** glibc detected *** ", 23}, {"free(): invalid pointer", 23}, {": 0x", 4}, {"0000000000504640", 16}, {" ***\n"
, 5}], 5) = 71
rt_sigprocmask(SIG_UNBLOCK, [ABRT], NULL, 8) = 0
tgkill(14983, 14983, SIGABRT) = 0
--- SIGABRT (Aborted) @ 0 (0) ---

---

### Post by ruibernardo on 2007-07-13
Hi govindaraju,

I must say that I found scponly useful because:

- scponly uses SFTP with the encryption of SSH;

- it doesn't give a shell to the users;

- gives a chroot environment to the users.

I confess that I did not try to use scponly with a normal SSH server (not chrooted) working on the same computer on the default ports.

I've tried this on Ubuntu Feisty, and it worked as expected, although I did had to copy my /etc/localtime to the /home/scponly/etc/ folder. Then I could login to SSH as a normal user (not chrooted), and I could login to SFTP and transfer files to the computer (incoming folder) with the chroot scponly user.

I've "googled" for your error and found this: [https://lists.ccs.neu.edu/pipermail/scponly/2007-May/001759.html](https://lists.ccs.neu.edu/pipermail/scponly/2007-May/001759.html), which is very similar to your error. 

It states that the environment variables are set by SSH when you connect to it, so I think that those errors you got are related to this and not to scponly.

Here are the configure options used to compile scponly in Ubuntu/Debian, from the source package found in the repositories:

./configure CFLAGS='$(CFLAGS)' --host=$(DEB_HOST_GNU_TYPE) --build=$(DEUILD_GNU_TYPE) --prefix=/usr --mandir=\$${prefix}/share/man --infodir=\$${prefix}/share/info --sysconfdir=\$${prefix}/../etc --enable-scp-compat --enable-winscp-compat --enable-rsync-compat --enable-unison-compat --enable-chrooted-binary --enable-passwd-compat --enable-svn-compat PROG_USERADD=/usr/sbin/useradd

To see what options were used to compile openssh-server in Ubuntu, download the source package and look for the "rules" file in "debian" folder (apt-get source openssh-server).

Since you have compiled scponly, maybe if you compile these two packages with this options, you can get scponly to work in RH (a shoot in the dark here). :roll:

Hope this helps.

---

### Post by BarnabasDK on 2007-08-22
On BSD it seems to be a case of missing access to the /dev folders in a scponlyc chroot.

[http://www.bsdforums.org/forums/showthread.php?t=49388](http://www.bsdforums.org/forums/showthread.php?t=49388)

I must admit I have no clue why this is the case.

I have two existing jails:

1) Has old ssh libraries in it and works with last version of scponly
2) Has new ssh libraries in it and does not.

However the above fixed the issue for me.

- Nikolaj

---

### Post by ruibernardo on 2007-08-22
This seems another workaround to create the /dev environment for scponly.

Is there any equivalent to "devfs" command in linux?

---

### Post by cypher35 on 2007-09-15
I just got this working finally after some amd64 headaches...  (apparently the setup_chroot script was not designed to handle the 64bit libs)

Anyway, I was wondering if I could do one of the following:

**A)** set the user's default directory to a subdirectory within the chroot
-or-
**B)** hide all of the following directories from the scponly user (bin, dev, etc, lib, lib64, and usr).


Is there any way short of recompiling 'ls' to hide these directories from the sftp user?


**EDIT:**
actually I found a solution within the scponly wiki...  you can choose a default subdirectory within the chroot by separating it with two slashes ('//') in the passwd entry like so:
```
sftpguest:x:1001:1001::/home/sftpguest//default:/usr/sbin/scponlyc
```
(not I used a different username than the above examples, but you get the idea)

---

### Post by ruibernardo on 2007-09-16
That is very useful, cypher35. I've added this to the howto. Thank you. :D

---

### Post by MrUmunhum on 2007-10-03
I am having the same problem with scponlyc.  It starts sftp-server
but then it quits.  I got it to work after the first install but after
I added a user, it stopped work all together.

Anyone have a fix for this??

---

### Post by ruibernardo on 2007-10-03
Hi MrUmunhum,

did you run setup_chroot.sh to setup that new user? Did it stop working to all users?

---

### Post by randyrick on 2007-12-14
I'm able to get scponly installed and access the chroot'd dir as above, but am having trouble with this

```
mkdir /home/scponly/stuff

mount -o bind /mnt/stuff /home/scponly/stuff

```


After I bind mount the directory to the chroot'd user's home dir, a listing shows nothing BUT 'df' shows that it's mounted.  

What am I doing wrong?

---

### Post by riaal on 2007-12-19
I don't get it, I tested this on my lab installation and got 

"WinSCP: this is end-of-file:0" when I tried to login with ssh?
Isn't there supse to be a chrooted shell?

Thanks
/riaal

EDIT: sftp works

---

### Post by elraun on 2008-01-17
i am working in a vserver so i couldn't use the mount/bind options as shown. instead, i moved the directory i wanted the user to write to into their home dir and then created a ln -s link to it from the original location. that seems to work fine.

---

### Post by Kosmonaut on 2008-01-24
Hi freaks!

I could need some advice. I have got scponly running like it should. I have got a "jailed" ssh account...so far, so good.
Now here is my question: is it possible to add a *fusesbm folder* in that jailed home, so that my scponly-user can access to SMB-Shares?
I tried to add a fusesmb folder in the writable folder, but it didn't work, since my scponly-user seems not to have enough rights to do it. Then I have tried to mount an already existing fusesmb-drive into the writable folder (from a different user(what didn't work, obviously!)) then I tried set a link to the existing fusesmb foder (didn't work to).
As you see, I am not very familiar with all this stuff. So is it possible to get this working? Or is scponly and fusesmb not "compatible". Or are there some other ways to get this to work.

Greetings K.

---

### Post by iramhernandez on 2008-01-30
> **cypher35 said:**
> I just got this working finally after some amd64 headaches...  (apparently the setup_chroot script was not designed to handle the 64bit libs)


cypher35, can you give a bit more detail on getting this to work on a 64 bit system?  I can get it running fine except when running in chroot and I believe that this is due to the same issue you had.

---

### Post by dmonty on 2008-02-06
I was getting:
 failed: /usr/lib/sftp-server with error No such file or directory

I fixed it by copying the following libraries into my chroot

```

cd /home/dean
cp -p /lib/libncurses.so.5 lib/
cp -p /lib/libdl.so.2 lib/
cp -p /lib/libc.so.6 lib/
mkdir lib64
cp -p /lib64/ld-linux-x86-64.so.2 lib64/

```

---

### Post by acacs on 2008-02-08
I also had to setuid the scponlyc binary to use the chroot functionality.

---

### Post by hrvooje on 2008-04-06
here is my log. i can't connect . if anyone can help ... 

```


read(6, "\0\0\0\5", 4)                  = 4
read(6, "\v\0\0\0\0", 5)                = 5
write(6, "\0\0\0\5\f", 5)               = 5
write(6, "\0\0\0\0", 4)                 = 4
time(NULL)                              = 1207481590
open("/etc/localtime", O_RDONLY)        = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fa2000
read(4, "TZif\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\6\0\0\0\6\0"..., 4096) = 696
close(4)                                = 0
munmap(0xb7fa2000, 4096)                = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
socket(PF_FILE, SOCK_DGRAM, 0)          = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
connect(4, {sa_family=AF_FILE, path="/dev/log"}, 110) = 0
send(4, "<38>Apr  6 13:33:10 sshd[460]: F"..., 90, MSG_NOSIGNAL) = 90
close(4)                                = 0
read(6, "\0\0\0\v", 4)                  = 4
read(6, "\v\0\0\0\6upload", 11)         = 11
time(NULL)                              = 1207481593
getuid32()                              = 0
open("/etc/passwd", O_RDONLY)           = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
_llseek(4, 0, [0], SEEK_CUR)            = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=1872, ...}) = 0
mmap2(NULL, 1872, PROT_READ, MAP_SHARED, 4, 0) = 0xb7fa2000
_llseek(4, 1872, [1872], SEEK_SET)      = 0
munmap(0xb7fa2000, 1872)                = 0
close(4)                                = 0
open("/etc/shadow", O_RDONLY)           = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
_llseek(4, 0, [0], SEEK_CUR)            = 0
fstat64(4, {st_mode=S_IFREG|0640, st_size=1226, ...}) = 0
mmap2(NULL, 1226, PROT_READ, MAP_SHARED, 4, 0) = 0xb7fa2000
_llseek(4, 1226, [1226], SEEK_SET)      = 0
munmap(0xb7fa2000, 1226)                = 0
close(4)                                = 0
write(6, "\0\0\0\5\f", 5)               = 5
write(6, "\0\0\0\1", 4)                 = 4
read(6, "\0\0\0\1", 4)                  = 4
read(6, "1", 1)                         = 1
open("/etc/nologin", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
getuid32()                              = 0
open("/etc/passwd", O_RDONLY)           = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
_llseek(4, 0, [0], SEEK_CUR)            = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=1872, ...}) = 0
mmap2(NULL, 1872, PROT_READ, MAP_SHARED, 4, 0) = 0xb7fa2000
_llseek(4, 1872, [1872], SEEK_SET)      = 0
munmap(0xb7fa2000, 1872)                = 0
close(4)                                = 0
open("/etc/shadow", O_RDONLY)           = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
_llseek(4, 0, [0], SEEK_CUR)            = 0
fstat64(4, {st_mode=S_IFREG|0640, st_size=1226, ...}) = 0
mmap2(NULL, 1226, PROT_READ, MAP_SHARED, 4, 0) = 0xb7fa2000
_llseek(4, 1226, [1226], SEEK_SET)      = 0
munmap(0xb7fa2000, 1226)                = 0
close(4)                                = 0
time(NULL)                              = 1207481593
write(6, "\0\0\0\t2", 5)                = 5
write(6, "\0\0\0\1\0\0\0\0", 8)         = 8
--- SIGCHLD (Child exited) @ 0 (0) ---
time(NULL)                              = 1207481593
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=696, ...}) = 0
socket(PF_FILE, SOCK_DGRAM, 0)          = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
connect(4, {sa_family=AF_FILE, path="/dev/log"}, 110) = 0
send(4, "<38>Apr  6 13:33:13 sshd[460]: A"..., 92, MSG_NOSIGNAL) = 92
close(4)                                = 0
read(6, "\0\0\5\4", 4)                  = 4
read(6, "\31\0\0\0 \2 \30R2\306H\375B\223n\334\302>\317\215\230"..., 1284) = 1284
close(6)                                = 0
mmap2(NULL, 1310720, PROT_READ|PROT_WRITE, MAP_SHARED|MAP_ANONYMOUS, -1, 0) = 0xb786f000
munmap(0xb7b1c000, 65536)               = 0
waitpid(461, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0) = 461
alarm(0)                                = 5
rt_sigaction(SIGALRM, NULL, {0x80008300, [], SA_INTERRUPT}, 8) = 0
rt_sigaction(SIGALRM, {SIG_DFL}, NULL, 8) = 0
close(5)                                = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [4, 5]) = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7b4a6f8) = 469
close(4)                                = 0
rt_sigaction(SIGHUP, NULL, {SIG_DFL}, 8)                  = 0
rt_sigaction(SIGHUP, {0x80020110, [], 0}, NULL, 8)                   = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {0x80020110, [], 0}, NULL, 8)                        = 0
read(5, "\0\0\0\1", 4)   = 4
read(5, "=", 1)                         = 1
waitpid(469, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0) = 469
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(0)  


```

---

### Post by ifoam on 2008-06-23
[COLOR="Silver"]I've got this working correctly. But I need a little help adding new users.

i need two users. I have one called user1 with a home of /home/user1


i need another user (user2) that can log in (chrooted) to /home/user1 and access the same files. when I try to add another user, the user can't log in.

any ideas?[/COLOR]


I got it! Thanks!

---

### Post by daniel.harvey on 2008-07-05
Thanks. This is needed for Hardy 64 bit.

> **dmonty said:**
> I was getting:
 failed: /usr/lib/sftp-server with error No such file or directory

I fixed it by copying the following libraries into my chroot

```

cd /home/dean
cp -p /lib/libncurses.so.5 lib/
cp -p /lib/libdl.so.2 lib/
cp -p /lib/libc.so.6 lib/
mkdir lib64
cp -p /lib64/ld-linux-x86-64.so.2 lib64/

```

---

### Post by gertvdijk on 2008-07-07
> **cypher35 said:**
> 
actually I found a solution within the scponly wiki...  you can choose a default subdirectory within the chroot by separating it with two slashes ('//') in the passwd entry like so:
```
sftpguest:x:1001:1001::/home/sftpguest//default:/usr/sbin/scponlyc
```
(not I used a different username than the above examples, but you get the idea)
This is great and exactly what I'm looking for. :)
Except... It's not working. SSH (sshd) will always fail the authentication when logging in if using the double slash method. Using without a default chdir is working like a charm.

I'm using a dsa keypair to authenticate and the following setup:
*connecting from*: Debian Etch, 32-bit, kernel 2.6.9-023stab044.11-entnosplit on a VPS*(Virtuozzo), openssh-client Version: 1:4.3p2-9etch2
*connecting to*: Ubuntu Hardy, 64-bit, stock kernel, latest updates.

---

