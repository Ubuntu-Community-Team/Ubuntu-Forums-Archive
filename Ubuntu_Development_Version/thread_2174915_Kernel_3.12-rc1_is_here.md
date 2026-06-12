---
title: "Kernel 3.12-rc1 is here"
date: 2013-09-16
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-09-16
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc1-saucy/)

Nvidia module (304.108 legacy driver) fails to build.

```
... 
# define likely(x) __builtin_expect(!!(x), 1)
                                        ^
  if [ "-pg" = "-pg" ]; then if [ /var/lib/dkms/nvidia-304/304.108/build/os-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-3.12.0-031200rc1-generic/scripts/recordmcount  "/var/lib/dkms/nvidia-304/304.108/build/os-usermap.o"; fi; fi;
  /usr/bin/ld.bfd -m elf_x86_64   -r -o /var/lib/dkms/nvidia-304/304.108/build/nvidia.o /var/lib/dkms/nvidia-304/304.108/build/nv-kernel.o /var/lib/dkms/nvidia-304/304.108/build/nv.o /var/lib/dkms/nvidia-304/304.108/build/nv-acpi.o /var/lib/dkms/nvidia-304/304.108/build/nv-chrdev.o /var/lib/dkms/nvidia-304/304.108/build/nv-cray.o /var/lib/dkms/nvidia-304/304.108/build/nv-gvi.o /var/lib/dkms/nvidia-304/304.108/build/nv-i2c.o /var/lib/dkms/nvidia-304/304.108/build/nv-mempool.o /var/lib/dkms/nvidia-304/304.108/build/nv-mlock.o /var/lib/dkms/nvidia-304/304.108/build/nv-mmap.o /var/lib/dkms/nvidia-304/304.108/build/nv-p2p.o /var/lib/dkms/nvidia-304/304.108/build/nv-pat.o /var/lib/dkms/nvidia-304/304.108/build/nv-procfs.o /var/lib/dkms/nvidia-304/304.108/build/nv-usermap.o /var/lib/dkms/nvidia-304/304.108/build/nv-vm.o /var/lib/dkms/nvidia-304/304.108/build/nv-vtophys.o /var/lib/dkms/nvidia-304/304.108/build/os-agp.o /var/lib/dkms/nvidia-304/304.108/build/os-interface.o /var/lib/dkms/nvidia-304/304.108/build/os-mtrr.o /var/lib/dkms/nvidia-304/304.108/build/os-registry.o /var/lib/dkms/nvidia-304/304.108/build/os-smp.o /var/lib/dkms/nvidia-304/304.108/build/os-usermap.o 
(cat /dev/null;   echo kernel//var/lib/dkms/nvidia-304/304.108/build/nvidia.ko;) > /var/lib/dkms/nvidia-304/304.108/build/modules.order
make -f /usr/src/linux-headers-3.12.0-031200rc1-generic/scripts/Makefile.modpost
  find /var/lib/dkms/nvidia-304/304.108/build/.tmp_versions -name '*.mod' | xargs -r grep -h '\.ko$' | sort -u | sed 's/\.ko$/.o/' | scripts/mod/modpost -m -a -i /usr/src/linux-headers-3.12.0-031200rc1-generic/Module.symvers -I /var/lib/dkms/nvidia-304/304.108/build/Module.symvers  -o /var/lib/dkms/nvidia-304/304.108/build/Module.symvers -S -w -s -T -
WARNING: could not find /var/lib/dkms/nvidia-304/304.108/build/.nv-kernel.o.cmd for /var/lib/dkms/nvidia-304/304.108/build/nv-kernel.o
FATAL: modpost: GPL-incompatible module nvidia.ko uses GPL-only symbol 'acpi_bus_get_device'
make[3]: *** [__modpost] Error 1
make[2]: *** [modules] Error 2
NVIDIA: left KBUILD.
nvidia.ko failed to build!
make[1]: *** [module] Error 1
make: *** [module] Error 2
paul@lubuntu-64:~/3.12$ 
```

---

### Post by VinDSL on 2013-09-16
> **paul_in_london said:**
> [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc1-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12-rc1-saucy/)

Nvidia module (304.108 legacy driver) fails to build.

w00t!

Game on...  :D

Thanks!

---

### Post by fyfe54 on 2013-09-16
Downloaded and running on Inspiron 1545.  So far so good....

---

### Post by paul_in_london on 2013-09-16
Hi Vin,

