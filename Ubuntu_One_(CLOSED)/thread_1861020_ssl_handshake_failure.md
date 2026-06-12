---
title: "ssl handshake failure"
date: 2011-10-15
forum: Ubuntu One (CLOSED)
---

### Post by nutznboltz on 2011-10-15
How do I recover from this:

2011-10-15 09:25:50,025 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection made.
2011-10-15 09:26:11,132 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_READ_BYTES', 'ssl handshake failure')]
].

Details about the affected system:
$ lsb_release -ds
Ubuntu 11.10

$ uname -srvpi
Linux 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64

I know about this already:
[http://askubuntu.com/questions/58692/ubuntu-one-file-sync-problem-ssl-handshake-error](http://askubuntu.com/questions/58692/ubuntu-one-file-sync-problem-ssl-handshake-error)

It isn't helpful.

---

### Post by Widodh on 2011-10-18
UbuntuOne is experiencing some troubles lately. I already contacted their support and they said they were working on it.

Nothin you can fix here yourself.

---

### Post by nutznboltz on 2011-10-19
I found that if I go to the "Ubuntu One Control Panel" which is:

/usr/bin/python /usr/bin/ubuntuone-control-panel-gtk

but you can click on the U1 logo to get there with Unity.

Then press the "disconnect" control, wait a bit and press "connect" this will often establish a connection where previously there was

2011-10-15 09:26:11,132 - ubuntuone.SyncDaemon.StorageClient - INFO - Connection lost, reason: [Failure instance: Traceback (failure with no frames): <class 'OpenSSL.SSL.Error'>: [('SSL routines', 'SSL3_READ_BYTES', 'ssl handshake failure')]

in the 

~/.cache/ubuntuone/log/syncdaemon.log

file.

You may need to repeat this for it to work.

---

