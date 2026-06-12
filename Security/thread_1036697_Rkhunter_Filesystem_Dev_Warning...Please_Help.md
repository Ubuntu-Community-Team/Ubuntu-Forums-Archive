---
title: "Rkhunter Filesystem Dev Warning...Please Help"
date: 2009-01-11
forum: Security
---

### Post by AmbientOcclusion on 2009-01-11
I recently ran rkunter using the following switch:
**sudo rkhunter --check --pkgmgr dpkg**

The only warnings I received was in regards to a filesystem check and 3 hidden directories in dev. It found two suspicious files types. This has me a little worried.

Of course I did first:
**sudo rkhunter --propupd**

```
[00:54:45] Performing filesystem checks
[00:54:45] Info: Starting test name 'filesystem'
[00:54:45] Info: SCAN_MODE_DEV set to 'THOROUGH'
[00:54:54]   Checking /dev for suspicious file types         [ Warning ]
[00:54:54] Warning: Suspicious file types found in /dev:
[00:54:54]          /dev/shm/pulse-shm-1749480012: data
[00:54:54]          /dev/shm/pulse-shm-657238994: data
[00:54:54]   Checking for hidden files and directories       [ Warning ]
[00:54:54] Warning: Hidden directory found: /dev/.static
[00:54:54] Warning: Hidden directory found: /dev/.udev
[00:54:54] Warning: Hidden directory found: /dev/.initramfs
```

What do these indicate?

Thanks for your help...

---

### Post by thered on 2009-01-11
server problem... see below

---

### Post by thered on 2009-01-11
Spooky AmbientOcclusion! I too ran a RKrootkit scan today and need help on the output.

Hope you don't mine me posting my warnings here.

To others,  can you help me (us)? Should I be concerned?

