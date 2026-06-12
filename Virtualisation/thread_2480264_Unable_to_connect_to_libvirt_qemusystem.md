---
title: "Unable to connect to libvirt qemu:///system"
date: 2022-10-23
forum: Virtualisation
---

### Post by oygle on 2022-10-23
I've installed KVM/VirtManager ..

```
sudo apt-get install virt-manager
```

yet there were a few minor errors.

> Warning: The home dir /var/lib/swtpm you specified can't be accessed: No such file or directory
Adding system user `swtpm' (UID 124) ...
Adding new user `swtpm' (UID 124) with group `swtpm' ...
Not creating home directory `/var/lib/swtpm'.

Ran Virtual Machine Manger, double-clicked on the connection and got the following errors.

> 
Unable to connect to libvirt qemu:///system.

Verify that the 'libvirtd' daemon is running.

Libvirt URI is: qemu:///system

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 923, in _do_open
    self._backend.open(cb, data)
  File "/usr/share/virt-manager/virtinst/connection.py", line 153, in open
    conn = libvirt.openAuth(self._open_uri,
  File "/usr/lib/python3/dist-packages/libvirt.py", line 148, in openAuth
    raise libvirtError('virConnectOpenAuth() failed')
libvirt.libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt-sock': Permission denied

so, looking at the last line, and seems just a permissions error, this works okay

```
sudo virt-manager
```

and then went searching more. Found out it was most likely that I'm not in the group **libvirt** , so added gnome-system-tools, added myself to that group, yet the error still occurs. Any ideas please ?

---

### Post by oygle on 2022-10-23
This may help solve the problem ? - [https://kifarunix.com/how-to-fix-qemu-kvm-not-connected-error-on-ubuntu-20-04/](https://kifarunix.com/how-to-fix-qemu-kvm-not-connected-error-on-ubuntu-20-04/)

Do I need to install KVM, as qemu-kvm isn't installed ?

---

### Post by MAFoElffen on 2022-10-26
To use virt-manager, which runs under libvert, you need to add your user to group 'libvirt'.
```

sudo usermod -a -G libvirt $USER  # to add your username to group libvirt
id $USER  # To verfiy that you are added to that group

```

---

### Post by oygle on 2022-10-26
> **MAFoElffen said:**
> To use virt-manager, which runs under libvert, you need to add your user to group 'libvirt'.


Thanks, yes I had done that bu same problem. After spending a few hours on it I realised that KVM wasn't installed, nor was I in the group KVM from memory. Anyway, it was a case of having spent more time that I wanted to, so went for VirtualBox.

---

### Post by MAFoElffen on 2022-10-27
I think our assumption was made when you said:
> **oygle said:**
> I've installed KVM/VirtManager ..

Your choice, though my personal preference for a Virtual Host system is KVM/QEMU.

---

### Post by oygle on 2022-10-27
> **MAFoElffen said:**
> Your choice, though my personal preference for a Virtual Host system is KVM/QEMU.

I think some of the problems I encountered with the QEMU side of things were compounded by the fact that I didn't have KVM installed. Yet if KVM is a dependency of installing QEMU, then why didn't the QEMU installation also install KVM ?

---

### Post by #&amp;thj^% on 2022-10-27
> **oygle said:**
>  then why didn't the QEMU installation also install KVM ?

Just passing through:
```
apt-cache policy qemu-kvm qemu-common qemu-utils
```

---

### Post by oygle on 2022-10-27
> **1fallen said:**
> Just passing through:
```
apt-cache policy qemu-kvm qemu-common qemu-utils
```

Thanks ..

```
apt-cache policy qemu-kvm qemu-common qemu-utils
```

> qemu-kvm:
  Installed: (none)
  Candidate: (none)
  Version table:
qemu-utils:
  Installed: (none)
  Candidate: 1:6.2+dfsg-2ubuntu6.5
  Version table:
     1:6.2+dfsg-2ubuntu6.5 500 (phased 80%)
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
     1:6.2+dfsg-2ubuntu6.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages
     1:6.2+dfsg-2ubuntu6 500
        500 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
N: Unable to locate package qemu-common

So, this is okay - [https://packages.ubuntu.com/search?keywords=qemu-common&searchon=names&suite=jammy&section=all](https://packages.ubuntu.com/search?keywords=qemu-common&searchon=names&suite=jammy&section=all) , but if I follow the 'jammy-updates' link, I get a 500

---

### Post by #&amp;thj^% on 2022-10-27
Keep in mind the Phased aspect now, IE:
```
qemu-utils:
Installed: (none)
Candidate: 1:6.2+dfsg-2ubuntu6.5
Version table:
**_1:6.2+dfsg-2ubuntu6.5 500 (phased 80%)_**
500 http://au.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
1:6.2+dfsg-2ubuntu6.2 500
```
if needed to install correctly please try:
```
sudo apt remove --autoremove qemu-utils
```
I'm not trying to take over here but I just install like:
```
sudo apt install virt-manager virt-viewer
``` 
here's the impact:
```
 apt depends virt-manager virt-viewer qemu
