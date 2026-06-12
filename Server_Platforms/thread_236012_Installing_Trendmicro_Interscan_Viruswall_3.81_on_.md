---
title: "Installing Trendmicro Interscan Viruswall 3.81 on Ubuntu 6.06 Server"
date: 2006-08-14
forum: Server Platforms
---

### Post by [cp] on 2006-08-14
Hello all,

i tried to install Trendmicro Interscan Viruswall 3.81 on Ubuntu 6.06 Server but i have problems with the shared libs.

When running the installer it gives us the followging error:

/etc/iscan/sedini: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

So i tried the following: 

ln -s libstdc++-libc6.2-2.so.3 libstdc++-libc6.1-1.so.2

But after that, there are other errors:

/etc/iscan/sedini: symbol lookup error: /etc/iscan/sedini: undefined symbol: _t24__default_alloc_template2b1i0.free_list

So it seems to me that there is no other way to get around the problem than installing the old libs. Big question: Do this libraries exist for Ubuntu? If yes: Where can i get them? Google doesn't report any useful.

Thanks a lot!

Best regards,
Christian

---

### Post by fnjordy on 2006-08-14
Try the suggestions [here](http://support.nusphere.com/viewtopic.php?t=1823).

---

### Post by [cp] on 2006-08-14
Hum,

i tried to link stuff in the following two ways:

ln -s libstdc++.so.6.0.7 libstdc++-libc6.1-1.so.2
ln -s libstdc++.so.5.0.7 libstdc++-libc6.1-1.so.2

But both attempts will bring us the follwoging error at installation time:

/etc/iscan/sedini: symbol lookup error: /etc/iscan/sedini: undefined symbol: cerr

Any suggestions?

Best regars,
Christian

---

