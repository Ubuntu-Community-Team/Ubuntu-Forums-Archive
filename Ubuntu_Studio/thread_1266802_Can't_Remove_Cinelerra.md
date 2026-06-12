---
title: "Can't Remove Cinelerra"
date: 2009-09-15
forum: Ubuntu Studio
---

### Post by chessnerd on 2009-09-15
I tried Cinelerra but it wasn't really what I was looking for. I want to remove it, but when I tried to I got this:
```
Removing cinelerracv ...
Description:	Ubuntu 9.04
locale "en_US.ISO-8859-15" not in archive
locale "ru_RU.KOI8-R" not in archive
rm: cannot remove `/usr/bin/Cinelerra': No such file or directory
dpkg: error processing cinelerracv (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 cinelerracv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I also am now getting regular errors relating to cinelerracv whenever I do anything involving a package manager. I tried reinstalling it via Synaptic to make the errors stop but I can't do that either and get the error:
```
E: cinelerracv: subprocess post-installation script returned error exit status 4
``` 
Does anyone have any idea how to remove this program or at least reinstall it successfully to make the errors go away? (I'm willing to sacrifice a few MB of disk space for an error-free package manager)

---

