---
title: "Precise 12.04 LTS ... Error Installing VMware Tools"
date: 2014-04-11
forum: Virtualisation
---

### Post by Chad_White on 2014-04-11
[FONT=arial]Definitely not a Linux guru, but I am following the instructions from VMware's website for installing VMware Tools. [/FONT][INDENT][FONT=arial black]sudo ./Desktop/vmware-tools-distrib/vmware-install.pl -d[/FONT][/INDENT]


[FONT=arial]
When I run the installer I get the following error -- [/FONT][INDENT][FONT=arial black]The following VMware kernel modules have been found on your system that were not installed by the VMware Installer.  Please remove them then run this installer again.

vmci

I.e. - 'rm /lib/modules/3.11.0-15-generic/misc/<ModuleName>.{o,ko}'


[/FONT][/INDENT]
[FONT=arial black][FONT=arial]I do not have a misc directory in the recommended location. Any help would be greatly appreciated.

Thanks![/FONT][/FONT]

---

