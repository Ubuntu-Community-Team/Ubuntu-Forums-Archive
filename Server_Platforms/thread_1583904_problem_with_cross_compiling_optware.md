---
title: "problem with cross compiling optware"
date: 2010-09-28
forum: Server Platforms
---

### Post by gobbledigook on 2010-09-28
hello :)

i've been following the guide from [NSLU2]("http://www.nslu2-linux.org/wiki/Optware/AddAPackageToOptware")

decided i would play about with compiling my own optware packages. but i've run into some trouble! using ubuntu 10.04...

when i try to make i get:
```
server@server:~/optware/optware/packages-ddwrt.mk$ sudo make directories toolchain ipkg-utils
../Makefile:443: /home/server/optware/optware/platforms/toolchain-packages-ddwrt.mk.mk: No such file or directory
../Makefile:464: /home/server/optware/optware/platforms/packages-packages-ddwrt.mk.mk: No such file or directory
make: *** No rule to make target `/home/server/optware/optware/platforms/packages-packages-ddwrt.mk.mk'. Stop.

```

i think the problem is because of [b]ddwrt.mk.mk
[/b]
i have done:

```
server@server:~/optware$ svn co http://svn.nslu2-linux.org/svnroot/optware/trunk optware

server@server:~/optware/optware$ make packages-ddwrt.mk-target
[ -e /home/server/optware/optware/downloads ] || mkdir -p /home/server/optware/optware/down
[ -e packages-ddwrt.mk/Makefile ] || ( \
                mkdir -p packages-ddwrt.mk ; \
                echo "OPTWARE_TARGET=packages-ddwrt.mk" > packages-ddwrt.mk/Makefile ; \
                echo "include ../Makefile" >> packages-ddwrt.mk/Makefile ; \
                ln -s ../downloads packages-ddwrt.mk/downloads ; \
                ln -s ../make packages-ddwrt.mk/make ; \
                ln -s ../scripts packages-ddwrt.mk/scripts ; \
                ln -s ../sources packages-ddwrt.mk/sources ; \
        )
touch packages-ddwrt.mk/.configured


```

any ideas?

---

