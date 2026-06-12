---
title: "Cannot save LXD/LXC profile settings - settings are lost after saving the config"
date: 2017-01-14
forum: Virtualisation
---

### Post by itcrowdsource on 2017-01-14
I'm currently trying to build new profiles for LXD/LXC (2.0.8-0ubuntu1~ubuntu16.04.2)
When I use the command lxc profile edit <profile name> the editor appears. I'm able to make adjustments and enter ctrl-o to save the file.
If I run the same command lxc profile edit <profile name> again all previous settings are lost. It looks like that these configuration alterations aren't processed by the system and stalled in the /tmp folder. The /tmp folder contains several files named like lxd_editor_811591922 for each attempt to configure the settings.

I also tried to adjust the settings on a container level, but this produces the same problem. E.g. lxc config edit <container> doesn't save the settings either.

I'm able to reproduce this issue on another similar configured LXD instance.

Does anyone have experience with this issue and knows how to tackle it?

---

### Post by itcrowdsource on 2017-01-15
In addition to my previous post:
I'm able to adjust individual settings with the lxc profile device set command, like lxc profile device set bridged eth0 parent br0 but I'm also trying to work with the builtin editor for more convenience.

---

