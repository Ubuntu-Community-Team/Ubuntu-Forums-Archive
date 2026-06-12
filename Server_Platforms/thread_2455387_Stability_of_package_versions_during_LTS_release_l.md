---
title: "Stability of package versions during LTS release lifespan"
date: 2020-12-18
forum: Server Platforms
---

### Post by newbuntu2020 on 2020-12-18
I've not been able to find any information on how versions of things like PHP, httpd, MariaDB, might change during the lifespan of Ubuntu Server LTS releases. I know that in Red Hat Enterprise Linux the versions of things like  PHP stay the same for the entire lifespan of a major version. E.g.  RHEL 7 shipped with PHP 5.4 and it will always have PHP 5.4. So I'm  wondering how how Ubuntu Sever compares for stability of package  versions.  Right now Ubuntu Server 20.04 LTS has PHP 7.4 but


[LIST]
[*]Will it always have PHP 7.4? 
[*] Is there any reason to expect it might at some point have a newer version of PHP as well as 7.4? 
[*]If a newer version of PHP became available in the 20.04 LTS repos, would PHP automatically get upgraded to that newer version? 
[/LIST]

---

### Post by TheFu on 2020-12-18
I don't touch php.

LTS Servers should only change in the 3rd level, not the major or minor levels. There shouldn't be any API changes on Ubuntu Servers.
However, you can use a PPA if you need newer versions which will override what Canonical's Repos contain.

Some desktop applications are not maintained in that way.  Tools with core features tied directly to cloudy internet services may change in order to keep working.  So Firefox, Thunderbird, any twitter clients, etc which would stop working if they weren't updated could get updated from version to version.  If you don't want that, you can always freeze a specific package, but then YOU are 100% responsible for patching.

No Snap packages are maintained in that way. Snaps get updated whenever the snap manager chooses. We have no control - might was well be on Win10 Home.

In general, if php v7.4.1 is in the released base OS, then only the 3rd number would change over the entire lifespan of the LTS server release. v7.4.2 --> v7.4.8 --> v7.4.12 --> v7.4.38 --> v7.4.99 ..... as bugs or security fixes require. No new features and nothing that changes any API should happen, unless required for security. Security trumps everything.

---

### Post by newbuntu2020 on 2020-12-21
> **TheFu said:**
> 
Some desktop applications are not maintained in that way.

I don't install desktop environments on my servers. ;)

> **TheFu said:**
> 
No Snap packages are maintained in that way.

It is my intention that if I make Ubuntu servers they won't have any Snap packages.

> **TheFu said:**
> 
In  general, if php v7.4.1 is in the released base OS, then only the 3rd  number would change over the entire lifespan of the LTS server release.  v7.4.2 --> v7.4.8 --> v7.4.12 --> v7.4.38 --> v7.4.99 .....  as bugs or security fixes require. No new features and nothing that  changes any API should happen, unless required for security. Security  trumps everything.
That sounds good. Do you have a link for any official documentation that explains this?

---

### Post by Doug S on 2020-12-21
> **newbuntu2020 said:**
> That sounds good. Do you have a link for any official documentation that explains this?

those are typically referred to as micro-releases and are covered in the [Ubuntu SRU wiki]("https://wiki.ubuntu.com/StableReleaseUpdates#New_upstream_microreleases").
see also [here]("https://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software").

---

### Post by rsteinmetz70112 on 2020-12-22
You need to be a little careful here. If you install a .2 release of a LTS desktop release you will get newer versions of the Kernel and some other stuff. Server releases include the GA (General Availability)  It is explained here:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

You can also install the The Ubuntu LTS enablement (also called HWE or Hardware Enablement) which does update kernel and other stuff and can be helpful for newer hardware. If for example you install 18.04.1 LTS some newer hardware may not be supported.

---

