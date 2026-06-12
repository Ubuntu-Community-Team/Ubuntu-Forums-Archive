---
title: "Qt problems installing Sun VirtualBox 4.1.2 and Enthought Python 7.1 on Ubuntu 11.04"
date: 2011-09-28
forum: Virtualisation
---

### Post by locksmithone on 2011-09-28
**Qt-related problems when installing Sun VirtualBox 4.1.2 and Enthought Python 7.1 on Ubuntu 11.04**


**Issue:**

Installed Enthought Python 7.1 (Python 2.7.2) on Ubuntu Linux 11.04.  This package embeds some Qt libraries.  Installation was successful.

Afterwards, installed Sun VirtualBox 4.1.2 on same system.  Installation was successful.  However, when attempting to run Virtualbox from the GUI, nothing happened.  When attempting to run virtualbox from the command line, the following error message appeared:

[FONT="Fixedsys"]Qt FATAL: Cannot mix incompatible Qt library (version 0x40703) with this library (version 0x1040702)[/FONT]


**Explanation:**

It seems Enthought Python 7.1 (Python 2.7.2) install some Qt libraries version 40703, which conflicts with the version 40702 libraries installed in Ubuntu by default.


**Solution:**

As upgrading Ubuntu’s Qt libraries to 40703 seemed to be a severe task, taken from the resources (not) found in the internet, the solution was to uninstall the Qt libraries that came with Enthought Python.  The conflicting Qt libraries seem to be located mainly at [FONT="Fixedsys"]ENTHOUGHT_PYTHON_INSTALL_DIR/plugins[/FONT].  

Instead of removing manually, used the following command:

[FONT="Fixedsys"]sudo egginst --remove qt[/FONT]


**Follow up:**

Sun VirtualBox runs successfully after removing the version 40703 Qt libraries.  It remains to be evaluated whether Enthought Python suffers from this removal.

---

