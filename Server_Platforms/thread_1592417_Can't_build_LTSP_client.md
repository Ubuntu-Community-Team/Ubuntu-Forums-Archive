---
title: "Can't build LTSP client"
date: 2010-10-10
forum: Server Platforms
---

### Post by Davit_J on 2010-10-10
Hi guys,

I installed 10.04 on my G4 server without any problems. I also installed the edubuntu and ltsp packages. Initially, when I tried to build a client, I got the following error:

E: Couldn't download dists/lucid/main/binary-powerpc/Packages.gz

I figured it was because I was running a ported version of Linux, so I checked my sources.list, which was fine, and tried specifying ports.ubuntu.com as my mirror, but I still got the same error. Ok fine, I might as well use the files on my installation CD, so I popped in the CD and copied its content to /cdrom. I ran sudo ltsp-build-client with the --mirror file:///cdrom argument. It went farther, however I got the following error this time:

W: Failure trying to run: chroot /opt/ltsp/powerpc mount -t proc proc /proc

Maybe there is something wrong with my packages.gz file? I browsed over to its directory and noticed that it was only a couple of KBs, while the version in ports.ubuntu.com was a couple of megs. Replaced it and tried to build the client file again. This time I was presented with:

W: file:///cdrom/dists/lucid/main/binary-powerpc/Packages.gz was corrupt

I thought the reason why I was having this problem was because I was trying to build a PowerPC architecture client, so I tested it out with the --arch i386 option. I got the farthest with this one (it was downloading and verifying a bunch of packages). It also failed with:

W: Failure trying to run: chroot /opt/ltsp/i386 mount -t proc proc /proc

Any idea what might be causing this? I was thinking about installing an earlier version (6-PowerPC was officially supported, 9.10-edubuntu comes preinstalled, or maybe even jumping over to Debian's skolelinux), but I wanted to get a second opinion before I did.

---

