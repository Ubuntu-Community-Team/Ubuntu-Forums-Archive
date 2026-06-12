---
title: "Is there a way to monitor OpenSSH File Transfers"
date: 2008-05-07
forum: Server Platforms
---

### Post by 0graham0 on 2008-05-07
Hi,

I am running an openssh sftp server under ubuntu 8.04. Everything seems to be working fine, however clients are transferring large files and I was wondering if there is any way to monitor in-progress file transfers.

Thank you,
Graham

EDIT: just as i clicked the submit button I realized this is the forum for ubuntu server installs, not server-based programs running under ubuntu. sorry for posting in the wrong forum...

---

### Post by quelx on 2008-05-08
If they are using the interactive mode (just "sftp hostname" and then put and get commands) they can use ```
sftp> progress
``` to see the details of the transfer.  If the remote users have shell accounts they could probably also use **scp** directly w/o interaction and get progress feedback.

[http://www.eos.ncsu.edu/remoteaccess/man/sftp.html](http://www.eos.ncsu.edu/remoteaccess/man/sftp.html)

[http://www.eos.ncsu.edu/remoteaccess/man/scp.html](http://www.eos.ncsu.edu/remoteaccess/man/scp.html)

---

### Post by 0graham0 on 2008-05-08
thanks

---

