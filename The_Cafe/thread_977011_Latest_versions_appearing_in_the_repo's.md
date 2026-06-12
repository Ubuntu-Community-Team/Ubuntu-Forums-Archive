---
title: "Latest versions appearing in the repo's"
date: 2008-11-09
forum: The Cafe
---

### Post by chavon20 on 2008-11-09
Just wondering, how long does it take for an update to appear in the repos?  There are new versions of Brasero for example however in Synaptic it still shows the version that came with my Ubuntu.  Same with OpenOffice; 2.4.2 has been released, when will that appear in the repo's?  How long does it usually take for an update to appear?

Just on this, if for example OpenOffice.org decide to no longer support 2.4 and I am using an Ubuntu LTS, will version 3 then be able to able to be downloaded via the repos'?

---

### Post by BennBuntu on 2008-11-09
From my understanding, updates will show up when the package maintainer for ubuntu updates it. 
In the name of stability / predictability, they won't just throw new releases (ie office 3.0) in as a recommended update, but if you enable the proposed and backport repositories, you'll get options for installing newer packages.

If you want open office 3.0 now, you can just grab the debian package.

---

### Post by Grant A. on 2008-11-09
Unfortunately, Ubuntu's package maintainers seem very lazy when it comes to updating packages. Fluxbox is still version 1.0.0, when the latest (stable is unstable in Fluxbox, the real unstable ones are in the git repository) is 1.1.1.

  The best way to install things is to compile it from source. Go to the website, read their guide on installing it from source, and before you compile it, install this:

```

sudo apt-get install build-essential

```

That will install the necessary packages for building programs, however you will need to compile/find the libraries/programs the program requires (dependencies) yourself.

---

### Post by cardinals_fan on 2008-11-09
Ubuntu is not a rolling-release distro.  Only bugfixes / security updates during each release.  No new versions.

---

### Post by chavon20 on 2008-11-09
Thanks guys. I'll see about updating manually.  As for updating to Ooo 3.0 last night, no joy!  Even after following the tutorial from the Ooo forum.  Anyway, I'll give it another shot soon, thanks again!

---

