---
title: "Convert LXC Guests from privileged to unprivileged"
date: 2015-12-02
forum: Virtualisation
---

### Post by MACscr on 2015-12-02
I have an Ubuntu Trusty system with about 10 linux containers on it that were created by root using the normal "lxc-create -t ubuntu -n git". Nothing custom was setup for these guests that I can think of besides the network bridges and a few are mounting a directory from the host like so "lxc.mount.entry = /backups/r1soft backups none bind.rw 0.0". I do see that some of the older containers that were created do have the following in their containername/config files:

```
lxc.cgroup.devices.deny = alxc.cgroup.devices.allow = c *:* m
lxc.cgroup.devices.allow = b *:* m
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
lxc.cgroup.devices.allow = c 254:0 rwm
lxc.cgroup.devices.allow = c 10:229 rwm
lxc.cgroup.devices.allow = c 10:200 rwm
lxc.cgroup.devices.allow = c 1:7 rwm
lxc.cgroup.devices.allow = c 10:228 rwm
lxc.cgroup.devices.allow = c 10:232 rwm
```

But a majority do not and I am not aware of any special cgroup settings that I might have setup.

With all of that said, I am wanting to better isolate these containers from the host and was told that doing unprivileged was the way to go. A couple quick questions:

1) With all the information posted above, do you foresee any issues with them running as unprivileged?
2) How can I easily convert them to unprivileged containers (I have installed LXD, but done nothing else)
3) How do i ensure that future containers are only created as unprivileged containers?
4) Will this new "isolation" prevent host kernel notices, etc, from leaking into the containers syslog? Really makes it hard to troubleshoot things when entries are unrelated to the container and more related to the host or another container.

Thanks so much for your time and help on this. I truly appreciate it.

---

