---
title: "List of all default install packages?"
date: 2005-09-30
forum: The Cafe
---

### Post by AgenT on 2005-09-30
Is there a way to extract the list of default packages installed when one does an install from the Ubuntu Install CD?

This would be helpful for doing a comparison between packages installed now and packages installed when installing Ubuntu.

---

### Post by Wide on 2005-09-30
You can just do a 
```
dpkg --get-selections > mystuff.pkgs
```
This will drop a file called ```
mystuff.pkgs
``` into what ever directory you are in.
Hope this helps :D

---

### Post by AgenT on 2005-09-30
[quote=Wide]You can just do a 
```
dpkg --get-selections > mystuff.pkgs
``` This will drop a file called ```
mystuff.pkgs
``` into what ever directory you are in.
Hope this helps :D[/quote]

Thanks,  but this is actually not what I wanted. My post above was confusing. What I would like to do is have a list of packages that are installed by the default Ubuntu Install CD, not a list of packages I have now. Actually, I need both but I already knew how to get a list of packages I have installed now (which is what you provided).

---

### Post by UbuWu on 2005-10-01
[http://releases.ubuntu.com/hoary/ubuntu-5.04-live-i386.manifest](http://releases.ubuntu.com/hoary/ubuntu-5.04-live-i386.manifest)

^^ That is of the live cd, but isn't much different from the install cd.

---

### Post by AgenT on 2005-10-01
[quote=UbuWu][http://releases.ubuntu.com/hoary/ubuntu-5.04-live-i386.manifest]("http://releases.ubuntu.com/hoary/ubuntu-5.04-live-i386.manifest")

^^ That is of the live cd, but isn't much different from the install cd.[/quote]

Thank you. There is also a *list file that lists all files on the Install CD on [http://releases.ubuntu.com/]("http://releases.ubuntu.com/hoary/ubuntu-5.04-live-i386.manifest"). While not as precise as a complete list of the installed packages, it's good enough. Thank you again.

---

### Post by UbuWu on 2005-10-01
Also, on the install cd's there are these two files:

/dists/hoary/main/binary-i386/Packages
/dists/hoary/restricted/binary-i386/Packages

They contain a lot more info, if you would do a grep package: you would have a nice list. There are some more things on the cd though that are not installed by default (build-essential, thunderbird)

---

### Post by AgenT on 2005-10-01
Good catch, thank you.

---

