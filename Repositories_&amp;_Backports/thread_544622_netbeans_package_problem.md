---
title: "netbeans package problem"
date: 2007-09-06
forum: Repositories &amp; Backports
---

### Post by vadania on 2007-09-06
I like Ubuntu, but I am very much displeased of the Netbeans package in Feisty repository.

I realise Netbeans is still released under CDDL licence (unfortunately!), but it still should be easier to install it.
The package in Ubuntu repository is actually only an installer. This would not be as much of a problem if the package was set up to automatically download (wget could help?) Netbeans archive in the needed location. Since this would be done under Synaptic / sudo apt-get the Netbeans archive would already be owned by root.

Now I have to manually download netbeans and set it up correctly. Then every time i install something through apt I get a question about Netbeans. That question causes the package management tool to wait for an user to answer, breaking every automatic install script.

---

### Post by mslama on 2008-02-21
This was fixed. Fixed version is in backport repository as it was too late to get fixed version into regular repository.

---

