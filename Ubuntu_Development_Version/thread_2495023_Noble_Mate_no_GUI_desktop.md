---
title: "Noble Mate no GUI desktop"
date: 2024-02-04
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-02-04
I have just tried twice to install the Mate-noble-desktop.amd64.iso from today (Feb 4} as a VM in KVM/QEMU.
I downloaded the iso file using a zsync update from the xubuntu-noble-desktop.amd64.iso from Feb 2, which I have used successfully to install Xubuntu. Both used the pending version of the iso file which is what I use as default though today pending and current are identical iso files.

The iso runs well as a live system in KVM/QEMU with a fully working GUI but once installed to the virtual disk there is no GUI showing though the mouse cursor does show, just nothing more.

The VM uses UEFI mode and I have set it to use 2 CPU cores and 4G ram as I do with all my KVM systems.

Has anyone else seen this with the Mate version which is not a version I've tried before?

---

### Post by ajgreeny on 2024-02-05
Here is some further information that might be of consequence to this problem.

I today used zsync to update the iso to the pending version of Feb5 Noble-Mate.
It will still not run properly in KVM/QEMU though I have tried setting different virtual disk settings of Virtio and SATA with no success.  I have also tried different video settings, virtio, QXL and VGA, but again no success.

However by moving to tty3, logging in there and then running startx I did get to a Mate GUI, but there were some things that still would not work. eg plank will not run at all. If I attempt to start plank in terminal an error shows telling me that it will run only in an X11 sesion which I thought was what Mate used by default.  I do not see a GUI login screen so do not get the opportunity to choose wayland (is it even available in Mate?) or X11 when logging in.

---

### Post by #&amp;thj^% on 2024-02-05
ajgreeny I have not used Mate since wimpy left the building, but there is plans for an optional wayfire/wayland session: [https://github.com/mate-desktop/mate-wayland-session](https://github.com/mate-desktop/mate-wayland-session).

Possibly what your experiencing currently
```
apt depends wayfire
wayfire
  Depends: <libglx-vendor>
    libglx-amber0
    libglx-mesa0
    libnvidia-gl-390
    libnvidia-gl-470
    libnvidia-gl-470-server
    libnvidia-gl-535
    libnvidia-gl-535-server
    libnvidia-gl-545
    libnvidia-gl-550
  Depends: libc6 (>= 2.38)
  Depends: libcairo2 (>= 1.2.4)
  Depends: libegl1
  Depends: libevdev2 (>= 0.9.1)
  Depends: libgcc-s1 (>= 3.4)
  Depends: libgles2
  Depends: libglib2.0-0 (>= 2.12.0)
  Depends: libinput10 (>= 1.1.0)
  Depends: libjpeg8 (>= 8c)
  Depends: libpango-1.0-0 (>= 1.14.0)
  Depends: libpangocairo-1.0-0 (>= 1.14.0)
  Depends: libpixman-1-0 (>= 0.25.2)
  Depends: libpng16-16 (>= 1.6.2)
  Depends: libstdc++6 (>= 13.1)
  Depends: libwayland-client0 (>= 1.0.2)
  Depends: libwayland-server0 (>= 1.14.91)
  Depends: libwf-config1 (>= 0.8.0)
  Depends: libwf-utils0 (>= 0.8.0+git20240110)
  Depends: libwlroots12 (>= 0.17.0)
  Depends: libxcb1
  Depends: libxkbcommon0 (>= 0.5.0)

```

---

### Post by MAFoElffen on 2024-02-05
He is using KVM, so no NVidia or libnvdia*, unless he is doing passthrough.. 

I have Mantic Daily Mate VM's. I though I spun up a Noble Mate Daily VM, when I started the thread to check the blocks that we had everything covered. Yes, successful test-case with build 20230205.

DL'ing a Noble Mate Daily now for today's Daily.... Cam eup > Installing as ZFS-On-Root. Go big right?

Booting > Splash > Black screen for a very long time... Stuck on Black screen. Graphics Layers is not coming up.

Toggled to vtty4 > Logged in. Reviewing logs. Errors at end of log is about apparmor denied on snap desktop integration.

Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2052489](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2052489)

Please join as "I am also affected", which will bump it to confirmed.

---

### Post by ajgreeny on 2024-02-06
Added my name to the bug!

---

### Post by MAFoElffen on 2024-02-06
I think I narrowed it down to a problem with LightDM.

But also uncovered problems with apparmor, and with it trying to start Snap app FireFox during the boot process as user root... That is way odd.

@ajgreeny ---
Toggle over to one of the vtty consoles and loggin... You can either install gdm3 to finish testing the Mate Daily. I confirmed that works. Or the desktop will start the Mate Desktop manually via 'startx'.

