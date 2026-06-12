---
title: "Backports not authenticated"
date: 2005-07-15
forum: Ubuntu Backports
---

### Post by cacofonix on 2005-07-15
I am unable to install some codecs from the backports site (mirrormaxx) I get this output when I try to install w32codecs, libdvdcss2 etc apt-get output:

```

sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
Need to get 27.3kB of archives.
After unpacking 48.1kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libdvdcss2
Install these packages without verification [y/N]?
E: Some packages could not be authenticated

```

I tried searching the forums but I was unable to find anything. is this normal??

Thanks :) 

cacofonix

---

### Post by ShaneAu on 2005-07-15
[QUOTE=cacofonix]I am unable to install some codecs from the backports site (mirrormaxx) I get this output when I try to install w32codecs, libdvdcss2 etc apt-get output:

```

sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libdvdcss2
0 upgraded, 1 newly installed, 0 to remove and 30 not upgraded.
Need to get 27.3kB of archives.
After unpacking 48.1kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  libdvdcss2
Install these packages without verification [y/N]?
E: Some packages could not be authenticated

```

I tried searching the forums but I was unable to find anything. is this normal??

Thanks :) 

cacofonix[/QUOTE]
 That's fine, just press "y" to that and it will continue to install the package.

---

### Post by ricardo on 2005-07-16
[QUOTE=ShaneAu]That's fine[/QUOTE]

Why? There's a Release.gpg file in hoary-extras and hoary-backports. And I imported the public key with id 1A9653A3:

$ gpg --list-key 1A9653A3
pub  1024D/1A9653A3 2005-05-05 Ubuntu Backports Project (Ubuntu Backports Project Signing Key) <ubuntu-bp-devel@googlegroups.com>
sub  1024g/6966FF6B 2005-05-05

I think all is O.K., but... backports remains not authenticated. Why? Maybe I must do anymore?

---

### Post by ricardo on 2005-07-16
I investigated a bit, and I think the problem is that the Release.gpg file is in the wrong location into the servers.

Say (for example) hoary-extras. The Release.gpg file is now located with the *.deb files, for example in the dists/hoary-extras/main/binary-i386 directory.

However, hoary repository has the Release.gpg file in the dists/hoary directory.

Maybe the problem could be fixed simply putting the Release.gpg file into the correct location.

---

### Post by cacofonix on 2005-07-17
[QUOTE=ShaneAu]That's fine, just press "y" to that and it will continue to install the package.[/QUOTE]

I would prefer to have it authenticated, even if it is safe. Is it possible for the backports maintainer to fix it?

---

### Post by XDevHald on 2005-07-17
[QUOTE=cacofonix]I would prefer to have it authenticated, even if it is safe. Is it possible for the backports maintainer to fix it?[/QUOTE]
 That would require him to GPG sign the packages, he doesn't do that.

---

