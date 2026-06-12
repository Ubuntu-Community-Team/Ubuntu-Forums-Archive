---
title: "Syslog on remote server"
date: 2010-11-10
forum: Server Platforms
---

### Post by nirvana2307 on 2010-11-10
i am running TinyCore on a PC 104 computer. i need to throw the logs of tinycore over the network to my server's (ubuntu) log files. 

what configurations of syslog are needed on Host and server computers?

i tried

on tinycore

```

syslogd -R 192.168.0.99

```

on ubuntu

```

vi /etc/default/syslogd
SYSLOGD="-r"

```

it doesn't seem to work. the wireshark seem to be showing arrival and ack of packets.
Any idea , what is wrong?

---