---

### Post by ajgreeny on 2024-02-06
I have also tried the kernel option **apparmor=0** and can confirm that resulted in no difference; still booted to black screen with no GUI and no lightdm showing.
Not yet tried using gdm in place of lightdm yet but will do so as soon as I have some time to spare.

---

### Post by #&amp;thj^% on 2024-02-06
I'm on the fence with lightdm bug: (BTW who mentioned nvidia) ajgreeny dose not use nvidia at all.
```
apt policy gdm3
gdm3:
  Installed: (none)
  Candidate: 45.0.1-1ubuntu2
  Version table:
     45.0.1-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
me@me-Standard-PC-i440FX-PIIX-1996:~$ apt policy lightdm
lightdm:
  Installed: 1.30.0-0ubuntu8
  Candidate: 1.30.0-0ubuntu8
  Version table:
 *** 1.30.0-0ubuntu8 500
        500 http://us.archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        100 /var/lib/dpkg/status

```
apparmor is fine here:
```
sudo aa-status
[sudo] password for me: 
apparmor module is loaded.
115 profiles are loaded.
38 profiles are in enforce mode.
   /snap/snapd/20671/usr/lib/snapd/snap-confine
   /snap/snapd/20671/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/bin/man
   /usr/bin/redshift
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /{,usr/}sbin/dhclient
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   rsyslogd
   snap-update-ns.firefox
   snap-update-ns.snapd-desktop-integration
   snap-update-ns.software-boutique
   snap-update-ns.ubuntu-mate-welcome
   snap.firefox.firefox
   snap.firefox.geckodriver
   snap.firefox.hook.configure
   snap.firefox.hook.connect-plug-host-hunspell
   snap.firefox.hook.disconnect-plug-host-hunspell
   snap.firefox.hook.post-refresh
   snap.snapd-desktop-integration.hook.configure
   snap.snapd-desktop-integration.snapd-desktop-integration
   tcpdump
8 profiles are in complain mode.
   libreoffice-oosplash
   libreoffice-soffice
   snap.software-boutique.software-boutique
   snap.ubuntu-mate-welcome.hook.install
   snap.ubuntu-mate-welcome.hook.post-refresh
   snap.ubuntu-mate-welcome.hook.remove
   snap.ubuntu-mate-welcome.software-boutique
   snap.ubuntu-mate-welcome.ubuntu-mate-welcome
0 profiles are in prompt mode.
0 profiles are in kill mode.
69 profiles are in unconfined mode.
   /bin/toybox
   /opt/brave.com/brave/brave
   /opt/google/chrome/chrome
   /opt/microsoft/msedge/msedge
   /opt/vivaldi/vivaldi-bin
   /usr/bin/buildah
   /usr/bin/busybox
   /usr/bin/cam
   /usr/bin/ch-checkns
   /usr/bin/ch-run
   /usr/bin/crun
   /usr/bin/flatpak
   /usr/bin/ipa_verify
   /usr/bin/lc-compliance
   /usr/bin/libcamerify
   /usr/bin/lxc-attach
   /usr/bin/lxc-create
   /usr/bin/lxc-destroy
   /usr/bin/lxc-execute
   /usr/bin/lxc-stop
   /usr/bin/lxc-unshare
   /usr/bin/lxc-usernsexec
   /usr/bin/mmdebstrap
   /usr/bin/podman
   /usr/bin/qcam
   /usr/bin/rootlesskit
   /usr/bin/rpm
   /usr/bin/sbuild
   /usr/bin/sbuild-abort
   /usr/bin/sbuild-apt
   /usr/bin/sbuild-checkpackages
   /usr/bin/sbuild-clean
   /usr/bin/sbuild-createchroot
   /usr/bin/sbuild-distupgrade
   /usr/bin/sbuild-hold
   /usr/bin/sbuild-shell
   /usr/bin/sbuild-unhold
   /usr/bin/sbuild-update
   /usr/bin/sbuild-upgrade
   /usr/bin/slirp4netns
   /usr/bin/stress-ng
   /usr/bin/thunderbird
   /usr/bin/trinity
   /usr/bin/tup
   /usr/bin/userbindmount
   /usr/bin/uwsgi-core
   /usr/bin/vdens
   /usr/bin/vpnns
   /usr/lib/*-linux-gnu*/qt5/libexec/QtWebEngineProcess
   /usr/lib/qt6/libexec/QtWebEngineProcess
   /usr/lib/systemd/systemd-coredump
   /usr/libexec/*-linux-gnu*/bazel/linux-sandbox
   /usr/libexec/virtiofsd
   /usr/sbin/runc
   /usr/sbin/sbuild-adduser
   /usr/sbin/sbuild-destroychroot
   1password
   Discord
   MongoDB Compass
   code
   firefox
   github-desktop
   obsidian
   opera
   polypane
   signal-desktop
   slack
   steam
   wpcom
16 processes have profiles defined.
16 processes are in enforce mode.
   /usr/sbin/cups-browsed (1563) 
   /usr/sbin/cupsd (1490) 
   /usr/sbin/rsyslogd (1204) rsyslogd
   /snap/firefox/3728/usr/lib/firefox/firefox (4142) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4380) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4443) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4469) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4559) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4713) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4736) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4938) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (4995) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (5061) snap.firefox.firefox
   /snap/firefox/3728/usr/lib/firefox/firefox (5095) snap.firefox.firefox
   /snap/snapd-desktop-integration/83/usr/bin/snapd-desktop-integration (2381) snap.snapd-desktop-integration.snapd-desktop-integration
   /snap/snapd-desktop-integration/83/usr/bin/snapd-desktop-integration (2584) snap.snapd-desktop-integration.snapd-desktop-integration
0 processes are in complain mode.
0 processes are in prompt mode.
0 processes are in kill mode.
0 processes are unconfined but have a profile defined.
0 processes are in mixed mode.

```
lightdm:
```
systemctl status lightdm
&#9679; lightdm.service - Light Display Manager
     Loaded: loaded (/lib/systemd/system/lightdm.service; indirect; preset: ena>
     Active: active (running) since Tue 2024-02-06 12:14:24 MST; 13min ago
       Docs: man:lightdm(1)
   Main PID: 1506 (lightdm)
      Tasks: 6 (limit: 4564)
     Memory: 40.2M
        CPU: 595ms
     CGroup: /system.slice/lightdm.service
             &#9500;&#9472;1506 /usr/sbin/lightdm
             &#9492;&#9472;1553 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/ligh>

Feb 06 12:14:24 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Starting lightdm.se>
Feb 06 12:14:24 me-Standard-PC-i440FX-PIIX-1996 lightdm[1506]: Seat type 'xloca>
Feb 06 12:14:24 me-Standard-PC-i440FX-PIIX-1996 systemd[1]: Started lightdm.ser>
Feb 06 12:14:27 me-Standard-PC-i440FX-PIIX-1996 lightdm[1617]: pam_unix(lightdm>
Feb 06 12:14:27 me-Standard-PC-i440FX-PIIX-1996 lightdm[1617]: gkr-pam: couldn'>
Feb 06 12:14:27 me-Standard-PC-i440FX-PIIX-1996 lightdm[1617]: pam_env(lightdm->

```
forgot this:
```
inxi -S | grep Desktop
  Desktop: MATE v: 1.26.2 Distro: Ubuntu 24.04 (Noble Numbat)

```

