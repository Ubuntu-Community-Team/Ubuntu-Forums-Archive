---
title: "trying update QEMU on Ubuntu 16.04"
date: 2016-09-18
forum: Virtualisation
---

### Post by yakatape on 2016-09-18
Hi everyone,


I'm on an issue of update for QEMU 2.7.0 .. i've tried to remove the old version of QEMU (2.5.0) as you can see below (sorry for the french terminal..):
```
root@Yaka_XPS-dim. sept. 18-22:40:59 ~#apt-get remove qemu
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Le paquet « qemu » n'est pas installé, et ne peut donc être supprimé
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  cfortran comerr-dev fonts-freefont-otf krb5-multidev libafterimage0 libconfuse-common
  libconfuse0 libftgl2 libgl2ps-dev libgl2ps0 libgssrpc4 libidl-2-0 libkadm5clnt-mit9
  libkadm5srv-mit9 libkdb5-8 libkrb5-dev liborbit2 libroot-core-dev libroot-core5.34
  libroot-geom-dev libroot-geom5.34 libroot-graf2d-gpad-dev libroot-graf2d-gpad5.34
  libroot-graf2d-graf-dev libroot-graf2d-graf5.34 libroot-graf3d-g3d5.34
  libroot-graf3d-gl-dev libroot-graf3d-gl5.34 libroot-gui-dev libroot-gui-ged5.34
  libroot-gui5.34 libroot-hist-dev libroot-hist5.34 libroot-io-dev libroot-io5.34
  libroot-math-mathcore-dev libroot-math-mathcore5.34 libroot-math-matrix-dev
  libroot-math-matrix5.34 libroot-math-minuit5.34 libroot-net-dev libroot-net5.34
  libroot-proof-dev libroot-proof5.34 libroot-tree-dev libroot-tree-treeplayer5.34
  libroot-tree5.34 libssl-dev libssl-doc libxpm-dev python-gnome2 python-pyorbit
  root-plugin-geom-gdml root-plugin-geom-geombuilder root-plugin-geom-geompainter
  root-plugin-graf2d-asimage root-plugin-graf2d-x11 root-plugin-gui-guibuilder
  root-plugin-hist-histpainter root-plugin-io-xml root-system-common
Veuillez utiliser « apt autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

```


Step done for the Compilation and installation (QEMU 2.7.0) :
```
tar xvf qemu-2.7.0.tar.bz2 
cd qemu-2.7.0/
mkdir build
cd build/
../configure 
make && make install
```


Compiled and installed as we can see the version 2.7.0 installed below :
```
root@Yaka_XPS-dim. sept. 18-22:48:10 ~#kvm -version
QEMU emulator version 2.7.0, Copyright (c) 2003-2016 Fabrice Bellard and the QEMU Project developers

```


or from :
```
root@Yaka_XPS-dim. sept. 18-22:54:08 ~#qemu-system-x86_64 -version
QEMU emulator version 2.7.0, Copyright (c) 2003-2016 Fabrice Bellard and the QEMU Project developers

```


However when i'm looking through Virsh command line, still having the old QEMU version (2.5.0) Executed hypervisor :
```
root@Yaka_XPS-dim. sept. 18-22:49:47 ~#virsh -c qemu:///system version --daemon
Compiled against library: libvirt 1.3.1
Using library: libvirt 1.3.1
Utilisation de l'API : QEMU 1.3.1
Exécution de l'hyperviseur : QEMU 2.5.0
Running against daemon: 1.3.1

```


Can someone help me about it ? and how solve it ? :o

Thanks in advance for looking thread and answers :P
Yakatape

---

### Post by mörgæs on 2016-09-19
Hi, welcome to the fora.

Would Qemu 2.6 be OK?

---

### Post by yakatape on 2016-09-19
Hello Mörgaes,