virt-manager
  Depends: gir1.2-gtk-3.0 (>= 3.10)
  Depends: gir1.2-gtk-vnc-2.0
  Depends: gir1.2-gtksource-4
  Depends: gir1.2-libosinfo-1.0
  Depends: gir1.2-libvirt-glib-1.0
  Depends: gir1.2-vte-2.91
  Depends: python3-dbus
  Depends: python3-gi (>= 3.31.3~)
  Depends: python3-gi-cairo
  Depends: python3-libvirt (>= 0.7.1)
  Depends: virtinst (= 1:4.0.0-1)
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: <python3:any>
    python3:i386
    python3
 |Recommends: gir1.2-ayatanaappindicator3-0.1
  Recommends: gir1.2-appindicator3-0.1
  Recommends: gir1.2-spiceclientglib-2.0
  Recommends: gir1.2-spiceclientgtk-3.0
  Recommends: libvirt-daemon-system (>= 1.2.7)
  Suggests: gir1.2-secret-1
  Suggests: gnome-keyring
  Suggests: python3-guestfs
  Suggests: ssh-askpass
    ksshaskpass
    kwalletcli
    lxqt-openssh-askpass
    ssh-askpass-fullscreen
    ssh-askpass-gnome:i386
    ssh-askpass-gnome
  Suggests: virt-viewer
virt-viewer
  Depends: libc6 (>= 2.34)
  Depends: libgdk-pixbuf-2.0-0 (>= 2.25.2)
  Depends: libglib2.0-0 (>= 2.43.2)
  Depends: libgovirt2 (>= 0.3.6)
  Depends: libgtk-3-0 (>= 3.11.5)
  Depends: libgtk-vnc-2.0-0 (>= 0.4.1)
  Depends: libpango-1.0-0 (>= 1.14.0)
  Depends: librest-0.7-0 (>= 0.8.0)
  Depends: libspice-client-glib-2.0-8 (>= 0.35)
  Depends: libspice-client-gtk-3.0-5 (>= 0.35)
  Depends: libvirt-glib-1.0-0 (>= 0.1.8)
  Depends: libvirt0 (>= 1.2.8~rc2)
  Depends: libxml2 (>= 2.7.4)
  Suggests: netcat
    netcat-traditional
    netcat-openbsd
qemu
me@me-Standard-PC-Q35-ICH9-2009:~$ 

```

---

### Post by oygle on 2022-10-27
Thanks, I missed the 'phased' part. Have cleaned up now with

```
sudo apt remove --autoremove qemu-utils
```

Interesting on the dependencies, so qemu doesn't show any dependencies of KVM. But if Virtual manager is a GUI for KVM, wouldn't I need KVM installed ?

---

### Post by #&amp;thj^% on 2022-10-27
At first it's not a straight-forward tool, but after a short stay, >>> you'll be hooked. :D
here's how it all shakes out:
```
 apt depends kvm
<kvm>

```
On with the show using this command:
```
sudo apt install virt-manager virt-viewer
```
```
The following additional packages will be installed:
  cpu-checker dmeventd gir1.2-ayatanaappindicator3-0.1 gir1.2-gstreamer-1.0
  gir1.2-gtk-vnc-2.0 gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0
  gir1.2-spiceclientglib-2.0 gir1.2-spiceclientgtk-3.0 ibverbs-providers
  ipxe-qemu ipxe-qemu-256k-compat-efi-roms jq libaio1 libbrlapi0.8 libburn4
  libcacard0 libdaxctl1 libdecor-0-0 libdecor-0-plugin-1-cairo
  libdevmapper-event1.02.1 libfdt1 libgfapi0 libgfrpc0 libgfxdr0 libglusterfs0
  libgovirt-common libgovirt2 libgtk-vnc-2.0-0 libgvnc-1.0-0 libibverbs1
  libiscsi7 libisoburn1 libisofs6 libjq1 libjte2 liblvm2cmd2.03 libndctl6
  libnss-mymachines libonig5 libosinfo-1.0-0 libphodav-2.0-0
  libphodav-2.0-common libpmem1 libpmemobj1 librados2 librbd1 librdmacm1
  libsdl2-2.0-0 libslirp0 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5
  libspice-server1 libtpms0 liburing2 libusbredirhost1 libusbredirparser1
  libvirglrenderer1 libvirt-clients libvirt-daemon
  libvirt-daemon-config-network libvirt-daemon-config-nwfilter
  libvirt-daemon-driver-qemu libvirt-daemon-system
  libvirt-daemon-system-systemd libvirt-glib-1.0-0 libvirt-glib-1.0-data
  libvirt0 libxml2-utils lvm2 mdevctl msr-tools osinfo-db ovmf python3-libvirt
  python3-libxml2 qemu-block-extra qemu-system-common qemu-system-data
  qemu-system-gui qemu-system-x86 qemu-utils seabios
  spice-client-glib-usb-acl-helper swtpm swtpm-tools systemd-container
  thin-provisioning-tools virtinst xorriso
