---
title: "Thunderbird won't start after install"
date: 2009-10-30
forum: Ubuntuzilla
---

### Post by Mr_Freez3 on 2009-10-30
Installed ubuntuzilla-4.7.6-0ubuntu1-i386.deb earlier this morning using Gdebi.  That went ok.  Then installed latest Firefox and that went ok also.  Firefox 3.5.4 starts and runs fine.  Then installed latest Thunderbird and it installed fine. Tried to run Thunderbird and got this in terminal:

```
username@xxxxxx:~$ thunderbird
/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

Anyone know why Firefox works and Thunderbird doesn't?  This is Ubuntu 9.10 32-bit system.

Thanks.

---

### Post by nanotube on 2009-10-30
hrm apparently thunderbird still depends on libstdc++5

but karmic has removed this older library from the official repos.

so, grab the .deb of libstdc++5 from the jaunty repos, here:
[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)

and install. that will fix you up.

---

### Post by Mr_Freez3 on 2009-10-30
Thanks nanotube, that did the trick.  :guitar:

---

### Post by nanotube on 2009-10-30
excellent. :)

for future reference, the reason they removed libstdc++5 from the repos is because they took it out upstream in debian.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536776](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=536776)

---

