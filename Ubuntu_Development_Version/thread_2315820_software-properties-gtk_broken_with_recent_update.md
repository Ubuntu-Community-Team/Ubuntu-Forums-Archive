---
title: "software-properties-gtk broken with recent update"
date: 2016-03-02
forum: Ubuntu Development Version
---

### Post by SurfaceUnits on 2016-03-02
```
sudo software-properties-gtk

Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 101, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 98, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 109, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python3/dist-packages/softwareproperties/SoftwareProperties.py", line 599, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python3/dist-packages/aptsources/distro.py", line 89, in get_sources
    (self.id, self.codename))
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template for Ubuntu/Xenial
```


Recent Updates:

```
Commit Log for Wed Mar  2 10:04:04 2016


Upgraded the following packages:
activity-log-manager (0.9.7-0ubuntu22) to 0.9.7-0ubuntu23
activity-log-manager-control-center (0.9.7-0ubuntu22) to 0.9.7-0ubuntu23
appstream (0.9.1-1ubuntu1) to 0.9.2-0ubuntu1
apt (1.2.3) to 1.2.4
apt-transport-https (1.2.3) to 1.2.4
apt-utils (1.2.3) to 1.2.4
archdetect-deb (1.114ubuntu2) to 1.114ubuntu3
fontconfig (2.11.1-0ubuntu7) to 2.11.1-0ubuntu8
fontconfig-config (2.11.1-0ubuntu7) to 2.11.1-0ubuntu8
gnome-software (3.19.91~git20160229.ceb6b9d-0ubuntu1) to 3.19.92~git20160302.faa1f16-0ubuntu3
gnome-software-common (3.19.91~git20160229.ceb6b9d-0ubuntu1) to 3.19.92~git20160302.faa1f16-0ubuntu3
imagemagick (8:6.8.9.9-7) to 8:6.8.9.9-7ubuntu1
imagemagick-6.q16 (8:6.8.9.9-7) to 8:6.8.9.9-7ubuntu1
imagemagick-common (8:6.8.9.9-7) to 8:6.8.9.9-7ubuntu1
isc-dhcp-client (4.3.3-5ubuntu8) to 4.3.3-5ubuntu9
isc-dhcp-common (4.3.3-5ubuntu8) to 4.3.3-5ubuntu9
kpartx (0.5.0-7ubuntu15) to 0.5.0-7ubuntu16
kpartx-boot (0.5.0-7ubuntu15) to 0.5.0-7ubuntu16
libappstream-glib8 (0.5.10-0ubuntu2) to 0.5.10-0ubuntu3
libappstream3 (0.9.1-1ubuntu1) to 0.9.2-0ubuntu1
libapt-inst2.0 (1.2.3) to 1.2.4
libapt-pkg5.0 (1.2.3) to 1.2.4
libfontconfig1 (2.11.1-0ubuntu7) to 2.11.1-0ubuntu8
libmagickcore-6.q16-2 (8:6.8.9.9-7) to 8:6.8.9.9-7ubuntu1
libmagickcore-6.q16-2-extra (8:6.8.9.9-7) to 8:6.8.9.9-7ubuntu1
libmagickwand-6.q16-2 (8:6.8.9.9-7) to 8:6.8.9.9-7ubuntu1
linux-generic (4.4.0.8.9) to 4.4.0.9.10
linux-headers-generic (4.4.0.8.9) to 4.4.0.9.10
linux-image-generic (4.4.0.8.9) to 4.4.0.9.10
linux-libc-dev (4.4.0-8.23) to 4.4.0-9.24
python3-software-properties (0.96.17) to 0.96.18
software-properties-common (0.96.17) to 0.96.18
software-properties-gtk (0.96.17) to 0.96.18
```

Installed the following packages:
```
linux-headers-4.4.0-9 (4.4.0-9.24)
linux-headers-4.4.0-9-generic (4.4.0-9.24)
linux-image-4.4.0-9-generic (4.4.0-9.24)
linux-image-extra-4.4.0-9-generic (4.4.0-9.24)
```

---

### Post by SurfaceUnits on 2016-03-22
any one?

---

### Post by Gavin77 on 2016-03-22
You should never run GUI apps with sudo as it can break them, always use gksudo.  I don't know how to fix your problem though, sorry.

---

### Post by ventrical on 2016-03-23
You might look at this.

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13153370#post13153370](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13153370#post13153370)

---

