---
title: "rssh sftp/scp only chrooted account, lost no helpful errors"
date: 2011-11-02
forum: Server Platforms
---

### Post by egandt on 2011-11-02
Ok, so I started by creating a directory:
/home/android and a user android and a group by the same name and setting permissions for the directory

Next I ad the following line to rssh.conf in /etc
   user=android:077:000110:/home/android

Then I copied the file mkchroot.sh into /home/android and ran it, all looks fine now if I do an ls -lR


```
ls -lR
.:
total 28
drwxr-xr-x 2 root root 4096 Nov  2 19:44 dev
drwxr-xr-x 3 root root 4096 Nov  2 19:45 etc
drwxr-xr-x 2 root root 4096 Nov  2 19:44 lib
drwxr-xr-x 2 root root 4096 Nov  2 19:44 lib64
-rwxr-xr-x 1 root root 6479 Nov  2 19:39 mkchroot.sh
drwxr-xr-x 4 root root 4096 Nov  2 19:44 usr

./dev:
total 0
srw-rw-rw- 1 root root    0 Sep  5 16:50 log
crw-rw-rw- 1 root root 1, 3 May 31 14:20 null
crw-rw-rw- 1 root root 1, 5 May 31 14:20 zero

./etc:
total 56
-rw-r--r-- 1 root root    16 Nov  2 19:45 group
-rw-r--r-- 1 root root 34014 Nov  2 19:44 ld.so.cache
-rw-r--r-- 1 root root    34 Nov  2 19:44 ld.so.conf
drwxr-xr-x 2 root root  4096 Nov  2 19:44 ld.so.conf.d
-rw-r--r-- 1 root root   475 Nov  2 19:44 nsswitch.conf
-rw-r--r-- 1 root root    49 Nov  2 19:45 passwd

./etc/ld.so.conf.d:
total 8
-rw-r--r-- 1 root root 44 Nov  2 19:44 libc.conf
-rw-r--r-- 1 root root 68 Nov  2 19:44 x86_64-linux-gnu.conf

./lib:
total 1484
-rwxr-xr-x 1 root root 1432968 Nov  2 19:44 libc.so.6
-rw-r--r-- 1 root root   31616 Jan 23  2011 libnss_compat-2.11.2.so
lrwxrwxrwx 1 root root      23 Nov  2 19:44 libnss_compat.so.2 -> libnss_compat-2.11.2.so
-rw-r--r-- 1 root root   47616 Jan 23  2011 libnss_files-2.11.2.so
lrwxrwxrwx 1 root root      22 Nov  2 19:44 libnss_files.so.2 -> libnss_files-2.11.2.so

./lib64:
total 132
-rwxr-xr-x 1 root root 128744 Nov  2 19:44 ld-linux-x86-64.so.2

./usr:
total 8
drwxr-xr-x 2 root root 4096 Nov  2 19:44 bin
drwxr-xr-x 4 root root 4096 Nov  2 19:44 lib

./usr/bin:
total 92
-rwxr-xr-x 1 root root 25600 Nov  2 19:44 rssh
-rwxr-xr-x 1 root root 59448 Nov  2 19:44 scp

./usr/lib:
total 8
drwxr-xr-x 2 root root 4096 Nov  2 19:44 openssh
drwxr-xr-x 2 root root 4096 Nov  2 19:44 rssh

./usr/lib/openssh:
total 64
-rwxr-xr-x 1 root root 59432 Nov  2 19:44 sftp-server

./usr/lib/rssh:
total 28
-rwxr-xr-x 1 root root 24904 Nov  2 19:44 rssh_chroot_helper

```

So the files are fine, I also added etc/group manually as it was recommended


So now I try to login to it sftp -v android@localhost
```
sftp -v android@localhost
OpenSSH_5.5p1 Debian-6+squeeze1, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-6+squeeze1
debug1: match: OpenSSH_5.5p1 Debian-6+squeeze1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.5p1 Debian-6+squeeze1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
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
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/id_rsa
debug1: Trying private key: /root/.ssh/id_dsa
debug1: Next authentication method: password
android@localhost's password: 
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending subsystem: sftp
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
Transferred: sent 1528, received 1704 bytes, in 0.1 seconds
Bytes per second: sent 18571.7, received 20710.8
debug1: Exit status 1
Connection closed

```

