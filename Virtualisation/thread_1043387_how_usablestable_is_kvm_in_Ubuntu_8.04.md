---
title: "how usable/stable is kvm in Ubuntu 8.04?"
date: 2009-01-18
forum: Virtualisation
---

### Post by pytheas22 on 2009-01-18
I'm looking to set up several virtual servers on an IBM blade center that I've just built.  The host operating system will most likely be Ubuntu 8.04 server edition, and the clients will include Windows XP, Windows Server 2003, maybe some old Red Hat machines and other Linuxes.  I've been intrigued by what I've read about kvm--its efficiency and flexibility are impressive--and would like to give it a try instead of resorting to VMware.

However, I've also read things saying that kvm is not exactly stable yet, and I need it to be 100% reliable.  I've heard that there can be issues installing Windows in it, for example.  Can anyone here share his or her experience using kvm in a production environment?

In particular, I'd really like to know about the build of kvm that ships default with 8.04; I could compile a more recent version, but I'd prefer to keep everything within the package manager if possible (unless there's a repository I could add for more recent kvm packages...).  I don't want to use Ubuntu 8.10 because I need LTS.

Also, does kvm require X, or would I be able to use it without installing any GUIs on my Ubuntu host server?

---

### Post by ktulu73 on 2009-01-19
Hi,

you don't need X in KVM, because KVM redirects the graphic device to vnc (like xen), and the only issue I know in virtualizing WinXP is, that you have to disable acpi in Win.

But I really suggest a more recent KVM version, because there are a lot enhancements and performance inprovements in the releases after kvm62. 


Regards

---

