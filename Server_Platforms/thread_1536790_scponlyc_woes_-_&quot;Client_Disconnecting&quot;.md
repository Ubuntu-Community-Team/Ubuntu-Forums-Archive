---
title: "scponlyc woes - &quot;Client Disconnecting&quot;"
date: 2010-07-22
forum: Server Platforms
---

### Post by TrevorBradley on 2010-07-22
Hey everyone.. I'm trying to set up a chrooted sftp account using scponly.  I'm really close to having the problem cracked, but I'm hitting some kind of wall.

I've been following the instructions posted here:
[http://ubuntuforums.org/showthread.php?t=451510](http://ubuntuforums.org/showthread.php?t=451510)

Which seem to be pretty thorough and complete.  Everything seems to go OK.  However when I attempt to connect I get disconnected immediately.

Now I know the common problem with this symptom is that /dev/null isn't set up correctly in the chroot jail, but as far as I could tell /usr/share/doc/scponly/setup_chroot set it up correctly.  I even tried copying /dev/null manually, but no change.

Another weird thing.  If I set my debuglevel to "2", I get no scponly log output.  If I set it to 1, I do get output to auth.log, but it's very unhelpful:

```
==> auth.log <==
Jul 22 14:18:58 pergamon sshd[20261]: Accepted password for xxxxxx from ::1 port 53239 ssh2
Jul 22 14:18:58 pergamon sshd[20261]: pam_unix(sshd:session): session opened for user xxxxxx by (uid=0)
Jul 22 14:18:59 pergamon sshd[20365]: subsystem request for sftp
Jul 22 14:18:59 pergamon scponly[20366]: chrooted binary in place, will chroot()
Jul 22 14:18:59 pergamon scponly[20366]: 3 arguments in total.
Jul 22 14:18:59 pergamon scponly[20366]: #011arg 0 is scponlyc
Jul 22 14:18:59 pergamon scponly[20366]: #011arg 1 is -c
Jul 22 14:18:59 pergamon scponly[20366]: #011arg 2 is /usr/lib/openssh/sftp-server
Jul 22 14:18:59 pergamon scponly[20366]: opened log at LOG_AUTHPRIV, opts 0x00000009
Jul 22 14:18:59 pergamon scponly[20366]: determined USER is "xxxxxx" from environment
Jul 22 14:18:59 pergamon scponly[20366]: retrieved home directory of "/home/xxxxxx" for user "xxxxxx"
Jul 22 14:18:59 pergamon scponly[20366]: chrooting to dir: "/home/xxxxxx"
Jul 22 14:18:59 pergamon scponly[20366]: chdiring to dir: "/"
Jul 22 14:18:59 pergamon scponly[20366]: setting uid to 1007
Jul 22 14:18:59 pergamon scponly[20366]: processing request: "/usr/lib/openssh/sftp-server"
Jul 22 14:18:59 pergamon scponly[20366]: Using getopt processing for cmd /usr/lib/sftp-server#012 (username: xxxxxx(1007), IP/port: ::1 53239 22)
Jul 22 14:18:59 pergamon scponly[20366]: running: /usr/lib/sftp-server (username: xxxxxx(1007), IP/port: ::1 53239 22)
Jul 22 14:18:59 pergamon scponly[20366]: about to exec "/usr/lib/sftp-server" (username: xxxxxx(1007), IP/port: ::1 53239 22)
Jul 22 14:18:59 pergamon sshd[20365]: Received disconnect from ::1: 11: disconnected by user
Jul 22 14:18:59 pergamon sshd[20261]: pam_unix(sshd:session): session closed for user xxxxxx



```

Filezilla doesn't give the "Received disconnect" error, but both Filezilla and sftp connect properly and then immediately disconnect.

A listing of my jail:

```
$ ls -R
.:
bin  dev  etc  incoming  lib  usr

./bin:
chgrp  chmod  chown  echo  ln  ls  mkdir  mv  pwd  rm  rmdir

./dev:
null

./etc:
group  passwd

./incoming:

./lib:
ld-linux.so.2  libattr.so.1             libnss_compat.so.2  libpam.so.0      tls
libacl.so.1    libnss_compat-2.11.1.so  libpam_misc.so.0    libselinux.so.1

./lib/tls:
i686

./lib/tls/i686:
cmov

./lib/tls/i686/cmov:
libcrypt.so.1  libc.so.6  libdl.so.2  libpthread.so.0  librt.so.1

./usr:
bin  lib

./usr/bin:
groups  id  passwd  scp

./usr/lib:
sftp-server
```

Any help would be fantastic, thanks...

---

### Post by endeavor_ on 2010-07-30
I'm having the same issue. Any luck with a solution, Trevor?

This is on Ubuntu 10.04.1 LTS x86_64, fully up to date.

---

### Post by TrevorBradley on 2010-07-30
No Luck, sorry.

---

### Post by chasd00 on 2010-08-18
I had this exact issue, the problem was the setup_chroot.sh script does not copy file /lib/libnss_files.so.2 to the chroot lib directory.

Do this and you should be good to go.
cp /lib/libnss_files* -av <the_chrootdir>/lib

---

### Post by endeavor_ on 2010-08-18
> **chasd00 said:**
> I had this exact issue, the problem was the setup_chroot.sh script does not copy file /lib/libnss_files.so.2 to the chroot lib directory.

Do this and you should be good to go.
cp /lib/libnss_files* -av <the_chrootdir>/lib

That did the trick. Thanks chasd!

---

### Post by RainyCity on 2010-12-14
> **chasd00 said:**
> I had this exact issue, the problem was the setup_chroot.sh script does not copy file /lib/libnss_files.so.2 to the chroot lib directory.

Do this and you should be good to go.
cp /lib/libnss_files* -av <the_chrootdir>/lib


This was exactly the problem on my 10.04 system. Thanks for the tip.

---

### Post by sunta on 2011-06-17
> **chasd00 said:**
> I had this exact issue, the problem was the setup_chroot.sh script does not copy file /lib/libnss_files.so.2 to the chroot lib directory.

Do this and you should be good to go.
cp /lib/libnss_files* -av <the_chrootdir>/lib

tried that without any improvment :(

my auth.log:
Jun 17 14:39:44 dns sshd[6278]: debug1: Forked child 6296.
Jun 17 14:39:44 dns sshd[6296]: debug1: rexec start in 5 out 5 newsock 5 pipe 7 sock 8
Jun 17 14:39:44 dns sshd[6296]: debug1: inetd sockets after dupping: 3, 3
Jun 17 14:39:44 dns sshd[6296]: Connection from xxx port 51888
Jun 17 14:39:44 dns sshd[6296]: debug1: Client protocol version 2.0; client software version OpenSSH_5.8p1 Debian-1ubuntu3
Jun 17 14:39:44 dns sshd[6296]: debug1: match: OpenSSH_5.8p1 Debian-1ubuntu3 pat OpenSSH*
Jun 17 14:39:44 dns sshd[6296]: debug1: Enabling compatibility mode for protocol 2.0
Jun 17 14:39:44 dns sshd[6296]: debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu6
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: initializing for "scponly"
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: setting PAM_RHOST to "xxx"
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: setting PAM_TTY to "ssh"
Jun 17 14:39:44 dns sshd[6296]: Failed none for scponly from xxx port 51888 ssh2
Jun 17 14:39:44 dns sshd[6296]: debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
Jun 17 14:39:44 dns sshd[6296]: debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
Jun 17 14:39:44 dns sshd[6296]: debug1: temporarily_use_uid: 1005/1005 (e=0/0)
Jun 17 14:39:44 dns sshd[6296]: debug1: trying public key file /home/scponly/.ssh/authorized_keys
Jun 17 14:39:44 dns sshd[6296]: debug1: restore_uid: 0/0
Jun 17 14:39:44 dns sshd[6296]: debug1: temporarily_use_uid: 1005/1005 (e=0/0)
Jun 17 14:39:44 dns sshd[6296]: debug1: trying public key file /home/scponly/.ssh/authorized_keys2
Jun 17 14:39:44 dns sshd[6296]: debug1: restore_uid: 0/0
Jun 17 14:39:44 dns sshd[6296]: Failed publickey for scponly from xxx port 51888 ssh2
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: password authentication accepted for scponly
Jun 17 14:39:44 dns sshd[6296]: debug1: do_pam_account: called
Jun 17 14:39:44 dns sshd[6296]: Accepted password for scponly from xxx port 51888 ssh2
Jun 17 14:39:44 dns sshd[6296]: debug1: monitor_child_preauth: scponly has been authenticated by privileged process
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: establishing credentials
Jun 17 14:39:44 dns sshd[6296]: pam_unix(sshd:session): session opened for user scponly by (uid=0)
Jun 17 14:39:44 dns sshd[6296]: User child is on pid 6374
Jun 17 14:39:44 dns sshd[6374]: debug1: SELinux support disabled
Jun 17 14:39:44 dns sshd[6374]: debug1: PAM: establishing credentials
Jun 17 14:39:44 dns sshd[6374]: debug1: permanently_set_uid: 1005/1005
Jun 17 14:39:44 dns sshd[6374]: debug1: Entering interactive session for SSH2.
Jun 17 14:39:44 dns sshd[6374]: debug1: server_init_dispatch_20
Jun 17 14:39:44 dns sshd[6374]: debug1: server_input_channel_open: ctype session rchan 0 win 2097152 max 32768
Jun 17 14:39:44 dns sshd[6374]: debug1: input_session_request
Jun 17 14:39:44 dns sshd[6374]: debug1: channel 0: new [server-session]
Jun 17 14:39:44 dns sshd[6374]: debug1: session_new: session 0
Jun 17 14:39:44 dns sshd[6374]: debug1: session_open: channel 0
Jun 17 14:39:44 dns sshd[6374]: debug1: session_open: session 0: link with channel 0
Jun 17 14:39:44 dns sshd[6374]: debug1: server_input_channel_open: confirm session
Jun 17 14:39:44 dns sshd[6374]: debug1: server_input_global_request: rtype [email]no-more-sessions@openssh.com[/email] want_reply 0
Jun 17 14:39:44 dns sshd[6374]: debug1: server_input_channel_req: channel 0 request env reply 0
Jun 17 14:39:44 dns sshd[6374]: debug1: session_by_channel: session 0 channel 0
Jun 17 14:39:44 dns sshd[6374]: debug1: session_input_channel_req: session 0 req env
Jun 17 14:39:44 dns sshd[6374]: debug1: server_input_channel_req: channel 0 request subsystem reply 1
Jun 17 14:39:44 dns sshd[6374]: debug1: session_by_channel: session 0 channel 0
Jun 17 14:39:44 dns sshd[6374]: debug1: session_input_channel_req: session 0 req subsystem
Jun 17 14:39:44 dns sshd[6374]: subsystem request for sftp
Jun 17 14:39:44 dns sshd[6374]: debug1: subsystem: exec() /usr/lib/openssh/sftp-server
Jun 17 14:39:44 dns sshd[6374]: debug1: Received SIGCHLD.
Jun 17 14:39:44 dns sshd[6374]: debug1: session_by_pid: pid 6375
Jun 17 14:39:44 dns sshd[6374]: debug1: session_exit_message: session 0 channel 0 pid 6375
Jun 17 14:39:44 dns sshd[6374]: debug1: session_exit_message: release channel 0
Jun 17 14:39:44 dns sshd[6374]: Received disconnect from xxx: 11: disconnected by user
Jun 17 14:39:44 dns sshd[6374]: debug1: do_cleanup
Jun 17 14:39:44 dns sshd[6296]: debug1: do_cleanup
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: cleanup
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: closing session
Jun 17 14:39:44 dns sshd[6296]: pam_unix(sshd:session): session closed for user scponly
Jun 17 14:39:44 dns sshd[6296]: debug1: PAM: deleting credentials



ls -alR /home/scponly/
/home/scponly/:
total 4
drwxr-xr-x  9 root    root      83 2011-06-17 14:35 .
drwxr-xr-x 10 root    root     120 2011-06-17 14:16 ..
drwxr-xr-x  2 root    root     123 2011-06-17 14:35 bin
drwxr-xr-x  2 root    root      17 2011-06-17 14:35 dev
drwxr-xr-x  2 root    root      31 2011-06-17 14:35 etc
drwxr-xr-x  2 scponly scponly    6 2011-06-17 14:35 incoming
drwxr-xr-x  2 root    root    4096 2011-06-17 14:36 lib
drwxr-xr-x  2 root    root      33 2011-06-17 14:35 lib64
drwxr-xr-x  4 root    root      26 2011-06-17 14:35 usr

/home/scponly/bin:
total 680
drwxr-xr-x 2 root root    123 2011-06-17 14:35 .
drwxr-xr-x 9 root root     83 2011-06-17 14:35 ..
-rwxr-xr-x 1 root root  64128 2011-06-17 14:35 chgrp
-rwxr-xr-x 1 root root  60000 2011-06-17 14:35 chmod
-rwxr-xr-x 1 root root  64144 2011-06-17 14:35 chown
-rwxr-xr-x 1 root root  39328 2011-06-17 14:35 echo
-rwxr-xr-x 1 root root  55912 2011-06-17 14:35 ln
-rwxr-xr-x 1 root root 114032 2011-06-17 14:35 ls
-rwxr-xr-x 1 root root  43600 2011-06-17 14:35 mkdir
-rwxr-xr-x 1 root root  97352 2011-06-17 14:35 mv
-rwxr-xr-x 1 root root  39472 2011-06-17 14:35 pwd
-rwxr-xr-x 1 root root  64208 2011-06-17 14:35 rm
-rwxr-xr-x 1 root root  39392 2011-06-17 14:35 rmdir

/home/scponly/dev:
total 0
drwxr-xr-x 2 root root   17 2011-06-17 14:35 .
drwxr-xr-x 9 root root   83 2011-06-17 14:35 ..
crw-rw-rw- 1 root root 1, 3 2011-06-17 14:35 null

/home/scponly/etc:
total 8
drwxr-xr-x 2 root root  31 2011-06-17 14:35 .
drwxr-xr-x 9 root root  83 2011-06-17 14:35 ..
-rw-r--r-- 1 root root 881 2011-06-17 14:35 group
-rw-r--r-- 1 root root  54 2011-06-17 14:35 passwd

/home/scponly/incoming:
total 0
drwxr-xr-x 2 scponly scponly  6 2011-06-17 14:35 .
drwxr-xr-x 9 root    root    83 2011-06-17 14:35 ..

/home/scponly/lib:
total 2296
drwxr-xr-x 2 root root    4096 2011-06-17 14:36 .
drwxr-xr-x 9 root root      83 2011-06-17 14:35 ..
-rwxr-xr-x 1 root root  118060 2011-06-17 14:35 ld-linux.so.2
-rwxr-xr-x 1 root root   31208 2011-06-17 14:35 libacl.so.1
-rwxr-xr-x 1 root root   18704 2011-06-17 14:35 libattr.so.1
-rwxr-xr-x 1 root root   43296 2011-06-17 14:35 libcrypt.so.1
-rwxr-xr-x 1 root root 1572232 2011-06-17 14:35 libc.so.6
-rwxr-xr-x 1 root root   14696 2011-06-17 14:35 libdl.so.2
-rwxr-xr-x 1 root root   35712 2011-06-17 14:35 libnss_compat-2.11.1.so
-rwxr-xr-x 1 root root   35712 2011-06-17 14:35 libnss_compat.so.2
-rw-r--r-- 1 root root   51712 2011-06-17 14:36 libnss_files-2.11.1.so
-rw-r--r-- 1 root root   51712 2011-06-17 14:36 libnss_files.so.2
-rwxr-xr-x 1 root root   14576 2011-06-17 14:35 libpam_misc.so.0
-rwxr-xr-x 1 root root   51776 2011-06-17 14:35 libpam.so.0
-rwxr-xr-x 1 root root  135745 2011-06-17 14:35 libpthread.so.0
-rwxr-xr-x 1 root root   31744 2011-06-17 14:35 librt.so.1
-rwxr-xr-x 1 root root  117592 2011-06-17 14:35 libselinux.so.1

/home/scponly/lib64:
total 136
drwxr-xr-x 2 root root     33 2011-06-17 14:35 .
drwxr-xr-x 9 root root     83 2011-06-17 14:35 ..
-rwxr-xr-x 1 root root 136936 2011-06-17 14:35 ld-linux-x86-64.so.2

/home/scponly/usr:
total 0
drwxr-xr-x 4 root root 26 2011-06-17 14:35 .
drwxr-xr-x 9 root root 83 2011-06-17 14:35 ..
drwxr-xr-x 2 root root 51 2011-06-17 14:35 bin
drwxr-xr-x 2 root root 24 2011-06-17 14:35 lib

/home/scponly/usr/bin:
total 184
drwxr-xr-x 2 root root    51 2011-06-17 14:35 .
drwxr-xr-x 4 root root    26 2011-06-17 14:35 ..
-rwxr-xr-x 1 root root 39392 2011-06-17 14:35 groups
-rwxr-xr-x 1 root root 39440 2011-06-17 14:35 id
-rwxr-xr-x 1 root root 42856 2011-06-17 14:35 passwd
-rwxr-xr-x 1 root root 59528 2011-06-17 14:35 scp

/home/scponly/usr/lib:
total 56
drwxr-xr-x 2 root root    24 2011-06-17 14:35 .
drwxr-xr-x 4 root root    26 2011-06-17 14:35 ..
-rwxr-xr-x 1 root root 55424 2011-06-17 14:35 sftp-server




any ideas?

---

### Post by btindie on 2011-07-25
I'm running a Natty server and have exactly the same problem. I found that by doing as **chasd00** suggested fixed the problem, though the files are in a different directory.

For others with the same problem I used the following command to fix it:
```
sudo cp -av /lib/i386-linux-gnu/libnss_files* /home/scponly/lib/i386-linux-gnu/
```

---

### Post by kevinthecomputerguy on 2011-07-26
[http://woodel.com/domore](http://woodel.com/domore)

---

