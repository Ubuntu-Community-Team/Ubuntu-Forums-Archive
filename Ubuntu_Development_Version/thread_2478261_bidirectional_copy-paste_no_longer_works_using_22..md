---
title: "bidirectional copy-paste no longer works using 22.10 and virtualbox"
date: 2022-08-21
forum: Ubuntu Development Version
---

### Post by Claus7 on 2022-08-21
Hello,

don't know if you use this kind of configuration, 22.10 inside virtualbox, yet I noticed that after the upgrade of nautilus (Files) to 43 alpha, the bidirectional copy to clipboard or copy-paste doesn't work. I also noticed that it doesn't work using the desktop either, which I do not think that is controlled by Files.

Regards!

---

### Post by jbicha on 2022-08-21
Please file a bug.

Could you verify whether it works with Ubuntu 22.04 LTS?

---

### Post by zebra2 on 2022-08-22
Vbox has a history of not working with not yet released versions and there have been times when it wasn't ready even at the time of release.  I quit using it years ago for that reason and have opted to test on a separate machine. 
Aside from that, it isn't really Canonical's responsibility for Vbox not working any more than they are responsible for WINE running any particular piece of software. These are separate enterprises and sometimes they need a development version to be completed before they can address their own shortcomings. 
At any rate it makes sense to keep /Home on it's own partition and to always have an updated install disk handy.

---

### Post by Claus7 on 2022-08-22
Hello,

> **jbicha said:**
> Please file a bug.

Could you verify whether it works with Ubuntu 22.04 LTS?

I removed the 22.10 installation and created 3 new ones: bionic, jammy and kinetic using 22.04.1 as host. 

The installation of jammy had 2 issues:
1) When it was about to install the kernel at the end of the installation the following messages was appearing:
XDG_RUNTIME_DIR is not owned by us (uid 0), but by uid 999!(This could eg happen if you try to connect to a non-root PulseAudio as a root user, over the native protocol. Don't do that.)
and from here:
[https://askubuntu.com/questions/1241795/xdg-runtime-dir-is-not-owned-by-us-uid-0](https://askubuntu.com/questions/1241795/xdg-runtime-dir-is-not-owned-by-us-uid-0)

I let a lot of time to pass and installation finished normally.
2) After the installation and during boot this well known message appeared: 
mtd device must be supplied (device name is empty) .

Both jammy and kinetic were very slow for processes to finish. In all three I installed guest additions and then I rebooted. Then I enabled bidirectional Shared clipboard and Drag and drop. In all of them copy to clipboard was working, yet drag and drop not. In order to test the former I opened a terminal both to the host and guest and tested copy-paste between them.

I have one more machine that d&d is working. I think that it needs more investigation.
edit: I managed to d&d from host Documents to Bionic guest documents.
edit2: with today's kinetic, and after installation and some configuration I managed to d&d from guest to host, not using the desktop though.

Regards!

---

### Post by Claus7 on 2022-08-22
Hello,

> **zebra2 said:**
> Vbox has a history of not working with not yet released versions and there have been times when it wasn't ready even at the time of release.  I quit using it years ago for that reason and have opted to test on a separate machine. 
Aside from that, it isn't really Canonical's responsibility for Vbox not working any more than they are responsible for WINE running any particular piece of software. These are separate enterprises and sometimes they need a development version to be completed before they can address their own shortcomings. 
At any rate it makes sense to keep /Home on it's own partition and to always have an updated install disk handy.

thank you for your response. I do not know why this happened to my system. It was working. I just noticed it after the upgrade of Files in kinetic. It might took place by chance. At least copy to clipboard is working. This is nice since, if I would like to test something in a development version, then I do not have to type it, as long as bidirectional copy paste is working.

I thought so that newest versions might be an issue, that's why I tried also bionic . The same (edit: similar, see above) behaviour. In case someone else was using the same configuration I could tell with more certainty.
edit2: using flashback as guest (kinetic) I can d&d files from host to guest (desktop to desktop) and from guest to host (not yet from desktop, yet e.g. from Documents to Documents)

Regards!

---

