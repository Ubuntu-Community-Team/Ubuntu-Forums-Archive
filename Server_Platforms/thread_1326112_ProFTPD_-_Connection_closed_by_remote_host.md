---
title: "ProFTPD - Connection closed by remote host"
date: 2009-11-14
forum: Server Platforms
---

### Post by Grey08 on 2009-11-14
Hi,

The ftp server was running fine, but after i replaced a new router (Aztech DSL600ER), user can't connect to it externally (Internet).

The steps i have taken:
1. Set the port forwarding at router, under Apps, FTP server.

Is there a config file i need to re-assign IP address and port under ProFTPD? Where is the config file?



Best regards
Grey08

---

### Post by Grey08 on 2009-11-14
Why? Could it be updated?

---

### Post by Grey08 on 2009-11-14
Anyone knows whats the reason, please?

---

### Post by Grey08 on 2009-11-16
Hello, after trying so many times, I have removed the Proftpd, even the proftpd.bash in the /etc/init.d/

So, i apt-get install vsftpd, but the problem comes when vsftpd detected the /etc/init.d/proftpd not found. 

here is the error message:

```

invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd-basic (--remove);
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 Proftps-basic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i have gave up of using the proftpd, and trying to use vsftpd, but now...

Can anyone help me please??

---

### Post by gobbledigook on 2009-11-16
try to remove the proftp through apt rather than manually

```
sudo apt-get purge proftpd
```

then installing vsftpd

---

### Post by Grey08 on 2009-11-16
Thanks for reply, really appreaciate that.

But, something wrong to my server now, everytime i turn on my server now, the processes getting more and more, the increment of processes is like 10 processes every 2 seconds. 

What happened?

---

### Post by Grey08 on 2009-11-16
> **gobbledigook said:**
> try to remove the proftp through apt rather than manually
```
sudo apt-get purge proftpd
```

then installing vsftpd


```

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

my server now is getting very wrong, the processes go up to 3000 something after 5 mins or so... 

What happened???

---

### Post by Grey08 on 2009-11-16
i have checked from top,   ps -ef

found that invoke-rc.d   and proftpd rest is keep running.

how do i stop that?

---

### Post by cariboo on 2009-11-17
You probably still have proftp installed, to remove it, use:

```
sudo apt-get purge proftpd
```

It would help if you shut down proftpd first:

```
sudo /etc/init.d/proftpd stop
```

---

### Post by Grey08 on 2009-11-17
> **cariboo907 said:**
> You probably still have proftp installed, to remove it, use:

```
sudo apt-get purge proftpd
```

It would help if you shut down proftpd first:

```
sudo /etc/init.d/proftpd stop
```

Hi, Cariboo907

I have removed the /etc/init.d/proftpd, so it couldn't start/stop/restart or so.

when i type ```
sudo apt-get purge proftpd
```

it will result ```
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

Besides that, the processes of my server is increasing every time i turn on it, it goes to 3,000 processes, and whole system become very slow and not responding. When i type ```
grey@Edward> ps -ef

or

grey@Edward> top
```

i'll see that 

```
invoke-rc.d rp

and 

proftpd rest
```

are running with different ID.

I m really confusing now. 

For the problem of processes keep increasing, i guess that could be /etc/init.d/proftpd was deleted. I was thinking without it, i couldn't remove it, so when i saw there was a proftpd.bash(not sure) found from the system search, i pasted it to /etc/init.d/. Then the problem appeared ever since that.
 



I m not frustrated, really. I feel very happy now :D

---

### Post by Grey08 on 2009-11-17
Ok, i have settled the problems above. The problem now goes back to the initial parts, connection closed by remote host..

Could be the reason if the router doesn't have ddns feature?

---

