---
title: "Installing VirtualBox Headless on Ubuntu 14.04?"
date: 2014-08-31
forum: Server Platforms
---

### Post by victorhooi on 2014-08-31
Hi,

Is there a recommended way of installing VirtualBox headless on Ubuntu 14.04?

If I try to install it from the official Ubuntu repositories, it seems to pull in all these X packages - however, I only want to run the headless version of VirtualBox. I can't seem to a headless specific package:

```
sudo aptitude install virtualbox
The following NEW packages will be installed:
  dkms{a} fontconfig{a} libasound2{a} libasound2-data{a} libasyncns0{a} libaudio2{a} libcaca0{a} libdrm-intel1{a} libdrm-nouveau2{a} libdrm-radeon1{a} libflac8{a}
  libgl1-mesa-dri{a} libgl1-mesa-glx{a} libglapi-mesa{a} libgsoap4{a} libice6{a} libjbig0{a} libllvm3.4{a} libmysqlclient18{a} libogg0{a} libpciaccess0{a} libpulse0{a}
  libqt4-declarative{a} libqt4-network{a} libqt4-opengl{a} libqt4-script{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtdbus4{a}
  libqtgui4{a} libsdl1.2debian{a} libsm6{a} libsndfile1{a} libtiff5{a} libtxc-dxtn-s2tc0{a} libvncserver0{a} libvorbis0a{a} libvorbisenc2{a} libvpx1{a} libx11-xcb1{a}
  libxcb-dri2-0{a} libxcb-dri3-0{a} libxcb-glx0{a} libxcb-present0{a} libxcb-sync1{a} libxcursor1{a} libxdamage1{a} libxfixes3{a} libxi6{a} libxinerama1{a} libxmu6{a}
  libxrender1{a} libxshmfence1{a} libxt6{a} libxxf86vm1{a} mysql-common{a} qtcore4-l10n{a} virtualbox virtualbox-dkms{a} virtualbox-qt{a} x11-common{a}
0 packages upgraded, 64 newly installed, 0 to remove and 0 not to upgrade.
Need to get 47.1 MB of archives. After unpacking 205 MB will be used.
```

I also tried adding the Oracle repos ([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)), and installing VirtualBox 4.3 from there - I get:

