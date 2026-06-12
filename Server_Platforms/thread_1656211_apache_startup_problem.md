---
title: "apache startup problem"
date: 2010-12-30
forum: Server Platforms
---

### Post by koszta on 2010-12-30
Hi I have apache2 service configured to run at startup. 

```
$ sysv-rc-conf --list apache2
apache2      0:off	1:off	2:on	3:on	4:on	5:on	6:off

```

The thing is that when I reboot I cant access the web server...
so i tried

```
 service apache2 status
=> Apache2 is NOT running
```

BUT when I try torun it I get 
```
 * Starting web server apache2                                                  (98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
```

- So I checked netstat and found there is something listening 0.0.0.0:443 LISTEN

- well I did ```
ps -u root|grep apache2
``` and found :
```
 1243 ?        00:00:00 S91apache2
 1252 ?        00:00:00 apache2ctl
 1257 ?        00:00:00 apache2

```

What the heck?! He said it wasnt running... So I killed the apache2 and started the service (which finally worked)

BUT it suck - I need apache to start automatically at boot not to have a person start it... 

I think it also might be the thing that the apache is ssl (port 443)only and that it requires the password for the certificate when it starts. 

Any help much appreciated

---

### Post by koszta on 2011-02-08
I solved the problem by creating a certificate with no passphrase

---

