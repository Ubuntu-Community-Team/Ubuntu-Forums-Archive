---
title: "Error trying to upgrade to 12.04"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by thekeeperza on 2012-03-04
I have been trying to upgrade to 12.04 from 11.10 and get the following error
> 'E:Couldn't configure pre-depend libtinfo5 for libncurses5, probably a dependency cycle.'

I have made sure 11.10 was updated prior to upgrading.

Any ideas because I am :confused::confused::confused::confused:

---

### Post by paul_in_london on 2012-03-04
> **thekeeperza said:**
> I have been trying to upgrade to 12.04 from 11.10 and get the following error


I have made sure 11.10 was updated prior to upgrading.

Any ideas because I am :confused::confused::confused::confused:

See here:

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta1)

Try this work-around from that page?

> Upgrades

    The ia32-libs package that used to provide 32-bit libraries on 64-bit (amd64) installations has been removed in favour of multiarch. Systems using ia32-libs must migrate to multiarch in order to upgrade to 12.04. In most cases, this should be set up automatically by the upgrade process. Some users who upgraded through previous development releases may have removed /etc/dpkg/dpkg.cfg.d/multiarch, and must restore it with the contents foreign-architecture i386 in order to have 32-bit library support in 12.04.

    [B][COLOR="Red"]In some cases, the package manager in Ubuntu 11.10 may not be able to decide on a correct unpack ordering when upgrading 64-bit systems with the ia32-libs package installed; if this is the case, it will fail before starting to unpack any new packages with a message something like "Couldn't configure pre-depend libtinfo5 for libncurses5, probably a dependency cycle". A workaround is to install the apt and libapt-pkg4.12 packages from precise before starting the upgrade. (924079)
[/COLOR][/B]    
Landscape is currently incompatible with multiarch. We hope that this will be fixed in time for 12.04; but if you are using Landscape then you will need to either remain with 11.10 or remove any 32-bit libraries. 

EDIT: The error is mentioned in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079)

You may want to subscribe to this other bug report:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/894340](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/894340)

---

### Post by grahammechanical on 2012-03-04
Do not forget the 12.04 is still under development. An upgrade from 11.10 to 12.04 will bring in updated libraries but you may have a program installed in what was 11.10 that is using older libraries. Some of these libraries may be available in an updated 12.04 version but others may not yet be updated and so not available for download. Therefore you get unresolved dependency problems.

Also, remember that the developers of Ubuntu are developing a basic default version of Ubuntu. They give us a basic and default 11.10 and it is that that gets developed into 12.04.

We make all kinds of modifications to the default 11.10 and we add applications that are not part of the default install then things go wrong when we upgrade to the next release. Especially do things go wrong when we upgrade to the development release.

I upgraded a default 11.10 to 12.04 soon after work began developing 12.04. The other week an update removed the Ubuntu Software Centre. Libraries needed changing but one library was not ready so Software Centre was removed so that the downloading of some of the libraries would not break things.

A few days later the missing library was downloaded and I was able to re-install Software Centre. 

Such is life when using a development release.

You can try installing Synaptic Package Manager and using that to update libncurse5 or libtinfo5 and related packages. You may have to wait for certain packages to be brought up to standard for 12.04 before this issue can be corrected.

Welcome to being a beta tester.

Regards.

---

### Post by thekeeperza on 2012-03-04
Fantastic thank you.
working so far.

---

