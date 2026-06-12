---
title: "vmserver on gutsy via repository"
date: 2007-10-27
forum: Virtualisation
---

### Post by cope on 2007-10-27
when I try to install vmserver it dies due to uninstallable dependencies.. does anyone know how to fix this?

```
mark@desktop:~$ sudo apt-get install vmware-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vmware-server: Depends: vmware-server-kernel-modules but it is not installable
                 Depends: libssl0.9.7 but it is not installable
E: Broken packages

```

---

### Post by firebadger on 2008-01-19
Me too.

Anybody any thoughts?

---

### Post by fjgaude on 2008-01-19
I don't but I have lately, since Feisty, downloaded the binary from the vmware.com site and it has never failed to work correctly. Always used the same old lisence number they gave me months and months ago.

The download worked fine on both 64- and 32-bit Feisty and Gutsy installs.

---

### Post by firebadger on 2008-01-20
Hi,

Thanks for that.  I'll go that route.

Incidentally I know exactly what caused this error though.  I copied in the Feisty Cannonical repository to my sources.list when I am running Gutsy,

---

