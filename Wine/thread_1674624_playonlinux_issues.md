---
title: "playonlinux issues"
date: 2011-01-24
forum: Wine
---

### Post by garyhibdon on 2011-01-24
ok so i'm getting 2 error messages from this. the first happens ANY time i try to update my system or check for new update packages.

```
W: GPG error: http://deb.playonlinux.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186
```the second is i cannot get it to actually acknowledge diablo 2 or any other windows programs i have tried to install. it says the install was complete, but the items never show up on the list of usable applications.. PLEASE help!

I'm running ubuntu 10.10 32bit  updated wine and playonlinux(that im aware of) and patch 1.13 for diablo on a custom pc. 

i have diablo 2 running inside of wine, but was trying to run multiple windows operations at once.

---

### Post by izaac on 2011-01-24
wget -q "http://deb.playonlinux.com/public.gpg" -O - | apt-key add -
sudo apt-get update

shouldn't give you problems anymore.

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) 

Click Debian, for details.

---

### Post by garyhibdon on 2011-01-24
```
me@me-System-Product-Name:/$ wget -q "http://deb.playonlinux.com/public.gpg" -O - | apt-key add -
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
me@me-System-Product-Name:/$ wget -q "http://deb.playonlinux.com/public.gpg" 
me@me-System-Product-Name:/$ wget -q "http://deb.playonlinux.com/public.gpg" -O - | apt-key add - sudo apt-get update
gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error
me@me-System-Product-Name:/$ 
``` still a no go

---

### Post by izaac on 2011-01-24
alright try again this way:

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -

if still not working, do it separately:

wget "http://deb.playonlinux.com/public.gpg" 
sudo apt-key add public.gpg

---

### Post by garyhibdon on 2011-01-25
well, atleast its not saying the same thing any more

```
 me@me-System-Product-Name:/$ wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
[sudo] password for me: 
OK
me@me-System-Product-Name:/$ wget "http://deb.playonlinux.com/public.gpg"
--2011-01-25 17:13:49--  http://deb.playonlinux.com/public.gpg
Resolving deb.playonlinux.com... 91.121.5.64
Connecting to deb.playonlinux.com|91.121.5.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 926 [text/plain]
public.gpg: Permission denied

Cannot write to `public.gpg' (Permission denied).
me@me-System-Product-Name:/$ sudo apt-key add public.gpg
gpg: can't open `public.gpg': No such file or directory
me@me-System-Product-Name:/$ 
```

---

### Post by MelodiesonMusic on 2011-01-30
sudo? 

try this 

```
sudo wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
```

and see if you can get access

---

### Post by eurekabru on 2011-02-03
It worked for me as root. Thank you.

---

### Post by rmckean on 2011-05-24
Had the same issue. They must have moved the keys location. I had to use "http://rpm.playonlinux.com/public.gpg".

---

