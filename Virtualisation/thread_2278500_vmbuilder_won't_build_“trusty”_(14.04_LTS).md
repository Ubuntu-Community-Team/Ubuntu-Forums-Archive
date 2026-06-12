---
title: "vmbuilder won't build “trusty” (14.04 LTS)"
date: 2015-05-17
forum: Virtualisation
---

### Post by oz1cz on 2015-05-17
[FONT=arial]I can use this command to create a working VM running the "precise" (12.04 LTS) Ubuntu release:[/FONT]

       [FONT=courier new]vmbuilder kvm ubuntu -v --suite=precise \
      --libvirt=qemu:///system --arch=amd64 \
      --cpus=2 --mem=2047 --swapsize=4096 --rootsize=71680 --flavour=server \
      --hostname=xxx --mirror=http://archive.ubuntu.com/ubuntu \
      --components=main,universe --addpkg=openssh-server --user=claus \
      --pass=xxxx --dest=/home/claus/vm-xxx --bridge=br0
[/FONT][FONT=arial]
This appears to work fine.
[/FONT]
[FONT=arial]But if I replace "precise" with "trusty" (14.04 LTS), the build process halts after a few minutes.[/FONT]

[FONT=arial]In the log file from the unsuccessful "trusty" build, the last lines are:[/FONT]

       [FONT=courier new]2015-05-16 12:03 DEBUG   : I: Configuring ubuntu-minimal...
   2015-05-16 12:03 DEBUG   : I: Configuring libc-bin...
   2015-05-16 12:03 DEBUG   : I: Configuring initramfs-tools...
   2015-05-16 12:03 DEBUG   : I: Base system installed successfully.
[/FONT]  [FONT=arial]
At this point, nothing further happens. The vmbuilder program hasn't terminated, but nothing is happening.
[/FONT]
[FONT=arial]In the log file from the successful "precise" build, the above lines are followed by[/FONT]
  [FONT=courier new]
    2015-05-16 11:41 INFO    : Calling hook: configure_os
[/FONT]  [FONT=arial]
and the build process continues.
[/FONT]
[FONT=arial](I am running the commands on a "precise" (12.04) system.)[/FONT]
[FONT=arial]
What am I doing wrong in the "trusty" build?[/FONT]

---

