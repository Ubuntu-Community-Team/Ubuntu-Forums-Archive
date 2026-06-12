---
title: "dlm: Can't create listening comms socket"
date: 2007-05-17
forum: Server Platforms
---

### Post by swilson07 on 2007-05-17
We are attempting to run GFS on stock Ubuntu Feisty 2.6.20-15-server
kernel.  This error is produced when attempting to mount a gfs file
system created with lock_dlm protocol:

# mount -t gfs -v /dev/san/test /san
/sbin/mount.gfs: mount /dev/san/test /san
/sbin/mount.gfs: parse_opts: opts = "rw"
/sbin/mount.gfs:   clear flag 1 for "rw", flags = 0
/sbin/mount.gfs: parse_opts: flags = 0
/sbin/mount.gfs: parse_opts: extra = ""
/sbin/mount.gfs: parse_opts: hostdata = ""
/sbin/mount.gfs: parse_opts: lockproto = ""
/sbin/mount.gfs: parse_opts: locktable = ""
/sbin/mount.gfs: message to gfs_controld: asking to join mountgroup:
/sbin/mount.gfs: write "join /san gfs lock_dlm test:shared rw /dev/san/test"
/sbin/mount.gfs: lock_dlm_join: gfs_controld join error: -1
/sbin/mount.gfs: error mounting lockproto lock_dlm

Via dmesg and lsmod, we see what appears to be an issue with sctp
unloading properly:
...
[   16.890000] DLM (built Apr 15 2007 06:37:45) installed
[   16.910000] GFS2 (built Apr 15 2007 06:39:20) installed
[   16.910000] Lock_DLM (built Apr 15 2007 06:39:42) installed
[   21.690000] SCTP: Hash tables configured (established 65536 bind 65536)
[   21.690000] Module sctp cannot be unloaded due to unsafe usage in
net/sctp/protocol.c:1177
[   21.730000] dlm: Can't create listening comms socket
[   21.730000] dlm: cannot start dlm lowcomms -98
...
# lsmod | grep sctp
sctp                  160696  2 [unsafe]
ipv6                  273344  19 sctp

Line 1177 of net/scptp/protocol.c is:
 __unsafe(THIS_MODULE);

Presumably the sctp unoad failure also caused dlm to fail.  For grins
we commented out line 1177 of net/scptp/protocol.c, re-compiled,
installed and rebooted.  Now dmesg shows this:
...
[   22.630000] SCTP: Hash tables configured (established 65536 bind 65536)
[   22.680000] dlm: Can't create listening comms socket
[   22.680000] dlm: cannot start dlm lowcomms -98
...
Along with dmesg:
# lsmod | grep sctp
sctp                  161592  2
ipv6                  273344  19 sctp

At this point, we're really not sure what the next step should/could
be since it's not clear the sctp and dlm issues are related.

If we create a gfs file system using the lock_nolock protocol, our
system is able to mount gfs successfully, but of course this is isn't
a usable production solution.  Any insight regarding lock_dlm and it's
relationship to sctp would be helpful.

---