```
sudo aptitude install virtualbox-4.3
The following NEW packages will be installed:
  acl{a} at-spi2-core{a} colord{a} dconf-gsettings-backend{a} dconf-service{a} dkms{a} fontconfig{a} hicolor-icon-theme{a} libasound2{a} libasound2-data{a} libasyncns0{a}
  libatk-bridge2.0-0{a} libatk1.0-0{a} libatk1.0-data{a} libatspi2.0-0{a} libaudio2{a} libcaca0{a} libcairo-gobject2{a} libcairo2{a} libcolord1{a} libcolorhug1{a} libdatrie1{a}
  libdconf1{a} libdrm-intel1{a} libdrm-nouveau2{a} libdrm-radeon1{a} libexif12{a} libfile-basedir-perl{a} libfile-desktopentry-perl{a} libfile-mimeinfo-perl{a} libflac8{a}
  libfontenc1{a} libgd3{a} libgdk-pixbuf2.0-0{a} libgdk-pixbuf2.0-common{a} libgirara-gtk3-1{a} libgl1-mesa-dri{a} libgl1-mesa-glx{a} libglapi-mesa{a} libgphoto2-6{a}
  libgphoto2-l10n{a} libgphoto2-port10{a} libgraphite2-3{a} libgtk-3-0{a} libgtk-3-bin{a} libgtk-3-common{a} libgudev-1.0-0{a} libgusb2{a} libharfbuzz0b{a} libice6{a}
  libieee1284-3{a} libjasper1{a} libjbig0{a} libllvm3.4{a} libltdl7{a} libmysqlclient18{a} libogg0{a} libpango-1.0-0{a} libpangocairo-1.0-0{a} libpangoft2-1.0-0{a}
  libpciaccess0{a} libpixman-1-0{a} libpoppler-glib8{a} libpoppler44{a} libpulse0{a} libqt4-declarative{a} libqt4-network{a} libqt4-opengl{a} libqt4-script{a} libqt4-sql{a}
  libqt4-sql-mysql{a} libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtdbus4{a} libqtgui4{a} libsane{a} libsane-common{a} libsdl-ttf2.0-0{a} libsdl1.2debian{a} libsm6{a}
  libsndfile1{a} libthai-data{a} libthai0{a} libtiff5{a} libtxc-dxtn-s2tc0{a} libv4l-0{a} libv4lconvert0{a} libvorbis0a{a} libvorbisenc2{a} libvpx1{a} libwayland-client0{a}
  libwayland-cursor0{a} libx11-xcb1{a} libxaw7{a} libxcb-dri2-0{a} libxcb-dri3-0{a} libxcb-glx0{a} libxcb-present0{a} libxcb-render0{a} libxcb-shape0{a} libxcb-shm0{a}
  libxcb-sync1{a} libxcomposite1{a} libxcursor1{a} libxdamage1{a} libxfixes3{a} libxft2{a} libxi6{a} libxinerama1{a} libxkbcommon0{a} libxmu6{a} libxpm4{a} libxrandr2{a}
  libxrender1{a} libxshmfence1{a} libxt6{a} libxtst6{a} libxv1{a} libxxf86dga1{a} libxxf86vm1{a} mysql-common{a} qtcore4-l10n{a} shared-mime-info{a} virtualbox-4.3
  x11-common{a} x11-utils{a} x11-xserver-utils{a} xdg-utils{a} zathura{a}
0 packages upgraded, 130 newly installed, 0 to remove and 0 not to upgrade.
Need to get 107 MB of archives. After unpacking 323 MB will be used.
```

Is there a better way of doing this?

Essentially, I'm trying to run a Windows Server image in headless mode on the Ubuntu box, which I can just manage remotely via VRDP/RDP.

Thanks,
Victor

---

### Post by TheFu on 2014-08-31
> **victorhooi said:**
> 
Is there a better way of doing this?

Essentially, I'm trying to run a Windows Server image in headless mode on the Ubuntu box, which I can just manage remotely via VRDP/RDP.

Oracle has been lazy about requiring X/Windows libraries for decades. It isn't just virtualbox - some of their webserver products require it too. I know - crazy.  Those other products will not start without X/Windows on the system either!  Crazy!

Not the answer you want, but ... 

Is there a better way to do this?  Yes, there is. Don't use virtualbox for server needs.  KVM, proxmox, heck, even ESXi are better choices - IMHO.  VirtualBox is meant as a developer tool and for running desktops-on-desktops, not for servers.  Others will disagree, but I had to say it.

---

### Post by DigiAngel on 2014-08-31
Yea there's no easy way around all the libs that are needed.  But as an added buno you can use X-forwarding to run the GUI app to configure machines....which is a lot easier then command line.

---

### Post by volkswagner on 2014-08-31
I'm not sure how it will work (since I have not tried it), but you can try without-recommends.

Here is output of both commands on my 14.04.1 server:

