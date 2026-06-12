---
title: "sudo purge-old-kernels"
date: 2016-06-20
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2016-06-20
It may have been around for years, but this is my first encounter ...
[http://blog.dustinkirkland.com/2016/06/purge-old-kernels.html]("http://blog.dustinkirkland.com/2016/06/purge-old-kernels.html") and from there> Over time, you might find your /boot directory filled with vmlinuz kernels, consuming a considerable amount of disk space.  Sometimes, sudo apt-get autoremove will clean these up.  However, it doesn't always work very well (especially if you install a version of Ubuntu that's not yet released).and from [http://manpages.ubuntu.com/manpages/xenial/en/man1/purge-old-kernels.1.html](http://manpages.ubuntu.com/manpages/xenial/en/man1/purge-old-kernels.1.html)> purge-old-kernels will remove old kernel and header packages from the system, freeing disk space. It will never remove the currently running kernel. By default, it will keep at least the latest 2 kernels, but the user can override that value using the --keep parameter. Any additional parameters will be passed directly to apt-get(8).

Edit: to use the command, you'll need to install **byobu** in 16.04 or **bikeshed** (from Launchpad or Github) in older versions of *buntu. These packages aren't present in vanilla installs. Thanks, sudodus and coffeecat!

---

### Post by sudodus on 2016-06-21
Thanks vasa1 :-)

I would add the following information from Dustin Kirkland's blog:

> You'll already have the **purge-old-kernels** command in Ubuntu 16.04 LTS (and later), as part of the **byobu** package.  In earlier releases of Ubuntu, you might need to install **bikeshed**, you can grab it directly from Launchpad or Github.

***Edit:*** You get it installed into 16.04 LTS with the following command line,

```
sudo apt-get install byobu
```

---

### Post by vasa1 on 2016-06-21
And Lubuntu (and maybe Xubuntu) users may not have byobu installed by default.```
$ apt-cache policy byobu
byobu:
  Installed: (none)
  Candidate: 5.106-0ubuntu1
  Version table:
     5.106-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
$ 

```

---

### Post by coffeecat on 2016-06-21
> **vasa1 said:**
> And Lubuntu (and maybe Xubuntu) users may not have byobu installed by default.

As a point of information, neither is it included by default in Ubuntu itself. The "you'll already have" phrase in the blog is ambiguous, which I would read as already having the package installed by default, which it isn't.

```
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=16.04
DISTRIB_CODENAME=xenial
DISTRIB_DESCRIPTION="Ubuntu 16.04 LTS"

``````

$ apt-cache policy byobu
byobu:
  Installed: (none)
  Candidate: 5.106-0ubuntu1
  Version table:
     5.106-0ubuntu1 500
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        500 http://gb.archive.ubuntu.com/ubuntu xenial/main i386 Packages
```

And from the manifests for the ubuntu-16.04-desktop-amd64.iso:

>  
...
brltty	5.3.1-2ubuntu2
bsdmainutils	9.0.6ubuntu3
bsdutils	1:2.27.1-6ubuntu3
btrfs-tools	4.4-1
build-essential	12.1ubuntu2
busybox-initramfs	1:1.22.0-15ubuntu1
busybox-static	1:1.22.0-15ubuntu1
bzip2	1.0.6-8
ca-certificates	20160104ubuntu1
casper	1.376
checkbox-converged	1.2.4-0ubuntu1
checkbox-gui	1.2.4-0ubuntu1
...

And ubuntu-16.04-desktop-i386.iso:

> ...
brltty	5.3.1-2ubuntu2
bsdmainutils	9.0.6ubuntu3
bsdutils	1:2.27.1-6ubuntu3
btrfs-tools	4.4-1
build-essential	12.1ubuntu2
busybox-initramfs	1:1.22.0-15ubuntu1
busybox-static	1:1.22.0-15ubuntu1
bzip2	1.0.6-8
ca-certificates	20160104ubuntu1
casper	1.376
checkbox-converged	1.2.4-0ubuntu1
checkbox-gui	1.2.4-0ubuntu1
...

---

### Post by vasa1 on 2016-06-21
> **coffeecat said:**
> As a point of information, neither is it included by default in Ubuntu itself. The "you'll already have" phrase in the blog is ambiguous, which I would read as already having the package installed by default, which it isn't.
...
Thank you! I edited the first post to reflect that.

---

### Post by nargaroth_reg on 2016-06-21
Thanks for the information, I didn't know about this. I just tried it on xenial and it worked well, it's a handy utility.

---

### Post by kevdog on 2016-06-21
Great tip guys.  Well done.  Works well.  Easy installation with byobu package.

---

### Post by SantaFe on 2016-06-21
Neat find.  After installing the byobu package I opened my terminal with baited breath & entered the magic line 'sudo purge-old-kernels', only to get the disappointing reply "No kernels are eligible for removal" ;)  Darn, I would like to *have seen Montana*. (Watching Hunt For Red October whilst typing). ;)

One good thing is, I rather like the byobu terminal. :D

---