---

### Post by #&amp;thj^% on 2024-02-06
Ok fully updated and yes indeed lightdm fails, gdm3 works for the most part.
wayfire session selected wont work, yet.

---

### Post by #&amp;thj^% on 2024-02-06
BTW Slim DM works as well
```
System:
  Kernel: 6.6.0-14-generic arch: x86_64 bits: 64 compiler: gcc v: 13.2.0
  Desktop: MATE v: 1.26.2 wm: marco dm: SLiM Distro: Ubuntu 24.04 (Noble
    Numbat)
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996)
    v: pc-i440fx-8.2 serial: <superuser required> Chassis: type: 1
    v: pc-i440fx-8.2 serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: Arch Linux 1.16.3-1-1
    date: 04/01/2014
CPU:
  Info: 4x 1-core model: AMD Ryzen 5 5600H with Radeon Graphics bits: 64
    type: SMP arch: Zen 3 rev: 0 cache: L1: 4x 128 KiB (512 KiB)
    L2: 4x 512 KiB (2 MiB) L3: 4x 16 MiB (64 MiB)
  Speed (MHz): avg: 3294 min/max: N/A cores: 1: 3294 2: 3294 3: 3294 4: 3294
    bogomips: 26349
  Flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel ports:
    active: Virtual-1 empty: Virtual-2,Virtual-3,Virtual-4 bus-ID: 00:02.0
    chip-ID: 1b36:0100
  Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.4
    compositor: marco v: 1.26.2 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa dri: swrast gpu: qxl display-ID: :0.0
    screens: 1
  Screen-1: 0 s-res: 1680x1050 s-dpi: 96
  Monitor-1: Virtual-1 res: 1680x1050 size: N/A
  API: EGL v: 1.5 platforms: device: 0 drv: swrast gbm: drv: kms_swrast
    surfaceless: drv: swrast x11: drv: swrast inactive: wayland
  API: OpenGL v: 4.5 vendor: mesa v: 23.3.3-1ubuntu2 glx-v: 1.4
    direct-render: yes renderer: llvmpipe (LLVM 17.0.6 256 bits)
    device-ID: ffffffff:ffffffff
Audio:
  Device-1: Intel 82801FB/FBM/FR/FW/FRW High Definition Audio vendor: Red Hat
    QEMU Virtual Machine driver: snd_hda_intel v: kernel bus-ID: 00:04.0
    chip-ID: 8086:2668
  API: ALSA v: k6.6.0-14-generic status: kernel-api
  Server-1: PipeWire v: 1.0.2 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI vendor: Red Hat Qemu virtual machine
    type: network bridge driver: piix4_smbus v: N/A port: N/A bus-ID: 00:01.3
    chip-ID: 8086:7113
  Device-2: Red Hat Virtio network driver: virtio-pci v: 1 port: c120
    bus-ID: 00:03.0 chip-ID: 1af4:1000
  IF: ens3 state: up speed: -1 duplex: unknown mac: <filter>
RAID:
  Device-1: bpool type: zfs status: ONLINE level: linear raw: size: 1.62 GiB
    free: 1.5 GiB zfs-fs: size: 1.5 GiB free: 1.38 GiB
  Components: Online: 1: vda4
  Device-2: rpool type: zfs status: ONLINE level: linear raw: size: 20 GiB
    free: 13.6 GiB zfs-fs: size: 19.38 GiB free: 13.02 GiB
  Components: Online: 1: vda5
Drives:
  Local Storage: total: raw: 25 GiB usable: 24 GiB used: 6.49 GiB (27.0%)
  ID-1: /dev/vda model: N/A size: 25 GiB speed: <unknown> serial: N/A
Partition:
  ID-1: / size: 17.04 GiB used: 4.02 GiB (23.6%) fs: zfs
    logical: rpool/ROOT/ubuntu_gxertg
  ID-2: /boot size: 1.5 GiB used: 123.4 MiB (8.0%) fs: zfs
    logical: bpool/BOOT/ubuntu_gxertg
  ID-3: /boot/efi size: 512 MiB used: 16.8 MiB (3.3%) fs: vfat dev: /dev/vda2
  ID-4: /var/log size: 13.03 GiB used: 11.1 MiB (0.1%) fs: zfs
    logical: rpool/ROOT/ubuntu_gxertg/var/log
Swap:
  ID-1: swap-1 type: partition size: 2.62 GiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/vda3
Sensors:
  Src: lm-sensors+/sys Message: No sensor data found using /sys/class/hwmon or
    lm-sensors.
Info:
  Memory: total: 4 GiB available: 3.83 GiB used: 2.1 GiB (54.8%)
  Processes: 356 Power: uptime: 3m wakeups: 0 Init: systemd v: 253
    target: graphical (5) default: graphical
  Packages: 2249 pm: dpkg pkgs: 2243 pm: flatpak pkgs: 6 Compilers:
    gcc: 13.2.0 Shell: Bash v: 5.2.21 running-in: mate-terminal inxi: 3.3.32

```

