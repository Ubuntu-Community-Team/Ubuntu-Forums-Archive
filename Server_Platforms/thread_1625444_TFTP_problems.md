---
title: "TFTP problems"
date: 2010-11-19
forum: Server Platforms
---

### Post by Z.K. on 2010-11-19
I have a tftp server enabled and I can use this command

```

netstat -a |grep tftp

```

to see that the tftp server is running, but when I use this command

```

tftp localhost -c get pxelinux.0

```

I get this response

```

The program 'tftp' can be found in the following packages:
 * tftp-hpa
 * tftp
Try: sudo apt-get install <selected package>


```

If I try to boot a client, it assigns an IP address okay, but it times out on the tftp server.

```

# /etc/default/tftpd-hpa

TFTP_USERNAME="tftp"
#TFTP_DIRECTORY="/var/lib/tftpboot"
#TFTP_ADDRESS="0.0.0.0:69"
TFTP_ADDRESS=192.168.0.2:69"
#TFTP_OPTIONS="--secure"
TFTP_DIRECTORY="/tftpboot"
TFTP_OPTIONS="-l -s /tftpboot"
RUN_DAEMON="yes"


```

Anyone know what I might be doing wrong.

---

### Post by HermanAB on 2010-11-19
Howdy,

Tftp is a little funky, since it has no authentication built in.

Have a look at this page for some tips on tftp:
[http://www.aeronetworks.ca/howtos/ris-howto.html](http://www.aeronetworks.ca/howtos/ris-howto.html)

---

