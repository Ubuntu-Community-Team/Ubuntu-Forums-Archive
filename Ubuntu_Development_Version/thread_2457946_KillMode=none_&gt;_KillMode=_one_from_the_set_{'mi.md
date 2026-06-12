---
title: "KillMode=none &gt; KillMode= one from the set: {'mixed','control-group'}"
date: 2021-02-13
forum: Ubuntu Development Version
---

### Post by zika on 2021-02-13
```
[    4.623503] systemd[1]: /lib/systemd/system/plymouth-start.service:17: Unit configured to use KillMode=none. This is unsafe, as it disables systemd's process lifecycle management for the service. Please update your service to use a safer KillMode=, such as 'mixed' or 'control-group'. Support for KillMode=none is deprecated and will eventually be removed.
[    4.648823] systemd[1]: /lib/systemd/system/dbus.service:12: Unit configured to use KillMode=none. This is unsafe, as it disables systemd's process lifecycle management for the service. Please update your service to use a safer KillMode=, such as 'mixed' or 'control-group'. Support for KillMode=none is deprecated and will eventually be removed.
```
[https://gitlab.freedesktop.org/plymouth/plymouth/-/merge_requests/122](https://gitlab.freedesktop.org/plymouth/plymouth/-/merge_requests/122)
[https://github.com/containers/podman/issues/8615](https://github.com/containers/podman/issues/8615)
Replacing &#8222;none&#8220; with &#8222;mixed&#8220; in both files mentioned above solves it and machine is stable for a whole day now.
Replacing &#8222;none&#8220; with &#8222;control-group&#8220; in both files mentioned above solves it and machine is stable for a whole day now.
It seems a bit brisker with former.
After couple of days I'd recommend &#8222;mixed&#8220;...

---