Its same issue with 2.6.0 :(

---

### Post by mörgæs on 2016-09-19
I meant, if you can use 2.6 then I suggest that you install Buntu 16.10 (beta version) in which 2.6 is the standard Qemu. Then there will be no trouble with *build *and *make*. 

You can do a dual boot, keeping 16.04.1 for fall-back.

---

### Post by KillerKelvUK on 2016-09-19
Hi yakatape, if Google translate is working properly then the terminal output from your first post where you 'apt-get remove qemu' actually says "the qemu package is not installed..." and then apt is listing packages unrelated to qemu that are now orphaned and can be removed (this is unrelated but standard apt behaviour).  You need to be very specific in the package name to remove otherwise apt won't find it, you can use tab completion to verify you have a correct package name or your could list all the installed packaged on your system which contain "qemu" in their title i.e. with ```
 dpkg -l | grep qemu
``` You would then use these package names in your 'apt-get remove' commands.

---

### Post by yakatape on 2016-09-19
Hello and thanks for your feedback KillerKelvUK

about your commande you can see below the return of it :
```
root@Yaka_XPS-lun. sept. 19-22:08:09 ~#dpkg -l |grep qemu
ii  ipxe-qemu                                  1.0.0+git-20150424.a25a16d-1ubuntu1                         all          PXE boot firmware - ROM images for qemu
ii  qemu-block-extra:amd64                     1:2.5+dfsg-5ubuntu10.4                                      amd64        extra block backend modules for qemu-system and qemu-utils
ii  qemu-kvm                                   1:2.5+dfsg-5ubuntu10.4                                      amd64        QEMU Full virtualization
ii  qemu-system-common                         1:2.5+dfsg-5ubuntu10.4                                      amd64        QEMU full system emulation binaries (common files)
ii  qemu-system-x86                            1:2.5+dfsg-5ubuntu10.4                                      amd64        QEMU full system emulation binaries (x86)
ii  qemu-utils                                 1:2.5+dfsg-5ubuntu10.4                                      amd64        QEMU utilities



```

which one i've to remove ? :x
thanks for your time

---

### Post by KillerKelvUK on 2016-09-19
That kinda depends on what you are building from the qemu source tree, if you aren't certain yourself I'd suggest you need to tread very carefully.  Building from source will most certainly replace the qemu-system-x86 package but I also think it will build the qemu-utils as well, if you haven't done this previous I'd suggest you test out the process inside a VM on your current 2.5 versions.  You could also build the new packages in a build dir but not actually 'sudo make install' them, that way you should be able to run the built binaries from within the build directory to test what you need to test i.e. you may find you've omitted features you feel are necessary and thus you need to modify your ./configure parameters.

One other option for you to consider is to use a PPA to update all necessary package, this avoids you having to build but it does leave you a little difficulty if the PPA has broken binaries.  One I've used before which seems okay is ([https://launchpad.net/~jacob/+archive/ubuntu/virtualisation](https://launchpad.net/~jacob/+archive/ubuntu/virtualisation)).

---

### Post by yakatape on 2016-09-19
Ty again for your answer [[COLOR=#000000]KillerKelvUK[/COLOR]]("https://ubuntuforums.org/member.php?u=1728893")

i just tried to make "apt-get install qemu" and now i got the correct hypervisor version in virsh command :

root@Yaka_XPS-lun. sept. 19-23:28:17 qemu-2.7.0#virsh -c qemu:///system version
Compiled against library: libvirt 1.3.1
Using library: libvirt 1.3.1
Utilisation de l'API : QEMU 1.3.1
Exécution de l'hyperviseur : QEMU 2.7.0

Before trying this one, i wasnt able anymore to create new virtual machine with this error :
```
Impossible de terminer l'installation&#8239;: «&#8239;Couldn't create storage volume 'generic-1.qcow2': 'internal error: unable to parse qemu-img output ''' »

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/asyncjob.py", line 90, in cb_wrapper
    callback(asyncjob, *args, **kwargs)
  File "/usr/share/virt-manager/virtManager/create.py", line 2277, in _do_async_install
    guest.start_install(meter=meter)
  File "/usr/share/virt-manager/virtinst/guest.py", line 487, in start_install
    dev.setup(meter)
  File "/usr/share/virt-manager/virtinst/devicedisk.py", line 861, in setup
    vol_object = self._storage_backend.create(meter)
  File "/usr/share/virt-manager/virtinst/diskbackend.py", line 439, in create
    return self._vol_install.install(meter=progresscb)
  File "/usr/share/virt-manager/virtinst/storage.py", line 809, in install
    "'%s': '%s'" % (self.name, str(e)))