I think you're using the legacy nvidia driver too so presumably you're in the same boat?

Pretty much par for the course with the early rc's.

Btw, FYI - I happened to notice earlier you mentioned in the 3.11.1 thread having to reinstall the nvidia driver after kernel updates. I haven't been experiencing that problem myself. All of our installs have different quirks I suppose!
I didn't actually bother installing 3.11.1. Just thought I'd wait for a corresponding update through the repos.

Late here. Need to bail out soon.

Cheers,

Paul

---

### Post by VinDSL on 2013-09-16
> **paul_in_london said:**
> I think you're using the legacy nvidia driver too so presumably you're in the same boat?

Late here. Need to bail out soon.Hi Paul, 

Yes, we're in the same boat.  It always takes a few days for someone to patch the nVidia drivers for the latest kernel branch.

I'm winding down, too.  If I get a spurt of energy, before going to bed (106 degrees right now -- too hot to sleep), I'll switch over to Nouveau and give 3.12 a whirl.

---

### Post by paul_in_london on 2013-09-16
Yes. C'est la vie...

Still haven't got my broken pc fixed, but when I eventually do I'll see if I can swap my 8800GT card into this machine and then I can use nvidia-current again.

---

### Post by VinDSL on 2013-09-16
So far, so good...

First, I converted from nVidia => Nouveau

```
vindsl@Zuul:~$ echo && echo "~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~" && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    Dell UltraSharp 1907FP (analog input)" && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

~ VinDSL Unity Debug Script 13.07.08 (vindsl.com) ~
Current Date/Time: Tue Sep 17 02:20:41 UTC 2013
Distro Release: Ubuntu Saucy Salamander (development branch)
**[COLOR="#0000CD"]Kernel Release: Linux 3.11.1-031101-generic[/COLOR]**
Gnome Release: GNOME Shell 3.9.91
Unity Release: unity 7.1.0

[B][COLOR="#0000CD"]OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NV4B[/COLOR][/B]
OpenGL version string:  2.1 Mesa 9.2.0-devel

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 115
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
  Version: 9.2.0~git20130729+9.2.9b8ad643-0ubuntu0sarvatt

Package: xserver-xorg-core
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Package: xserver-common
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Package: xserver-xephyr
  Installed: 2:1.14.2.901+git20130808+server-1.14-branch.bc41226f-0ubuntu0ricotz

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82875P/E7210 Memory Controller Hub
           +-01.0-[01]----00.0  NVIDIA Corporation G73 [GeForce 7600 GT]
           +-06.0  Intel Corporation 82875P/E7210 Processor to I/O Memory Interface
           +-1d.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3
           +-1d.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4
           +-1d.7  Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller
           +-1e.0-[02]----0c.0  Lite-On Communications Inc LNE100TX
           +-1f.0  Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge
           +-1f.2  Intel Corporation 82801EB (ICH5) SATA Controller
           +-1f.3  Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller
           \-1f.5  Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller

Display Properties:
 lcd monitor:    Dell UltraSharp 1907FP (analog input)
  dimensions:    1280x1024 pixels (338x270 millimeters)
  resolution:    96x96 dots per inch

vindsl@Zuul:~$ 

```

Then, installed Linux 3.12-rc1