Suggested packages:
  libosinfo-l10n gstreamer1.0-plugins-bad libvirt-login-shell
  libvirt-daemon-driver-storage-gluster
  libvirt-daemon-driver-storage-iscsi-direct libvirt-daemon-driver-storage-rbd
  libvirt-daemon-driver-storage-zfs libvirt-daemon-driver-lxc
  libvirt-daemon-driver-vbox libvirt-daemon-driver-xen numad auditd nfs-common
  open-iscsi pm-utils systemtap zfsutils samba vde2 debootstrap trousers
  python3-guestfs ssh-askpass python3-argcomplete xorriso-tcltk jigit cdck
The following NEW packages will be installed:
  cpu-checker dmeventd gir1.2-ayatanaappindicator3-0.1 gir1.2-gstreamer-1.0
  gir1.2-gtk-vnc-2.0 gir1.2-libosinfo-1.0 gir1.2-libvirt-glib-1.0
  gir1.2-spiceclientglib-2.0 gir1.2-spiceclientgtk-3.0 ibverbs-providers
  ipxe-qemu ipxe-qemu-256k-compat-efi-roms jq libaio1 libbrlapi0.8 libburn4
  libcacard0 libdaxctl1 libdecor-0-0 libdecor-0-plugin-1-cairo
  libdevmapper-event1.02.1 libfdt1 libgfapi0 libgfrpc0 libgfxdr0 libglusterfs0
  libgovirt-common libgovirt2 libgtk-vnc-2.0-0 libgvnc-1.0-0 libibverbs1
  libiscsi7 libisoburn1 libisofs6 libjq1 libjte2 liblvm2cmd2.03 libndctl6
  libnss-mymachines libonig5 libosinfo-1.0-0 libphodav-2.0-0
  libphodav-2.0-common libpmem1 libpmemobj1 librados2 librbd1 librdmacm1
  libsdl2-2.0-0 libslirp0 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5
  libspice-server1 libtpms0 liburing2 libusbredirhost1 libusbredirparser1
  libvirglrenderer1 libvirt-clients libvirt-daemon
  libvirt-daemon-config-network libvirt-daemon-config-nwfilter
  libvirt-daemon-driver-qemu libvirt-daemon-system
  libvirt-daemon-system-systemd libvirt-glib-1.0-0 libvirt-glib-1.0-data
  libvirt0 libxml2-utils lvm2 mdevctl msr-tools osinfo-db ovmf python3-libvirt
  python3-libxml2 qemu-block-extra qemu-system-common qemu-system-data
  qemu-system-gui qemu-system-x86 qemu-utils seabios
  spice-client-glib-usb-acl-helper swtpm swtpm-tools systemd-container
  thin-provisioning-tools virt-manager virt-viewer virtinst xorriso
