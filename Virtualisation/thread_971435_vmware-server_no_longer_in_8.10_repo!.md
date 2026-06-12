---
title: "vmware-server no longer in 8.10 repo?!"
date: 2008-11-05
forum: Virtualisation
---

### Post by tj.milligan on 2008-11-05
After a fresh Intrepid install (previously running Gutsy 7.10), I added the line ```
deb http://archive.canonical.com/ubuntu intrepid partner
``` to /etc/apt/sources.list to include commercial apps. But **[FONT="Courier New"]sudo apt-get update; sudo apt-get install vmware-server[/FONT]** no longer works. Anyone know a way to install vmware-server from the repos?

I still have nightmares (kernel problems after every kernel update, gcc incompatibilities, vmware-any-any patches, etc) from when I used to install vmware manually via vmware-install.pl pre-7.04 and 7.10.

EDIT: In a way, I was able to resolve this by installing vmware workstation. It is left a mystery why vmware-server is absent from the repos though...

---

### Post by tj.milligan on 2008-11-05
Solved.

Downloaded Workstation 6.5 .bundle file from VMware. sudo sh VMware-Workstation-6.5.0-118166.i386.bundle launches a gui installer that installs vmware FLAWLESSLY. Good thing this allows me to use my 6.0 license. :D

---

### Post by bodhi.zazen on 2008-11-05
> **tj.milligan said:**
> EDIT: In a way, I was able to resolve this by installing vmware workstation. It is left a mystery why vmware-server is absent from the repos though...

vmware-server has not been in the repos for a while now.

---

### Post by rbmorse on 2008-11-05
VMware doesn't officially support 8.10, yet.  Or, let me put it this way. VMware hasn't officially recognized 8.10, yet.  The bundle installer works because it's designed to be kernel agnostic and the architecture changes from 8.04 aren't that great.  If you install 8.10 as a VM under workstation 6.5 you'll have trouble installing the VMware tools package, at this time. I'm told they're working on it, but don't have an estimate of when it will be ready, if ever.

---

