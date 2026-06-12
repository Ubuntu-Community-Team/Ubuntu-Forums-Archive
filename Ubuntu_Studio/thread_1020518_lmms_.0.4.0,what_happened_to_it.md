---
title: "lmms .0.4.0,what happened to it??"
date: 2008-12-24
forum: Ubuntu Studio
---

### Post by rixtr66 on 2008-12-24
just a few weeks ago i was able to get lmms.0.4.0 through apt-get.
now its not available for ubuntu 8.04?only for intrepid.
i just installed ubuntu studio 8.04 and would like to know how i can get
lmms 0.4.0.if i have to build it does anyone know the dependencies?
any help would be appreciated!!
Rick ](*,)

---

### Post by Stochastic on 2008-12-24
according to the package listing here: [http://packages.ubuntu.com]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=lmms")
No official Ubuntu repository has 0.4.0  (only ppa repos such as [https://launchpad.net/~tobydox/+archive](https://launchpad.net/~tobydox/+archive) )

You'll need to either get it from a ppa repo or download it from their website: [http://lmms.sourceforge.net/download.php](http://lmms.sourceforge.net/download.php)
The dependencies should be listed in the install documentation (either inside the tar.bz2 or at [http://lmms.sourceforge.net/wiki/index.php?title=Installation](http://lmms.sourceforge.net/wiki/index.php?title=Installation)

---

### Post by Patrick793 on 2008-12-24
This will keep LMMS up to date using Tobydox's repository.

```
gksudo gedit /etc/apt/sources.list
```
Add this to the end
```
## Toby's PPA
deb http://ppa.launchpad.net/tobydox/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tobydox/ubuntu intrepid main
```
Save the file, update the repositories.
```
sudo apt-get update
```
Time to install lmms.
```
sudo apt-get install lmms-common lmms lmms-extras
```

---

### Post by rixtr66 on 2008-12-24
ive tried that through the toybox repository,for 8.04 its not there anymore.
@stochastic;Thanks for the links,i built and installed lmms 0.4.2 successfully,
but,i seem to have the same strange problem with lmms constantly starting in 1st run mode,
wich starts with a dummy sound client wich in turn means no sound??
also is the extras package available for building,i really want that as i was using the
zynaddsubfx plugin heavily.
Rick

---

### Post by Patrick793 on 2008-12-24
Weird. Last time I checked it was there.

Try sending an email to the lmms-users mailing list?

---

### Post by Stochastic on 2008-12-24
> **rixtr66 said:**
> ive tried that through the toybox repository,for 8.04 its not there anymore.
Rick

You're quite right, the hardy branch of tobybox's ppa has been cleared out.  That's the trouble with relying on ppa repos, it's up to the maintainer what stays and what goes.  Looks like you need to compile it from source, don't worry it's not that hard.  If you get stuck, here's a handy guide: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by rixtr66 on 2008-12-24
even with the new version,still getting starts everytime in start mode
with the sound set to dummy,dohh!ive had this problem before but im not sure how i fxed it.now im searching for the lmms extras .0.4.2,need the zynaddsubfx plugin!
thanks for the links big help!!
compiled without a hitch.
Rick

---

