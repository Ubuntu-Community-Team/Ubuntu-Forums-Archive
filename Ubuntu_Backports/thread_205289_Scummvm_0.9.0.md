---
title: "Scummvm 0.9.0"
date: 2006-06-28
forum: Ubuntu Backports
---

### Post by anodizer on 2006-06-28
Can it be backported to dapper? I think it's already -or it will be soon- in edgy repositories.
The version in dapper's repo is very old anyway.

---

### Post by squell on 2006-06-28
I'd also like to see this in dapper.

can this be done or has someone made a .deb for Ubuntu 6.06???

---

### Post by abelthorne on 2006-07-01
It'd be great to have the updated version in the repositories.

I've tried to install or compile the Debian version with no success : compilation ends with an error message if I use the "deb" option and installation from the existing Debian package displays **Error: Dependency is not satisfiable; libasound2** (I do have the library installed ; I guess it's a version problem ?).

---

### Post by mlind on 2006-07-01
I managed to build scummvm 0.9. It has new theme that I still need to include on the .deb package.
I'll try to upload package somewhere tomorrow.

---

### Post by Kangaroo on 2006-07-03
@mlind 

Did the package-building work out well ? 
Have you found some webspace to upload ? 
(Sorry for naggin', i really would like to check out "The Feeble Files")

---

### Post by mlind on 2006-07-03
[QUOTE=Kangaroo]@mlind 

Did the package-building work out well ? 
Have you found some webspace to upload ? 
(Sorry for naggin', i really would like to check out "The Feeble Files")[/QUOTE]

Okay, I'll upload this soon :mrgreen:

---

### Post by mlind on 2006-07-03
I haven't tested this with any games, but it looks to be working alright. Version 0.9.0
contains new theme called *modern*, which I decided to put on */usr/lib/scummvm/themes/modern*. 

I couldn't find how to force this globally as default without making a wrapper script,
scummvm doesn't seem to know about /etc/scummvmrc. If anyone has ideas how to
do this, please drop a line.

To get this theme working, select */usr/lib/scummvm/themes/modern* as Theme Path from
scummvm options, or define **themepath** on ~/.scummvmrc after you've lanched scummvm once
```

themepath=/usr/lib/scummvm/themes/modern

```

[http://www.freefilehoster.com/uploads/1151932240scummvm_0.9.0-dapper.tar.gz](http://www.freefilehoster.com/uploads/1151932240scummvm_0.9.0-dapper.tar.gz)

/edit
wrong image used on .desktop entry, re-uploaded.

---

### Post by anodizer on 2006-07-03
Works great, thnx :)

---

### Post by mlind on 2006-07-03
[QUOTE=anodizer]Works great, thnx :)[/QUOTE]

I used wrong icon on .desktop file, so I uploaded it again.
Sorry for the inconvenience.

---

### Post by Kangaroo on 2006-07-04
Thanks, perfect !

---

### Post by bocmaxima on 2006-07-04
Awesome, the new theme is great, and everything seems to work perfectly.

---

### Post by LordMau on 2006-08-05
I do believe this i available in this repo:
```

deb http://www.elisanet.fi/mlind/ubuntu dapper main
GPG key: D0AFFF5E937215FF

```
I had this for quod libet 0.22, and so happens that scummvm 0.9 also appeared here.

---

