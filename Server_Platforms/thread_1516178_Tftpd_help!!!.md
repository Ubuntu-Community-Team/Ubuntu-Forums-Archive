---
title: "Tftpd help!!!"
date: 2010-06-23
forum: Server Platforms
---

### Post by PyrexKidd on 2010-06-23
I followed this guide for setting up the tftpd server.
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

first when i tried to start it, xinetd returned:
```

/etc/init.d/xinetd start
 * Starting internet superserver xinetd                                  [fail]

```so I tried:
```

/etc/init.d/xinetd restart
 * Stopping internet superserver xinetd                                  [ OK ] 
 * Starting internet superserver xinetd                                   [ OK ]

```amazing...
But...  When I run nmap from a remote machine, nmap returns:
```

Interesting ports on ip.address.goes.here
Not shown: 997 closed ports
PORT   STATE SERVICE
21/tcp open  ftp
22/tcp open  ssh
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 1.63 seconds

```when i try to connect to my host using tftp all commands are returned invalid except get and put which time out...

It seems like my tftpd server is not listening on port 69.

Here is my /etc/xinetd.d/tftpd file
```

service tftp
{
protocol            = udp
port                 = 69
socket_type     = dgram
wait                = yes
user                = nobody
server             = /usr/sbin/in.tftpd
server_args     = -s /cisco
disable            = no
}

```here is /etc/defaults/tftp-hpa
```

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /cisco"

```
/etc/xinetd.conf
```

# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d

```
(I'd really like to get the logging working, however, getting tftpd working is first priority)
I also set permissions to:
```

chmod 777 -R /cisco

```Can someone please point me in the right direction.
Have I skipped a step in installing, configuring, or trouble shooting the tftpd?
TYA!

---

### Post by koenn on 2010-06-23
> **PyrexKidd said:**
> when i try to connect to my host using tftp all commands are returned invalid except get and put which time out...


That sounds not too bad, as AFAIK 'get' and 'put' are the only actions tftp supports. 

what are you trying to do ? you already have ftp, apparently, so why add tftp ?

---

### Post by PyrexKidd on 2010-06-23
I have different devices that use the tftp protocol.

It's basically a boot server for devices that uses the tftp protocol.  I tried to get them working on ftp... (F***ING Cisco...)  but the will only communicate via port 69 on tftp.

---

