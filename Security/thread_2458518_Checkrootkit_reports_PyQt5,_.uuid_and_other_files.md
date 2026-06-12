---
title: "Checkrootkit reports PyQt5, .uuid and other files"
date: 2021-02-26
forum: Security
---

### Post by smith73 on 2021-02-26
I ran chkrootkit on Ubuntu (Mate) 20.04 and for the majority or checked items the results were 
"not found, not infected, no suspect files, nothing found"

The bothering part of chkrootkit report is the following:

```
The following suspicious files and directories were found:  
/usr/lib/python3/dist-packages/PyQt5/uic/widget-plugins/.noinit /usr/lib/debug/.build-id /usr/lib/libreoffice/share/fonts/truetype/.uuid /usr/lib/modules/5.4.0-66-generic/vdso/.build-id /usr/lib/modules/5.4.0-65-generic/vdso/.build-id
/usr/lib/debug/.build-id /usr/lib/modules/5.4.0-66-generic/vdso/.build-id /usr/lib/modules/5.4.0-65-generic/vdso/.build-id

Checking `lkm'...                                           chkproc: nothing detected
lstat(/tmp/.mount_P6cJj8): Permission denied

Checking `sniffer'...                                       /proc/6559/fd/1023: Permission denied
lo: not promisc and no packet sniffer sockets

Checking `OSX_RSPLUG'...                                    not tested
```


While running chkrootkit several days ago on the same installation, there was also this part in the report:

```
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
eno1: PACKET SNIFFER(/usr/sbin/NetworkManager[885])
```

I installed a bit of software from official Ubuntu repositories (Software centers, apt-cache). From apt-cache I installed ubuntu-restricted-extras,
which may be related to fonts related item in the report and uninstalled it. I also installed youtube-dl via pip from github repo. And I am running a
free version of Iris software for Linux, which seems not be installed at all, as I clicked on the Iris-0.9.2.2.AppImage file and the software got running. 

While a bit of googling it was mentioned that "build-id" maybe false positives files, but are /usr/lib/python3/dist-packages/PyQt5/uic/widget-plugins/.noinit  /usr/lib/debug/.build-id /usr/lib/libreoffice/share/fonts/truetype/.uuid files same false positives? Do these files from checkrootkit report pose a risk?

---

### Post by schragge on 2021-02-26
See **/usr/share/doc/chrootkit/README.FALSE-POSITIVES** and [chrootkit FAQ#8]("http://www.chkrootkit.org/faq/#8").
> the false positives that have been reported to me have fallen into to five basic camps: hidden process, hidden files under /usr/lib, a specific file is found, legitimate sniffers, and listening on well known ports.
[...]
the hidden files issue continues to crop up now and again.  basically, if chkrootkit sees a hidden file (a file that begins with .) under /usr/lib, it flags it as suspicious.  there are various packages that contain these hidden files and they are innocuous.  however, it appears that arbitrary hidden files under /usr/lib is a sign of a rootkit, so, again, it's the safe vs sorry argument.

---

