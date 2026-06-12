---
title: "Software sources problem"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hannysabbagh on 2012-02-13
hello

i have a problem in the software sources too as you said, when running"sudo software-proprites-gtk" it give:
> Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 104, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 85, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 96, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/SoftwareProperties.py", line 580, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.7/dist-packages/aptsources/distro.py", line 91, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

and the software sources can not be opened, and i can't add a new repo for the system, i could not open the bug report because launchpad is forbidden in my country, anyone have the solution please?
thx

---

### Post by dino99 on 2012-02-13
> **hannysabbagh said:**
> hello

i have a problem in the software sources too as you said, when running"sudo software-proprites-gtk" it give:

and the software sources can not be opened, and i can't add a new repo for the system, i could not open the bug report because launchpad is forbidden in my country, anyone have the solution please?
thx

This thread is about Synaptic, nothing else, so please open your thread. But i cant get your issue from a terminal, everything works on i386.

---

### Post by cariboo on 2012-02-13
Moved to a thread of it's own.

Software sources work here on 64-bit. This is what I get when I run it:

> sudo ./software-properties-gtk
gpg: /tmp/tmpdm7fod/trustdb.gpg: trustdb created


---

