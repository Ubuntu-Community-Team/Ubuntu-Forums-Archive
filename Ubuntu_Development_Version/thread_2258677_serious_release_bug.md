---
title: "serious release bug"
date: 2014-12-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-12-29
Apparently this one slipped through the qa tracker.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1406396](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1406396)

---

### Post by kansasnoob on 2014-12-29
The devs dumped a huge ubiquity update shortly after Alpha 1 was released on the 18th:

> ubiquity (2.21.2) vivid; urgency=medium

  [ Dimitri John Ledkov ]
  * Add --quiet option to dmidecode calls, in the future release that will
    prevent dmidecode from printing error banner if a newer than dmidecode
    smbios version has happened to be in use. LP: #1353580.
  * Add "support" for Gauja laptops and self-builts - that is do not use
    "To be filled by O.E.M." as a valid model name.
  * Remove setting translated placeholder text in the usersetup
    plugin. (LP: #1283047)
  * Drop translation messages from ubiquity.templates.
  
  [ Unit 193 ]
  * Enable the ubiquity panel in xfwm4 now since it is functional.
  
  [ Tim Lunn ]
  * scripts/plugininstall.py: Remove obsolete code to generate wallpaper
    cache, unity-settings-daemon/gnome-settings-daemon now run in install
    mode (LP: #1318621) 

  [ Martin Wimpress ]
  * Improve support for Mate desktop.

  [ Shih-Yuan Lee (FourDollars) ]
  * Fix the usage of effective uid/gid and the HOME environment variable.

  [ Dimitri John Ledkov ]
  * Automatic update of included source packages: clock-setup
    0.121ubuntu1, console-setup 1.70ubuntu11, partman-basicfilesystems
    108ubuntu1, partman-crypto 78ubuntu1, partman-jfs 45, partman-lvm
    102, partman-xfs 55.

 -- Dimitri John Ledkov <dimitri.j.ledkov@linux.intel.com>  Sun, 21 Dec 2014 06:46:46 +0000


---

### Post by ventrical on 2014-12-30
At least it allowed apport to report the second bug but it was really touchy there for a minute because firefox had crashed(but popped up back open) also in the live session so it wasn't a complete fail.

---

