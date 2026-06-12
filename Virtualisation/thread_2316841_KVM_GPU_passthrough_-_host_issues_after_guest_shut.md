---
title: "KVM GPU passthrough - host issues after guest shutdown"
date: 2016-03-11
forum: Virtualisation
---

### Post by dik232 on 2016-03-11
I have got GPU passthrough working on 14.04 with Win10 guest using the very helpful post [here]("http://ubuntuforums.org/showthread.php?t=2266916")

Using virt-manager I can boot the guest and everything works as expected, until I shutdown the guest.

It doesn't seem to matter how I shutdown the end result is the same. The guest closes and after a few seconds virt-manager disconnects giving the message

```
 Error polling connection 'qemu:///system': internal error: received hangup / error event on socketTraceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/engine.py", line 343, in _handle_tick_queue
    conn.tick_from_engine(**kwargs)
  File "/usr/share/virt-manager/virtManager/connection.py", line 1271, in tick_from_engine
    raise e  # pylint: disable=raising-bad-type
libvirtError: internal error: received hangup / error event on socket

```

I've increased the logging in libvirtd.conf but see no error or warning messages. Same is true of syslog and kern.long

Other symptoms include:

[LIST]
[*]virsh being unable to connect to qemu:///system
[*]Both sudo lshw and sudo lspci producing nothing / hanging on PCI (sysfs)
[*]Host is unable to suspend, reboot or shutdown - I have to hard reset
[*]Load increases with no cpu and iotop reporting high IO for "kworker" but no read / write
[/LIST]
Any ideas? I've been find to find a solution for this for a couple of weeks with no joy

4.2.0-30-generic
libvirt-bin 1.2.2-0ubuntu13.1.17
qemu 2.0.0+dfsg-2ubuntu1.22

---

### Post by dik232 on 2016-03-29
So after 2 weeks and over 150 views not a single answer. Fortunately I've managed to work this out for myself and here's what I've come up with....

The problem I was having is based around a problem that exists with [AMD Bonaire and Hawaii GPUs]("https://lists.gnu.org/archive/html/qemu-devel/2015-04/msg03128.html") not to responding to a PCI bus reset. I have a R9 290x, a Hawaii card.

The patch was included in [QEMU 2.4]("http://wiki.qemu.org/ChangeLog/2.4#VFIO"). Unfortunately there's no 2.4 or above available for 14.04, I can't even find a ppa, so I had to compile from source. For good measure I used QEMU 2.5.

COMPILE QEMU 2.5, MAKE DEB FILE AND INSTALL:

First you need to install the required packages:

```
sudo apt-get install build-essential git libtool pkg-config intltool-debian checkinstall libglib2.0-dev libfdt-dev libpixman-1-dev zlib1g-dev libaio-dev libbluetooth-dev libbrlapi-dev libbz2-dev  libcap-dev libcap-ng-dev libcurl4-gnutls-dev libgtk-3-dev libibverbs-dev libjpeg8-dev libncurses5-dev libnuma-dev librbd-dev librdmacm-dev libsasl2-dev libsdl1.2-dev libseccomp-dev libsnappy-dev libssh2-1-dev libvde-dev libvdeplug-dev libvte-2.90-dev libxen-dev liblzo2-dev valgrind xfslibs-dev nettle-dev glusterfs-common libgoogle-perftools-dev texinfo libspice-server-dev libusb-1.0-0-dev libusbredirhost-dev
```

You might already have some of these installed but I've just tested on a fresh 14.04.3 install and this is what I needed.

Next download and extract the QEMU source:

```
cd /tmp
wget http://wiki.qemu-project.org/download/qemu-2.5.0.tar.bz2
tar xf qemu-2.5.0.tar.bz2
```

Configure QEMU:

```
cd /tmp/qemu-2.5.0
./configure --target-list=i386-linux-user,i386-softmmu,x86_64-linux-user,x86_64-softmmu --enable-system --enable-sdl --enable-gtk --enable-vte --enable-kvm --enable-bzip2 --enable-libssh2 --enable-linux-user --enable-docs --enable-gnutls --enable-nettle --enable-curses --enable-modules --enable-vhost-net --enable-curl --enable-fdt --enable-rdma --enable-uuid --enable-vde --enable-linux-aio --enable-cap-ng --enable-attr --enable-vhost-net --enable-spice --enable-rbd --enable-libusb --enable-usb-redir --enable-lzo --enable-snappy --enable-seccomp --enable-coroutine-pool --enable-glusterfs --enable-tpm --enable-vhdx --enable-numa --enable-tcmalloc
```

Perhaps not all of these options are necessary but this works for me.

Next run make (my CPU has 8 threads, you might want to adjust this to suit yours):

```
make -j8
```

Produce .deb package:

```
sudo checkinstall --install=no
```

You will be asked some questions, it's fine to go with the defaults.

Now, in folder /tmp/qemu-2.5.0, you should have a qemu_2.5.0-1_amd64.deb package. This can be installed by opening in it in the GUI or by:

```
sudo dpkg -i qemu_2.5.0-1_amd64.deb
```

In order to use QEMU 2.5 you'll now have to restart libvirt:

```
sudo service libvirt-bin restart
```


Hang on.... **IT STILL DOESN'T WORK**. What is this fool on about?

Exactly my thoughts until I discovered that apparently there's also a [bug in the kernel]("https://bugs.launchpad.net/qemu/+bug/1488363") from the [Wiley LTS Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") I was using. Using a newer kernel is useful because it allows vfio-pci in place of pci-stub so I updated my kernel to the Xenial version that's available in the repository:

```
sudo apt-get install linux-image-generic-lts-xenial
```

And now it works!! It's not 100% stable but it's a massive improvement over having to hard reset my machine every time I close a VM that I've passed my GPU or be unable to suspend, reboot or run the VM again. A little test I use is to run lspci in a terminal. If it works I'm good, if it hangs then it's hard reset o'clock.


Hope this helps someone. N&#822;o&#822; &#822;o&#822;n&#822;e&#822; &#822;w&#822;a&#822;n&#822;t&#822;e&#822;d&#822; &#822;t&#822;o&#822; &#822;h&#822;e&#822;l&#822;p&#822; &#822;m&#822;e&#822; :D

---

### Post by dik232 on 2016-04-04
Update:

libvirt doesn't start with linux-image-4.4.0-15-generic so if you're using linux-image-generic-lts-xenial then go with linux-image-4.4.0-13-generic

---

