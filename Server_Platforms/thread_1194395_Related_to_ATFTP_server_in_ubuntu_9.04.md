---
title: "Related to ATFTP server in ubuntu 9.04"
date: 2009-06-22
forum: Server Platforms
---

### Post by ankit89 on 2009-06-22
Can someone tell me how can i send my file from atftp client to atftp server??

My atftp server is 192.168.1.9 and the file to be sent to 192.168.1.62, so wat shall be done to get this going?

i have installed atftp package and I cant able to run this command (sudo invoke-rc.d atftpd start )in ubuntu 9.04  as stated in many forums on websites.So how can i setup my atftp server? please reply..

---

### Post by Bram-NL on 2009-07-12
Maybe some extra info would help to get this question answered.
[quote]i have installed atftp package and I cant able to run this command (sudo invoke-rc.d atftpd start )in ubuntu 9.04 as stated in many forums on websites.So how can i setup my atftp server? please reply..[/]
Why can't you be able to run that command?

---

### Post by sohnman on 2009-08-10
I can't run atftpd in ubuntu 9.04 too.  My /var/log/syslog says like below,

Aug 11 00:24:23 ubt-904 atftpd[19366]: Advanced Trivial FTP server started (0.7)
Aug 11 00:24:23 ubt-904 atftpd[19366]: Failed to set socket option: Socket operation on non-socket
Aug 11 00:29:23 ubt-904 atftpd[19366]: atftpd terminating after 300 seconds
Aug 11 00:29:23 ubt-904 atftpd[19366]: Main thread exiting

FYI, my /etc/default/atftpd is,

USE_INETD=false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /tftpboot"

And /tftpboot directory is world readable and writable.

In the previous ubuntu version it has worked well...  Could you share your ideas ?  Thanks in advance.  ;-)

---

### Post by hessiess on 2009-08-10
Just use SFTP.

---

### Post by theredguy on 2009-09-23
I ran in the same problem and found the solution here:
[http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-advanced-tftp-server-in-ubuntu.html)

Just add **--daemon** to your atftpd options.
In my case atftpd worked after this.

---