---

### Post by ajgreeny on 2024-02-06
Lack of available time has I'm afraid meant that in order to keep testing the Mate version I have ended up using autologin, not something I want to do but in these circumstances it saves so much time.
I can and will still keep trying new daily iso files so will be aware very quickly once this problem has been overcome and I can then start again with a completely new VM.

---

### Post by ajgreeny on 2024-02-07
I have now installed **slim** dm and it's working fine.

I did consider gdm3 but it needed to pull in so much cruft of the gnome desktop that I didn't bother, having seen the comment about **slim** dm. I wonder if **xdm** would also work?  I might try it on another Mate-Noble just for my own information.

While I'm here, how do I remove the annoying home icon from the desktop?

---

### Post by #&amp;thj^% on 2024-02-07
> **ajgreeny said:**
> 
While I'm here, how do I remove the annoying home icon from the desktop?

Control Center>>.Mate Tweak>>Un tick show Desktop Icons gets them all.

---

### Post by ajgreeny on 2024-02-07
Thanks 1fallen.
I didn't think to look there but should have done as that is how you change the mouse pointer.  It would make more sense if it was in a more obvious place but perhaps that is what I get for having used Xfce exclusively for about 15 years.

---

### Post by ajgreeny on 2024-02-10
I have tried again today, Feb 10th, using the pending daily iso file of Mate-Noble but still there is no lightdm screen appearing so have again gone to a virtual tty and installed and configured **slim** dm. to my preferences.