```
vindsl@Zuul:~/Downloads/Kernels$ sudo dpkg -i *.deb[sudo] password for vindsl:         
Selecting previously unselected package linux-headers-3.12.0-031200rc1.
(Reading database ... 436472 files and directories currently installed.)
Unpacking linux-headers-3.12.0-031200rc1 (from linux-headers-3.12.0-031200rc1_3.12.0-031200rc1.201309161735_all.deb) ...
Selecting previously unselected package linux-headers-3.12.0-031200rc1-generic.
Unpacking linux-headers-3.12.0-031200rc1-generic (from linux-headers-3.12.0-031200rc1-generic_3.12.0-031200rc1.201309161735_i386.deb) ...
Selecting previously unselected package linux-image-3.12.0-031200rc1-generic.
Unpacking linux-image-3.12.0-031200rc1-generic (from linux-image-3.12.0-031200rc1-generic_3.12.0-031200rc1.201309161735_i386.deb) ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
Done.
[B][COLOR="#0000CD"]Setting up linux-headers-3.12.0-031200rc1 (3.12.0-031200rc1.201309161735) ...
Setting up linux-headers-3.12.0-031200rc1-generic (3.12.0-031200rc1.201309161735) ...[/COLOR][/B]
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
**[COLOR="#0000CD"]Setting up linux-image-3.12.0-031200rc1-generic (3.12.0-031200rc1.201309161735) ...[/COLOR]**
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
update-initramfs: Generating /boot/initrd.img-3.12.0-031200rc1-generic
/usr/share/initramfs-tools/hooks/intel_microcode: 136: /usr/share/initramfs-tools/hooks/intel_microcode: prepend_earlyinitramfs: not found
E: intel-microcode: failed to prepend early firmware to initramfs
W: intel-microcode: will try to use late initramfs update mode...
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.12.0-031200rc1-generic...
P: Writing config for /boot/vmlinuz-3.11.1-031101-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.12.0-031200rc1-generic /boot/vmlinuz-3.12.0-031200rc1-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.12.0-031200rc1-generic
Found initrd image: /boot/initrd.img-3.12.0-031200rc1-generic
Found linux image: /boot/vmlinuz-3.11.1-031101-generic
Found initrd image: /boot/initrd.img-3.11.1-031101-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 10.10 (10.10) on /dev/sda1
done
vindsl@Zuul:~/Downloads/Kernels$ 

```

Let's see if it survives a cold boot...  ;)

---

### Post by VinDSL on 2013-09-16
Working fine on Nouveau...  :KS


[INDENT]**[COLOR="#800080"]Ubuntu 13.10 / Gnome-Shell 3.9.91 Staging / Linux 3.12-rc1 Mainline Kernel /  Plank / Conky / ConkyWX [/COLOR]**
[URL="http://vindsl.com/images/vindsl-desktop-16-sep-2013-1.png"]
[IMG]http://vindsl.com/images/vindsl-desktop-16-sep-2013-1(650x520).png[/IMG][/URL][/INDENT]

---

### Post by VinDSL on 2013-09-16
> **fyfe54 said:**
> Downloaded and running on Inspiron 1545.  So far so good....
I might try this on my Latitude D620.  ;)

---

### Post by paul_in_london on 2013-09-19
While we're waiting for the nvidia driver to be patched to work with 3.12-rcN I thought I'd try switching to nouveau because I haven't used it before.

```
sudo aptitude purge nvidia-304 # which removed /etc/modprobe.d/nvidia-304_hybrid.conf and  /etc/modprobe.d/nvidia-graphics-drivers.conf
sudo aptitude reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-nouveau
sudo aptitude install libgl1-mesa-dri-experimental
```

Created a minimal /etc/X11/xorg.conf (saved as /etc/X11/xorg.conf.nouveau) just in case I needed it:

```
Section "Device"
Identifier "n"
Driver "nouveau"
EndSection
```

but my original version was fine:

```
Section "DRI"
Mode 0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
EndSection
Section "ServerFlags"
     Option "blank time" "0"
     Option "standby time" "0"
     Option "suspend time" "0"
     Option "off time" "0"
     Option "dpms" "false"
     Option "IgnoreABI" "True"
EndSection
```

```
paul@lubuntu-64:~$ uname -a
Linux lubuntu-64 3.12.0-031200rc1-generic #201309161735 SMP Mon Sep 16 21:38:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@lubuntu-64:~$
```

```
paul@lubuntu-64:~$ lsmod | grep nouveau
nouveau               984490  2 
mxm_wmi                13021  1 nouveau
wmi                    19363  2 mxm_wmi,nouveau
video                  19574  1 nouveau
ttm                    84699  1 nouveau
drm_kms_helper         53165  1 nouveau
drm                   303157  4 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13564  1 nouveau
paul@lubuntu-64:~$
```


Seems to be working nicely. :)

---

### Post by VinDSL on 2013-09-19
> **paul_in_london said:**
> While we're waiting for the nvidia driver to be patched to work with 3.12-rcN I thought I'd try switching to nouveau because I haven't used it before.[...]

Seems to be working nicely. :)
Good to hear!

The trick, if you will, is to keep the llvmpipe driver from loading.  llvm is hideously slow and choppy on this rig.

That aside, Nouveau works great, albeit a little warmer.  GPU runs +10C on this machine,  Nouveau vs. nVidia.

---

### Post by paul_in_london on 2013-09-19
> **VinDSL said:**
> Good to hear!