So obviously something is missing now I did  add the entry 
SYSLOGD="-a /home/android/dev/log" as well.

but in the /var/log directory I only see:
auth.log
```
Nov  2 19:57:16 XXX sshd[9424]: Accepted password for android from 127.0.0.1 port 42730 ssh2
Nov  2 19:57:16 XXX sshd[9424]: pam_unix(sshd:session): session opened for user android by (uid=0)
Nov  2 19:57:16 XXX sshd[9426]: subsystem request for sftp
Nov  2 19:57:17 XXX sshd[9426]: Received disconnect from 127.0.0.1: 11: disconnected by user
Nov  2 19:57:17 XXX sshd[9424]: pam_unix(sshd:session): session closed for user android

```


deamon.log:
```
Nov  2 19:57:17 mughi rssh[9427]: setting log facility to LOG_USER

```

debug:
```
Nov  2 19:57:17 mughi rssh[9427]: setting log facility to LOG_USER
Nov  2 19:57:17 XXX rssh[9427]: setting umask to 022
Nov  2 19:57:17 XXX rssh[9427]: line 30: configuring user android
Nov  2 19:57:17 XXX rssh[9427]: setting android's umask to 077
Nov  2 19:57:17 XXX rssh[9427]: allowing scp to user android
Nov  2 19:57:17 XXX rssh[9427]: allowing sftp to user android
Nov  2 19:57:17 XXX rssh[9427]: chrooting android to /home/android

```

messages:
```
Nov  2 19:57:17 XXX rssh[9427]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"
Nov  2 19:57:17 XXX rssh_chroot_helper[9427]: new session for android, UID=1001

```

syslog:
```

Nov  2 19:57:17 mughi rssh_chroot_helper[9427]: new session for android, UID=1001
Nov  2 19:57:17 mughi rssh_chroot_helper[9427]: chroot() failed, 2: Operation not permitted

```


None of these explain why well I can not login via SFTP to as this user, the problem is the chroot as without it all is fine, but then security is worthless so that is not an option.  I really thought this would be easy, but I've tried from scratch 3 times now over the last 2 hours and never gotten any further than this.  


Lastly I tried ruuning "dpkg-reconnfigure rssh" and set the setuid on /usr/lib/rssh/rssh_chroot_helper, which then get me a little further:

syslogd is now:
```

Nov  2 20:18:28 XXX rssh_chroot_helper[9694]: user's home dir is /home/android
Nov  2 20:18:28 XXX rssh[9694]: setting log facility to LOG_USER
Nov  2 20:18:28 XXX rssh_chroot_helper[9694]: couldn't find /home/android in chroot jail
Nov  2 20:18:28 XXX rssh[9694]: setting umask to 022
Nov  2 20:18:28 XXX rssh_chroot_helper[9694]: chrooted to /home/android
Nov  2 20:18:28 XXX rssh[9694]: line 30: configuring user android
Nov  2 20:18:28 XXX rssh_chroot_helper[9694]: changing working directory to / (inside jail)
Nov  2 20:18:28 XXX rssh[9694]: setting android's umask to 077
Nov  2 20:18:28 XXX rssh[9694]: allowing scp to user android
Nov  2 20:18:28 XXX rssh[9694]: allowing sftp to user android
Nov  2 20:18:28 XXX rssh[9694]: chrooting android to /home/android
Nov  2 20:18:28 XXX rssh[9694]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"

```


What am I doing wrong, how can I get some actually useful error messages?   Since what I'm getting does not explain what is wrong or hint at how to fix it.  Finally the message "rssh_chroot_helper[9694]: couldn't find /home/android in chroot jail" makes perfect sense as it is already chrooted, but then why is it trying again, I do not think this is a critical issue, but ....

Thanks,
ERIC

---

### Post by egandt on 2011-11-02
After another hour of beating my head into a wall running strace on the executables and the like I'm down to teh following error, which I think is meaningful:


