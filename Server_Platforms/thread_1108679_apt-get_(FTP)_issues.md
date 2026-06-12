---
title: "apt-get (FTP) issues"
date: 2009-03-27
forum: Server Platforms
---

### Post by m3bik on 2009-03-27
I've recently installed Ubuntu Server Edition 8.10 and trying to install an FTP server.

The ftp server would be for local use, and only one user account needed (me).

I'm not picky about which one to install as long as it works.

I've tried:

```
sudo apt-get install vsftpd
```

I get the response "Couldn't find package vsftpd"


I've also tried:

```
sudo apt-get install proftpd
```

I get the response "Couldn't find package proftpd"


Am I missing something?

---

### Post by Mister.Vash on 2009-03-28
The package looks to be in the main repostiry
[http://packages.ubuntu.com/intrepid/vsftpd](http://packages.ubuntu.com/intrepid/vsftpd)

do you get and errors from running the following?
```
sudo apt-get update
```

If you do, that might be what's causing the error, if not, then you might not have the right repository enabled.   Post your /etc/apt/sources.list and any other .list file under that directory.

---

### Post by m3bik on 2009-03-28
Thanks for your help.

I finally got it working.

I enabled the right repository.

I ran:

```
sudo apt-get update
```

I was still having problems originally, BUT...

I've learned that one of the computers on my network, apparently, has the Trojan Flush.M which hijacks the DNS servers, so the server wasn't actually connecting to the internet correctly. Fixed that issue. Works great now!

---