```
[11:40:41] /bin/su                                           [ Warning ]
[11:40:41] Warning: The file properties have changed:
[11:40:41]          File: /bin/su
[11:40:41]          Current inode: 33357    Stored inode: 32806
[11:40:42]          Current file modification time: 1228727845
[11:40:42]          Stored file modification time : 1213035031

[11:40:50] /usr/bin/lastlog                                  [ Warning ]
[11:40:50] Warning: The file properties have changed:
[11:40:50]          File: /usr/bin/lastlog
[11:40:50]          Current inode: 3457789    Stored inode: 3459982
[11:40:50]          Current file modification time: 1228727845
[11:40:50]          Stored file modification time : 1213035031

[11:40:54] /usr/bin/newgrp                                   [ Warning ]
[11:40:54] Warning: The file properties have changed:
[11:40:54]          File: /usr/bin/newgrp
[11:40:54]          Current inode: 3457792    Stored inode: 3459983
[11:40:54]          Current file modification time: 1228727845
[11:40:55]          Stored file modification time : 1213035031
[11:40:55] /usr/bin/passwd                                   [ Warning ]
[11:40:55] Warning: The file properties have changed:
[11:40:55]          File: /usr/bin/passwd
[11:40:55]          Current inode: 3458215    Stored inode: 3457235
[11:40:55]          Current file modification time: 1228727843
[11:40:55]          Stored file modification time : 1213035028
[11:40:56] /usr/bin/perl                                     [ Warning ]
[11:40:56] Warning: The file properties have changed:
[11:40:56]          File: /usr/bin/perl
[11:40:56]          Current inode: 1278014    Stored inode: 3458447
[11:40:56]          Current file modification time: 1230000637
[11:40:56]          Stored file modification time : 1216891204

[11:41:15] /usr/sbin/groupadd                                [ Warning ]
[11:41:15] Warning: The file properties have changed:
[11:41:15]          File: /usr/sbin/groupadd
[11:41:15]          Current inode: 3458288    Stored inode: 3460072
[11:41:15]          Current file modification time: 1228727843
[11:41:15]          Stored file modification time : 1213035028
[11:41:15] /usr/sbin/groupdel                                [ Warning ]
[11:41:16] Warning: The file properties have changed:
[11:41:16]          File: /usr/sbin/groupdel
[11:41:16]          Current inode: 3458294    Stored inode: 3460078
[11:41:16]          Current file modification time: 1228727843
[11:41:16]          Stored file modification time : 1213035028
[11:41:16] /usr/sbin/groupmod                                [ Warning ]
[11:41:16] Warning: The file properties have changed:
[11:41:16]          File: /usr/sbin/groupmod
[11:41:16]          Current inode: 3458295    Stored inode: 3460079
[11:41:16]          Current file modification time: 1228727843
[11:41:16]          Stored file modification time : 1213035028
[11:41:17] /usr/sbin/grpck                                   [ Warning ]
[11:41:17] Warning: The file properties have changed:
[11:41:17]          File: /usr/sbin/grpck
[11:41:17]          Current inode: 3458297    Stored inode: 3460113
[11:41:17]          Current file modification time: 1228727843
[11:41:17]          Stored file modification time : 1213035028
[11:41:17] /usr/sbin/nologin                                 [ Warning ]
[11:41:17] Warning: The file properties have changed:
[11:41:17]          File: /usr/sbin/nologin
[11:41:18]          Current inode: 3457760    Stored inode: 3457750
[11:41:18]          Current file modification time: 1228727845
[11:41:18]          Stored file modification time : 1213035031
[11:41:18] /usr/sbin/pwck                                    [ Warning ]
[11:41:18] Warning: The file properties have changed:
[11:41:18]          File: /usr/sbin/pwck
[11:41:18]          Current inode: 3458939    Stored inode: 3460118
[11:41:18]          Current file modification time: 1228727843
[11:41:18]          Stored file modification time : 1213035028
[11:41:19] /usr/sbin/tcpd                                    [ OK ]
[11:41:19] /usr/sbin/useradd                                 [ Warning ]
[11:41:19] Warning: The file properties have changed:
[11:41:19]          File: /usr/sbin/useradd
[11:41:20]          Current inode: 3458943    Stored inode: 3460122
[11:41:20]          Current file modification time: 1228727843
[11:41:20]          Stored file modification time : 1213035028
[11:41:20] /usr/sbin/userdel                                 [ Warning ]
[11:41:20] Warning: The file properties have changed:
[11:41:20]          File: /usr/sbin/userdel
[11:41:20]          Current inode: 3458946    Stored inode: 3460144
[11:41:20]          Current file modification time: 1228727843
[11:41:20]          Stored file modification time : 1213035028
[11:41:20] /usr/sbin/usermod                                 [ Warning ]
[11:41:21] Warning: The file properties have changed:
[11:41:21]          File: /usr/sbin/usermod
[11:41:21]          Current inode: 3458947    Stored inode: 3460157
[11:41:21]          Current file modification time: 1228727843
[11:41:21]          Stored file modification time : 1213035028
[11:41:21] /usr/sbin/vipw                                    [ Warning ]
[11:41:21] Warning: The file properties have changed:
[11:41:21]          File: /usr/sbin/vipw
[11:41:21]          Current inode: 3458952    Stored inode: 3460158
[11:41:21]          Current file modification time: 1228727843
[11:41:21]          Stored file modification time : 1213035028
```

---

### Post by firstlife on 2009-01-26
AmbientOcclusion, your log looks like false positives. The file /dev/shm/pulse-shm-* is for pulse audio, and is actually an example for excluded files in the rkhunter.conf.

There is a config option that can help you, "ALLOWDEVFILE". Look for the following part in rkhunter.conf, and add/uncomment the last line.

```

# Allow the specified files to be present in the /dev directory.
# One file per line (use multiple ALLOWDEVFILE lines).
#
#ALLOWDEVFILE=/dev/abc
ALLOWDEVFILE=/dev/shm/pulse-shm-*

```

I had the same issue with a text file for a custom script. Now no more alloying "ASCII" warnings! For more info see 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=445716](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=445716)

---------

As for thered, unless you have installed custom software that would modify your login and user executable, you should be worried. In english, it says that after asking apt for the stored file info, it found that since their last install/update time, these executables have been moved on the disk, and have been modified. That should never happen.

So, check your system. Those are very critical programs for system security. Perhaps you should have apt reinstall them? (google is your friend).

I had this happen on a system where I installed a program from source (various reasons). I had to exclude two files, because they had been modified outside of the package manager (apt):

```

ATTRWHITELIST=/bin/lsattr
ATTRWHITELIST=/bin/chattr

```

Best of luck

---

### Post by thered on 2009-02-16
WOW.. firstlife: sorry about delay in getting back to this.

I am worried now.  I'll look into what you say, but all my installs are via synaptic package manager with default repositories.

cheers

---