The trick, if you will, is to keep the llvmpipe driver from loading.  llvm is hideously slow and choppy on this rig.

That aside, Nouveau works great, albeit a little warmer.  GPU runs +10C on this machine,  Nouveau vs. nVidia.

Hi Vin,

I'm not familiar with llvmpipe. That module doesn't seem to be loaded on my box. Something to do with Unity? Too late for me to look into it right now, but I'm just using a text login to fluxbox. Have various other modules blacklisted. Can't get much leaner without compiling my own kernel. Lol.

Full lsmod output:

```
Module                  Size  Used by
ipt_REJECT             12576  1 
xt_LOG                 17832  5 
xt_limit               12711  7 
xt_tcpudp              12924  21 
xt_addrtype            12713  4 
nf_conntrack_ipv4      15063  7 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
xt_conntrack           12760  7 
ip6_tables             27502  0 
nf_conntrack_netbios_ns    12665  0 
nf_conntrack_broadcast    12589  1 nf_conntrack_netbios_ns
nf_nat_ftp             12796  0 
snd_hda_codec_realtek    56649  1 
snd_hda_intel          57183  3 
nf_nat                 21664  1 nf_nat_ftp
snd_hda_codec         194881  2 snd_hda_codec_realtek,snd_hda_intel
nf_conntrack_ftp       18685  1 nf_nat_ftp
lm90                   20371  0 
snd_hwdep              13613  1 snd_hda_codec
nf_conntrack           93105  7 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_conntrack,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27716  1 iptable_filter
nouveau               984490  2 
snd_pcm               107140  3 snd_hda_codec,snd_hda_intel
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
mxm_wmi                13021  1 nouveau
wmi                    19363  2 mxm_wmi,nouveau
snd_seq_midi           13324  0 
x_tables               34194  9 ip_tables,xt_tcpudp,xt_limit,xt_conntrack,xt_LOG,iptable_filter,ipt_REJECT,ip6_tables,xt_addrtype
video                  19574  1 nouveau
snd_seq_midi_event     14899  1 snd_seq_midi
kvm                   457597  0 
gpio_ich               13526  0 
snd_rawmidi            30465  1 snd_seq_midi
ttm                    84699  1 nouveau
drm_kms_helper         53165  1 nouveau
snd_seq                66061  2 snd_seq_midi_event,snd_seq_midi
drm                   303157  4 ttm,drm_kms_helper,nouveau
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              30038  3 snd_pcm,snd_seq
i2c_algo_bit           13564  1 nouveau
snd                    73802  14 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21163  0 
mac_hid                13253  0 
microcode              23650  0 
soundcore              12680  1 snd
btrfs                 849758  1 
xor                    21411  1 btrfs
hid_logitech           26721  0 
ff_memless             13704  1 hid_logitech
usbhid                 53067  0 
hid                   106050  2 hid_logitech,usbhid
raid6_pq               97812  1 btrfs
libcrc32c              12615  1 btrfs
tg3                   170345  0 
ahci                   30063  1 
libahci                32088  1 ahci
ptp                    18980  1 tg3
pps_core               19352  1 ptp
paul@lubuntu-64:~$
```

---

### Post by VinDSL on 2013-09-19
> **paul_in_london said:**
> I'm not familiar with llvmpipe. That module doesn't seem to be loaded on my box.
Hi Paul,

The only time I've had llvmpipe crop up, is when I forget to check my '/etc/modprobe.d/' conf files, to see if nouveau is blacklisted. 


Example(s):

**Nouveau Blacklisted**
```
OpenGL vendor string:   **[COLOR="#0000CD"]VMware, Inc[/COLOR]**.
OpenGL renderer string: **[COLOR="#0000CD"]Gallium 0.4[/COLOR][COLOR="red"] on llvmpipe (LLVM 3.2, 128 bits)[/COLOR]**
OpenGL version string:  2.1 Mesa 9.2.0

```


**Nouveau Enabled**
```
OpenGL vendor string:   **[COLOR="#0000CD"]nouveau[/COLOR]**
OpenGL renderer string:**[COLOR="#0000CD"] Gallium 0.4 on NV4B[/COLOR]**
OpenGL version string:  2.1 Mesa 9.2.0
```

My modprobe is clean, right now...  ;)

```
vindsl@Zuul:~$ cat /etc/modprobe.d/* | grep -H 'blacklist nouveau'
vindsl@Zuul:~$ 

```

---