```
printadmin@printsrv:~$ sudo aptitude install virtualbox
The following NEW packages will be installed:
  binutils{a} cpp{a} cpp-4.8{a} dkms{a} fakeroot{a} fontconfig{a} fontconfig-config{a} fonts-dejavu-core{a} gcc{a} gcc-4.8{a} libasan0{a} libasound2{a} libasound2-data{a} libasyncns0{a} libatomic1{a} 
  libaudio2{a} libc-dev-bin{a} libc6-dev{a} libcaca0{a} libcloog-isl4{a} libcurl3{a} libdrm-nouveau2{a} libfakeroot{a} libflac8{a} libfontconfig1{a} libgcc-4.8-dev{a} libgl1-mesa-dri{a} 
  libgl1-mesa-glx{a} libglapi-mesa{a} libgomp1{a} libgsoap4{a} libice6{a} libisl10{a} libitm1{a} libjbig0{a} libjpeg-turbo8{a} libjpeg8{a} libllvm3.4{a} libmpc3{a} libmpfr4{a} libmysqlclient18{a} 
  libogg0{a} libpulse0{a} libqt4-declarative{a} libqt4-network{a} libqt4-opengl{a} libqt4-script{a} libqt4-sql{a} libqt4-sql-mysql{a} libqt4-xml{a} libqt4-xmlpatterns{a} libqtcore4{a} libqtdbus4{a} 
  libqtgui4{a} libquadmath0{a} libsdl1.2debian{a} libsm6{a} libsndfile1{a} libtiff5{a} libtsan0{a} libtxc-dxtn-s2tc0{a} libvncserver0{a} libvorbis0a{a} libvorbisenc2{a} libvpx1{a} libx11-xcb1{a} 
  libxcb-dri2-0{a} libxcb-dri3-0{a} libxcb-glx0{a} libxcb-present0{a} libxcb-sync1{a} libxcursor1{a} libxdamage1{a} libxfixes3{a} libxi6{a} libxinerama1{a} libxmu6{a} libxrender1{a} libxshmfence1{a} 
  libxt6{a} libxxf86vm1{a} linux-libc-dev{a} make{a} manpages-dev{a} mysql-common{a} patch{a} qtcore4-l10n{a} virtualbox virtualbox-dkms{a} virtualbox-qt{a} x11-common{a} 
The following packages will be upgraded:
  libc6 
1 packages upgraded, 91 newly installed, 0 to remove and 26 not upgraded.
Need to get 72.3 MB of archives. After unpacking 280 MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
printadmin@printsrv:~$ sudo aptitude install virtualbox --without-recommends
The following NEW packages will be installed:
  libasound2{a} libasound2-data{a} libasyncns0{a} libcaca0{a} libcurl3{a} libflac8{a} libgsoap4{a} libice6{a} libjpeg-turbo8{a} libjpeg8{a} libogg0{a} libpulse0{a} libsdl1.2debian{a} libsm6{a} 
  libsndfile1{a} libvncserver0{a} libvorbis0a{a} libvorbisenc2{a} libvpx1{a} libxcursor1{a} libxfixes3{a} libxmu6{a} libxrender1{a} libxt6{a} virtualbox x11-common{a} 
The following packages are RECOMMENDED but will NOT be installed:
  libgl1-mesa-glx libqt4-opengl libqtcore4 libqtgui4 virtualbox-dkms virtualbox-qt virtualbox-source 
0 packages upgraded, 26 newly installed, 0 to remove and 27 not upgraded.
Need to get 18.8 MB of archives. After unpacking 72.7 MB will be used.
```

I agree with others, KVM would be a better choice.

---

### Post by nerdtron on 2014-08-31
+1 to KVM, why use GUI on a server when you can control VM remotely using a GUI.

This one is really easy:
Server without GUI: ubuntu-virt-server (this one will do the virtualization without a GUI)
On your Ubuntu desktop: virt-manager (this one will control the VM on the server using a nice GUI)

Tutorial:
[http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

---

### Post by victorhooi on 2014-08-31
Hi,

Hmm, ok, so the consensus seems to be to just use KVM instead =).