0 upgraded, 92 newly installed, 0 to remove and 3 not upgraded.
Need to get 46.3 MB of archives.
After this operation, 172 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
```

---

### Post by oygle on 2022-10-27
> **1fallen said:**
> At first it's not a straight-forward tool, but after a short stay, >>> you'll be hooked. :D


Yes, I may be tempted to try it out. Thanks  :)

---

### Post by MAFoElffen on 2022-10-27
I love KVM and have been using for over a decade now. What you need to understand is that you are not locked into using Virt-Manager to access your VM's. You can start your VM's from the commandline, Virt Manager, have them autostart, etc... 

Then access the running VM's via ssh, VNC, Xrdp, GnomeBoxes. etc. There are so many choices, it's mind boggling. From there it is truely a personal preference.

What is good for me, is that I can emulate many different machine architectures and hardware to test on different arch'es than what I own... As well as replicating different virtual network architectures.

---

### Post by oygle on 2022-10-27
> **MAFoElffen said:**
> I love KVM and have been using for over a decade now. What you need to understand is that you are not locked into using Virt-Manager to access your VM's. You can start your VM's from the commandline, Virt Manager, have them autostart, etc... 

Then access the running VM's via ssh, VNC, Xrdp, GnomeBoxes. etc. There are so many choices, it's mind boggling. From there it is truely a personal preference.

What is good for me, is that I can emulate many different machine architectures and hardware to test on different arch'es than what I own... As well as replicating different virtual network architectures.

Okay thanks. It does seem I should have gone the KVM route and not jumped straight into Virt-manager and then got myself into a spot of trouble. I may consider installing it alongside VirtualBox, so that I can try it out.

---

### Post by TheFu on 2022-10-31
> **oygle said:**
> Thanks, I missed the 'phased' part. Have cleaned up now with

```
sudo apt remove --autoremove qemu-utils
```

Interesting on the dependencies, so qemu doesn't show any dependencies of KVM. But if Virtual manager is a GUI for KVM, wouldn't I need KVM installed ?

QEMU can happily be used without KVM. There is no dependency in that direction.
Also, libvirt and virt-manager are for managing VMs and containers which don't have to be KVM-based.

I think that's the confusion.  These are powerful tools.  Almost every how-to guide will have you run 'kvm-ok' to verify that things are ready for KVM.
```
$ kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used
```

Virtualbox is an all-in-one tool and suitable for desktop-on-desktop virtualization.  It isn't as flexible and has less performance and an ugly (my opinion) PEULA for the guest additions.  If you are virtualizing servers, kvm+qemu+libvirt is the best, fastest, most flexible, option available today.  But what's best for me doesn't have to be the best for anyone else.  OTOH, all the big VPS providers world-wide use KVM.  There's a reason.  Some of the largest even migrated from other hypervisors to KVM.

KVM doesn't hold our hands. There are tools like Boxes or MultiPass or Virtualbox, if that is needed.  Of course, there are trade-offs in using any of them, just like there are trade-offs in using virt-manager, libvirt, and whatever hypervisors it supports.  With that flexibility come some added complexity.

For non-experts, only 1 hypervisor can be installed at a time in the same OS.  There will be conflicts if two are installed, but if you are happy to manually load and unload the VT-x/AMD-v driver support as needed by the specific hypervisor you choose, go for it.

BTW, with each different release, dependencies change a little, so whenever asking any questions, please, please, please, include the exact release being used.  Also, we can have our APT settings configured a little different. Some people never want any "suggested" packages installed, while others want all suggested packages installed.  Personal preference, but different people have different preferences for different reasons.

Flexibility.  Sometimes too much flexibility.

---

### Post by oygle on 2022-10-31
> **TheFu said:**
> For non-experts, only 1 hypervisor can be installed at a time in the same OS.  There will be conflicts if two are installed, but if you are happy to manually load and unload the VT-x/AMD-v driver support as needed by the specific hypervisor you choose, go for it.

Thanks for your clarification on all those other VM type tools, etc. I _was_ going to install KVM beside VirtualBox, but now see I shouldn't. Thanks.

VirtualBox does seem to use a lot of resources. I'm only using it to go into Windows 8.1 on the guest, run MS Money, export a few files, and back out again, and then shutdown Win 8.1. But most of the time when I'm doing that, the performance degradation in Kubuntu is very noticeable.

Next time I go down the VM route, I will definitely try out KVM.

---

### Post by TheFu on 2022-11-01
MS-Windows is bloated, so regardless of the VM host, it will feel that way.
I had to boot Windows (in a VM) today to do some financial stuff myself.  It runs in KVM with libvirt to make VM management easier.  The VM has, let me look ... 
2 vCPUs ; because selecting 1 loaded a different Windows kernel.
1.5G of RAM
~100G of storage - 60G for the OS and 40G for data.
For years, this VM was a Windows Media Center for my network.  When free schedule data ended, I purged all the media center stuff and retained just the financial programs.

This VM has moved from a number of VM hosts over the decades.  It started on a Core2 Duo, moved to a Core i5, then to a Ryzen 5 where it sits today.  The CPU change from Intel to AMD did require some changes to the VM settings, but the other moves were nearly file copies on the "easy" scale.

Around 5 yrs ago, I switched to using SPICE for the display, which makes it very usable on the same LAN. Prior to that, I was using the cirrus/VGA emulations.  SPICE was a huge vGPU improvement.  I think newer versions of Ubuntu support something even better than SPICE called virtio.  We've had virtio for networking and disk access for over a decade. I look forward to using virtio for the virtual GPUs.  Alas, 99% of the VMs I run are servers and there isn't any "desktop" used.  After networking is enabled during installation, I use ssh to perform all work and management on those systems.

BTW, the connection string I use to connect to my Windows VM is 
```
/usr/bin/virt-viewer --connect qemu+ssh://hadar/system WinUlt
```
when I'm on a different system.  I'm seldom sitting on the same computer as my VM host stuff runs.  MSFT gave a way the Ultimate OS to people in the business at a release party they hosted.  Thank you MSFT. I've made good use of that freebie.
I have a script that looks to see of the VM is running. If not, it starts it and waits 20 seconds before attempting the virt-viewer command.  There is a virt-viewer for Windows too.  I've used it a few times, but not recently.  My daily driver is a highly custom version of Ubuntu with no DE, old-guy WM and only the bloat that isn't easily removed.  ;)

---

### Post by MAFoElffen on 2022-11-02
Just to followup, these are the 3 commands I use to install KVM on Ubuntu 20.04 and newer:
```

