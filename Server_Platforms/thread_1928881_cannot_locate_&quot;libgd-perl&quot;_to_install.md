---
title: "cannot locate &quot;libgd-perl&quot; to install"
date: 2012-02-20
forum: Server Platforms
---

### Post by antiartist on 2012-02-20
(Ubuntu 10.04.2)

I am installing the webmin admin module for ClamAV and am being prompted to install the perl module GD from package libgd-perl.

But when I apt-get libgd-perl, the following occurs:

```
Reading package lists...
Building dependency tree...
Reading state information...
Package libgd-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgd-perl has no installation candidate
```

Accepting that I may not have a specific repository listed in the sources file, I went looking for this to download manually.  I am turning up with nothing.  I installed the  libgd2-xpm-dev under the belief this would have the perl module I'm looking for...and no such luck.  Help would be appreciated :)

---

### Post by ruffEdgz on 2012-02-23
I don't think the name 'libgd-perl' isn't being used anymore and I believe its been replaced with the name 'libgd-gd2-perl'. The package you are talking about hasn't been in use since Ubuntu Breezy Badger and Dapper Drake days.

When I did a search on my 11.10 machine, this is what I found:
```

p   libgd-gd2-perl    - Perl module wrapper for libgd - gd2 variant

```

---

### Post by antiartist on 2012-02-25
I installed the package name you have on your system and the webmin module for ClamAV is now working.  Thanks for your help.

While I installing the GD:Text GD perl module through CSPAN, the system attempted (again) to install the outdated package name and it of course failed.  I'm not even sure who/how to have that script updated :)

---