And apparently this can run an un-modified Windows guest, so I should be good there. However, I will need to make sure my VT flags are enabled, correct? Otherwise it falls back to QEMU? (Not sure if that's still true).

From what I can tell, VT should be enabled:

```

$ cat /proc/cpuinfo | grep vmx
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca lahf_lm dtherm tpr_shadow
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm dca lahf_lm dtherm tpr_shadow

```

This is a Intel Xeon 5140. The exact server model is:

```

sudo dmidecode | grep -A3 '^System Information'
System Information
	Manufacturer: HP
	Product Name: ProLiant DL360 G5
	Version: Not Specified

```

However, I have only 2 Gb of RAM on this box. The Linux portion is just running a Samba server, serving around 2-3 Windows clients, as well as a Unifi Video controller (basically NVR software) - this is a Java webapp, backed by MongoDB. Not sure how KVM is going to perform on this box with this sort of constrained RAM...

Can anybody comment on the relative performance of KVM with Windows, versus VirtualBox with Windows? And are there any caveats I should be aware of, trying to virtualise Windows Server 2012 R2 under Ubuntu 14.04 on this kind of hardware?

Regards,
Victor

---

### Post by nerdtron on 2014-08-31
I think you can still virtualise Windows Server 2012 on your 2GB host machine. If the host machine is not too busy you can allocate upto 1GB ram on the VM. After installation of windows vm, you need to install drivers for the virtualized network interface.

---

### Post by victorhooi on 2014-08-31
Hi,

Aha, ok, thanks, I will give it a shot - I'll leave 1Gb for the Linux host, and 1Gb for the Windows 2012 R2 guest VM.

I've installed the ubuntu-virt-server meta package. I have the ISO for Windows Server 2012 on the disk.

What would be the next steps for creating a new KVM virtual machine, and installing Windows Server 2012? I know there's a Ubuntu GUI KVM manager, but my client OS in this case is OSX. Is there any way I can manage KVM and the Windows installation from an OSX box? Or do I need a Ubuntu desktop box to manage it?

Networking wise, I was hoping to do the equivalent of bridged networking in VMWare, where the Windows guest would just pull another IP address from the DHCP server. You're saying I also need to install custom NIC drivers in Windows for the KVM network interface, as it doesn't work out of the box?

Regards,
Victor

---

### Post by TheFu on 2014-08-31
KVM is lighter on resources than virtualbox.

KVM uses whatever Linux networking you configure. Normally, configuring a simple Linux bridge is how to handle this.  Many how-tos for that - I've posted examples in these forums a few times. Think I posted one today.  It is a 1-time setup and forget it.  Because of the flexibility in Linux networking, it doesn't make sense for KVM to setup bridges - that wouldn't be nearly as useful for many configurations.

While virt-manager is the easy, remote GUI to handle this stuff, you can use any libvirt-based client you prefer. These are the ubuntu forums, so of course, we know about the ubuntu solution. I can't help with OSX - not my bag, baby.  You can use virsh from a terminal, if you like. However, it isn't point-n-click like virt-manager.  You know, Apple makes hardware that runs Linux really well. I'm certain we can help you wipe that OSX stuff and get Ubuntu on your great hardware, if you like. :)

---

### Post by nerdtron on 2014-08-31
> What would be the next steps for creating a new KVM virtual machine, and  installing Windows Server 2012? I know there's a Ubuntu GUI KVM  manager, but my client OS in this case is OSX. Is there any way I can  manage KVM and the Windows installation from an OSX box? Or do I need a  Ubuntu desktop box to manage it?

Manage the VMs via command line or via GUI. But the GUI virt-manager can only be installed on Ubuntu machine. If you have OSX, you can create a VM on there with Ubuntu using virtual box, then install the virt-manager on Ubuntu. Don't worry on this, you can use mutiple Ubuntu installations (with virt-manager installed) to control the KVM on the server.

> Networking wise, I was hoping to do the equivalent of bridged networking  in VMWare, where the Windows guest would just pull another IP address  from the DHCP server. You're saying I also need to install custom NIC  drivers in Windows for the KVM network interface, as it doesn't work out  of the box?

It does support bridged mode. But unlike in virtual box where a bridged interface is already created on the HOST server, you need to manually create a bridge interface. The default is NAT, so if you want to have a bridge interface, I can post you a sample config.
For Ubuntu VMs, bridge inerfaces are no problem, however, last time I tried Windows XP, it had a problem on detecting bridged interface. There is a driver, I can provide a link too. NAT interface on the other hand, I think it works on Windows VM.

---

### Post by victorhooi on 2014-09-01
Hi,

Ok, I have created a raw file image, and I'm going to install it using virt-install, based on the steps here:

[http://docs.openstack.org/image-guide/content/virt-install.html](http://docs.openstack.org/image-guide/content/virt-install.html)

I tried:

```
$ virt-install --virt-type kvm --name windows2012 --ram 1024 --cdrom=/home/victorhooi/en-gb_windows_8.1_enterprise_n_with_update_x64_dvd_4048595.iso --disk path=/var/lib/libvirt/images/windows_2012_server.img --network network=default --graphics vnc,listen=0.0.0.0 --noautoconsole --os-type=windows --os-variant=win2k8
ERROR    No domains available for virt type 'hvm', arch 'x86_64', domain type 'kvm'

```

This ServerFault post ([http://serverfault.com/questions/559502/libvirt-error-no-domains-available-for-virt-type-hvm-arch-x86-64-domain-t](http://serverfault.com/questions/559502/libvirt-error-no-domains-available-for-virt-type-hvm-arch-x86-64-domain-t)) suggested adding --connect qemu:///system, still the same error though:

```
virt-install --virt-type kvm --connect qemu:///system --name windows2012 --ram 1024 --cdrom=/home/victorhooi/en-gb_windows_8.1_enterprise_n_with_update_x64_dvd_4048595.iso --disk path=/var/lib/libvirt/images/windows_2012_server.img --network network=default --graphics vnc,listen=0.0.0.0 --noautoconsole --os-type=windows --os-variant=win2k8
ERROR    No domains available for virt type 'hvm', arch 'x86_64', domain type 'kvm'

```

If I remove the --virt-type kvm though:
```

$ virt-install --connect qemu:///system --name windows2012 --ram 1024 --cdrom=/home/victorhooi/en-gb_windows_8.1_enterprise_n_with_update_x64_dvd_4048595.iso --disk path=/var/lib/libvirt/images/windows_2012_server.img --network network=default --graphics vnc,listen=0.0.0.0 --noautoconsole --os-type=windows --os-variant=win2k8
WARNING  KVM acceleration not available, using 'qemu'

Starting install...
Creating domain...                                                                                                                                                                                                                                                                                                                                   |    0 B     00:01
Domain installation still in progress. Waiting for installation to complete.
^CDomain install interrupted.
Installation aborted at user request

```

I check kvm-ok:
```

$ sudo /usr/sbin/kvm-ok
[sudo] password for victorhooi:
INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: Your CPU supports KVM extensions
INFO: KVM (vmx) is disabled by your BIOS
HINT: Enter your BIOS setup and enable Virtualization Technology (VT),
      and then hard poweroff/poweron your system
KVM acceleration can NOT be used

```

Also, I tried this suggestion to double-check:
```

victorhooi@ensign-primary:~$ sudo modprobe msr
victorhooi@ensign-primary:~$ sudo rdmsr 0x3a
1

```

So it seems that the VT extensions aren't enabled, even though I thought they were based on /proc/cpu-info. Hmm, guess I will need to remedy that later today, when we can reboot the server.

Does my virt-install command line otherwise look sane?

I suppose there's little point in proceeding ahead with the QEMU fallback for now, since I  assume it will be excruciatingly slow.

With the networking - I'm using the default, which I believe is NAT - what are the disadvantages of using NAT versus Bridging? Ideally, I'd like users to be able to RDP into the Windows Server, and I'm guessing that will be difficult with a NAT setup?

If it's not too much to ask, @nerdtron, would you be able to provide the appropriate setup steps for Ubuntu 14.04, and a bridging setup?

Also, will I need to install network drivers in the Windows guest before being able to use the network? I'm guessing it's one of the drivers from here?

[http://www.linux-kvm.org/page/WindowsGuestDrivers](http://www.linux-kvm.org/page/WindowsGuestDrivers)

How should you get the drivers onto the box then, if you don't have network access yet?

Regards,
Victor

---

### Post by victorhooi on 2014-09-01
Hi,

Ok, I managed to get the iLO access going =), and I've enabled VT.

I'm now looking at setting up the bridged interface. Based on the following:

[http://www.linux-kvm.org/page/Networking](http://www.linux-kvm.org/page/Networking)
[https://wiki.debian.org/BridgeNetworkConnections](https://wiki.debian.org/BridgeNetworkConnections)
[https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking)

I have something like this now in /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

Does that look reasonably sane? I'm not quite sure why eth0 is set to manual - does that mean I need to manually bring it up on each boot?

Still not sure about how to get the Windows NIC drivers onto the box.

Regards,
Victor

---

### Post by TheFu on 2014-09-01
The host br0 needs normal network stanza and really, really needs to be on a static IP, not DHCP.  Also missing the nameserver/DNS settings which are usually important.
The eth0 stanza is correct as you have it.

There is nothing special about loading network drivers for Windows - just tell the VM to provide an Intel PRO/1000 virtual network card - oh - WinXP doesn't have those drivers built-in - so you'll need to get them from Intel or choose a lower-end card to virtually provide.  Might be worth the trouble to use the Windows virtio drivers.  Get them from the KVM website (which is a link to the redhat drivers).

---

### Post by victorhooi on 2014-09-01
Hi,

Aha, what do you mean by normal network stanza please?

What does the "manual" for eth0 do in this case? From reading [https://wiki.debian.org/NetworkConfiguration](https://wiki.debian.org/NetworkConfiguration), I'm gathering that it does need to brought up manually - is that right?

Also, is there a specific reason it needs to be a static IP? I've actually got it as a static DHCP mapping on my router - is that similar enough? The DNS settings should also be pushed out as part of the DHCP config as well.

The OS in this case is Windows Server 2012 R2 - I'm fairly sure that has a driver for an Intel Pro/1000 NIC. So in that case, I don't need to do anything special to have the network work out of the box?

Regards,
Victor

---

### Post by TheFu on 2014-09-01
> **victorhooi said:**
> 
The OS in this case is Windows Server 2012 R2 - I'm fairly sure that has a driver for an Intel Pro/1000 NIC. So in that case, I don't need to do anything special to have the network work out of the box?

Yes, that is correct. You will be fine - provided you tell the VM environment to provide an Intel PRO/1000 virtualNIC. Nothing to it inside the VM.

No - you do not need to do anything to bring up eth0 - the bridge handles that.
Static DHCP reservations are a workable solution - should be fine with that for your bridge.  I didn't assume that - most posters here don't do it. I think you are ready to install now - host network bridge is ready.

You can check that with **ifconfig** on the host and **route**.

I use DHCP reservations only for portable devices. Never felt "right" to do that with a server. Call it a *personal bias*. No good reason for why I do it that way, just less-than-great reasons, I suppose.

---

### Post by volkswagner on 2014-09-01
You can use virt-manager from OSX if you setup X forwarding.

I have this working with Mavericks after installing XQuartz (X11 component). This does require
installing virt-manager on the server which will pull some X11 components.


From my notes on the server:

```

aptitude install virt-manager --without-recommends
adduser foo libvirt
adduser foo libvirt-qemu


```

I don't have notes on exact steps for enabling X forwarding on OSX Mavericks, Google should help here.
Basically you'll need the mentioned Xquartz, and on server allow SSH X forward sessions in /etc/ssh/sshd_config

```
X11Forwarding yes
```

Once all is working, you can ssh into the server and launch virt-manager

---

### Post by victorhooi on 2014-09-01
Hi,

Ok, so we've rebooted, bridge interfaces seems to be up correctly:
```
$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq master br0 state UP group default qlen 1000
    link/ether 00:1b:78:02:9b:ec brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:1b:78:02:9b:e6 brd ff:ff:ff:ff:ff:ff
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
    link/ether 00:1b:78:02:9b:ec brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.120/24 brd 192.168.2.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fe80::21b:78ff:fe02:9bec/64 scope link
       valid_lft forever preferred_lft forever
5: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default
    link/ether 16:42:1f:0c:27:46 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
6: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UNKNOWN group default qlen 500
    link/ether fe:54:00:e2:51:10 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fc54:ff:fee2:5110/64 scope link
       valid_lft forever preferred_lft forever
victorhooi@ensign-primary:~$

```

I had to do a virsh undefine to remove the previous attempt to create the VM (before VT was enabled):
```
$ virsh undefine windows2012
Domain windows2012 has been undefined
```

I now try to run virt-install again:

```
$ virt-install --virt-type kvm --name windows2012 --ram 1024 --cdrom=/home/victorhooi/en-gb_windows_8.1_enterprise_n_with_update_x64_dvd_4048595.iso --disk path=/var/lib/libvirt/images/windows_2012_server.img --network bridge=br0 --graphics vnc,listen=0.0.0.0 --noautoconsole --os-type=windows --os-variant=win2k8

Starting install...
Creating domain...                                                                                                                                                                                                                                                                                                                                   |    0 B     00:00
Domain installation still in progress. Waiting for installation to complete.
```

It appears to stall there. virsh list does list the domain as running, but the install itself doesn't seem to proceed. According to top, I do have a qemu-system-x86 process running, and it is using around 52.4% of memory, which is to be expected.

Any ideas on how to prod the installer along?

Also, after I get the install going, what IP address should I connect to with my VNC client? br0 has an address, and I believe this is my host - however, eth0 and eth1 do not have an address (see ip addr output above).

Regards,
Victor

---

### Post by volkswagner on 2014-09-02
> **victorhooi said:**
> 

Also, after I get the install going, what IP address should I connect to with my VNC client? br0 has an address, and I believe this is my host - however, eth0 and eth1 do not have an address (see ip addr output above).

Regards,
Victor

It's normal for eth0 not to have an address, since it's part of the bridge.  I assume you have nothing attached to eth1.

Your virtual machines will have an address in the 192.168.122.1/24 range.

On my Debain 7 machine, I can find a list of addresses in /var/lib/libvirt/dnsmasq/default.leases.

You can also use the arp command on the server:
```
arp -an
```

---

### Post by TheFu on 2014-09-02
So - inside virt-manager, the VNC port can be set or can be automatic.  I haven't a clue how to do it from the CLI - but suspect it ends up inside the VM-settings.xml file in /etc/libvirt/qemu/ - these are the "defined" VMs that libvirt is managing. Do not edit these files directly.  There is an editor built into virsh ... or virt-manager will handle it similar to the way that VMware Player/workstation/vsphere or virtualbox GUIs do.

The IP for VNC is the hostOS. It is just the port that changes per VM. Of course, this assumes that VNC is enabled for the guest THROUGH the KVM startup parameters.  Generally, if I want a remote desktop, I use x2go and install the server INSIDE the VM. Then it works just like any other x2go server on any platform.  Plus VNC doesn't have any real security.  virt-manager will use an ssh tunnel to access VNC guestOSes.  Don't know if running it through a CLI connection will. Sorry.  They are both libvirt, so there is hope.

---

### Post by nerdtron on 2014-09-02
If the VM is a Linux machine it would be easy to just connect using the command line from the host machine:
virsh list - to list the vms running
virsh console [name] - to connect to this vm's console

It's a windows vm after all. I'd rather go the the GUI virt-manager though. Saves a ton of headache and no command line kung fu.

---

