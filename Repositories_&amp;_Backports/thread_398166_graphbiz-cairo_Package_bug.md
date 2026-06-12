---
title: "graphbiz-cairo Package bug"
date: 2007-03-31
forum: Repositories &amp; Backports
---

### Post by kahrytan on 2007-03-31
I recently tried to installed a package named graphviz-cairo. It refuses to install correctly and now I am unable to remove it. Synaptic says it is installed. It is marked for uninstall and remains marked. Even after closing Synaptic.

This broken package has broken Aptitude / Synaptic.  Add/Remove programs refuses to install anything without trying to uninstall this broken package. Uninstall is permanently marked in Synaptic. I can't use the Update Manager because of this broken package.The command   ```
apt-get  uninstall -f  graphviz-cairo 
```  does not work. Same error.

During Install: 

```
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

During Removal 
```
Removing graphviz-cairo ...
/var/lib/dpkg/info/graphviz-cairo.postrm: 11: dot: not found
dpkg: error processing graphviz-cairo (--remove):
 subprocess post-removal script returned error exit status 127
```


Please help me

---

### Post by alek66 on 2007-04-07
Heres the fix
> sudo rm -f /var/lib/dpkg/info/graphviz-cairo.postrm
sudo apt-get remove graphviz-cairo

---

### Post by madrix on 2007-04-15
Had the same problem, the post above me worked great.

fyi, encountered this buy while trying to install dotgraph graph editor

---

