---
title: "apt-get suddenly stopped working"
date: 2010-05-18
forum: Server Platforms
---

### Post by ktritty on 2010-05-18
Hello.

For no reason that I can devise, apt-get or aptitude will not work suddenly.  I did not make any changes to interfaces or other fundamental networking stuff.

I know that it is my computer, because apt-get still works great from my other ubuntu machines.  That and the fact that I manage the server remotely via ssh, so it is not the internet connection.

```

webmaster00@ftpserver1:~$ sudo bash
root@ftpserver1:~# aptitude update
Err http://us.archive.ubuntu.com karmic Release.gpg                         
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com karmic-security Release.gpg                  
  Could not resolve 'security.ubuntu.com'
....AND SO ON
```

Ideas on can I go about troubleshooting this?

Ironically, this first started to happen when I tried to do apt-get install lynx, so I could use the CUPS web tool, and generally have a browser on hand in case I ever had to troubleshoot something like this (Alanis Morisette...).  So, I currently have no web browser at my disposal for troubleshooting use, at least that I am aware of.

Thanks!

---

### Post by noway2 on 2010-05-18
It may not be you and there may be something else going on.  I ran into the same, or at least similar problem a few minutes ago trying to update a fresh install of 10.04.  It complains that it can't resolve any of the repositories, but yet normal stuff resolves just fine.

---

### Post by arrrghhh on 2010-05-18
Try to ping security.ubuntu.com, us.archive.ubuntu.com, etc...

If you can't there's your answer.  Try using an alternate mirror :D

---

### Post by lykwydchykyn on 2010-05-18
"could not resolve" means there is a DNS issue.  See what you get from 
```

host us.archive.ubuntu.com

```

If it can't return an IP, check your DNS settings in /etc/resolv.conf.

---

### Post by CharlesA on 2010-05-18
Thanks for the command. It looks like it does the same as nslookup.

---

### Post by ktritty on 2010-05-20
> **lykwydchykyn said:**
> "could not resolve" means there is a DNS issue.  See what you get from 
```

host us.archive.ubuntu.com

```If it can't return an IP, check your DNS settings in /etc/resolv.conf.

Here is the result:

```
webmaster00@ftpserver1:~$ host us.archive.ubuntu.com
us.archive.ubuntu.com has address 91.189.88.30
us.archive.ubuntu.com has address 91.189.88.40
us.archive.ubuntu.com has address 91.189.88.45
us.archive.ubuntu.com has address 91.189.88.46
us.archive.ubuntu.com has address 91.189.92.166
webmaster00@ftpserver1:~$ sudo apt-get update
Err http://us.archive.ubuntu.com karmic Release.gpg                         
  Could not resolve 'us.archive.ubuntu.com'

```

Ideas??

Thanks for the help so far.  There was a problem with resolv.conf.  The above is after restarting /etc/init.d/networking

---

### Post by ktritty on 2010-05-20
SOLVED!

I went back through some recent work configuring SAMBA.  I went off a howto.  They had me modify the contents of /etc/nsswitch.conf to work with WINS.  The order they suggested may have not been so good....

The BAD VERSION:
hosts:          files mdns4_minimal hosts wins [NOTFOUND=return] dns mdns4

THE WORKING VERSION:
hosts:          files mdns4_minimal hosts [NOTFOUND=return] dns mdns4 wins

Thank you everybody for your support, and hooray for trial-and-error sometimes actually panning out.

---

