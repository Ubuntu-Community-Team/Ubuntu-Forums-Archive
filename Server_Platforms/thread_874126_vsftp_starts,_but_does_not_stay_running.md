---
title: "vsftp starts, but does not stay running"
date: 2008-07-29
forum: Server Platforms
---

### Post by tdcdodger on 2008-07-29
I have an ubuntu server that I would like to use as a ftp server (I would like to run VSftpd because I am farmiliar with it).

I can install vsftpd with no problems. When I start vsftpd (/etc/init.d/vsftpd start), it does not report any problems. However, if I try to STOP vsftpd (/etc/init.d/vsftpd stop) immediately after starting it, I get a message:

 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.

My only guess is that the SSH's sftp-server may be causing some problems, however no matter what I do, I cannot get sftp-server disabled (I have tried commenting it out of the /etc/ssh/sshd.config).

Is there anything I can do to disable sftp-server?

Are there any logs I can check or logging options I can set for vsftp to provide more information? (the one at /var/log/vsftpd.log doesnt provide squat)

Any help or comments are more than appreciated. I have been trying to solve this problem for a while now.

---

