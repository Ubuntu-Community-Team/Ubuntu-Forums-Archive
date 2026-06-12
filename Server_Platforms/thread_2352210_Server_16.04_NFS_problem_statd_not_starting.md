---
title: "Server 16.04 NFS problem: statd not starting"
date: 2017-02-10
forum: Server Platforms
---

### Post by henrylaw on 2017-02-10
Building 16.04 NFS server to replace one running 14.04.  User's home directory is hosted via NFS.  For testing, rsync'd user's complete home directory to the new server, edited fstab to point (temporarily) at the new server, rebooted. [FONT=courier new]/etc/exports[/FONT] contains the same line in both servers.

User logon takes over a minute; opening a web page takes twice that: completely unusable.  syslog has a stream of messages like this (where "servername" is the host name of the server, which is in [FONT=courier new]/etc/hosts[/FONT]) ```
localhost kernel: [  344.087213] lockd: cannot monitor servername
```

Researching, found it may be a statd problem, and verified via [FONT=courier new]ps[/FONT] that it's not running. Tried running statd in server foreground via [FONT=courier new]sudo rpc.statd -Fd[/FONT].  The "cannot monitor" messages disappear, user logon is now a second or two ... everything is fine.

So I stopped statd, expecting things to go bad again; they don't.  statd is definitely not running, but user performance is still OK.  Very puzzling.

I don't think I should have to put rpc.statd into one of the startup scripts, though of course I could.  Surely it's supposed to start automatically with NFS?

Advice as to what I've done wrong, and what I should do to put it right, would be very gratefully received.

---

