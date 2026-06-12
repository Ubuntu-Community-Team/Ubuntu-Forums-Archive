---
title: "Snap, Spotify and Chromium"
date: 2018-03-31
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-03-31
I installed the 30/3 ISO and used Software to install the Spotify snap. Spotify worked as expected. I closed Spotify and installed the Chromium snap, which also worked OK.
Started both Chromium and Spotify. When I played a song in Spotify, page load in Chromium became much slower. When I opened a page in Chromium and played a video, Spotify stopped playing.
I uninstalled the snap version of Chromium, installed the non snap version and both Spotify and Chromium worked as expected.
```
p-i@pi-GA-990FXA-UD3:~$ inxi -F
System:    Host: pi-GA-990FXA-UD3 Kernel: 4.15.0-13-generic x86_64 bits: 64
           Desktop: Gnome 3.28.0
           Distro: Ubuntu Bionic Beaver (development branch)
Machine:   Device: desktop Mobo: Gigabyte model: GA-990FXA-UD3 v: x.x serial: N/A
           BIOS: Award v: F5 date: 10/13/2011
CPU:       8 core AMD FX-8120 Eight-Core (-MCP-) cache: 16384 KB
           clock speeds: max: 4000 MHz 1: 1435 MHz 2: 1411 MHz 3: 1431 MHz
           4: 2656 MHz 5: 1415 MHz 6: 1417 MHz 7: 1410 MHz 8: 1455 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Barts PRO [Radeon HD 6850]
           Display Server: x11 (X.Org 1.19.6 ) driver: radeon
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: AMD BARTS (DRM 2.50.0 / 4.15.0-13-generic, LLVM 6.0.0)
           version: 3.3 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Barts HDMI Audio [Radeon HD 6790/6850/6870 / 7720 OEM]
           driver: snd_hda_intel
           Card-2 Advanced Micro Devices [AMD/ATI] SBx00 Azalia (Intel HDA)
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-13-generic
Network:   Card-1: Qualcomm Atheros AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
           driver: ath9k
           IF: wlp3s0 state: up mac: 00:21:91:0b:5f:11
           Card-2: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp5s0 state: down 
Drives:    HDD Total Size: 880.2GB (0.8% used)
           ID-1: /dev/sda model: KINGSTON_SV300S3 size: 120.0GB
           ID-2: /dev/sdb model: KINGSTON_SV300S3 size: 120.0GB
           ID-3: /dev/sdc model: WDC_WD6400AAKS size: 640.1GB
Partition: ID-1: / size: 110G used: 6.7G (7%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 26.4C mobo: N/A gpu: 37.5
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 306 Uptime: 18:43 Memory: 2080.4/7958.4MB
           Client: Shell (bash) inxi: 2.3.56 
p-i@pi-GA-990FXA-UD3:~$ 

```

---

