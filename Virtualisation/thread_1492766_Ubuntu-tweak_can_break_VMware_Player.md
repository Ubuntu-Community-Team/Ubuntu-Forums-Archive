---
title: "Ubuntu-tweak can break VMware Player"
date: 2010-05-25
forum: Virtualisation
---

### Post by dcstar on 2010-05-25
The Ubuntu-tweak package has an option to stop Recently used files from appearing by changing the ~.recently-used.xbel file into a folder (this seems to be a common method in the various HOWTOs on disabling the Recent list).

This breaks the Library list (all the VMs) in VMware Player 3.1.0 (and possibly other versions) as it saves all that information in that file.

Anyone who has their VMware Player suddenly lose the list of VMs may want to check that they still have this file.

[https://bugs.launchpad.net/ubuntu-tweak/+bug/585268](https://bugs.launchpad.net/ubuntu-tweak/+bug/585268)

---

