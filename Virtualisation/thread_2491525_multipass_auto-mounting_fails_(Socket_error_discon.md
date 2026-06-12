---
title: "multipass auto-mounting fails (Socket error: disconnected), manual mounting succeeds"
date: 2023-10-12
forum: Virtualisation
---

### Post by jdeepwell on 2023-10-12
Hi all!

My multipass installation is working OK, despite one issue: After mounting a directory successfully manually, when shutting down the (primary) VM instance and starting it up again it fails to re-mount with error:
[SIZE=3]**[FONT=courier new]Removing mount "/aaa/bbb/ccc" from 'primary': ssh failed to authenticate: 'Socket error: disconnected'[/FONT]**
[/SIZE]*(directory redacted as /aaa/bbb/ccc)*


So I start an instance, mount a folder (works), then stop the instance and start it up again and instead of the folder getting auto-mounted again I get the error...
If I then try to manually mount, it works.

Anyone any idea?

The network setup seems to be OK:
- http connection from the host OS into the instance works as expected
- Network connections from inside the instance to the internet also work as expected

`multipass shell` also works as expected.

Any help would be greatly appreciated!

Regards
Johannes


**[SIZE=3]Additional info[/SIZE]**
OS: Ventura 13.6 (22G120)
multipass version: multipass 1.12.2+mac / multipassd 1.12.2+mac

**multipass info --all:**
Name: primary
State: Running
IPv4: 192.168.64.10
Release: Ubuntu 22.04.3 LTS
Image hash: 5167c1b13cb3 (Ubuntu 22.04 LTS)
CPU(s): 4
Load: 0.08 0.11 0.14
Disk usage: 4.8GiB out of 69.7GiB
Memory usage: 1.9GiB out of 3.8GiB
Mounts: /Users/valerianquell/Developer/workspace/kencube => /var/www/KenCube_source
UID map: 501:33
GID map: 20:33


**multipass get local.driver**
qemu

---

### Post by MAFoElffen on 2023-10-12
What happens if you umount the mount before shutdown or reboot... On that next / subsequent boot?

If that corrects that, then add a script that does that, triggered by a unit that runs right before those service unit files...

Or since a VM, most likely KVM, you could handle that with libvirt hooks: [https://libvirt.org/hooks.html](https://libvirt.org/hooks.html)

---

### Post by jdeepwell on 2023-10-13
Hey @MAFoElffen,

thx for your reply!

I played around with it a little more (also on different machines). It only happens on the slower ones so I suspected it to be a timing issue: maybe the sshd is not fully ready to accept logins, which are needed for the mount command, but a short while later (when manually mounting) it is.

So I filed a bug report and Ricardo Abreu from canonical responded, confirming my suspicion:

[https://github.com/canonical/multipass/issues/3252](https://github.com/canonical/multipass/issues/3252)

---

### Post by MAFoElffen on 2023-10-13
I see that in the logs. It looks like the timing of that it is a matter of 20 to 30 seconds where it goes from denying to opening back up for the auth...

Glad that they could reproduce the problem and he is working on correcting it.

Please keep us updated on how this goes.

---

### Post by jdeepwell on 2023-10-21
New status as of 2023-10-18:


The issue was added to the 1.13.0 milestone.

[https://github.com/canonical/multipass/milestone/20](https://github.com/canonical/multipass/milestone/20)

(fingers crossed :))

---

