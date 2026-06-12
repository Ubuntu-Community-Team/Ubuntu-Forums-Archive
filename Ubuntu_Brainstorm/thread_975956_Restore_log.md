---
title: "Restore log"
date: 2008-11-08
forum: Ubuntu Brainstorm
---

### Post by Efros on 2008-11-08
Some method of automatically keeping track of installed and uninstalled software in the form of a script. If the user wishes to reinstall Ubuntu at any point then all that is required following installation of the base OS is to run the generated script to install all the packages that were installed on the old installation.

Any thoughts?

---

### Post by smartboyathome on 2008-11-08
I think this could potentially be good, but also leaves me to wonder what about if someone's favorite program is not included in Ubuntu, and/or they have 3rd party repos they use?

---

### Post by gnomeuser on 2008-11-09
There are two ways to do this. Either you can implement this in the package management system (like rPath does with Conary[1]) or you can do it in the filesystem (like btrfs or zfs).

I would be a fan of the latter solution as it is not only useful for package management but for all transactions where you need rollback. Now you would still need to add UI to do the rollback but this task should be simplified as PackageKit likely can be hooked up to do this.

Conary does this today though, and it has other really impressive tricks up it's sleeve such as only updating the bits of a package that actually changes (so if the only change is in 1 file the remaining ones aren't touched - as opposed to what dpkg does which is basically unpackaging a tarball on top of your existing files). This greatly reduces the amount of data you need to download and it lessens the problem existing solutions create when overwriting configuration files. Conary also does many very cool things aside this like autogenerate packages using simple python scripts (in fact that is how most packages are added, making the maintainer burden much lower) and the system as a built in distributed version control system so you can have the baseline upstream branch, followed by branches for every distribution with the tweaks and patches they apply. This makes it very easy to merge back changes to upstream and ensure every one has the same bugfixes. Sad part, switching to Conary or something like it is a lot of work, granted tools like PackageKit make it easy to abstract the changes away from the user but you still need to have every package available in the new format, change every tool that does PMS interaction to use PackageKit (or Conary directly).. in short lots of work

[1] [http://en.wikipedia.org/wiki/Conary_(package_manager](http://en.wikipedia.org/wiki/Conary_(package_manager))

---

### Post by Efros on 2008-11-09
The source of the installed packages would have to be saved and if they came from third party repos then when you come to re-install your packages these repos could be reinstated by a prompt from the script or indeed automatically.

I really see this as a one up on the mainstream OSes, think of how long it takes to reinstall all the crud that you need from all the different CDs DVDs etc for a working and functional XP/Vista system with all your bells an whistles.

---