sudo apt install -y qemu qemu-kvm libvirt-daemon libvirt-clients virt-manager bridge-utils
sudo usermod -a -G libvirt $USER
sudo usermod -a -G kvm $USER

```
With the installation of package 'bridge-utils' as optional

Optional KVM/QEMU Utils I use beyond that are:
```

qemu-system 
qemu-system-alpha
qemu-system-arm
qemu-system-riscv64 
qemu-system-mips 
qemu-system-misc 
qemu-system-or1k
qemu-system-ppc 
qemu-system-riscv64
qemu-system-s390x 
qemu-system-sparc 
qemu-user 
qemu-user-binfmt

```
Most of those are emulations...

---

### Post by TheFu on 2022-11-02
virt-manager is a GUI, so not needed on the KVM/QEMU host system, unless it is a desktop.  Ewww. I feel dirty just thinking of doing that.  ;)
All the other packages are what I have installed on a 20.04 KVM host.  I don't remember adding the groups, but my userid is a member of those two groups.

One thing I've noticed is that EFI still isn't the default boot method on 20.04:
```
# efibootmgr
EFI variables are not supported on this system.
```

That with a 20.04 KVM host and a 22.10 Xubuntu guest VM.

---

### Post by oygle on 2022-11-02
> **TheFu said:**
> MS-Windows is bloated, so regardless of the VM host, it will feel that way.
I had to boot Windows (in a VM) today to do some financial stuff myself.  It runs in KVM with libvirt to make VM management easier.  The VM has, let me look ... 
2 vCPUs ; because selecting 1 loaded a different Windows kernel.

Thanks, interesting to know, yet I wouldn't know one Windows kernel from another. It "seems" to work okay, just open MS Money, export a small file. You certainly are right into VM's, and it seems a 'non desktop' approach (is that headless ?).

> **MAFoElffen said:**
> Just to followup, these are the 3 commands I use to install KVM on Ubuntu 20.04 and newer:
```

sudo apt install -y qemu qemu-kvm libvirt-daemon libvirt-clients virt-manager bridge-utils
sudo usermod -a -G libvirt $USER
sudo usermod -a -G kvm $USER

```
With the installation of package 'bridge-utils' as optional

Thanks, I'll use the when I install it.

> **TheFu said:**
> virt-manager is a GUI, so not needed on the KVM/QEMU host system, unless it is a desktop.  Ewww. I feel dirty just thinking of doing that.  ;)

...LOL, .. I see the preference for headless.   :)

> **TheFu said:**
> All the other packages are what I have installed on a 20.04 KVM host.  I don't remember adding the groups, but my userid is a member of those two groups.

One thing I've noticed is that EFI still isn't the default boot method on 20.04:
```
# efibootmgr
EFI variables are not supported on this system.
```

That with a 20.04 KVM host and a 22.10 Xubuntu guest VM.

I don't think I had to do anything as such, with 22.04

```
efibootmgr
```

> BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0000,0001,0002,0008,0007,0005,0006
Boot0000* P0: ST1000LM024 HN-M101MBB    
Boot0001* P1: HL-DT-ST DVD+/-RW GU90N   
Boot0002* Realtek PXE B07 D00
Boot0005* Onboard NIC(IPV4)
Boot0006* Onboard NIC(IPV6)
Boot0007* ubuntu
Boot0008* ubuntu


---

