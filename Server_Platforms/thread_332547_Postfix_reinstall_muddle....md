---
title: "Postfix reinstall muddle..."
date: 2007-01-06
forum: Server Platforms
---

### Post by malarky on 2007-01-06
I've gotten myself into a bit of a muddle with postfix - when i pulled down the package and apt-get installed it, it asked for a hostname which I mistyped and discovered my keyboard wouldn't delete. I just hit enter, thinking I could dpkg-reconfigure it after the install. 

I was wrong - because I entered spaces in the hostname, it took it to mean there were multiple hostnames, and didn't complete the install correctly. Then, dpkg-reconfigure wouldn't run because the install was broken. 

I tried to manually edit the hostname in /etc/postfix/main.cf, and the hostname in /etc/mailname, and then remove and reinstall the package; no dice. I've tried this a few times in different orders and it's not working; it always reports the install failed because of that hostname I specified when i originally installed it.

Now, I deleted /etc/init.d/postfix, but I think this was a mistake since I did it before I removed postfix with apt-get; now it won't remove it at all because /etc/init.d/postfix is not there.

I thought I was getting the hang of linux! 

Any ideas? I've run out.

---

### Post by chrisfay on 2007-01-06
Have you tried either:

```
sudo apt-get --purge remove postfix
```
or
```
sudo dpkg -P postfix
```

---

### Post by malarky on 2007-01-06
On trying the dpkg -P i get:
```
steve@server:~$ sudo dpkg -P postfix
dpkg: dependency problems prevent removal of postfix:
 subversion-tools depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
dpkg: error processing postfix (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 postfix
```

And on the apt-get purge, I get:
```
Removing postfix ...
/var/lib/dpkg/info/postfix.prerm: 41: /etc/init.d/postfix: not found
dpkg: error processing postfix (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by malarky on 2007-01-06
Anyone? I've google and looked at the postfix site but i'm still stuck....

---

### Post by sav2005 on 2007-01-09
Try creating a file called /etc/init.d/postfix with this command:
sudo touch /etc/init.d/postfix

---

