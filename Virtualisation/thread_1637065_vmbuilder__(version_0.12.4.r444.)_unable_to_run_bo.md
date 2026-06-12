---
title: "vmbuilder  (version 0.12.4.r444.) unable to run boot.sh"
date: 2010-12-04
forum: Virtualisation
---

### Post by fire-fly on 2010-12-04
Hi 
I am using vmbuilder version 0.12.4.r444. It seem that boot.sh did not execute.

The boot.sh is to install openssh-server as shown below.
I deliberately not using  -qqy  hoping to see some result.

boot.sh
-rwxr-xr-x 1 root root   85 2010-12-04 11:42 boot.sh
> # Install openssh-server
apt-get update
apt-get install  --force-yes openssh-server


The following was executed.
> 
vmbuilder kvm ubuntu --suite=lucid --flavour=virtual --arch=i386 --mirror=http://hk.archive.ubuntu.com/ubuntu -o --libvirt=qemu:///system --ip=192.160.1.51 --gw=192.160.1.1 --part=vmbuilder.partition --templates=mytemplates --user=mememe --name=mememe --pass=mememe51 --addpkg=vim-nox --addpkg=unattended-upgrades --addpkg=acpid --firstboot=/kvm/vm1/boot.sh --mem=256 --hostname=vm1 --bridge=br0

The screen output is
> 2010-12-04 10:58:22,078 INFO    : Calling hook: preflight_check
2010-12-04 10:58:22,080 INFO    : Calling hook: set_defaults
2010-12-04 10:58:22,080 INFO    : Calling hook: bootstrap
2010-12-04 11:11:59,722 INFO    : Calling hook: configure_os
2010-12-04 11:13:42,805 INFO    : update-rc.d: warning: unattended-upgrades start runlevel arguments (none) do not match LSB Default-Start values (0 6)
2010-12-04 11:13:42,805 INFO    : update-rc.d: warning: unattended-upgrades stop runlevel arguments (0 6) do not match LSB Default-Stop values (none)
2010-12-04 11:13:46,661 INFO    :
2010-12-04 11:13:46,662 INFO    : Current default time zone: 'Etc/UTC'
2010-12-04 11:13:46,665 INFO    : Local time is now:      Sat Dec  4 03:13:46 UTC 2010.
2010-12-04 11:13:46,665 INFO    : Universal Time is now:  Sat Dec  4 03:13:46 UTC 2010.
2010-12-04 11:13:46,665 INFO    :
Extracting templates from packages: 100%
2010-12-04 11:14:43,318 INFO    :
2010-12-04 11:14:43,318 INFO    : Current default time zone: 'Etc/UTC'
2010-12-04 11:14:43,319 INFO    : Local time is now:      Sat Dec  4 03:14:43 UTC 2010.
2010-12-04 11:14:43,319 INFO    : Universal Time is now:  Sat Dec  4 03:14:43 UTC 2010.


After starting up vm1, I was able to ping it but not ssh to it.

I rebuild the vm1 using --addpkg=openssh-server instead and it work.
> vmbuilde kvm ubuntu --suite=lucid --flavour=virtual --arch=i386 --mirror=http://hk.archive.ubuntu.com/ubuntu -o --libvirt=qemu:///system --ip=192.160.1.51 --gw=192.160.1.1 --part=vmbuilder.partition --templates=mytemplates --user=mememe --name=mememe --pass=mememe51 --addpkg=openssh-server --addpkg=vim-nox --addpkg=unattended-upgrades --addpkg=acpid  --mem=256 --hostname=vm1 --bridge=br0

Where went wrong ?

Thanks in advanced

---

### Post by FiVAL on 2011-03-30
You can try:

boot.sh
```

# Wait for network to come up...
while (! ping -c 1 www.google.com); do sleep 1; done

# Install openssh-server
apt-get update
apt-get install --force-yes openssh-server

```

---

