---
title: "[SOLVED] need to remove vmware and virtualBox"
date: 2008-12-02
forum: Virtualisation
---

### Post by satellitex86 on 2008-12-02
I have installed both vmware and sun VirtualBox over the past weeks, and after using Qemu decided to uninstall vmware and VBox.

This is where I've run into problems. Neither are found by synaptics, and I don't know the package names, so I can't use "sudo apt-get remove".

Can anyone help?

---

### Post by bodhi.zazen on 2008-12-02
For VirtualBox should be either :

```
sudo dpkg -r virtualbox
```

* could be VirtualBox

Or

```
sudo apt-get remove --purge virtualbox
```

For VMWare

```
sudo vmware-uninstall.pl
```

Or you may need the full path :

```
sudo /usr/bin/vmware-uninstall.pl
```

---

### Post by satellitex86 on 2008-12-16
Thank you,
That worked.

---