SFTP:
```

Nov  2 21:39:53 XXX rssh_chroot_helper[11287]: new session for android, UID=1001
Nov  2 21:39:54 XXX rssh_chroot_helper[11287]: user's home dir is /home/android
Nov  2 21:39:54 XXX rssh[11287]: setting log facility to LOG_USER
Nov  2 21:39:54 XXX rssh_chroot_helper[11287]: couldn't find /home/android in chroot jail
Nov  2 21:39:54 XXX rssh[11287]: setting umask to 022
Nov  2 21:39:54 XXX rssh_chroot_helper[11287]: chrooted to /home/android
Nov  2 21:39:54 XXX rssh[11287]: line 30: configuring user android
Nov  2 21:39:54 XXX rssh_chroot_helper[11287]: changing working directory to / (inside jail)
Nov  2 21:39:54 XXX rssh[11287]: setting android's umask to 077
Nov  2 21:39:54 XXX rssh_chroot_helper[11287]: execv() failed, /usr/lib/openssh/sftp-server: Permission denied
Nov  2 21:39:54 XXX rssh[11287]: allowing scp to user android
Nov  2 21:39:54 XXX rssh[11287]: allowing sftp to user android
Nov  2 21:39:54 XXX rssh[11287]: chrooting android to /home/android
Nov  2 21:39:54 XXX rssh[11287]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 2 "/usr/lib/openssh/sftp-server"

```

SCP:
```

Nov  2 21:43:02 XXX rssh_chroot_helper[11346]: chrooted to /home/android
Nov  2 21:43:02 XXX rssh[11346]: setting android's umask to 077
Nov  2 21:43:02 XXX rssh_chroot_helper[11346]: changing working directory to / (inside jail)
Nov  2 21:43:02 XXX rssh[11346]: allowing scp to user android
Nov  2 21:43:02 XXX rssh_chroot_helper[11346]: execv() failed, /usr/bin/scp: Permission denied
Nov  2 21:43:02 XXX rssh[11346]: allowing sftp to user android
Nov  2 21:43:02 XXX rssh[11346]: chrooting android to /home/android
Nov  2 21:43:02 XXX rssh[11346]: chroot cmd line: /usr/lib/rssh/rssh_chroot_helper 1 "scp -t -- /files/"

```


Files permissions:
```

ls -alR
.:
total 16
drwxr-xr-x 4 root    root    4096 Nov  2 19:44 .
drwxrwx--- 8 android android 4096 Nov  2 20:27 ..
drwxr-xr-x 2 root    root    4096 Nov  2 21:47 bin
drwxr-xr-x 4 root    root    4096 Nov  2 19:44 lib

./bin:
total 100
drwxr-xr-x 2 root root  4096 Nov  2 21:47 .
drwxr-xr-x 4 root root  4096 Nov  2 19:44 ..
-rwxr-xr-x 1 root root 25600 Nov  2 19:44 rssh
-rwxr-xr-x 1 root root 59448 Nov  2 19:44 scp

./lib:
total 16
drwxr-xr-x 4 root root 4096 Nov  2 19:44 .
drwxr-xr-x 4 root root 4096 Nov  2 19:44 ..
drwxr-xr-x 2 root root 4096 Nov  2 21:37 openssh
drwxr-xr-x 2 root root 4096 Nov  2 19:44 rssh

./lib/openssh:
total 80
drwxr-xr-x 2 root root  4096 Nov  2 21:37 .
drwxr-xr-x 4 root root  4096 Nov  2 19:44 ..
-rw-r--r-- 1 root root  6408 Nov  2 21:37 1
-rwxr-xr-x 1 root root 59432 Nov  2 19:44 sftp-server

./lib/rssh:
total 36
drwxr-xr-x 2 root root  4096 Nov  2 19:44 .
drwxr-xr-x 4 root root  4096 Nov  2 19:44 ..
-rwsr-xr-x 1 root root 24904 Nov  2 19:44 rssh_chroot_helper

```


So basically while I seem to have every library these files need (based on strace), yet obvious they do not execute when in the chroot.  In fact trying to run rssh like 
```

root@XXX:/home/android/etc# chroot /home/android /usr/bin/rssh
chroot: failed to run command `/usr/bin/rssh': Permission denied

```


Let copy over and try dash which has no dependencies:
```

root@XXX:/home/android/etc# chroot /home/android/ /dash
chroot: failed to run command `/dash': Permission denied

```
Same issue, can not exec the file, so its obviously to do with execution permissions, which these files all have.  Searching on this has turned up nothing helpful.


Thanks,
ERIC

---

