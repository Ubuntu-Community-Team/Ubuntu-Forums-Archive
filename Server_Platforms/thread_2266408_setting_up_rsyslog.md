---
title: "setting up rsyslog"
date: 2015-02-22
forum: Server Platforms
---

### Post by saur02 on 2015-02-22
I have setup rsyslog on Ubuntu server, and would like it to receive logs from various devices on my network. I have mounted a separate drive to store the logs on (/mnt/storage/logs). I have uncommitted the ```
$ModLoad imudp
``` and ```
$UDPServerRun 514
``` lines in /etc/rsyslog.conf.

I have added a file /etc/rsyslog.d/30-gateway.conf with the following code, and the server is receiving logs successfully from my router. 

```
$template DynFile,"/mnt/storage/logs/gateway/%$year%%$month%%$day%.log"
:fromhost-ip, isequal, "192.168.2.1" ?DynFile
:fromhost-ip, isequal, "192.168.2.1" ~
```

I have also added a file for the media server (ubuntu), but the server is not receiving the logs. 

```
$template DynFile,"/mnt/storage/logs/media/%$year%%$month%%$day%.log"
:fromhost-ip, isequal, "192.168.2.13" ?DynFile
:fromhost-ip, isequal, "192.168.2.13" ~
```

On the media server I have added the following code to /etc/rsyslog.conf

```
$ModLoad imuxsock # provides support for local system logging$ModLoad imklog   # provides kernel logging support
#$ModLoad immark  # provides --MARK-- message capability

*.* @192.168.2.12:514
```

---

### Post by ikki_72 on 2015-02-23
sometimes, even not tabbing between source and destination also could trigger this

---

### Post by saur02 on 2015-03-01
Ok so it looks like it was working all along, but what I was trying to do (and expecting to happen) was for the log files from each client to stored in a separate directory. Is this possible with rsyslog?

---

### Post by Habitual on 2015-03-02
> **saur02 said:**
> Ok so it looks like it was working all along, but what I was trying to do (and expecting to happen) was for the log files from each client to stored in a separate directory. Is this possible with rsyslog?
Have a look at the 
%HOSTNAME% parameter of $template

---

