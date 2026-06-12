---
title: "emacs23-nox not installing properly on Lucid Server"
date: 2011-03-02
forum: Server Platforms
---

### Post by SabreWolfy on 2011-03-02
Installing emacs23-nox on a headless Ubuntu 10.04 (Lucid) server "works" in the sense that I can launch emacs, but the installation throws out all of this:

```

# sudo aptitude install emacs23-nox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  emacs23-bin-common{a} emacs23-common{a} emacs23-nox emacsen-common{a} 
0 packages upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/23.6MB of archives. After unpacking 73.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Selecting previously deselected package emacsen-common.
(Reading database ... 158533 files and directories currently installed.)
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu1_all.deb) ...
Selecting previously deselected package emacs23-common.
Unpacking emacs23-common (from .../emacs23-common_23.1+1-4ubuntu7.1_all.deb) ...
Selecting previously deselected package emacs23-bin-common.
Unpacking emacs23-bin-common (from .../emacs23-bin-common_23.1+1-4ubuntu7.1_i386.deb) ...
Selecting previously deselected package emacs23-nox.
Unpacking emacs23-nox (from .../emacs23-nox_23.1+1-4ubuntu7.1_i386.deb) ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up emacsen-common (1.4.19ubuntu1) ...
emacsen-common: Handling install of emacsen flavor emacs

Setting up emacs23-common (23.1+1-4ubuntu7.1) ...

Setting up emacs23-bin-common (23.1+1-4ubuntu7.1) ...
update-alternatives: using /usr/bin/b2m.emacs23 to provide /usr/bin/b2m (b2m) in auto mode.
update-alternatives: using /usr/bin/ctags.emacs23 to provide /usr/bin/ctags (ctags) in auto mode.
update-alternatives: using /usr/bin/ebrowse.emacs23 to provide /usr/bin/ebrowse (ebrowse) in auto mode.
update-alternatives: using /usr/bin/emacsclient.emacs23 to provide /usr/bin/emacsclient (emacsclient) in auto mode.
update-alternatives: using /usr/bin/etags.emacs23 to provide /usr/bin/etags (etags) in auto mode.
update-alternatives: using /usr/bin/grep-changelog.emacs23 to provide /usr/bin/grep-changelog (grep-changelog) in auto mode.
update-alternatives: using /usr/bin/rcs-checkin.emacs23 to provide /usr/bin/rcs-checkin (rcs-checkin) in auto mode.

Setting up emacs23-nox (23.1+1-4ubuntu7.1) ...
update-alternatives: using /usr/bin/emacs23-nox to provide /usr/bin/emacs (emacs) in auto mode.
emacs-install emacs23
install/dictionaries-common: Byte-compiling for emacsen flavour emacs23
Wrote /usr/share/emacs23/site-lisp/dictionaries-common/debian-ispell.elc
Wrote /usr/share/emacs23/site-lisp/dictionaries-common/ispell.elc
Wrote /usr/share/emacs23/site-lisp/dictionaries-common/flyspell.elc
emacsen-common: Handling install of emacsen flavor emacs23
emacsen-common: byte-compiling for emacs23
Wrote /etc/emacs23/site-start.d/00debian-vars.elc

In debian-run-directories:
debian-startup.el:131:25:Warning: `mapcar' called for effect; use `mapc' or
    `dolist' instead
Wrote /usr/share/emacs23/site-lisp/debian-startup.elc
install/global: byte-compiling for emacs23
cp: cannot stat `/usr/share/emacs/site-lisp/global/gtags.el': No such file or directory
emacs-install: /usr/lib/emacsen-common/packages/install/global emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 3.
dpkg: error processing emacs23-nox (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs23-nox
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up emacs23-nox (23.1+1-4ubuntu7.1) ...
emacs-install emacs23
install/dictionaries-common: Already byte-compiled for emacs23. Skipping ...
emacsen-common: Handling install of emacsen flavor emacs23
emacsen-common: byte-compiling for emacs23
Wrote /etc/emacs23/site-start.d/00debian-vars.elc

In debian-run-directories:
debian-startup.el:131:25:Warning: `mapcar' called for effect; use `mapc' or
    `dolist' instead
Wrote /usr/share/emacs23/site-lisp/debian-startup.elc
install/global: byte-compiling for emacs23
cp: cannot stat `/usr/share/emacs/site-lisp/global/gtags.el': No such file or directory
emacs-install: /usr/lib/emacsen-common/packages/install/global emacs23 failed at /usr/lib/emacsen-common/emacs-install line 28, <TSORT> line 3.
dpkg: error processing emacs23-nox (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 emacs23-nox
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

```

I want to install "ess", but it chokes because emacs is not configured properly. Suggestions please.

---

### Post by SabreWolfy on 2011-03-02
Same result if I remove emacs23-nox and install emacs22-nox or emacs23. Something is broken somewhere :(

Bug report [here]("https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/727780").

---

### Post by SabreWolfy on 2011-03-08
Solved by removing package "global" (see discussion in [bug]("https://bugs.launchpad.net/ubuntu/+source/emacs23/+bug/727780") report).

---