### Post by egandt on 2011-11-03
OK here is what I had to do to get it to work, I first off believe that you need a bin/dash bin/sh in order to test that everything works in the chrooted setup, otherwise you will never get it to work.

In the end the files I needed were:
```

root@fileserver:/raid6/syncHome# ls -ltR
.:
total 32
drwxr-xr-x 2 root root 4096 2011-11-03 07:45 bin
drwxr-xr-x 2 root root 4096 2011-11-03 07:44 lib64
drwxr-xr-x 3 root root 4096 2011-11-03 07:42 etc
lrwxrwxrwx 1 root root    6 2011-11-03 07:29 lib -> lib64/
drwxr-xr-x 2 root root 4096 2011-11-03 07:26 dev
drwxr-xr-x 4 root root 4096 2011-11-03 07:26 usr
-rwxr-xr-x 1 root root 6479 2011-11-03 07:25 mkchroot.sh
drwxr-xr-x 3 root root 4096 2011-11-03 07:15 files

./bin:
total 1128
-rwxr-xr-x 1 root root 934336 2011-11-03 07:45 bash
lrwxrwxrwx 1 root root      4 2011-11-03 07:36 sh -> dash
-rwxr-xr-x 1 root root 114032 2011-11-03 07:28 ls
-rwxr-xr-x 1 root root 101608 2011-11-03 07:28 dash

./lib64:
total 2608
-rwxr-xr-x 1 root root   43552 2011-11-03 07:44 libnss_nis.so.2
-rwxr-xr-x 1 root root   97256 2011-11-03 07:44 libnsl.so.1
-rwxr-xr-x 1 root root   22928 2011-11-03 07:44 libnss_dns.so.2
-rwxr-xr-x 1 root root   18864 2011-11-03 07:43 libnss_hesiod.so.2
-rwxr-xr-x 1 root root   44008 2011-11-03 07:35 libpopt.so.0
-rwxr-xr-x 1 root root  274360 2011-11-03 07:33 libncurses.so.5
-rwxr-xr-x 1 root root   18704 2011-11-03 07:29 libattr.so.1
-rwxr-xr-x 1 root root   14696 2011-11-03 07:29 libdl.so.2
-rwxr-xr-x 1 root root  135745 2011-11-03 07:29 libpthread.so.0
-rwxr-xr-x 1 root root   31208 2011-11-03 07:29 libacl.so.1
-rwxr-xr-x 1 root root  117592 2011-11-03 07:29 libselinux.so.1
-rwxr-xr-x 1 root root   31744 2011-11-03 07:29 librt.so.1
lrwxrwxrwx 1 root root      23 2011-11-03 07:26 libnss_compat.so.2 -> libnss_compat-2.11.1.so
lrwxrwxrwx 1 root root      22 2011-11-03 07:26 libnss_files.so.2 -> libnss_files-2.11.1.so
-rwxr-xr-x 1 root root  136936 2011-11-03 07:26 ld-linux-x86-64.so.2
-rwxr-xr-x 1 root root 1572232 2011-11-03 07:26 libc.so.6
-rwxr-xr-x 1 root root   35712 2011-01-21 17:23 libnss_compat-2.11.1.so
-rwxr-xr-x 1 root root   51712 2011-01-21 17:23 libnss_files-2.11.1.so

./etc:
total 144
-rw-r--r-- 1 root root   1887 2011-11-03 07:42 rssh.conf
-rw-r--r-- 1 root root    513 2011-11-03 07:32 nsswitch.conf
-rw-r--r-- 1 root root    132 2011-11-03 07:32 resolv.conf
-rw-r--r-- 1 root root    497 2011-11-03 07:32 profile
-rw-r--r-- 1 root root   3519 2011-11-03 07:32 localtime
-rw-r--r-- 1 root root    451 2011-11-03 07:32 group
-rw-r--r-- 1 root root    982 2011-11-03 07:31 passwd
-rw-r--r-- 1 root root 107762 2011-11-03 07:26 ld.so.cache
-rw-r--r-- 1 root root     34 2011-11-03 07:26 ld.so.conf
drwxr-xr-x 2 root root   4096 2011-11-03 07:26 ld.so.conf.d

./etc/ld.so.conf.d:
total 16
lrwxrwxrwx 1 root root 25 2011-11-03 07:26 GL.conf -> /etc/alternatives/gl_conf
-rw-r--r-- 1 root root 20 2011-11-03 07:26 lib32asound2.conf
-rw-r--r-- 1 root root 18 2011-11-03 07:26 libasound2.conf
-rw-r--r-- 1 root root 44 2011-11-03 07:26 libc.conf
-rw-r--r-- 1 root root 68 2011-11-03 07:26 x86_64-linux-gnu.conf

./dev:
total 0
srw-rw-rw- 1 root root    0 2011-10-20 16:53 log
crw-rw-rw- 1 root root 1, 5 2011-10-20 16:53 zero
crw-rw-rw- 1 root root 1, 3 2011-10-20 16:53 null

./usr:
total 8
drwxr-xr-x 2 root root 4096 2011-11-03 07:34 bin
drwxr-xr-x 4 root root 4096 2011-11-03 07:26 lib

./usr/bin:
total 484
-rwxr-xr-x 1 root root 405368 2011-11-03 07:34 rsync
-rwxr-xr-x 1 root root  27160 2011-11-03 07:26 rssh
-rwxr-xr-x 1 root root  59528 2011-11-03 07:26 scp

./usr/lib:
total 8
drwxr-xr-x 2 root root 4096 2011-11-03 07:26 rssh
drwxr-xr-x 2 root root 4096 2011-11-03 07:26 openssh

./usr/lib/rssh:
total 28
-rwsr-xr-x 1 root root 27152 2011-11-03 07:26 rssh_chroot_helper

./usr/lib/openssh:
total 56
-rwxr-xr-x 1 root root 55424 2011-11-03 07:26 sftp-server

./files:
total 4
drwxr-xr-x 3 android android 4096 2011-11-03 07:47 android

```

