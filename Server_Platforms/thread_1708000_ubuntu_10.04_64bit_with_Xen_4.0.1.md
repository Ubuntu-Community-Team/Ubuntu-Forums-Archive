---
title: "ubuntu 10.04 64bit with Xen 4.0.1"
date: 2011-03-16
forum: Server Platforms
---

### Post by roadofking on 2011-03-16
[LEFT]hi there,
I got a xend start problem when I install xen 4.0.1 on ubuntu 10.04 64_bit:(

my installation steps are as follows:

first, install packages[INDENT]$sudo apt-get install bcc bin86 gawk bridge-utils iproute libcurl3 libcurl4-openssl-dev bzip2 module-init-tools transfig tgif texinfo texlive-latex-base texlive-latex-recommended texlive-fonts-extra texlive-fonts-recommended pciutils-dev mercurial build-essential make gcc libc6-dev zlib1g-dev python python-dev python-twisted libncurses5-dev patch libvncserver-dev libsdl1.2-dev libjpeg62-dev iasl libbz2-dev e2fslibs-dev git-core uuid-dev ocaml libx11-dev bison flex
[/INDENT][INDENT]
$sudo apt-get install gcc-multilib xz-utils
[/INDENT]second, download xen 4.0.1 from [http://www.xen.org/products/downloads.html](http://www.xen.org/products/downloads.html) to /usr/src and install[INDENT]$sudo make xen
$sudo make tools
$sudo make stubdom 

$sudo make install-xen
$sudo make install-tools PYTHON_PREFIX_ARG=
$sudo make install-stubdom
[/INDENT]third, download xen dom0 kernel from &#700;jeremy&#700; to /usr/src and install it[INDENT]$sudo git clone -o xen -n git://git.kernel.org/pub/scm/linux/kernel/git/jeremy/xen.git linux-2.6-xen
$sudo git reset --hard
$sudo git pull

$sudo cp /boot/config-2.6.32-24-generic /usr/src/linux-2.6-xen
$sudo mv config-2.6.32-24-generic .config

$sudo make menuconfig

$make sure follows options are chosed
CONFIG_XEN=y
CONFIG_XEN_PVHVM=y
CONFIG_XEN_MAX_DOMAIN_MEMORY=128
CONFIG_XEN_SAVE_RESTORE=y
CONFIG_XEN_DEBUG_FS=y
CONFIG_SWIOTLB_XEN=y
CONFIG_MICROCODE_XEN=y
CONFIG_XEN_DOM0=y
CONFIG_XEN_PRIVILEGED_GUEST=y
CONFIG_XEN_DOM0_PCI=y
CONFIG_XEN_PCI_PASSTHROUGH=y
CONFIG_PCI_XEN=y
CONFIG_XEN_PCIDEV_FRONTEND=y
CONFIG_XEN_BLKDEV_FRONTEND=y
CONFIG_NETXEN_NIC=m
CONFIG_XEN_NETDEV_FRONTEND=m
CONFIG_XEN_KBDDEV_FRONTEND=y
CONFIG_HVC_XEN=y
CONFIG_XEN_FBDEV_FRONTEND=y
CONFIG_XEN_BALLOON=y
CONFIG_XEN_SCRUB_PAGES=y
CONFIG_XEN_DEV_EVTCHN=y
CONFIG_XEN_BACKEND=y
CONFIG_XEN_NETDEV_BACKEND=m
CONFIG_XEN_BLKDEV_BACKEND=m
CONFIG_XEN_BLKDEV_TAP=m
CONFIG_XEN_BLKBACK_PAGEMAP=m
CONFIG_XEN_PCIDEV_BACKEND=m
CONFIG_XEN_PCIDEV_BACKEND_VPCI=y
CONFIG_XENFS=y
CONFIG_XEN_COMPAT_XENFS=y
CONFIG_XEN_SYS_HYPERVISOR=y
CONFIG_XEN_MCE=y
CONFIG_XEN_XENBUS_FRONTEND=y
CONFIG_XEN_GNTDEV=y
CONFIG_XEN_S3=y
CONFIG_ACPI_PROCESSOR_XEN=y
CONFIG_XEN_PLATFORM_PCI=m

$sudo make
$sudo make modules_install install
[/INDENT]forth, modify grub2 file and others[INDENT]$cd /boot
$sudo update-initramfs -c -k 2.6.32.32 (I got 2.6.32.32 from &#700;jeremy&#700;)

$update-grub

$sudo gedit /etc/xen/xend-config.sxp 
change #(xend-unix-server no) to (xend-unix-server yes)

$sudo reboot

$sudo update-rc.d xend defaults 20 21
$sudo update-rc.d xendomains defaults 21 20

$sudo gedit /boot/grub/grub.cfg
change to 
menuentry 'Ubuntu, with Linux 2.6.32.32' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    multiboot (hd0,1)/boot/xen-4.0.gz dummy=dummy
    module  /boot/vmlinuz-2.6.32.32 dummy=dummy root=UUID=XXXX ro nomodeset
    module  /boot/initrd.img-2.6.32.32
}

$sudo reboot
[/INDENT]finally, I try xen command to verify installation is successful or not, it failed[INDENT]$sudo xm info
Error: Unable to connect to xend: No such file or directory. Is xend running?

$sudo xend start
ifdown: interface eth0 not configured
RTNETLINK answers: Device or resource busy

i$fconfig
eth0      Link encap:Ethernet  HWaddr 48:5b:39:49:6d:08  
          inet addr:XXX  Bcast:XXX Mask:255.255.255.0
          inet6 addr: XXX Scope:Global
          inet6 addr: XXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3381275 (3.3 MB)  TX bytes:510689 (510.6 KB)
          Interrupt:223 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

$sudo gedit /etc/network/interfaces
and added 
iface eth0 inet static
address XXX
netmask 255.255.255.0
network XXX
broadcast XXX
gateway XXX

$sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                          [ OK ]

$sudo ifup eth0

$sudo xend start
got nothing

$sudo xm info
Error: Unable to connect to xend: No such file or directory. Is xend running?
[/INDENT]I have no idea about this problem, did I do anything wrong in my installation steps?
or did I miss anything should be done?

here I got some log in  /var/log/xen/xend-debug.log, as follows[INDENT]cat: /sys/bus/scsi/devices/host0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host0/model: No such file or directory
cat: /sys/bus/scsi/devices/host0/type: No such file or directory
cat: /sys/bus/scsi/devices/host0/rev: No such file or directory
cat: /sys/bus/scsi/devices/host0/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host1/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host1/model: No such file or directory
cat: /sys/bus/scsi/devices/host1/type: No such file or directory
cat: /sys/bus/scsi/devices/host1/rev: No such file or directory
cat: /sys/bus/scsi/devices/host1/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host2/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host2/model: No such file or directory
cat: /sys/bus/scsi/devices/host2/type: No such file or directory
cat: /sys/bus/scsi/devices/host2/rev: No such file or directory
cat: /sys/bus/scsi/devices/host2/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host3/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host3/model: No such file or directory
cat: /sys/bus/scsi/devices/host3/type: No such file or directory
cat: /sys/bus/scsi/devices/host3/rev: No such file or directory
cat: /sys/bus/scsi/devices/host3/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/model: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/type: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/rev: No such file or directory
cat: /sys/bus/scsi/devices/target0:0:0/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/vendor: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/model: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/type: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/rev: No such file or directory
cat: /sys/bus/scsi/devices/target1:0:0/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host4/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host4/model: No such file or directory
cat: /sys/bus/scsi/devices/host4/type: No such file or directory
cat: /sys/bus/scsi/devices/host4/rev: No such file or directory
cat: /sys/bus/scsi/devices/host4/scsi_level: No such file or directory
cat: /sys/bus/scsi/devices/host5/vendor: No such file or directory
cat: /sys/bus/scsi/devices/host5/model: No such file or directory
cat: /sys/bus/scsi/devices/host5/type: No such file or directory
cat: /sys/bus/scsi/devices/host5/rev: No such file or directory
cat: /sys/bus/scsi/devices/host5/scsi_level: No such file or directory
Exception starting xend: (111, 'Connection refused')
[/INDENT]and in /var/log/xen/xend.log, as follows[INDENT][2011-03-16 15:18:19 1091] INFO (SrvDaemon:227) Xend stopped due to signal 15.
[2011-03-16 15:19:05 1062] INFO (SrvDaemon:332) Xend Daemon started
[2011-03-16 15:19:05 1062] INFO (SrvDaemon:336) Xend changeset: unavailable.
[2011-03-16 15:19:09 1062] ERROR (SrvDaemon:349) Exception starting xend ((111, 'Connection refused'))
Traceback (most recent call last):
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/server/SrvDaemon.py", line 341, in run
    servers = SrvServer.create()
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/server/SrvServer.py", line 251, in create
    root.putChild('xend', SrvRoot())
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/server/SrvRoot.py", line 40, in __init__
    self.get(name)
  File "/usr/local/lib/python2.6/dist-packages/xen/web/SrvDir.py", line 84, in get
    val = val.getobj()
  File "/usr/local/lib/python2.6/dist-packages/xen/web/SrvDir.py", line 52, in getobj
    self.obj = klassobj()
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/server/SrvDomainDir.py", line 41, in __init__
    self.xd = XendDomain.instance()
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/XendDomain.py", line 1882, in instance
    inst.init()
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/XendDomain.py", line 114, in init
    xstransact.Mkdir(XS_VMROOT)
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/xenstore/xstransact.py", line 355, in Mkdir
    complete(path, lambda t: t.mkdir(*args))
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/xenstore/xstransact.py", line 361, in complete
    t = xstransact(path)
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/xenstore/xstransact.py", line 29, in __init__
    self.transaction = xshandle().transaction_start()
  File "/usr/local/lib/python2.6/dist-packages/xen/xend/xenstore/xsutil.py", line 18, in xshandle
    xs_handle = xen.lowlevel.xs.xs()
Error: (111, 'Connection refused')
[/INDENT]hope anyone could help me, thank you 




[/LEFT]

---

### Post by roadofking on 2011-03-16
by the way I've add 
[INDENT]none /proc/xen xenfs defaults 0 0
[/INDENT]to /etc/fstab

---

### Post by roadofking on 2011-03-16
this is solved by updating 'jeremy' kernel and make install it again

---

### Post by unicell on 2011-12-24
I run into exactly the same problem here with Ubuntu 10.04 64bit, Xen 4.0.3 hg tree, and Jeremy pvops 2.6.32.48 combination.

Still didn't figure it out why, but after I switch to Xen 4.1 hg tree, it works like a charm~ :)

Guess it could be some remaining files caused the conflict after several Xen version switching.

---

