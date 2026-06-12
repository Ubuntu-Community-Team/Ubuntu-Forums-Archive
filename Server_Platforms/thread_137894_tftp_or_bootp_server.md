---
title: "tftp or bootp server"
date: 2006-02-28
forum: Server Platforms
---

### Post by Kartik Babu on 2006-02-28
I have a little Single board computer that I would like to setup using my desktop.
In order to do so I need to setup a tftp server or a bootp server. (prefer tftp).

i installed atftpd and atftp... and here are my /etc/inetd.conf files
```
tftp            dgram   udp     wait    nobody /usr/sbin/tcpd /usr/sbin/atftpd --tftpd-timeout 300 --retry-timeout 5     --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5  /tftpboot
```

Oddly enough inetd is substituted with inetutils-inetd (i wonder if this is correct now)

if I try connecting with atftp I keep getting timeout messages and put/get finally aborts.  

I created both  /tftpboot and /var/lib/tftpboot and they have full permissions. plus I also copied test files for download into both directories.

So whats going on here?

---

### Post by UbNewbie on 2006-03-13
Hi,

tftp is not started automatically. Normaly it use inetd to start for but indeed I can't find any /etc/init.d/inetd startup file on my Ubuntu Desktop.
So I change the /etc/default/atftpd and /etc/init.d/atftpd. Change the line "USE_INETD=true" into "USE_INETD=false", and start the server or daemon using "/etc/init.d/atftpd start"..

Hope this helps.

Regards,

H2T

---