The critical steps I took to get here here:

[LIST=1]
[*]Create a directory for the chroot
[*]Next a created a new home directory for the chrooted users in my case I called it files
[*]Create the user account for a chrooted user in my case android under this chroot/files
[*]Copy over mkchroot.sh and execute it, While this should have correctly setup the system it does not (but it makes things easier), so we need to manually copy over more files and configure things as well.
[*]I started with etc, we also need: group, profile, resolv.conf, rssh.conf, nsswitch.conf, localtime
[*]Remove unneeded entries from groups and password (such as none-chrooted users and the like, this is only for extra security).
[*]Edit rssh.conf remove any references to chroot as we already have done that it is present it tries to do it twice.
[*]Next I created a bin directory under the chroot and added dash, bash and ls to it (you can later once everything works remove them if you want)
[*]For every executable to be under chrooted run ldd <executable> and ensure any linked library is present in chroot/lib  I found that as I'm 64bit all files should be in lib64 and lib should be a symbolic link, so I moved the files place in lib by mkchroot.sh to lib64 and created a symbolic lic from lib64 to lib.
[*]run "chmod u+s rssh_chroot_helper" for both the chrooted and  root system executables (this was key to getting anything to work for me)
[*]In /etc/default/rsyslog add update the line so that it looks like 
RSYSLOGD_OPTIONS="-c4 -a /<chrooted dir>/dev/log" (this way you will have logging from the chroot, otherwise you will be working blind)
[*]Now in theory this is a function chrooted directory you can test by running "chroot /<ch root directory> /bin/bash" (likely this will still fail, as we need more shared objects and I'm unsure why, see directory listing above for what I found required, your install may differ some however, sorry I can not fully explain why these are needed)
[*]Assuming you have all the shared objects present run "chroot /<ch root directory> /bin/bash" again you should now be in the chroot and see a simple prompt "#"
[*] manually execute all the executables now they should all function if any fails write down what shared object is missing so you can add it.
[*]type "exit" to leave the chroot fix and libraries and repeat as needed.
[*]Once every executable works, try scp and sftp (or whatever else you are using chrooted) they should work.
[*]If any of them fail, go back and look at /var/log/syslog for some ideas, as for me everything at this point was operational.
[*]If you want remove bash, dash and ls now, but I left them to use trouble shooting in the future.
[/LIST]

Yes there are a lot of extra steps, but when all is said and done I'm feeling far better and have a viable chrooted account to use for sync my android devices, which supports sftp, scp and rsync.   Hope this helps out ours with similar issues.

ERIC

---

