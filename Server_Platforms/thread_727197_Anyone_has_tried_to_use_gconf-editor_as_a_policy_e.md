---
title: "Anyone has tried to use gconf-editor as a policy editor?"
date: 2008-03-17
forum: Server Platforms
---

### Post by netlogic on 2008-03-17
One interesting thing about Windows NT line of workstations are policy editors. Able to lock down the workstations based on their credentials. I know gconf-editor gives options to configure the workstations. Can this tool also used as a policy editor? Is it possible to prevent users to not adjust certain settings? Is it possible to copy the data to local machine without restarting the gdm when they login? Anyone has looked into a gconf-editor as a policy editor?

Thanks again.

---

### Post by ShodanjoDM on 2008-03-17
If you run gconf-editor as root, it will gives you more control (you can enable certain options as mandatory) so every other users will have to follow it.

---

