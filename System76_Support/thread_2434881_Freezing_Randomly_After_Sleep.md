---
title: "Freezing Randomly After Sleep"
date: 2020-01-12
forum: System76 Support
---

### Post by 618C on 2020-01-12
Bought a new Darter Pro from System76, installed Ubuntu Budgie 18.04. I've been experiencing random freezes waking the laptop from sleep.
When I say random, I mean it only happens a small percent of the time. When it does, it's usually 5-10 seconds after waking when it does freeze.

I can't switch TTY sessions, mouse and keyboard seem unresponsive. Hard reboot seems to be the only thing I can do. I've opened a ticket with System76, but wanted to know if there's anything else I can look into to resolve the issue.

```
Linux bullseye 5.3.0-7625-generic #27~1576774585~18.04~c7868f8~dev-Ubuntu SMP Thu Dec 19 20:37:32  x86_64 x86_64 x86_64 GNU/Linux
```

Logs shown right before I gave it a hard reboot but after I woke it up and it froze.

```

Jan 12 21:54:56 bullseye systemd[1]: Stopped target Sleep.
Jan 12 21:54:56 bullseye systemd[1]: tlp-sleep.service: Unit not needed anymore. Stopping.
Jan 12 21:54:56 bullseye systemd[1]: Stopping TLP suspend/resume...
Jan 12 21:54:56 bullseye systemd[1]: Reached target Suspend.
Jan 12 21:54:56 bullseye systemd[1]: suspend.target: Unit not needed anymore. Stopping.
Jan 12 21:54:56 bullseye systemd[1]: Stopped target Suspend.
Jan 12 21:54:56 bullseye systemd-logind[1214]: Operation 'sleep' finished.
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0229] keyfile: new connection /etc/NetworkManager/system-connections/{omitted}
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0232] get unmanaged devices count: 0
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0233] manager: rfkill: WiFi enabled by radio killswitch; enabled by state file
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0233] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0233] manager: Networking is enabled by state file
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0234] dhcp-init: Using DHCP client 'dhclient'
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0234] Loaded device plugin: NMBondDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMBridgeDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMDummyDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMEthernetDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMInfinibandDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMIPTunnelDeviceFactory (internal)
Jan 12 21:54:57 bullseye nm-dispatcher[22890]: req:3 'hostname': new request (2 scripts)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMMacsecDeviceFactory (internal)
Jan 12 21:54:57 bullseye nm-dispatcher[22890]: req:3 'hostname': start running ordered scripts...
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0235] Loaded device plugin: NMMacvlanDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0236] Loaded device plugin: NMPppDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0236] Loaded device plugin: NMTunDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0236] Loaded device plugin: NMVethDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0236] Loaded device plugin: NMVlanDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0236] Loaded device plugin: NMVxlanDeviceFactory (internal)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0242] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-devi
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0247] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-dev
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0249] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-devi
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0251] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-devi
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0254] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-devic
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0261] device (lo): carrier: link connected
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0268] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Jan 12 21:54:57 bullseye NetworkManager[23210]: <info>  [1578884097.0277] manager: (docker0): new Bridge device (/org/freedesktop/NetworkManager/Devices/2)
-- Reboot --

```

---

### Post by wildmanne39 on 2020-01-12
*Thread moved to **System76 Support a more appropriate sub-forum**.*

---

### Post by CelticWarrior on 2020-01-13
Have you installed the System76 drivers?

---

### Post by ra7411 on 2020-01-13
With an AMD cpu desktop computer, I've experienced similar wakeup problems with Ub 14.04, 16.04, and for a short period with 18.04 after which it stopped.

I never could find a fix. The problem seemed to mostly occur shortly after Ub updates. I wound up using qt5-fsarchiver to backup the o/s after a period of no problems - that is the state of the o/s  wasn't having the problem. I reduced doing updates to once or twice a month. If the wakeup problem reoccurred, I would recover the saved o/s that was running ok, use it for a while, then update. Usually, I'd get a stretch of usage without the wakeup problem recurring and once I felt like I had a good o/s state, I'd backup that one.

Hope that helps.

---

### Post by 618C on 2020-01-13
Yes, I have the system76 driver installed. I'm also using the same kernel version that came installed with the laptop. Adding the lists below.

```
ii  linux-image-5.3.0-7625-generic         5.3.0-7625.27~1576774585~18.04~c7868f8~dev 
```

```

&#10140;  ~ dpkg -l | grep system76
ii  gnome-shell-extension-system76-power   1.0.0~1561669692~18.04~436b648~dev                 all          Gnome-shell extension for System76 Power Management
ii  linux-firmware                         1.183.2+system76~1573660723~18.04~813d257~dev      all          Firmware for Linux kernel drivers
ii  linux-system76                         5.3.0-7625.27~1576774585~18.04~c7868f8~dev         amd64        System76 recommended Linux kernel
ii  system76-acpi-dkms                     1.0.1~1571170639~18.04~d625910~dev                 amd64        System76 ACPI Driver (DKMS)
ii  system76-dkms                          1.0.6~1568425791~18.04~5ba8ce9~dev                 amd64        System76 DKMS driver
ii  system76-driver                        19.04.20~1572357231~18.04~d3d1aef~dev              all          Universal driver for System76 computers
ii  system76-firmware-daemon               1.0.6~1571257561~18.04~95fa4da~dev                 amd64        System76 Firmware Daemon
ii  system76-io-dkms                       1.0.1~1559663713~18.04~ea5f61a~dev                 amd64        System76 Io DKMS driver
ii  system76-oled                          0.1.3~1571160127~18.04~5eb2e41~dev                 amd64        Control brightness on OLED displays
ii  system76-power                         1.0.2~1578336229~18.04~0cab18b~dev                 amd64        System76 Power Management
ii  system76-wallpapers                    18.04.2~1525874807~18.04~d6171e2~dev               all          System76 Wallpapers

```

---

### Post by meijer.o on 2020-09-23
Add "i8042.nomux=1" as kernel parameter in /etc/default/grub, update grub and see if that works. It worked for me.

---

