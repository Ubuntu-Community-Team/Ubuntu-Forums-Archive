---
title: "how to delete corrupted file"
date: 2007-06-20
forum: Server Platforms
---

### Post by fortran01 on 2007-06-20
OS: Ubuntu 6.06.1 LTS (server)

I can't install the locales packages because of this error:

```
Unpacking replacement locales ...
dpkg: error processing /var/cache/apt/archives/locales_2.3.18.3_all.deb (--unpack):
 unable to install new version of `./usr/share/doc/locales/copyright': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/locales_2.3.18.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Upon taking a closer look, the directory /usr/share/doc/locales/ contains the following files:

```
cd /usr/share/doc/locales/
root@host_name:/usr/share/doc/locales# ls -l
total 0
?--------- ? ? ? ?            ? changelog.gz
?--------- ? ? ? ?            ? copyright
```

I can't do rm -rf or unlink. Any ideas how to forcefully delete this "corrupted" file?

Thanks.

---

### Post by earobinson on 2007-06-20
not the best solution but what happens if you do a ```
sudo nautilus
``` then try and remove the files using the gui?

---

### Post by earobinson on 2007-06-20
you could also try and cat the files or do a ```
sudo -s
echo "take that bad file" > <badfilename>
rm <badfilename>
```

---

### Post by Mr. C. on 2007-06-20
unmount and run an fsck on that file system.  If its the root file system, force a recheck on reboot:

```
sudo touch /forcefsck
sudo reboot

```

MrC

---

