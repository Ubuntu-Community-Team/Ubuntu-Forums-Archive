---
title: "Apparmor is not listening to the permissions I gave in the apparmor profile"
date: 2022-08-12
forum: Security
---

### Post by ubcandles49 on 2022-08-12
OS and software:
- OS: Ubuntu 20.04
- Firefox version: 103
- Apparmor version: 3.0.6 build from source

Firefox with an apparmor profile doesn't work with proxychains for me. At first I faced the problem with curl and solved it. But the doing the same with the firefox profile doesn't work for me.
```

$ proxychains curl
[proxychains] config file found: /etc/proxychains.conf
[proxychains] preloading /usr/lib/x86_64-linux-gnu/libproxychains.so.4
couldnt read configuration file: Permission denied

```
apparmor gave me this error:

```

Aug 12 09:03:17 hostname kernel: audit: type=1400 audit(1660294997.611:17636): apparmor="DENIED" operation="open" profile="curl" name="/etc/proxychains4.conf" pid=39377 comm="curl" requested_mask="r" denation="open" profile="curl" name="/etc/proxychains4.conf" pid=39377 comm="curl" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```

I added "/etc/proxychains4.conf ,r" to my curl apparmor profile at the bottom of the file. It solved the problem for curl. After that I added "/etc/proxychains4.conf r," to the bottom of my firefox apparmor profile. I reloaded the apparmor service and profile (later I even desperately rebooted). Ran firefox with proxychains again:

```

$ proxychains firefox
[proxychains] config file found: /etc/proxychains4.conf
[proxychains] preloading /usr/lib/x86_64-linux-gnu/libproxychains.so.4
[proxychains] DLL init: proxychains-ng 4.14
[proxychains] DLL init: proxychains-ng 4.14
couldnt read configuration file: Permission denied

```
I get the error that firefox can't read the proxychains4.conf while I gave it permissions to read it through apparmor:
```

Aug 12 09:27:45 hostname kernel: audit: type=1400 audit(1660296465.474:17939): apparmor="DENIED" operation="open" profile="firefox" name="/etc/proxychains4.conf" pid=40118 comm="firefox" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

```
My firefox apparmor profile/policy:

