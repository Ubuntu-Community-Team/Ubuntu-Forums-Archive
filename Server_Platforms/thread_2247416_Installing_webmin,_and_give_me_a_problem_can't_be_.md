---
title: "Installing webmin, and give me a problem can't be fixed by apt-get -f install"
date: 2014-10-07
forum: Server Platforms
---

### Post by Leo_Chen on 2014-10-07
Ubuntu 13.04 64-bit
--------------
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring

----------------------------------------------

Hi people

The problem that I have encountered is:

1. wget the webmin package
2. dpkg --install it
3. apt-get install the missing dependencies
4. all the other dependencies have been installed, but [B]libauthen-pam-perl

[/B]The error message shows:
**```
**The following packages have unmet dependencies: libauthen-pam-perl : Depends: perlapi-5.10.0

E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[B]
```

[/B]I ran the apt-get -f install" command as suggested, however, it just simply suggest me to remove webmin package...... I have been searching on the internet for hours, but I don't see anyone else have the same issue. 

Please help. Thanks in advance

Cheers

---

### Post by LukeMorrison on 2014-10-08
First off, welcome to the forums.   As I was looking around, I could not tell whether 13.04 server is still supported, but I know the desktop edition is out of support.  If 13.04 server is still under support, have you tried using ```
 sudo apt-get install libauthen-pam-perl 
```

Luke Morrison

---

### Post by Chris of Arabia on 2014-10-08
Have a look at this link. This is what I followed when I installed it on 12/13.xx. It seems to have survived all upgrades so far and is now happily running under 14.04

[http://patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524](http://patrickjwaters.com/blog/2011-07-13/my-favorite-web-server-setup-ubuntu-server-lamp-webmin-and-virtualmin/3524)

---

### Post by nerdtron on 2014-10-09
```
Ubuntu 13.04 64-bit
--------------
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring

----------------------------------------------
```

Might as well put your effort on 12.04 or 14.04 which are both Long-Term-Support cycles. Your current version is End-of-Life already (no more updates and support).
See: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

