---
title: "Catch-22 while installing a patched rsync."
date: 2013-12-20
forum: Server Platforms
---

### Post by DiagonalArg on 2013-12-20
I'm installing a patched rsync, to get --copy-devices & --write-devices to work.  I don't want to "make install" over the ubuntu's rsync as I'm afraid I'll break something.  (Likely, as the "make install" installs to different directories than the stock rsync.)  So, I'm trying "aptitude purge rsync" first.  Problem is, rsync is part of package "ubuntu-standard", so aptitude won't let me get rid of rsync without getting rid of a whole scad of CLI commands - and that might break Ubuntu.


Typing "x" to manually resolve dependencies and try to get it to go ahead anyway, gets me nowhere (see below).


Thoughts?


/DA

------------------

```
 ubuntu-standard : Depends: rsync but it is not going to be installed.
Resolve these dependencies by hand? [N/+/-/_/:/?] -rsync
  rsync{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 653 kB will be freed.
Resolve these dependencies by hand? [N/+/-/_/:/?] y
Enter a package management command (such as '+ package' to install a package), 'R' to attempt automatic dependency resolution or 'N' to abort.
Resolve these dependencies by hand? [N/+/-/_/:/?]

```

---

