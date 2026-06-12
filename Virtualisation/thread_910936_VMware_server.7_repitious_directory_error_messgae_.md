---
title: "VMware server.7 repitious directory error messgae during installation"
date: 2008-09-05
forum: Virtualisation
---

### Post by rwilhoi on 2008-09-05
In which directory do you want to install the manual files?
[/var/lib/vmware/man]

The path "/var/lib/vmware/man" does not exist currently. This program is going
to create it, including needed parent directories. Is this what you want?
[yes] y

In which directory do you want to install the documentation files?
[/var/lib/vmware/doc/vmware]

The path "/var/lib/vmware/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes] y

Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.

This error has occurred for both v1.0.6 and .7, and so far I have not been able to figure out why. Any help would be greatly appreciated.

---

### Post by gtdaqua on 2008-09-05
Looks like a permission problem. From where are you trying to execute the installation (the path)?

Its best to extract the tar.gz to /tmp and run the installation from there.

---

### Post by rwilhoi on 2008-09-05
That is what I did, and I agree, but it has not prompted for the serial number yet so that is where I am baffled. It allowed me access to many of the other files but this one file has given me problems when trying to install both V1.0.7 and V1.0.6

---

