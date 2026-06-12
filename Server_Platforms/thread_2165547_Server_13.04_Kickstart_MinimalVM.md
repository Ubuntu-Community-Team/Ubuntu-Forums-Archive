---
title: "Server 13.04 Kickstart MinimalVM"
date: 2013-08-05
forum: Server Platforms
---

### Post by FiVAL on 2013-08-05
Hi All,

We are experimenting with unattended installations for virtual-guest-ubuntu-servers.
The untended installs are installing very smooth... Only they are way to BIG!

If you read the manual: [https://help.ubuntu.com/13.04/serverguide/preparing-to-install.html#system-requirements](https://help.ubuntu.com/13.04/serverguide/preparing-to-install.html#system-requirements)
***"Server (Minimal) Base System: 700 megabytes All Tasks Installed: 1.4 gigabytes"***

In the manual the minimum says 700 Mb, but I thought the minimal VM install is even smaller!?

Our installation exceeds always the 1,3 Gb...
Does anyone has an idea what we are doing wrong?


Detailed information:

_ks.preseed_
```

d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

```


_ks.cfg_
```

#platform=AMD64 or Intel EM64T

url --url http://ubuntu.<company>.lan/ubuntu

preseed mirror/country string manual
preseed mirror/http/hostname string ubuntu.<company>.lan
preseed mirror/http/directory string /ubuntu
preseed apt-setup/security_host string ubuntu.<company>.lan
preseed apt-setup/security_path string /ubuntu-security

lang en_US
langsupport nl_NL --default=en_US

keyboard us_intl
mouse
timezone --utc Europe/Amsterdam
rootpw --disabled
user administrator --fullname "administrator" --iscrypted --password $1$bibeDe94$iR3sFputadnDnpU7qFUid/

reboot
text
#Install OS instead of upgrade
install

bootloader --location=mbr
zerombr yes
clearpart --all --initlabel
auth  --useshadow  --enablemd5

network --bootproto=dhcp --device=eth0
firewall --disabled

#Do not configure the X Window System
skipx

%packages
openssh-server
nano
ntp

#post --nochroot --interpreter=/bin/bash
%post
echo "Post Install !"
apt-get update
apt-get upgrade -y
apt-get dist-upgrade -y
apt-get check
apt-get autoclean -y
apt-get autoremove -y

```

_isolinux/txt.cfg_
```

default autoinstall
label autoinstall
  menu label ^The Auto Ubuntu Server install
  kernel /install/vmlinuz
  append  file=/cdrom/preseed/ubuntu-server-minimalvm.seed initrd=/install/initrd.gz ks=cdrom:/ks.cfg preseed/file=/cdrom/ks.preseed --

```

_isolinux/isolinux.cfg_
```

# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 10
ui gfxboot bootlogo

```

---

### Post by FiVAL on 2013-08-07
**First of all:** if you also want to build an unattended install ISO, read first the following links:

[http://askubuntu.com/questions/122505/how-do-i-create-completely-unattended-install-for-ubuntu](http://askubuntu.com/questions/122505/how-do-i-create-completely-unattended-install-for-ubuntu)
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
[http://www.utech.de/2013/05/shell-script-creating-a-cd-for-unattended-ubuntu-server-installations/](http://www.utech.de/2013/05/shell-script-creating-a-cd-for-unattended-ubuntu-server-installations/)


**Second:** I have managed to bring to install back to 813 MB !
I add the following lines to the ks.cfg:

```

preseed base-installer/kernel/override-image   string  linux-virtual
preseed base-installer/install-recommends      boolean false
preseed pkgsel/install-language-support        boolean false

```

Time to install this Unattended install takes now (with local mirror ubuntu repos.):
_Virtualbox:_ 15 min (SATA HDD -> image file on host, network VirtIO-net)
_KVM:_ 8 min (RAW HDD direct LVM partion on host,  network VirtIO-net)


But still, i find it way to big and it takes still a lot of time...
Turnkey Linux for example managed within 600 MB,
this also means it will install even faster..!

Anyone, any ideas to try? ThX!

---

### Post by Cheesemill on 2013-08-07
This doesn't really help you out with your installation but this post I made shows the resources used by different VM installation methods.
These were all manual installs though so I can't help with your kickstart files.

[http://ubuntuforums.org/showthread.php?t=2037561&p=12156448&viewfull=1#post12156448](http://ubuntuforums.org/showthread.php?t=2037561&p=12156448&viewfull=1#post12156448)

---

### Post by FiVAL on 2013-08-07
That are very interesting figures... ThX!
With my experiment I am now very close to your figures:

[INDENT]**Ubuntu 12.04 i386 / RAM - 512MB**
Server CD - Install a minimal virtual machine option.
Used RAM - 16MB
Used HD - 622MB
# of packages - 203[/INDENT]

Compare to my current status:

[INDENT]**Ubuntu 13.04 x86_64 / RAM - 512MB**
Ubuntu Repos Mirror - With kickstart file
Used RAM - ?
Used HD - 626MB
# of packages - 319
Time to install in Virtualbox: 13 min[/INDENT]

_ks.cfg (part)_
```

preseed base-installer/kernel/override-image    string linux-virtual
preseed base-installer/install-recommends       boolean false
preseed tasksel/first                           multiselect
preseed tasksel/skip-tasks                      multiselect server
preseed pkgsel/ubuntu-standard                  boolean false
preseed pkgsel/install-language-support         boolean false
preseed pkgsel/language-pack-patterns           string
preseed pkgsel/language-packs                   multiselect

```

---

