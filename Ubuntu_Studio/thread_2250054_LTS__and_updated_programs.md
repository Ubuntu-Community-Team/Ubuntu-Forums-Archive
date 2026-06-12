---
title: "LTS  and updated programs"
date: 2014-10-26
forum: Ubuntu Studio
---

### Post by Be__ok on 2014-10-26
Hi, As the team advice to stay with the LTS version,how do we update the programs we use ? 
This because normaly programs are updated with a new Ubuntu release.

---

### Post by bapoumba on 2014-10-26
Latest LTS being 14.04, some packages may be backported from 14.10. Which packages are you looking for ?
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Other alternatives are to install a package from a third party repo (this has drawbacks) or a deb file if it has been packaged for debian-based distributions, or even compile the source package.

---

### Post by Be__ok on 2014-10-26
Wil look at that, thanks. Drawbacks no doubt, i will not wait 2 years for a updated version. I have the problem how to replace a version!
Let say i had LMMS installed (1.0)  now i download 1.0.3 .Then i have to compile it . Ok  the make i get but no idea HOW to remove the old  before i do install.
And the how-to compile never touch that point.
So if the dev,s want users to stick 2 years to the LTS version, i hope the make a how-to solve this type of problems.Or point to relevant info.
As many info is OLD,and i have no idea if that is ok to use. (doubt it)

Edited after reading the backports story.  My goodness  what a mumbo yumbo , if i read it corectly backports are installed in all  from 11.04 on.
Automatic install is activated from 11.04 on.  O so if there is a backport for a studio program it installs automatic. At least that what i think to read.

---

### Post by ian-weisser on 2014-10-26
UbuntuStudio does recommend the 14.04 LTS version, *and* will also publish 6-month releases (including updated applications).
The 6-month releases are still fully supported with updated kernel and applications, bugfixes, and ongoing security updates; they just won't see many new features until the next LTS.
I think your use case (want frequently updated applications) calls for the 6-month releases. Try it - it's free. You can always re-install 14.04 instead if 14.10 and subsequent don't work for you.

The Ubuntu -backports repository is *not* enabled by default. You must enable it. 
If you enable the -backports repository, then you will receive all backports automatically.
Backports do not receive security updates from the Ubuntu Security Team, and support for backported software may be limited.

---

