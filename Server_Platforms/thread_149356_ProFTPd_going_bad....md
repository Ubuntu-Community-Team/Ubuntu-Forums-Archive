---
title: "ProFTPd going bad..."
date: 2006-03-23
forum: Server Platforms
---

### Post by Elrohir on 2006-03-23
Hey folks!

I have a strange problem here... I just installed proftpd but when I try to connect, an error message comes up saying: ```
ftp: connect: Connection refused
```any thoughts anyone? why does the server reject me? I attached the conf file just to check if there's anything wrong with it...

---

### Post by colo on 2006-03-24
Paste the output of
```
netstat -nlp | grep 21
```
on the machine running your ftpd.

---

### Post by Elrohir on 2006-03-24
you sure you need that output? anyway, here's what I got:```
unix  2      [ ACC ]     STREAM     LISTENING     10088    6786/bonobo-activat /tmp/orbit-elrohir/linc-1a82-0-7989437246321
unix  2      [ ACC ]     STREAM     LISTENING     10217    6830/metacity       /tmp/orbit-elrohir/linc-1aae-0-d5e3117aec66
unix  2      [ ACC ]     STREAM     LISTENING     7821     5836/acpid          /var/run/acpid.socket
``` 
EDIT: just got it, no one is listening on the port 21...

---

### Post by Elrohir on 2006-03-24
weird! because I load the ftpd from inetd and according to services-admin the service is active... here are the screenshots...

---

### Post by Elrohir on 2006-03-26
seems like nobody has a clue...

there goes the FTP service for me...

---

### Post by colo on 2006-03-27
Most probably the daemon has died. Check its logfile for more information.

"services-admin" most probably keeps track of a services' status by checking for lock- or pid-files, and not checking running processes. You'd want to have nagios or some other monitoring tool for that.

---

### Post by amac777 on 2007-12-24
I had the same problem. I fixed it by reconfiguring the ftp server to run as standalone instead of started via inet.d.

```
sudo dpkg-reconfigure proftpd
```

then select standalone and use the package maintainer's config file.

That should get you up and running.

---

### Post by Elrohir on 2007-12-24
yeah... I figured that last year... how you came with this OLD (march 2k6) thread?

---