### Post by henrylaw on 2017-02-12
Found it, I think.  This forum entry [http://askubuntu.com/questions/771319/in-ubuntu-16-04-not-start-rpcbind-on-boot](http://askubuntu.com/questions/771319/in-ubuntu-16-04-not-start-rpcbind-on-boot) indicates that Bug #1558196 causes this.  It's fixed in release 0.2.3-0.4 of rpcbind, apparently, but Ubuntu 16.04 LTS has 0.2.3-0.2 so you need to implement the work-round described in the bug description.

I've done this and NFS performance seems normal.

---

### Post by henrylaw on 2017-02-12
I spoke too soon.  I tested NFS just by mounting a directory and doing ls -lR on it, which plainly didn't exercise something: locking I should imagine.  When I exported user home directories via NFS the "cannot monitor" messages came back and performance hit the floor.

---

### Post by henrylaw on 2017-02-12
Well, I give up.  It's something to do with the message that appears in syslog "Failed to read /var/lib/nfs/state: Success" and rpc.lockd is no longer running.  I put [FONT=courier new]rpc.lockd[/FONT] into [FONT=courier new]/etc/rc.local[/FONT], so that it starts at boot, and NFS performance for users is now normal.

There should be a better way of fixing this, but I've spent two days on it already.  It's a brand-new Ubuntu Server 16.04 installation (I re-did it again yesterday, to be sure) so it's not something I've done.

---

### Post by henrylaw on 2017-02-15
For completeness I'm adding more to this despite marking it "solved".  I just built another 16.04 server today and exactly the same thing happens.  I have cured it in the same way.

---

### Post by techspiration on 2017-02-15
I've run into a similar issue with Server 16.04.1 and NFS.
NFS is starting but having issues.  User home directory shared via NFS and is not even usable because of the lockd related errors.
Errors:
Feb 15 11:19:12 myserver kernel: [ 6620.949565] lockd: cannot monitor myhost
Feb 15 11:19:18 myserver kernel: [ 6626.965202] lockd: cannot monitor myhost
Feb 15 11:19:24 myserver kernel: [ 6632.980803] lockd: cannot monitor myhost

However, I've found a slightly different solution than you have mentioned here - just start up rpc.statd.

Details:
I noticed that rpc.statd wasn't running which seemed to relate to these errors.  When starting it by hand, it cured the issues.  Now working to assure it gets started up at boot time.

Server details - my 16.04.1 install is fairly recent - from December.
Please cue me if more details would be helpful.

Ubuntu version:
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

NFS packages are up to date - 

# apt show nfs-common
Package: nfs-common
Version: 1:1.2.8-9ubuntu12
Priority: optional
Section: net
Source: nfs-utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian kernel team <debian-kernel@lists.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 734 kB
Provides: nfs-client
Depends: libc6 (>= 2.15), libcap2 (>= 1:2.10), libcomerr2 (>= 1.01), libdevmapper1.02.1 (>= 2:1.02.97), libevent-2.0-5 (>= 2.0.10-stable), libgssapi-krb5-2 (>= 1.12.1+dfsg-2), libkeyutils1 (>= 1.4), libkrb5-3 (>= 1.6.dfsg.2), libmount1 (>= 2.19.1), libnfsidmap2, libtirpc1 (>= 0.2.4), libwrap0 (>= 7.6-4~), init-system-helpers (>= 1.18~), lsb-base (>= 4.1+Debian11ubuntu7), rpcbind (>= 0.2.0-6ubuntu1), adduser, ucf, initscripts (>= 2.88dsf-13.10ubuntu1), keyutils
Recommends: python
Suggests: open-iscsi, watchdog
Conflicts: nfs-client
Breaks: nfs-kernel-server (<< 1:1.2.8-9ubuntu7~)
Replaces: mount (<< 2.13~), nfs-client, nfs-kernel-server (<< 1:1.2.8-9ubuntu7~)
Homepage: [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)
Supported: 5y
Download-Size: 185 kB
APT-Manual-Installed: yes
APT-Sources: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
Description: NFS support files common to client and server
 Use this package on any machine that uses NFS, either as client or
 server.  Programs included: lockd, statd, showmount, nfsstat, gssd,
 idmapd and mount.nfs.

# apt show nfs-kernel-server
Package: nfs-kernel-server
Version: 1:1.2.8-9ubuntu12
Priority: optional
Section: net
Source: nfs-utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian kernel team <debian-kernel@lists.debian.org>
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Installed-Size: 487 kB
Provides: knfs, nfs-server
Depends: libblkid1 (>= 2.16), libc6 (>= 2.15), libcap2 (>= 1:2.10), libsqlite3-0 (>= 3.5.9), libtirpc1 (>= 0.2.4), libwrap0 (>= 7.6-4~), init-system-helpers (>= 1.18~), nfs-common (= 1:1.2.8-9ubuntu12), ucf, lsb-base (>= 1.3-9ubuntu3)
Conflicts: knfs, nfs-server
Replaces: knfs, nfs-server
Homepage: [http://nfs.sourceforge.net/](http://nfs.sourceforge.net/)
Supported: 5y
Download-Size: 88.0 kB
APT-Manual-Installed: yes
APT-Sources: [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
Description: support for NFS kernel server
 The NFS kernel server is currently the recommended NFS server for use
 with Linux, featuring features such as NFSv3 and NFSv4, Kerberos
 support via GSS, and much more. It is also significantly faster and
 usually more reliable than the user-space NFS servers (from the
 unfs3 and nfs-user-server packages). However, it is more difficult to
 debug than the user-space servers, and has a slightly different
 feature set.
 .
 This package contains the user-space support needed to use the
 NFS kernel server. Most administrators wishing to set up an NFS server
 would want to install this package.

---

### Post by henrylaw on 2017-02-15
Indeed; the same problem precisely.  I too am making sure it "starts at boot time", except I'm using the lazy way: [FONT=courier new]/etc/rc.local[/FONT]!  I can't find out why it's either stopping after boot or not starting at all.  There is nothing in syslog other than that obscure message about [FONT=courier new]/var/lib/nfs/state[/FONT].

---

### Post by techspiration on 2017-02-16
Interesting.  I see a similar message just once in my logs despite multiple reboots and statd being started by hand at first, then by the service changes below multiple times:
Feb 15 11:23:55 myserver rpc.statd[17964]: Failed to read /var/lib/nfs/state: Success

When I looked at this sequence of posts and the ones linked in and from the related bug reports linked in, I saw references for lockd and rpcbind having the issue... in my case, I was seeing statd as the missing piece.  lockd was running just fine.  
There was such a mixing of the rpcbind, lockd and more in these posts and the starting issues weren't quite exactly matching my case or what I was seeing.  Therefore, initially I missed one of the suggested workarounds not thinking it was applicable.  Your follow up to my earlier comments made me go back again to take a closer look and find that indeed there was a workaround that could help me.

For me, this workaround is working (followed by a reboot) on several systems we've tested:
systemctl add-wants multi-user.target rpc-statd.service

Before adjusting to the workaround above using "add-wants", I initially just enabled the rpc-statd.service using systemctl not worrying about the dependency which also made statd start on reboot as needed.

And so far, NFS testing is successful following the small workaround above to get statd up and running.

---

### Post by henrylaw on 2017-02-16
Hmm.  I tried the "systemctl add-wants" fix, having found it in the same slightly random way that you did, and as I recall it didn't help.  But I confess I was rattling around slightly at the time and I should go back and do it again in a more systematic way.  You know what it's like, though: you find something ugly that fixes your problem, and immediately the heat is off and you move on to other more pressing things ...

---

### Post by techspiration on 2017-02-16
Sounds like we've traveled the same path... and I can totally understand how finding a fix, even if it feels a bit rough, means that something like this doesn't get the detailed attention in follow up!  More pressing things almost always abound.
Make sure it's the "right" add-wants... as I mentioned, for me it was statd that I needed to add, as rpcbind and lockd were already running and not the source of my issue.  Perhaps you just need a different argument for that workaround.

BTW - I appreciate your recent creation of this thread and posting on this front, as it caused me to dig in a bit in a different way and find what appears to be a better, more standardized solution.

---

