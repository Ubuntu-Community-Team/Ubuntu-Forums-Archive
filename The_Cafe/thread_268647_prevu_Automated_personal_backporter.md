---
title: "prevu: Automated personal backporter"
date: 2006-09-30
forum: The Cafe
---

### Post by jdong on 2006-09-30
I got bored this morning and wrote "prevu", a fully automated backporting script. It allows you to build your own backports right on your own computer, with a single command. prevu uses pbuilder and apt-get source to do its work, and generates fully dapper-backports compliant packages.
Development is done on launchpad at: [https://launchpad.net/products/prevu](https://launchpad.net/products/prevu)

**Getting prevu**
Download built debs from [http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=206140&release_id=451774](http://sourceforge.net/project/showfiles.php?group_id=125877&package_id=206140&release_id=451774)

Or, advanced users may go to Launchpad and use bzr to check out the latest development snapshot.

**First time setup**
Run **sudo prevu-init**. This creates the prevu build environment at /var/cache/prevu. This command needs to download packages from archive.ubuntu.com, and may take some time.

Also, you need to add a deb-src line for Edgy, such as
```

deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
```

**Make sure you do deb-src and not just deb!** That'll upgrade your system to Edgy!

**Keeping prevu updated**
Periodically run **sudo prevu-update**. This performs an update / dist-upgrade of your build environment.

**Usage**
Run sudo prevu packagename. For example, **prevu ktorrent**. Prevu will confirm the action with you by showing you what version it intends to backport. If you accept, it'll build and put the resulting debs in /var/cache/prevu/debs. You can use gdebi/dpkg to install those. Source packages are also generated if you intend on distributing the debs.

**Advanced Usage**
Running prevu with no arguments is just like running pdebuild with no arguments. In other words, you can extract your own sources, change into that directory, then issue **prevu**. Prevu will put a backport version trailer and build in its build environment.

**Known Issues**
Prevu is rough in the UI department. It lacks descriptive errors and often relies on Python exceptions to do error handling. I will add more meaningful error messages soon.

You need to be in the admin group to run prevu. Root access is needed to chroot in the the build environment. Root privileges are, however, dropped in the build environment for security reasons.

**Reporting bugs**
File bugs on launchpad: [https://launchpad.net/products/prevu/+filebug](https://launchpad.net/products/prevu/+filebug)

**Disclaimers**
 * Prevu has been hard-coded to build for Dapper. You may use it on Edgy, but it'll still make packages for Dapper
 * Backported packages may have bugs from the development version. Proceed at your own risk.
 * Backported packages may not be compatible with Dapper due to Edgy-specific changes.
 * Backported packages are not supported by Canonical or Ubuntu developers. **Please do not ask them for help regarding prevu or prevu-generated packages!** File bugs in prevu instead!
 * Careful backporting from non-Ubuntu repositories. It may work, it may not work. Have fun!

---

### Post by jdong on 2006-09-30
If you downloaded it recently, please redownload. I had to add a few more dependencies, such as fakeroot, dpkg-dev.

---

### Post by xXx 0wn3d xXx on 2006-09-30
Very cool. I will try this when I am back on Ubuntu. So this is just like an actual  repository ? Others can use it ?

---

### Post by jdong on 2006-09-30
It's not a "repository", it recompiles Edgy sources (or Debian Sid sources), whatever, into Dapper binaries, just like what the Backports project does.

This allows you to generate your own debs for packages that were rejected as backports requests, etc.

---

### Post by matthew on 2006-09-30
I've downloaded it and am running 'sudo prevu-init' right now. If I run into any bugs I'll post them on Launchpad. Thanks for doing this, jdong!

---

### Post by balloons on 2006-10-02
Well I was first to download prevu_0.2.2-3_all.deb. :-D 

Funny I was working on this myself LAST night. Trying to build automate building a few packages from sources. Guess I don't have to finish now. THANKS!

---

### Post by TheMono on 2006-10-02
Wow. This sounds great for people that want to stick with 'stable' dapper but still may want new versions of software.

So after you do this, it just leaves you with a deb package that will work in any dapper installation - ie, I could do this and then install the deb on a flatmates machine too?

---

### Post by balloons on 2006-10-02
yep the debs are in /var/cache/prevu/debs. You can use gdebi/dpkg to install them on any dapper machine. I'm upping my gnome to 2.16 this way.

---

### Post by Iandefor on 2006-10-02
Thanks so much, jdong! Just what the doctor ordered.

---

### Post by jdong on 2006-10-03
BTW, I've yet to mention this in this thread (don't know if you guys stumbled on this yet), but /var/cache/prevu/debs is actually an APT repository with recent releases of prevu. (You need to run a sudo prevu-update before the Packages file regenerates properly though. Sorry. that's been fixed in the newest update, too, for new users)

Simply add
```

deb file:/var/cache/prevu/debs ./

```

to sources.list, and you can use APT to help you install new backports. Useful if you're being a daredevil and backporting an entire stack of packages and don't want to use dpkg to deal with 30 packages :D

---

### Post by byteshack on 2006-10-17
What are the dependencies for prevu?  What command can I issue against the .deb to figure that out?

---

### Post by thk on 2006-12-18
This is a terrific tool. Thanks.

The problem I have is that I want to build packages that build against prevu-backported packages. The backported packages show up in the chroot environment in /var/cache/prevu/edgy-debs/, but do not get installed when I want to build other packages that list them as dependencies. Instead, prevu grabs the -dev packages from edgy and builds against them. That means I cannot install both the backported -dev packages and the backported packages depending on the -dev packages because the packages that depend on the backported -dev packages get built against the edgy versions, not the prevu versions. Anyone know a fix?

Do I need to use apt options to force installation of the local prevu-backported -dev packages?

Also, quick question. Does callling "prevu-init" a second time reset the entire chroot environment?

---

### Post by jdong on 2006-12-18
(1) To make prevu aware of its built packages, like -dev packages, you need to run a **prevu-update** after you've built all the -dev packages

(2) The only way to 'force' a page to install within prevu is to list it in Build-Depends of debian/control.

(3) Yes, running a prevu-init will rebuild the /var/cache/prevu/$distro.tgz file, which basically recreates the build environment.

---

### Post by thk on 2006-12-18
> **jdong said:**
> (1) To make prevu aware of its built packages, like -dev packages, you need to run a **prevu-update** after you've built all the -dev packages

The problem turned out to be different from what I thought it was. I did use prevu-update, and I think the package was in fact being built against the -dev packages.

The problem was installing on other machines through apt-get. I exported /var/cache/prevu/edgy-debs via apache and put a source line on other machines to pull from the repository. That works nicely. For some reason however, one of the packages I built with prevu was invisible to apt-get. That package (qgis) has the same version in fiesty as in edgy. Nothing I did could convince apt-get to install the prevu built version. I had to force things by manually copying and dpkg -i. It appears that when apt-get sees two packages with the same version information, it drops the latter one. At least that's the best I can come up with.

If anyone knows of a solution, I'd be happy to hear it.

---

### Post by JurB on 2006-12-18
Thanks for this great tool!

i've got a problem backporting bmpx (from their edgy repo)

```
 -> Considering  libcairomm-1.0-dev (>= 1.2)
W: Unable to locate package libcairomm-1.0-dev
E: No packages found
      Tried versions:
   -> Does not satisfy version, not trying
E: Could not satisfy build-dependency.
E: pbuilder-satisfydepends failed.
Copying back the cached apt archive contents
 -> unmounting dev/pts filesystem
 -> unmounting proc filesystem
 -> unmounting /var/cache/prevu/debs filesystem
 -> cleaning the build env
    -> removing directory /var/cache/prevu/builds/9918 and its subdirectories
Traceback (most recent call last):
  File "/usr/bin/prevu", line 78, in ?
    do_build()
  File "/usr/bin/prevu", line 50, in do_build
    raise ValueError("Build failed.")
ValueError: Build failed.

```

How do i go about fixing this?

tnx

---

### Post by JurB on 2006-12-19
Never mind, i gave in and upgraded to Edgy :rolleyes:

---

### Post by jdong on 2006-12-19
> **thk said:**
> The problem turned out to be different from what I thought it was. I did use prevu-update, and I think the package was in fact being built against the -dev packages.

The problem was installing on other machines through apt-get. I exported /var/cache/prevu/edgy-debs via apache and put a source line on other machines to pull from the repository. That works nicely. For some reason however, one of the packages I built with prevu was invisible to apt-get. That package (qgis) has the same version in fiesty as in edgy. Nothing I did could convince apt-get to install the prevu built version. I had to force things by manually copying and dpkg -i. It appears that when apt-get sees two packages with the same version information, it drops the latter one. At least that's the best I can come up with.

If anyone knows of a solution, I'd be happy to hear it.

If you backport a package that's the same version that you already can install from the repos, then yeah, it won't work. Backported packages are designed to be overridden by repository packages @ the same version... I guess I still don't understand why you're backporting qgis from feisty to edgy if both have the same version?

---

### Post by thk on 2006-12-19
> **jdong said:**
> If you backport a package that's the same version that you already can install from the repos, then yeah, it won't work. Backported packages are designed to be overridden by repository packages @ the same version... I guess I still don't understand why you're backporting qgis from feisty to edgy if both have the same version?

I backported libgdal to get version 1.3.2 which I need for running rgdal, a package for R. (I also backported R to 2.4.0.) If I install qgis from the main repositories, it tries to downgrade libgdal to 1.3.1, the version in Edgy. So I built a qgis deb against the backported libgdal. Same version of qgis, but built against different library versions. Works great if I manually install qgis. Would be even better if I could figure out how to get apt to install the backported version. What about a prevu switch which would allow one to increment the version so that apt will pull the backported version?

---

### Post by jdong on 2006-12-19
Increment the version itself, like by editing debian/changelog and append +1build1 to the version number.

---

### Post by thk on 2006-12-19
> **jdong said:**
> Increment the version itself, like by editing debian/changelog and append +1build1 to the version number.
Is this a question or a suggestion?

---

### Post by jdong on 2006-12-20
That is the answer to your problem. That forces your rebuild to register as an upgrade instead of a downgrade.

---

### Post by thk on 2006-12-20
> **jdong said:**
> That is the answer to your problem. That forces your rebuild to register as an upgrade instead of a downgrade.
Does the changelog exist cached somewhere in the chroot environment? Or do I need to download and unpack the source package and then use dpkg-buildpackge or something similar?

---

### Post by jdong on 2006-12-20
> **thk said:**
> Does the changelog exist cached somewhere in the chroot environment? Or do I need to download and unpack the source package and then use dpkg-buildpackge or something similar?

You need to download and unpack the source.... prevu cleans out the temporary build materials between builds to avoid clogging up your HD.

But instead of where you'd issue dpkg-buildpackage to build a package, issue **prevu** (with no arguments). It's a drop-in replacement for dpkg-buildpackage or debuild.

---

### Post by thk on 2006-12-20
> **jdong said:**
> You need to download and unpack the source.... prevu cleans out the temporary build materials between builds to avoid clogging up your HD.

But instead of where you'd issue dpkg-buildpackage to build a package, issue **prevu** (with no arguments). It's a drop-in replacement for dpkg-buildpackage or debuild.
OK. Last question. Do I unpack the downloaded source package in the prevu chroot environment (ie after calling prevu-chroot) or in the base file system?

---

### Post by jdong on 2006-12-20
> **thk said:**
> OK. Last question. Do I unpack the downloaded source package in the prevu chroot environment (ie after calling prevu-chroot) or in the base file system?

The base filesystem is fine. Once you issue the prevu command, prevu will make a copy of the present directory to /var/cache/prevu/src/<tmpdir> and build as if the source came from apt-get source.

---

