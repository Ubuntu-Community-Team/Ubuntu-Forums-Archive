---
title: "virt-manager 0.8.2 local ISO and PXE boot install option greyed out on  pv-dom0"
date: 2011-03-01
forum: Virtualisation
---

### Post by tapas_mishra on 2011-03-01
Hi,
I just installed a pv-ops Dom0 2.6.32.27 Kernel on a 64 bit non VT machine.
Following instructions here
[http://wiki.xensource.com/xenwiki/Xen4.0](http://wiki.xensource.com/xenwiki/Xen4.0)
for 64 bit Ubuntu 10.04
```

apt-get install bcc bin86 gawk bridge-utils iproute libcurl3
libcurl4-openssl-dev bzip2 module-init-tools transfig tgif texinfo
texlive-latex-base texlive-latex-recommended texlive-fonts-extra
texlive-fonts-recommended pciutils-dev mercurial build-essential 
make gcc libc6-dev zlib1g-dev python python-dev python-twisted
libncurses5-dev patch libvncserver-dev libsdl-dev libjpeg62-dev iasl libbz2-dev e2fslibs-dev git-core uuid-dev ocaml libx11-dev bison flex

apt-get install gcc-multilib
apt-get install xz-utils

make xen
make tools
make install-xen
make install-tools PYTHON_PREFIX_ARG=
```

I did not do```
 make install-stubdom.
```



It is a Ubuntu Desktop 10.04 amd64 bit version.
Then as  mentioned here on this guide
[http://bderzhavets.wordpress.com/2010/03/26/virst-installvirt-manager-at-xen-4-0-rc8-2-6-32-10-pvops-dom0-on-top-ubuntu-karmic-koala-server/](http://bderzhavets.wordpress.com/2010/03/26/virst-installvirt-manager-at-xen-4-0-rc8-2-6-32-10-pvops-dom0-on-top-ubuntu-karmic-koala-server/)
(I did not follow the above guide strictly)

Commented out (xend-unix-server yes) in ```
/etc/xen/xend-config.sxp 
```,
here is my xend-config.sxp
[http://pastebin.com/M8CfrqBc](http://pastebin.com/M8CfrqBc)
Then  exported variable  ```
VIRSH_DEFAULT_CONNECT_URI=”xen:///”
```
in root’s .bashrc.
Then :-
```
# apt-get install ubuntu-virt-server ubuntu-virt-mgmt
```

Now when I open virt-manager the option to install from Local ISO or
PXE are greyed out.
virt-manager version is 0.8.2


Let me know if there is any possibility of improvement so that I can get the option of install from Local ISO here.

---