RuntimeError: Couldn't create storage volume 'generic-1.qcow2': 'internal error: unable to parse qemu-img output '''



```


since i've make the apt-get install qemu (who show the correct version under virsh) the problem still here i've catch the syslog event :
```
Sep 19 23:33:12 XPS-15-9550 kernel: [ 1007.871744] audit: type=1400 audit(1474320792.676:434): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-img" pid=6166 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0Sep 19 23:33:12 XPS-15-9550 libvirtd[5709]: internal error: unable to parse qemu-img output ''

```


and when i restart the /etc/init.d/libvirtd-bin i got following error on my syslog :
```
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.096535] audit: type=1400 audit(1474320983.899:435): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-alpha" pid=6351 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0Sep 19 23:36:23 XPS-15-9550 libvirtd[6205]: libvirt version: 1.3.1, package: 1ubuntu10.1 (dann frazier <dannf@ubuntu.com> Fri, 03 Jun 2016 14:41:21 -0600)
Sep 19 23:36:23 XPS-15-9550 libvirtd[6205]: hostname: XPS-15-9550
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.106101] audit: type=1400 audit(1474320983.907:436): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-alpha" pid=6352 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.115574] audit: type=1400 audit(1474320983.915:437): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-arm" pid=6353 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.125294] audit: type=1400 audit(1474320983.927:438): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-arm" pid=6354 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.134900] audit: type=1400 audit(1474320983.935:439): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-aarch64" pid=6355 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.144650] audit: type=1400 audit(1474320983.947:440): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-aarch64" pid=6356 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.154331] audit: type=1400 audit(1474320983.955:441): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-cris" pid=6357 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.164035] audit: type=1400 audit(1474320983.963:442): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-cris" pid=6358 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.174000] audit: type=1400 audit(1474320983.975:443): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-i386" pid=6359 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
Sep 19 23:36:23 XPS-15-9550 kernel: [ 1199.182669] audit: type=1400 audit(1474320983.983:444): apparmor="DENIED" operation="exec" profile="/usr/sbin/libvirtd" name="/usr/local/bin/qemu-system-i386" pid=6360 comm="libvirtd" requested_mask="x" denied_mask="x" fsuid=0 ouid=0
```

:confused: its a question of libvirtd profile under apparmor ? :o

---

### Post by KillerKelvUK on 2016-09-19
Yes, this looks like apparmor is denying the qemu binaries for qemu-img and others.  At a guess I'd say this is because you've installed your built qemu binaries into a non-standard (for ubuntu at least) location.  Looking at the log entries you've shared for apparmor it looks like your binaries are now stored in /usr/local/bin/ whereas the stock qemu binaries are normally stored in /usr/bin, as such the exist apparmor profiles are stopping the processes.  You could test this by disabling apparmor 'sudo update-rc.d apparmor disable' and then reboot the host.

If I am correct this is because the ./configure parameters you used when building are different to the stock Ubuntu builds.

---

### Post by yakatape on 2016-09-19
With apparmor turned off, the error is now different :

From virt-manager :
```
Impossible de terminer l'installation&#8239;: «&#8239;internal error: process exited while connecting to monitor: qemu-system-x86_64: -spice port=5900,addr=127.0.0.1,disable-ticketing,image-compression=off,seamless-migration=on: There is no option group 'spice'
qemu-system-x86_64: -spice port=5900,addr=127.0.0.1,disable-ticketing,image-compression=off,seamless-migration=on: spice support is disabled »
```

From syslog :
```
Sep 20 00:02:30 XPS-15-9550 systemd[1]: Started Virtual machine log manager.
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.0174] manager: (vnet0): new Tun device (/org/freedesktop/NetworkManager/Devices/12)
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.0230] devices added (path: /sys/devices/virtual/net/vnet0, iface: vnet0)
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.0230] device added (path: /sys/devices/virtual/net/vnet0, iface: vnet0): no ifupdown configuration found.
Sep 20 00:02:30 XPS-15-9550 kernel: [   90.892840] device vnet0 entered promiscuous mode
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.0985] device (vnet0): state change: unmanaged -> unavailable (reason 'connection-assumed') [10 20 41]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1004] keyfile: add connection in-memory (5d4c18da-57a7-4ed5-a804-e4b13fef4baf,"vnet0")
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1015] device (vnet0): state change: unavailable -> disconnected (reason 'connection-assumed') [20 30 41]
Sep 20 00:02:30 XPS-15-9550 kernel: [   90.917029] virbr0: port 1(vnet0) entered listening state
Sep 20 00:02:30 XPS-15-9550 kernel: [   90.917056] virbr0: port 1(vnet0) entered listening state
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1030] device (vnet0): Activation: starting connection 'vnet0' (5d4c18da-57a7-4ed5-a804-e4b13fef4baf)
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1043] device (vnet0): state change: disconnected -> prepare (reason 'none') [30 40 0]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1054] device (vnet0): state change: prepare -> config (reason 'none') [40 50 0]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1061] device (vnet0): state change: config -> ip-config (reason 'none') [50 70 0]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1063] device (virbr0): bridge port vnet0 was attached
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1063] device (vnet0): Activation: connection 'vnet0' enslaved, continuing activation
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1071] device (vnet0): state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1076] device (vnet0): state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.1144] device (vnet0): Activation: successful, device activated.
Sep 20 00:02:30 XPS-15-9550 dbus[841]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Sep 20 00:02:30 XPS-15-9550 systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 20 00:02:30 XPS-15-9550 libvirtd[1012]: Domain id=1 name='win2k12r2-2' uuid=5146ac9a-0187-48ab-a2d2-a8ae25b5a063 is tainted: high-privileges
Sep 20 00:02:30 XPS-15-9550 dbus[841]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Sep 20 00:02:30 XPS-15-9550 systemd[1]: Started Network Manager Script Dispatcher Service.
Sep 20 00:02:30 XPS-15-9550 nm-dispatcher: req:1 'up' [vnet0]: new request (1 scripts)
Sep 20 00:02:30 XPS-15-9550 nm-dispatcher: req:1 'up' [vnet0]: start running ordered scripts...
Sep 20 00:02:30 XPS-15-9550 kernel: [   90.986305] virbr0: port 1(vnet0) entered disabled state
Sep 20 00:02:30 XPS-15-9550 kernel: [   90.987739] device vnet0 left promiscuous mode
Sep 20 00:02:30 XPS-15-9550 kernel: [   90.987740] virbr0: port 1(vnet0) entered disabled state
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.2070] device (vnet0): state change: activated -> unmanaged (reason 'unmanaged') [100 10 3]
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.2071] device (virbr0): bridge port vnet0 was detached
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.2071] device (vnet0): released from master device virbr0
Sep 20 00:02:30 XPS-15-9550 NetworkManager[869]: <info>  [1474322550.2137] devices removed (path: /sys/devices/virtual/net/vnet0, iface: vnet0)
Sep 20 00:02:30 XPS-15-9550 nm-dispatcher: req:2 'down' [vnet0]: new request (1 scripts)
Sep 20 00:02:30 XPS-15-9550 systemd[1]: Reloading OpenBSD Secure Shell server.
Sep 20 00:02:30 XPS-15-9550 systemd[1]: Reloaded OpenBSD Secure Shell server.
Sep 20 00:02:30 XPS-15-9550 nm-dispatcher: req:2 'down' [vnet0]: start running ordered scripts...
Sep 20 00:02:30 XPS-15-9550 libvirtd[1012]: failed to connect to monitor socket: Aucun processus de ce type
Sep 20 00:02:30 XPS-15-9550 virtlogd[3403]: libvirt version: 1.3.1, package: 1ubuntu10.1 (dann frazier <dannf@ubuntu.com> Fri, 03 Jun 2016 14:41:21 -0600)
Sep 20 00:02:30 XPS-15-9550 virtlogd[3403]: hostname: XPS-15-9550
Sep 20 00:02:30 XPS-15-9550 virtlogd[3403]: End of file while reading data: Erreur d'entrée/sortie
Sep 20 00:02:30 XPS-15-9550 virtlogd[3403]: End of file while reading data: Erreur d'entrée/sortie
Sep 20 00:03:12 XPS-15-9550 systemd[1]: Stopping User Manager for UID 108...
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Reached target Shutdown.
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Stopped target Default.
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Starting Exit the Session...
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Stopped target Basic System.
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Stopped target Timers.
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Stopped target Sockets.
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Stopped target Paths.
Sep 20 00:03:12 XPS-15-9550 systemd[2152]: Received SIGRTMIN+24 from PID 3961 (kill).
Sep 20 00:03:12 XPS-15-9550 systemd[1]: Stopped User Manager for UID 108.
Sep 20 00:03:12 XPS-15-9550 systemd[1]: Removed slice User Slice of lightdm.



```

---

### Post by KillerKelvUK on 2016-09-19
Well the error message is pretty clear "There is no option group 'spice'"...you could maybe work around this by changing the Display from Spice to VNC however this is a hack, you'd need to debug why you have this error i.e. did the ./configure output in the build process confirm SPICE support.

---

### Post by yakatape on 2016-09-19
Yeah exactly i've work on it but when i try : ./configure --enable-spice i got ouput something like 'you need first install spice client and control."
I've compiled the control spice and installed but for the spice client i need first celt051 and celt libs where i need to find the source and compile it again and retry the compilation of spice client.

I think make a rollback to 2.5.0, and work on it through a VM for the version 2.7.0:)

Thanks again

---

### Post by KillerKelvUK on 2016-09-20
So the below are the packages I believe are required on your host to build a feature rich qemu installation, you'll find the spice packages listed.  If you want all the latest features of qemu 2.7.0 then you need to build and install the virglrenderer package first and then qemu however if you aren't interested in '-vga virtio' then you can skip this part.  You could also skip building the later version of libvirt but be aware that if you then try and use a newer feature of qemu that your older version of libvirt isn't aware off then you'll need to use qemu:commandline arg's in your libvirt xml.

```

general:


    build-essential
    git


virglrenderer : (needed for -vga virtio, https://virgil3d.github.io/)


    dh-autoreconf
    libgbm-dev


qemu v2.6.1 & 2.7.0 :


    python2.7-dev 
    pkg-config
    zlib1g-dev 
    libglib2.0-dev 
    libpixman-1-dev 
    libfdt-dev 
    libsdl1.2-dev 
    libglib2.0-dev 
    libfdt-dev 
    libpixman-1-dev 
    zlib1g-dev 
    libaio-dev 
    libbluetooth-dev 
    libbrlapi-dev 
    libbz2-dev  
    libcap-dev 
    libcap-ng-dev 
    libcurl4-gnutls-dev 
    libgtk-3-dev 
    libibverbs-dev 
    libjpeg8-dev 
    libncurses5-dev 
    libnuma-dev 
    librbd-dev 
    librdmacm-dev 
    libsasl2-dev 
    libsdl1.2-dev 
    libseccomp-dev 
    libsnappy-dev 
    libssh2-1-dev 
    libvde-dev 
    libvdeplug-dev 
    libxen-dev 
    liblzo2-dev 
    valgrind 
    xfslibs-dev
    libspice-server-dev 
    libusb-1.0-0-dev 
    libusbredirparser-dev 
    libusbredirhost-dev 
    libnfs-dev 
    texinfo
    libiscsi-dev 


libvirt v1.3.5 :


    libxml-xpath-perl
    libxml2-utils
    xsltproc
    libpciaccess-dev
    libyajl-dev
    libxml2-dev
    libdevmapper-dev
    libnl-3-dev
    libnl-route-3-dev

```

---