### Post by mc4man on 2018-03-31
Seems ok here if using Intel gpu, however if I switch to nvidia drivers then many snaps have issues. Some recover in less than optimal fashion (vlc), some recover ok (spotify), some never recover (chromium
If you open your snaps from a terminal (snap run appname) does anything of interest appear?

---

### Post by P-I H on 2018-03-31
It worked OK today. I don't know why, but there was some updates today and I have installed and later uninstalled Chromium browser.
There are however some problems
```
p-i@pi-GA-990FXA-UD3:~$ snap run chromium
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gkr-Message: secret service operation failed: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.266" (uid=1000 pid=32072 comm="/snap/chromium/266/usr/lib/chromium-browser/chromi" label="snap.chromium.chromium (enforce)") interface="org.freedesktop.DBus.Peer" member="Ping" error name="(unset)" requested_reply="0" destination="org.freedesktop.secrets" (uid=1000 pid=1271 comm="/usr/bin/gnome-keyring-daemon --daemonize --login " label="unconfined")
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[32352:32352:0331/173308.596795:ERROR:sandbox_linux.cc(375)] InitializeSandbox() called with multiple threads in process gpu-process.
Gkr-Message: secret service operation failed: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.266" (uid=1000 pid=32072 comm="/snap/chromium/266/usr/lib/chromium-browser/chromi" label="snap.chromium.chromium (enforce)") interface="org.freedesktop.Secret.Service" member="SearchItems" error name="(unset)" requested_reply="0" destination="org.freedesktop.secrets" (uid=1000 pid=1271 comm="/usr/bin/gnome-keyring-daemon --daemonize --login " label="unconfined")
[32072:32210:0331/173308.811937:ERROR:upload_data_presenter.cc(73)] Not implemented reached in virtual void extensions::RawDataPresenter::FeedNext(const net::UploadElementReader &)
[32072:32389:0331/173308.843054:ERROR:object_proxy.cc(626)] Failed to call method: org.freedesktop.NetworkManager.GetDevices: object_path= /org/freedesktop/NetworkManager: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.306" (uid=1000 pid=32072 comm="/snap/chromium/266/usr/lib/chromium-browser/chromi" label="snap.chromium.chromium (enforce)") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=794 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
[32072:32389:0331/173308.843096:ERROR:networking_private_linux.cc(733)] Failed to enumerate network devices
[32072:32210:0331/173308.848538:ERROR:upload_data_presenter.cc(73)] Not implemented reached in virtual void extensions::RawDataPresenter::FeedNext(const net::UploadElementReader &)
[32072:32210:0331/173308.965679:ERROR:upload_data_presenter.cc(73)] Not implemented reached in virtual void extensions::RawDataPresenter::FeedNext(const net::UploadElementReader &)
[32072:32389:0331/173328.202548:ERROR:object_proxy.cc(626)] Failed to call method: org.freedesktop.NetworkManager.GetDevices: object_path= /org/freedesktop/NetworkManager: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.306" (uid=1000 pid=32072 comm="/snap/chromium/266/usr/lib/chromium-browser/chromi" label="snap.chromium.chromium (enforce)") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=794 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
[32072:32389:0331/173328.202582:ERROR:networking_private_linux.cc(733)] Failed to enumerate network devices
[32072:32210:0331/173338.652742:ERROR:upload_data_presenter.cc(73)] Not implemented reached in virtual void extensions::RawDataPresenter::FeedNext(const net::UploadElementReader &)
[32072:32210:0331/173338.690710:ERROR:upload_data_presenter.cc(73)] Not implemented reached in virtual void extensions::RawDataPresenter::FeedNext(const net::UploadElementReader &)
[32072:32210:0331/173338.822803:ERROR:upload_data_presenter.cc(73)] Not implemented reached in virtual void extensions::RawDataPresenter::FeedNext(const net::UploadElementReader &)
[32072:32389:0331/173348.640197:ERROR:object_proxy.cc(626)] Failed to call method: org.freedesktop.NetworkManager.GetDevices: object_path= /org/freedesktop/NetworkManager: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.306" (uid=1000 pid=32072 comm="/snap/chromium/266/usr/lib/chromium-browser/chromi" label="snap.chromium.chromium (enforce)") interface="org.freedesktop.NetworkManager" member="GetDevices" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=794 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
[32072:32389:0331/173348.640228:ERROR:networking_private_linux.cc(733)] Failed to enumerate network devices
p-i@pi-GA-990FXA-UD3:~$ 
```
```
p-i@pi-GA-990FXA-UD3:~$ snap run spotify
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"
[0331/174406.820438:ERROR:sandbox_linux.cc(344)] InitializeSandbox() called with multiple threads in process gpu-process.
p-i@pi-GA-990FXA-UD3:~$ 

```

---

### Post by mc4man on 2018-04-03
You could try the current snap core beta, i.e,  16-2.32.2 or wait for next stable version..
```
snap refresh --beta core
```

---

