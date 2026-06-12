---
title: "It scared the hell out of me... ;)"
date: 2021-02-07
forum: Ubuntu Development Version
---

### Post by zika on 2021-02-07
```
:~$ sudo apt dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libc6:i386 libcom-err2:i386 libcrypt1:i386 libgcc-s1:i386 libgssapi-krb5-2:i386 libidn2-0:i386 libk5crypto3:i386
  libkeyutils1:i386 libkrb5-3:i386 libkrb5support0:i386 libnsl2:i386 libnss-nis:i386 libnss-nisplus:i386
  libssl1.1:i386 libtirpc3:i386 libunistring2:i386 zlib1g:i386
The following packages will be upgraded:
  libc-dev-bin libc6 libc6-dbg libc6-dev
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  libgcc-s1:i386 libc6:i386 (due to libgcc-s1:i386)
4 upgraded, 0 newly installed, 17 to remove and 0 not upgraded.
Need to get 13,5 MB of archives.
After this operation, 22,0 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?]
```
I'll have to purge all i386 packages but this phrase does not work... ;)

---

### Post by grahammechanical on 2021-02-07
It would me as well.

Isn't dist-upgrade the same as the partial upgrade offered by Update Manager? Agree to it if the development version has become boring and you are in need of some excitement. 

Conflict resolution by removing the less important packages. Have fun. :)

Regards

---

### Post by zika on 2021-02-08
> **grahammechanical said:**
> It would me as well.
Isn't dist-upgrade the same as the partial upgrade offered by Update Manager? Agree to it if the development version has become boring and you are in need of some excitement. 
Conflict resolution by removing the less important packages. Have fun. :)
RegardsNo, that is not my machine, not any from the set that I'm working on... ;)
I do not use UM so, it might be. This is output that someone send me to see what is going on his machine, asking for help. That was just a moment in HH's life, yesterday, I did even see that message up to that message I've received. After C was build as a whole it disappeared.
Yes, I did perceive it as fun since, if Yo may believe, I did not see it before. Good way to protect, as far as one can, instalation from...
Old guys do not need much to have fun.
You can always reproduce it, for example, by asking Ubuntu to remove all i386-arch-packages... ;) That I've learned a bit later, investigating, for myself, a bit deeper, after correspondent was happy and at peace...
Since this is a message found on Development edition it is appropriate fore being here but I will close this thread not to bake reasonable rules we have here.

---

