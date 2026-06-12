---
title: "LXC --&gt; Mount harddisk directly inside the container"
date: 2015-03-23
forum: Virtualisation
---

### Post by alex351 on 2015-03-23
Hi all,

I run a daily script that mounts a drive and unmounts it and puts it to sleep when the task is done.

I have been trying to achieve this inside my LXC container, however had no luck. what I did:

- I tried changing inside the lxc config file the app.armor profile but that gave me a lot of around (one of them not being able to switch to the mount profile)
- I add mount option to the lxc-default apparmor profile --> no more error messages and the container boots up a it usually does

However I seem to be missing something - because mount does not work on the respective device - either by path nor by uuid (preferred):

```

sudo mount UUID=68a47b7b-c844-41c9-9cae-484b698b4f57 /data/parity_disk -o noatime
mount: special device UUID=68a47b7b-c844-41c9-9cae-484b698b4f57 does not exist

sudo mount /dev/sdd /data/parity_disk -o noatime
mount: special device /dev/sdd does not exist

```

---

### Post by ian-weisser on 2015-03-24
Boy, if  'mount' worked inside a container, then it wouldn't really be containing anything.
The host needs to do the mounting.
And the host must be configured to mount to a location that the container can access.

---

### Post by alex351 on 2015-03-24
...i guess you are right - it defeats the purpose of a container....though for me the main reason for a container is portability..
So, no chance that I could allow for a specific drive to be mounted from inside the container?

---

