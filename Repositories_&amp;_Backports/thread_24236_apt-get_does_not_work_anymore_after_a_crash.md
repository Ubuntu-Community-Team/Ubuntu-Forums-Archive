---
title: "apt-get does not work anymore after a crash"
date: 2005-04-06
forum: Repositories &amp; Backports
---

### Post by davidlks on 2005-04-06
Hi all,

I've been using Hoary for a while and has no problems with it until this morning when I did an update using synaptic. The update returns some error and rendered the filesystem read-only! I rebooted and the system adviced me to do a fcsk manually, which I did. There was quite a number of errors but it managed to boot normally after that.

Now, it seems that I couldn't update any new packages on the system. This is the error I got when I tried to update a package : 

```
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/gwenview_1.2.0-0ubuntu2_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `vlc': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/gwenview_1.2.0-0ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas? Everything else seems to work ok..

Btw, I'm using Hoary in my Dell D505 notebook.

---

### Post by davidlks on 2005-04-06
I've managed to fix this. It seems that the file list **vlc.list** in /var/lib/dpkg/info folder was somehow 'turned' into a 'folder'. Removing it and reinstalling the package **vlc** solve this.  :mrgreen:

---