Everything else seems to be working fine though I'm still preferring Xfce simply because I know where and how all its detailed tricks and configurations are.

---

### Post by ajgreeny on 2024-02-11
I was unfortunately wrong about slim dm working fine as I have now found on two different KVM installations on a laptop and a desktop that shutdown is always interrupted and machines either sit going nowhere or just restart.
Shutting down using terminal or from a virtual tty command line work fine.
having mentioned before that I wanted  to try xdm I have also installed that and it works without the reboot problem so for now I'm leaving xdm in charge.

---

### Post by #&amp;thj^% on 2024-02-11
> **ajgreeny said:**
> I was unfortunately wrong about slim dm working fine as I have now found on two different KVM installations on a laptop and a desktop that shutdown is always interrupted and machines either sit going nowhere or just restart.
Shutting down using terminal or from a virtual tty command line work fine.
having mentioned before that I wanted  to try xdm I have also installed that and it works without the reboot problem so for now I'm leaving xdm in charge.

How weird, everything here is still good on slim dm....2 Laptops both Lenovo one intel i7 and the other amd and all functions like logout, restart, and shutdown work perfectly.
But nice to see you verify xdm is working good for you. and it shows another option for others to try. :)
Thanks ajgreeny

---

### Post by ajgreeny on 2024-02-12
I wonder if KVM is my problem; I can't remember but are your Mate systems bare metal or virtual installations?

---

### Post by Irihapeti on 2024-02-12
I tried Mate on my old Acer Travelmate. It would not boot to GUI. Just a black screen. So, not KVM (yes, I tried that as well).

But when I logged in from another console, I tried running startx. And it worked.

Actually, I ought to try that on KVM as well...

Edit: startx works on KVM.

---

### Post by ajgreeny on 2024-02-12
Yes we know startx works but it would make a lot more sense to get lightdm working as it should!

Have you tried slim and/or xdm, both of which worked for me for logging in but slim refused to let me shutdown the VMs.

---

### Post by Irihapeti on 2024-02-12
No, I've not tried anything other than what comes with it. I might do so and see how it goes.

---

### Post by Irihapeti on 2024-02-12
Slim and xdm work on the old laptop and on the KVM VM. I have no difficulty shutting down with either of them, on either machine.

---

### Post by #&amp;thj^% on 2024-02-12
> **ajgreeny said:**
> I wonder if KVM is my problem; I can't remember but are your Mate systems bare metal or virtual installations?

KVM's
```
virsh list --all
 Id   Name          State
------------------------------
 -    ubuntu22.04   shut off
 -    ubuntu24.04   shut off

```
One of those is actually 20.04

---

### Post by deadflowr on 2024-02-12
Try changing the lightdm greeter.

---

### Post by ajgreeny on 2024-02-12
> **deadflowr said:**
> Try changing the lightdm greeter.
If this was a comment for me I have stopped trying **lightdm** as it does not appear at boot or after logging out; it just sits at a black screen meaning startx is needed from a virtual tty in my KVM system.

It is **slim** that did not allow a full shutdown though **xdm** works as it should for both login and shutdown.

I have not tried changing the **lightdm** settings if that is what you meant. Are you suggesting that doing so might get it working properly again?

---

### Post by ajgreeny on 2024-02-19
A further update on this annoying problem.
Having found that xdm was working beautifully I purged lightdm which also removed arctica-greeter, which surprised me as I had assumed that it would use lightdm-greeter.

I therefore decided to reinstall lightdm but this time with lightdm-gtk-greeter, lightdm-gtk-greeter settings, but not arctica-greeter. 
Lightdm did work now after I chose to use lightdm instead of xdm.
I also installed lightdm-settings.

Lightdm started first time with just a black background so I have also chosen to add ubuntu-mate-lightdm-theme.
So let's see if everything now works properly, not just working with black background.

OK. I have just rebooted after using **lightdm-gtk-greeter-settings** from the menu and adding a background image.
Everything is now working exactly as it should have done right from the start.

---

### Post by ajgreeny on 2024-02-27
I have just installed today's iso pending file Ubuntu-MATE 24.04 LTS "Noble Numbat" - Daily amd64 (20240226) and the installation worked perfectly wit a GUI appearing as expected after logging in.
Whatever the problem was with the arctica-greeter has apparently been solved; let's hope that continues to work from now on.

I have updated the bug mentioned earlier [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2052489](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2052489)  with this information.

---

### Post by Irihapeti on 2024-02-27
I can confirm that after testing on QEMU/KVM VM. I've left a comment in the bug thread.

---

