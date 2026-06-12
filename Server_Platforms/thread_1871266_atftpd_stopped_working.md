---
title: "atftpd stopped working"
date: 2011-10-28
forum: Server Platforms
---

### Post by 2Wheels on 2011-10-28
Hi,

Recently, I upgraded a Ubuntu server 10.10 installation to 11.10.   Fortunately, everything went smoothly except that now my atftpd service is broken.  It is not using inetd and here is the configuration from /etc/default/atftpd.conf
USE_INETD=false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /backup/tftp"
a

I have executed sudo /etc/init.d/atftpd restart several times and it always reports "Restarting Advanced TFTP server: atftpd."

Yet, there's no connectivity to it.  As I said, this was working prior to the upgrade.  I did check file permissions and the /backup/tftp folder is 777.

The error that I get when sending a file, testcopy, to the ftp daemon is the following:
%Error writing tftp://192.168.101.191/testcopy (Timed out attempting to connect)

What else should I look at?  

Thanks

---

### Post by 2Wheels on 2011-10-28
As a follow-up, I took a look into /var/log/syslog.  I get the following each time I attempt to restart atftpd:
Oct 28 16:33:10 hrcserver5 atftpd[1719]: Advanced Trivial FTP server started (0.7)
Oct 28 16:33:10 hrcserver5 atftpd[1720]: atftpd: invalid IP address

So, that's possibly helpful.  I don't know why it thinks there's an invalid IP address.  If config shows eth0 with the correct address and lo with the normal 127.0.0.1

Thanks

---

