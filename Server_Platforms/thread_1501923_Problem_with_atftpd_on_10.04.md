---
title: "Problem with atftpd on 10.04"
date: 2010-06-04
forum: Server Platforms
---

### Post by Juggler00 on 2010-06-04
I had previously been able to get atftpd to work on 9.04. Having just done a fresh install of 10.04 server, I have tried to install atftpd. The install works, but I have yet to be able to either "put" or "get" a single file.

The following are the step-by-step commands I used:
```
$ sudo apt-get install atftpd
$ sudo vi /etc/default/atftpd
[INDENT]USE_INETD=false
OPTIONS="--daemon --port 69 --tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /var/tftp"
[/INDENT]$ sudo invoke-rc.d atftpd start
/var$ sudo mkdir tftp
/var$ sudo chmod -R 777 tftp/
/var$ sudo chown -R nobody tftp/
/var$ sudo /etc/init.d/atftpd restart

```
I've even tried rebooting, to no avail. Any thoughts?

---

### Post by Juggler00 on 2010-06-05
Problem solved...

For whatever reason, a second re-boot has fixed the problem. Not sure why... but all is well.

---

