---
title: "virt-v2v version too low on 18.04 to p2v 18.04"
date: 2019-08-24
forum: Virtualisation
---

### Post by sean-liu on 2019-08-24
Hi folks,

I've tried to p2v an existing 18.04 physical box to KVM on a 18.04 server.
I used virt-p2v-make-disk on the server and created a USB stick, the utility used debian-9 image. The created image was problematic because it booted right into GUI login instead of the p2v GUI.
That was relative easy to fix, with chroot + useradd I created a local user on the stick and then started the process again. Then manually started the p2v GUI.
Now the process aborted with following message:
...
libguestfs: trace: v2v: command_lines = ["/.", "/usr", "/usr/share", "/usr/share/doc", "/usr/share/doc/linux-image-generic", "/usr/share/doc/linux-image-generic/changelog.gz", "/usr/share/doc/linux-image-generic/copyright"]
installed kernel packages in this guest:
virt-v2v: error: no installed kernel packages were found.


This probably indicates that virt-v2v was unable to inspect this guest properly.
...
...

A google search pointed me to this bug:
[https://github.com/libguestfs/libguestfs/commit/500acb15f8f777e9fe99a60c4216daf84a92aae3](https://github.com/libguestfs/libguestfs/commit/500acb15f8f777e9fe99a60c4216daf84a92aae3)

I believe the libguestfs version on 18.04 is too low?


/tmp/virt-p2v-20190821-eh2fpkpx# dpkg --list |grep libguestfs-tools
ii  libguestfs-tools                      1:1.36.13-1ubuntu3.3                   amd64        guest disk image management system - tools
/tmp/virt-p2v-20190821-eh2fpkpx# virt-v2v -V
virt-v2v 1.36.13



It seems a bit wrong for 18.04 not being able to p2v its own version. So is there a plan to have a higher version update?
Sorry if I guess the wrong way.

Thanks,

Sean

---

### Post by TheFu on 2019-08-25
I just remove proprietary GPU drivers, then use my normal backup/restore processes to move machines around.  Works every time.

---

### Post by sean-liu on 2019-08-25
Well I could do a fresh install too, but that's beside the point :-)
The tools shipped with 18.04 should at least be able to p2v itself...

Thanks,

Sean

---

