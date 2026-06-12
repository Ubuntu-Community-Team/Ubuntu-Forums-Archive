---
title: "apt-file does not find anything besides automatix"
date: 2007-02-02
forum: Repositories &amp; Backports
---

### Post by HugoRune on 2007-02-02
(System: Ubuntu edgy 64bit with kubuntu-desktop installed)

I installed apt-file, but it does not seem to find anything, no matter what I search

sudo apt-file update works fine

apt-file search or apt-file update only seems to return a few files concerning automatix, in most cases no results at all are returned.

For example:
"apt-file list z" returns no results at all

"apt-file -v list z" has the follwoing output:

```
D: got 'deb http://www.getautomatix.com/apt edgy main': Bad file descriptor
D: kept 'deb http://www.getautomatix.com/apt edgy main'
D: got 'deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted'
D: kept 'deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted'
D: got 'deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted'
D: kept 'deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted'
D: regexp: ^(\S+)\s+(\S*/x.*)$
D: Search in \/var\/cache\/apt\/www\.getautomatix\.com_apt_dists_edgy_Contents\-amd64\.gz

```

---

### Post by bapoumba on 2007-02-02
[http://debaday.debian.net/2007/01/24/apt-file-search-for-files-in-packages-installed-or-not/]("http://debaday.debian.net/2007/01/24/apt-file-search-for-files-in-packages-installed-or-not/")
You may already know that link.
Can you post your sources.list ?

---

### Post by HugoRune on 2007-02-04
I think I already did everyting described by that link.

My sources.list is:

```

## [lots of comments]
#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt edgy main




#AUTOMATIX REPOS END
deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted

```

---

### Post by bapoumba on 2007-02-05
Hi,
in addition to security and updates repositories, you should also have these ones in your sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
```

---

### Post by HugoRune on 2007-02-06
That did it. apt-file seems to be working now.

Thanks a lot!

---

