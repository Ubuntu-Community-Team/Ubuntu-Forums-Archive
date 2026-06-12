---
title: "Systemd-networkd-wait-online and slow boot"
date: 2024-01-27
forum: Virtualisation
---

### Post by Irihapeti on 2024-01-27
I have a Xen VPS which is booting slowly. OS is Ubuntu 22.04, originally upgraded from 20.04. In recent months (since 30 September, to be precise), it's taking ages to boot. 

The culprit turns out to be systemd-networkd-wait-online, with its obligatory 2-minute wait if it's not happy for some reason.

networkctl shows
```

IDX LINK     TYPE     OPERATIONAL SETUP    
  1 lo       loopback carrier     unmanaged
  2 bond0    bond     off         unmanaged
  3 dummy0   ether    off         unmanaged
  4 teql0    void     off         unmanaged
  5 gre0     ipgre    off         unmanaged
  6 gretap0  ether    off         unmanaged
  7 erspan0  ether    off         unmanaged
  8 ip_vti0  tunnel   off         unmanaged
  9 ip6_vti0 tunnel6  off         unmanaged
 10 sit0     sit      off         unmanaged
 11 ip6tnl0  tunnel6  off         unmanaged
 12 ip6gre0  ip6gre   off         unmanaged
 13 eth0     ether    routable    unmanaged

```
which looks to me like systemd-networkd isn't managing anything.

(The hosting people are using ifupdown to manage the network.)

If it's relevant, just before the first problematic boot, I ran apt upgrade and it pulled in several systemd-related packages.

From apt/history.log:
```

Start-Date: 2023-09-30  19:39:05
Commandline: apt upgrade
Requested-By: user (1000)
Upgrade: udev:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), openssh-client:amd64 (1:8.9p1-3ubuntu0.3, 1:8.9p1-3ubuntu0.4), systemd-timesyncd:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), libpam-systemd:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), ssh:amd64 (1:8.9p1-3ubuntu0.3, 1:8.9p1-3ubuntu0.4), libsystemd0:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), libnss-systemd:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), openssh-server:amd64 (1:8.9p1-3ubuntu0.3, 1:8.9p1-3ubuntu0.4), systemd:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), libudev1:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), libc6:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.3), locales:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.3), libc-dev-bin:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.3), openssh-sftp-server:amd64 (1:8.9p1-3ubuntu0.3, 1:8.9p1-3ubuntu0.4), libc-bin:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.3), libc-devtools:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.3), libc6-dev:amd64 (2.35-0ubuntu3.1, 2.35-0ubuntu3.3), systemd-sysv:amd64 (249.11-0ubuntu3.9, 249.11-0ubuntu3.10), ubuntu-advantage-tools:amd64 (28.1~22.04, 29.4~22.04)
End-Date: 2023-09-30  19:39:32

```
What could I do to stop this delay? Do I need systemd-networkd at all? I'm hesitant to just try disabling or removing things, since I don't want to end up breaking anything.

---

### Post by MAFoElffen on 2024-01-27
In your /etc/netplan/<named>.yaml file, for each named device/port add the line "optional: yes". Remeber to have it as the same indent space as the dhcp4 option.

Here is an example:
```

network:
  version: 2
  renderer: networkd
  ethernets: 
    enp0s25: 
      dhcp4: yes
      dhcp6: yes
      optional: yes

```
What that will do is to skip checking if it is up at that time of the boot process, and check it later. This is fine, because it usually comes up at a later time anyways.

---

### Post by Irihapeti on 2024-01-27
Unfortunately, netplan isn't installed at all, and so there's no .yaml file to edit. The network is managed with ifupdown (I know it's old-fashioned, but it's still available). Maybe I need to contact support and see what they say. These are Linux people, so I know I'll get some sense out of them.

But thanks for the reply. Now I'm wondering why I didn't think of that for some of the devices on my home network that have been slow booting...

---

### Post by oldfred on 2024-01-27
From these sites I have changed a few settings. Originally from 20.04 but still use in 22.04.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

I use Kubuntu on NVMe SSD, so they both make for faster boot.

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.282s (kernel) + 5.676s (userspace) = 9.959s  
graphical.target reached after 5.639s in userspace
[/FONT]
```

Main settings I change from above links.
turned off NetworkManager-wait with systemctl, 
systemctl disable NetworkManager-wait-online.service
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo, 
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting,
removed snaps

If UEFI firmware update not supported (yet)
sudo apt-get purge fwupd

systemctl status bolt
boltctl list
systemctl mask bolt.service

---

### Post by MAFoElffen on 2024-01-28
How about this?: [https://askubuntu.com/a/1245672/138255](https://askubuntu.com/a/1245672/138255)

Seemed to match how you are doing things...

---

### Post by Irihapeti on 2024-01-28
@MAFoElffen:

Thanks for the link. The whole thread was worth reading and I've bookmarked it for future reference.


After running systemd-analyze critical-chain on most of the server programs, and not seeing anything that included systemd-networkd-wait-online or systemd-networkd, I figured that it wasn't actually doing anything other than hold up the boot process. After disabling systemd-networkd, bootup time is now in the order of 11 seconds total and the various internet-facing servers are up at about 5-6 seconds. MUCH better. And obviously, I didn't break anything.

I'll give it a day or so to settle (and make sure everything *is* OK), then I'll mark this solved.

Thanks, all.

---

