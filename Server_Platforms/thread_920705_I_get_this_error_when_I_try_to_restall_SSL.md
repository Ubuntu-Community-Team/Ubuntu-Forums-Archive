---
title: "I get this error when I try to restall SSL"
date: 2008-09-15
forum: Server Platforms
---

### Post by kustomjs on 2008-09-15
hey guys
I am getting this error when I try to remove and reinstal SSL on to my 8.04 server:
Setting up ssl-cert (1.0.14-0ubuntu2.1) ...
/var/lib/dpkg/info/ssl-cert.postinst: 37: cannot open /etc/ssl/certs/ssl-cert-snakeoil.pem: No such file
/var/lib/dpkg/info/ssl-cert.postinst: 37: cannot open /etc/ssl/certs/ssl-cert-snakeoil.pem: No such file
chgrp: cannot access `/etc/ssl/private': No such file or directory
chmod: cannot access `/etc/ssl/private': No such file or directory

---

### Post by kustomjs on 2008-09-16
can somebody please help!!!

---

### Post by schettj on 2008-09-16
Don't Panic...

You're missing some bits of ssl...

Do you have open-ssl installed?

---

### Post by kustomjs on 2008-09-16
Yes I do I got openssl and mod_ssl installed onto my server.

---

### Post by schettj on 2008-09-16
2 minutes with google found this:

> 
I managed to regenerate default snakeoil certificate with folowing command:
sudo make-ssl-cert generate-default-snakeoil --force-overwrite

In this thread
[http://ubuntuforums.org/showthread.php?t=803827](http://ubuntuforums.org/showthread.php?t=803827)

So try that to get your snakeoil back ;)

---

### Post by kustomjs on 2008-09-16
thanks for that help there. but now I dont see a folder for my SSL

I get this when I go through putty

xxxm@sxxx:~$ sudo apt-get remove ssl-cert
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  openssl-blacklist
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ssl-cert
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 46236 files and directories currently installed.)
Removing ssl-cert ...
chgrp: cannot access `/etc/ssl/private': No such file or directory
chmod: cannot access `/etc/ssl/private': No such file or directory

---

### Post by schettj on 2008-09-16
Wow. not sure how you fubared it that bad. 

some combination of -m and/or -f to ignore/force around the errors may help...

---

### Post by kustomjs on 2008-09-16
well should I just unstall openssl then reinstall it?

---

### Post by schettj on 2008-09-17
can't hurt to try

---

### Post by kustomjs on 2008-09-17
alright i will give it a shoot

just a update i was able to get my SSL certs back and i had to remove webmin and re download it and restall webmin.

and if anybody delete SSL certs you also to remove openssl and restall it then you got to install this also sudo apt-get install ca-certificates openssl-doc

then you got to restall ssl-certs

now can somebody help me setup SSL on virtual host because I got 4 sites needs ssl

---

### Post by kustomjs on 2008-09-17
alright i got my ssl certs back now I just need to install SSL on 4 virtual hosted sites on my server.

---

