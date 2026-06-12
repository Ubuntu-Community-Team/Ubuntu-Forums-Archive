---
title: "OpenVZ kernel build error"
date: 2012-08-02
forum: Virtualisation
---

### Post by user1389734 on 2012-08-02
I've been following this guide so far:
[https://help.ubuntu.com/community/OpenVZ]("https://help.ubuntu.com/community/OpenVZ")

I've gotten up to the stage where I build the kernel image into a debian package with the "make-kpkg" command. It is at this stage I get the following error:
```

root@server:/usr/src/linux# make-kpkg --initrd --append-to-version=$VersionAppendix --revision=1 kernel_image kernel_headers
exec make kpkg_version=12.036+nmu2 -f /usr/share/kernel-package/ruleset/minimal.mk debian DEBIAN_REVISION=1  APPEND_TO_VERSION=-openvz  INITRD=YES
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version 12.036+nmu2.
test -d debian             || mkdir debian
test ! -e stamp-building || rm -f stamp-building
install -p -m 755 /usr/share/kernel-package/rules debian/rules
for file in ChangeLog  Control  Control.bin86 config templates.in rules; do                                      \
            cp -f  /usr/share/kernel-package/$file ./debian/;                               \
        done
for dir  in Config docs examples ruleset scripts pkg po;  do                                      \
          cp -af /usr/share/kernel-package/$dir  ./debian/;                                 \
        done
test -f debian/control || sed         -e 's/=V/2.6.32.28-openvz/g'  \
                -e 's/=D/1/g'         -e 's/=A/amd64/g'  \
                -e 's/=SA//g'  \
                -e 's/=I//g'                                \
                -e 's/=CV/2.6/g'                            \
                -e 's/=M/echo "CONCURRENCY_LEVEL := 2" >> /etc/kernel-pkg.conf <tar -xpf linux-2.6.32.tar.bz2>/g'                           \
                -e 's/=ST/linux/g'      -e 's/=B/x86_64/g'    \
                  /usr/share/kernel-package/Control > debian/control
sed: -e expression #7, char 41: unknown option to `s'
make: *** [debian/stamp/conf/minimal_debian] Error 1
Failed to create a ./debian directory: No such file or directory at /usr/bin/make-kpkg line 984.
root@server:/usr/src/linux#

```

It appears that others are having this problem:
[http://www.google.com/search?q="char+41%3A+unknown+option+to+%60s'"]("http://www.google.com/search?q="char+41%3A+unknown+option+to+%60s'"")

Also, I'm using:
```
# cat /etc/issue
Ubuntu 12.04 LTS \n \l

```

How do I fix this?

---

