---
title: "Error starting Virtual Machine Manager"
date: 2019-04-23
forum: Virtualisation
---

### Post by dik232 on 2019-04-23
Having problems starting VMM:

```
Error starting Virtual Machine Manager: '_CLIConfig' object has no attribute 'gsettings_dir'

Traceback (most recent call last):
  File "/usr/share/virt-manager/virt-manager", line 291, in <module>
    main()
  File "/usr/share/virt-manager/virt-manager", line 223, in main
    "virt-manager", CLIConfig, options.test_first_run)
  File "/usr/share/virt-manager/virtManager/config.py", line 176, in __init__
    CLIConfig.gsettings_dir, self.test_first_run)
AttributeError: '_CLIConfig' object has no attribute 'gsettings_dir'

```

There doesn't seem to be much useful online.  Any ideas?

Edit:  have purged and reinstalled virt-manager

---

### Post by dik232 on 2019-04-24
To add to this if I start from shell I get:

```

$ virt-manager
/usr/share/virt-manager/virtinst/osdict.py:26: PyGIWarning: Libosinfo was imported without specifying a version first. Use gi.require_version('Libosinfo', '1.0') before import to ensure that the right version gets loaded.
  from gi.repository import Libosinfo as libosinfo

```

---

### Post by dik232 on 2019-04-30
This [page]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=803469") contains the answer.  Purge python-ipaddr and then reinstall virt-manager etc

This part of the forum seems completely dead, 2 views in 6 days.  Did I post in the wrong place??

---

