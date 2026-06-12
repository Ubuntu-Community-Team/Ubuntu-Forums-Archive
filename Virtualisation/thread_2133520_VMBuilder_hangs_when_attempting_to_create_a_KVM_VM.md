---
title: "VMBuilder hangs when attempting to create a KVM VM in ubuntu 12.04"
date: 2013-04-08
forum: Virtualisation
---

### Post by redmage123 on 2013-04-08
Hello all, 

i'm trying to run the following command: 

/var/lib/libvirt/images# vmbuilder kvm ubuntu --suite=precise --flavour=virtual --arch=amd64 --libvirt=qemu:///system --ip=10.10.12.5 --gw=10.10.12.1 --part=vmbuilder.partition --templates=mytemplates --domain=testvm --hostname=testdb --user=postgres --pass=postgres --addpkg=vim --addpkg=openssh-server --addpkg=acpid --addpkg=avahi-daemon --dns=62.77.181.194 --mask=255.255.255.0 --mirror=http://ftp.heanet.ie/mirrors/ubuntu/ --bridge=br0


On an Ubuntu 12.04 system.   Unfortunately, all that happens is that it hangs on the following:

2013-04-08 16:41:08,201 INFO    : Calling hook: preflight_check
2013-04-08 16:41:08,204 INFO    : Calling hook: set_defaults
2013-04-08 16:41:08,204 INFO    : Calling hook: bootstrap


I attached to the process with strace and get the following system calls over and over: 

stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3533, ...}) = 0
write(5, "2013-04-08 16:53 DEBUG   : I: Va"..., 64) = 64
select(5, [4], [], [], NULL)            = 1 (in [4])
fstat(4, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
lseek(4, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
read(4, "I: Ret", 6)                    = 6
fstat(4, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
lseek(4, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
read(4, "rievin", 6)                    = 6
fstat(4, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
lseek(4, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
read(4, "g liblo", 7)                   = 7
fstat(4, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
lseek(4, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
read(4, "ckfile-b", 8)                  = 8
fstat(4, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
lseek(4, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
read(4, "in\n", 9)                      = 3
read(4, 0x27a02a2, 6)                   = -1 EAGAIN (Resource temporarily unavailable)
stat("/etc/localtime", {st_mode=S_IFREG|0644, st_size=3533, ...}) = 0
write(5, "2013-04-08 16:53 DEBUG   : I: Re"..., 57) = 57
select(5, [4], [], [], NULL


anybody know what's going on here? 

Thanks,

Braun Brelin

---

### Post by garfonzo on 2013-11-12
Did you ever determine the problem? I'm having the same issue.

---

