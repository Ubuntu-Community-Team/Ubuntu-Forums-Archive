---
title: "LXC: &quot;unknown key lxc.uts.name&quot; after moving container to another host"
date: 2018-06-17
forum: Virtualisation
---

### Post by snakyjake on 2018-06-17
**Situation:**
Archived LXC container via...
Shutdown container from local host
Archive container from local host
Copy container to remote host
Unarchive container on remote host
Attempted to start container on the remote host...

root@brown:/var/lib/lxc/ubuntu_lxc# lxc-start -n ubuntu_lxc
lxc-start: confile.c: parse_line: 2014 [COLOR="#FF0000"]unknown key lxc.uts.name[/COLOR]
lxc-start: parse.c: lxc_file_for_each_line: 57 [COLOR="#FF0000"]Failed to parse config: lxc.uts.name = ubuntu_lxc[/COLOR]
lxc-start: tools/lxc_start.c: main: 284 Failed to create lxc_container

The container I archived and copied the remote server is named "ubuntu_lxc", is the folder name, and is the name in the config file.

What did I miss?

---