```

abi <abi/3.0>,
include <tunables/global>

/usr/bin/firefox {
  #include <abstractions/base>
  #include <abstractions/mesa>
  #include <abstractions/nameservice>
  #include <abstractions/ubuntu-browsers.d/ubuntu-integration>
  #include <abstractions/gnome>
  #include <abstractions/fonts>
  #include <abstractions/krathalans-common-gui>
  
  # If you want audio then enable this.
  include <abstractions/audio>
  /usr/bin/jackd mrix,
  
  # Hardware acceleration
  #include <abstractions/krathalans-hwaccel>
  @{sys}/devices/pci[0-9]*/**/drm/ r,
  @{sys}/devices/pci[0-9]*/**/{revision,config,uevent} r,

  # Dconf
  owner /run/user/*/dconf/ w,
  owner /run/user/*/dconf/user rw,
  owner @{HOME}/.config/dconf/user r,
  
  # Network
  #include <abstractions/krathalans-networking>
  network netlink raw,
  network tcp,
  network udp,
  network inet dgram,
  network inet stream,
  network inet6 dgram,
  network inet6 stream,
    
  # Spell checking
  include <abstractions/enchant>

  deny /etc/host.conf r,
  deny /etc/hosts r,
  deny /etc/nsswitch.conf r,
  deny /etc/passwd r,
  deny /etc/group r,
  
  deny /etc/machine-id r,
  deny /var/lib/dbus/machine-id r,

  /dev/ r,
  /dev/shm/ r,
  
  
  # SSL certificates   
  /etc/ca-certificates/trust-source/ r,
  /etc/ca-certificates/trust-source/anchors/ r,
  /etc/ca-certificates/trust-source/blacklist/ r,

  /usr/bin/{bash,dash} rix,
  # Use px instead of Px to avoid env scrubbing for LD_PRELOAD libEGL.so, libmozsandbox.so
  /{usr/bin,usr/lib/firefox*}/firefox* mrpx,
  /usr/lib/firefox/firefox mrix,

  # Intel
  /proc/sys/dev/i915/perf_stream_paranoid r,
  /opt/intel/mediasdk/lib/libmfx.so.* mr,

  # Wayland
  owner /dev/shm/wayland.mozilla.ipc.* rw,  
  
  # systemd-homed
  /{,var/}run/systemd/userdb/ r,
 
  # Needed to install addons, export files from addons
  owner /tmp/{,**} rwkl,
  
  # Don't allow launching other applications to open files
  deny /usr/bin/gio-launch-desktop rx,
  deny /etc/mailcap r,

  # GVFS is unnecessary
  deny /usr/share/gvfs/remote-volume-monitors/ r,

  # Deny /var and /tmp
  deny /var/{,**} rw,

  # Don't allow executable mapping of arbitrary files
  deny @{HOME}/#* mrw,
  deny @{HOME}/.gl* mrw,
  
  /usr/share/gtk-3.0/settings.ini r,
  /usr/share/icons/ r,

  /usr/share/pixmaps/ r,
  owner /dev/shm/shmfd-* rw,
  owner /dev/shm/org.{chromium,mozilla}.{,ipc.}* rw,
  owner @{HOME}/.ICEauthority r,
  owner @{HOME}/.Xauthority r,

  owner @{HOME}/.mozilla/ r,
  owner @{HOME}/.mozilla/* r,
  owner @{HOME}/.mozilla/firefox/ rw,
  owner @{HOME}/.mozilla/firefox/** rwk,
  owner @{HOME}/.mozilla/firefox/*.default/ rwk,
  owner @{HOME}/.mozilla/firefox/*.default/** rwk,
  owner @{HOME}/.mozilla/firefox/profiles.ini r,
  owner @{HOME}/.mozilla/firefox/*.default/extensions/ rwk,
  owner @{HOME}/.mozilla/firefox/*.default/extensions/** rwk,

  owner @{HOME}/.cache/mozilla/ r,
  owner @{HOME}/.cache/mozilla/firefox/ rw,
  owner @{HOME}/.cache/mozilla/firefox/** rwk,
  owner @{HOME}/.cache/mozilla/firefox/*.default/ rwk,
  owner @{HOME}/.cache/mozilla/firefox/*.default/** rwk,
  owner @{HOME}/.cache/mozilla/firefox/*.default/startupCache/ rwk, 
  owner @{HOME}/.cache/mozilla/firefox/*.default/startupCache/* rwk,
  
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # Deny unnecessary /proc
  deny @{PROC}/@{pid}/{,**} rw,
  deny @{PROC}/bus/pci/devices r,
  deny @{PROC}/sys/kernel/random/boot_id r,
  
  owner @{PROC}/@{pid}/fd/ r,
  owner @{PROC}/@{pid}/mountinfo r,
  owner @{PROC}/@{pid}/stat r,
  owner @{PROC}/@{pid}/status r,
  owner @{PROC}/@{pid}/task/*/stat r,
  @{PROC}/sys/kernel/random/uuid r,

  /etc/mime.types r,
  /usr/share/ r,
  /usr/share/glib-[0-9]*/schemas/gschemas.compiled r,
  /usr/share/mime/ r,
  /usr/share/themes/ r,
  /usr/share/applications/** rk,
  /usr/share/gnome/applications/ r,
  /usr/share/gnome/applications/kde4/ r,
  /usr/share/poppler/{,**} r,

  /sys/devices/system/cpu/ r,
  /sys/devices/system/cpu/present r,
  /sys/devices/system/node/ r,
  /sys/devices/system/node/node[0-9]*/meminfo r,
  deny /sys/devices/virtual/block/*/uevent r,

  /etc/udev/udev.conf r,
  /{,var/}run/udev/data/+pci:[0-9]* r,
  /sys/devices/pci[0-9]*/**/uevent r,
  owner /{dev,run}/shm/shmfd-* rw,
  owner /{dev,run}/shm/org.chromium.* rw,
  deny /dev/dri/** rwklx,

  # Silence denial logs about permissions we don't need
  deny /dev/dri/   rwklx,
  deny @{HOME}/.cache/fontconfig/ rw,
  deny @{HOME}/.cache/fontconfig/** rw,
  deny @{HOME}/.config/gtk-2.0/ rw,
  deny @{HOME}/.config/gtk-2.0/** rw,
  deny @{PROC}/@{pid}/net/route r,
  deny /sys/devices/system/cpu/cpufreq/policy[0-9]*/cpuinfo_max_freq r,
  deny /sys/devices/system/cpu/*/cache/index[0-9]*/size r,
  deny capability sys_admin,
  deny /usr/lib/firefox*/{crashreporter,pingsender} rx,
  deny @{sys}/bus/pci/devices/ r,
  deny /usr/bin/lsb_release rx,
  deny @{system_share_dirs}/applications/{,**} r,
  deny @{HOME}/Desktop/ w,
  deny @{HOME}/.cache/thumbnails/{,**} rw,
  deny @{HOME}/.local/{,**} rw,
  
  # Silence denial logs about PulseAudio
  deny /etc/pulse/client.conf r,
  deny /usr/bin/pulseaudio x,

  # KDE 4
  owner @{HOME}/.kde/share/config/* r,

  # Xfce4
  /etc/xfce4/defaults.list r,
  /usr/share/xfce4/applications/ r,

  owner /usr/lib/firefox/fonts/** rw,
  owner /usr/share/fonts/** rw,
  
  # Proxychains
  /etc/proxychains4.conf r,
  /etc/proxychains.conf r,

}

```

I see nothing strange in the abstractions and I have no idea why firefox doesn't read the apparmor permissions I gave to read proxychains4.conf. At the end I tried to move the line with read permission right under "/usr/bin/firefox {" in the apparmor profile. Didn't work.

What I'm doing wrong?


ps: "You shouldn't use tor with firefox" or "Use this application/extension to use proxies on firefox".
I don't use tor with firefox and I know about other applications. They can't do what I'm looking for.

---

### Post by vbgf3 on 2022-08-14
Did you do a 'sudo apparmor_parser -r <firefox profile> to activate the profile ?

---

