---
title: "I need both vsftpd and proftpd on the same machine"
date: 2016-01-12
forum: Server Platforms
---

### Post by pavera on 2016-01-12
I need proftpd to support sftp+virtual users+chroot, and I need vsftpd for ftps+virtual users+chroot.  Proftpd doesn't work reliably for large files that take a long time (we consistently see timeouts during large file transfers that close both the control and data channels).  We've tried every timeout setting in the book in proftpd to attempt to alleviate this issue, but we constantly see uploads fail due to control channel timeouts.  vsftpd does not have this issue at all, it works great for the ftps use case.  However we have a requirement to support sftp uploads as well, and openssh doesn't easily support virtual users or chroot, so enter proftpd, which works great for sftp+virtual users+chroot... 

Now to the ubuntu problem.  Due to the "ftp-server" meta package, these two packages cannot be installed at the same time which is a completely arbitrary ubuntu limitation.  This works fine in Rhel/centos.  So why the artificial mutual exclusion here?  I've installed and run nginx and apache on the same machine.  This should be perfectly fine.  We are going to be running the 2 servers listening on different ports, they have their own config files, there is no reason I can see to make these 2 servers mutually exclusive.  Why is this the case?  What can we do to work around this issue?  I don't see any apt-* flags to "ignore" meta packages, or any way to get apt to ignore this artificial limitation.  In fact, we manually installed both packages with dpkg, and both servers run just fine.  Only problem is now apt is permanently broken complaining about broken dependencies in vsftpd and proftpd-basic.

Is there no way to work around this problem other than build our "own" vsftpd or proftpd package that doesn't specify the "ftp-server" meta package?

---

