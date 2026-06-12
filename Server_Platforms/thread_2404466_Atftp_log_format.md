---
title: "Atftp log format"
date: 2018-10-24
forum: Server Platforms
---

### Post by sebastiaopburnay on 2018-10-24
Hello,

I'm running a 64bits Ubuntu Server 18.04 LTE. This server hosts an atftp server instance of version atftp-0.7

My problem is regarding the log entries format:
```

Oct 24 11:18:37 <SERVER_NAME> atftpd[22996.139938917275392]: Creating new socket: <SERVER_IP>:32941
Oct 24 11:18:37 <SERVER_NAME> atftpd[22996.139938917275392]: Serving <SOME_FILE> to <CLIENT_IP>:64244
Oct 24 11:18:37 <SERVER_NAME> atftpd[22996.139938917275392]: will do netascii convertion

```

These entries' timestamps do not show the year....

Does anyone know how to change that format?

For clearance I also show the options applied/enforced by the /etc/default/atftpd config file:
[LIST]
[*]--daemon 
[*]--user=tftp
[*]--verbose=7
[*]--logfile=/var/log/ftp/atftpd.log
[*]--tftpd-timeout 300
[*]--retry-timeout 5
[*]--mcast-port 1758
[*]--mcast-addr 239.239.239.0-255
[*]--mcast-ttl 1
[*]--maxthread 100
[*]/home/<USER>/ftp
[*]
[/LIST]

---

### Post by howefield on 2018-10-24
Thread moved to the "*Server Platforms*" forum.

---

