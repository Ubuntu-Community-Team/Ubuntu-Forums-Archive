---
title: "additional drivers gone/software sources crashes"
date: 2012-08-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-27
Just updated my Dell Inspiron b1390 and noticed additional-drivers is gone (with only transitional packaged) and now the software sources is suppossed to handle this work but just crashes into nowhere.

---

### Post by jbicha on 2012-08-27
Do you get an error message if you run software-properties-gtk from the command line?

---

### Post by humanisfood on 2012-09-09
damien@damien-GA-770TA-UD3:~$ software-properties-gtk
gpg: /tmp/tmpcx4o6y/trustdb.gpg: trustdb created
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 103, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 179, in __init__
    self.show_drivers()
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 1268, in show_drivers
    widget = Gtk.Label("{}: {}".format(self.devices[device]['vendor'], self.devices[device]['model']))
KeyError: 'vendor'


bug has been reported here... trying to find a work around without any luck.

[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1028388](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1028388)

---

### Post by humanisfood on 2012-09-11
a fix was released. good to go!

---

### Post by ventrical on 2012-09-12
Thanks all.

---

