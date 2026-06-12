---
title: "Why does this Chrome Apparmor profile not block downloads?"
date: 2011-11-03
forum: Security
---

### Post by Azrael84 on 2011-11-03
Hi,

I'm trying to set up a chrome apparmor profile based on another one I found by Jamie Strandboge (or maybe was already installed):

```

# Author: Jamie Strandboge <jamie@canonical.com>
#include <tunables/global>

/usr/lib/chromium-browser/chromium-browser {
  
  
  #include <abstractions/dbus-session>
  #include <abstractions/nameservice>
  #include <abstractions/cups-client>
  #include <abstractions/base>
  #include <abstractions/audio>
  #include <abstractions/fonts>



  # This include specifies which ubuntu-browsers.d abstractions to use. Eg, if
  # you want access to productivity applications, adjust the following file
  # accordingly.
  #include <abstractions/ubuntu-browsers.d/chromium-browser>

  # Networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # Should maybe be in abstractions
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/xdg/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,

  @{PROC}/[0-9]*/fd/ r,
  @{PROC}/filesystems r,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,

  # Newer chromium needs these now

   /sys/devices/pci[0-9]*/[0-9]*/class r,
  /sys/devices/pci[0-9]*/[0-9]*/device r,
  /sys/devices/pci[0-9]*/[0-9]*/irq r,
  /sys/devices/pci[0-9]*/[0-9]*/resource r,
  /sys/devices/pci[0-9]*/[0-9]*/vendor r,

   #added by me since it seems the above now changed:
  /sys/devices/pci[0-9]*/[0-9]*/[0-9]*/class r,
  /sys/devices/pci[0-9]*/[0-9]*/[0-9]*/device r,
  /sys/devices/pci[0-9]*/[0-9]*/[0-9]*/irq r,
  /sys/devices/pci[0-9]*/[0-9]*/[0-9]*/resource r,
  /sys/devices/pci[0-9]*/[0-9]*/[0-9]*/vendor r,

  # Needed for the crash reporter
  owner @{PROC}/[0-9]*/auxv r,

  # chromium mmaps all kinds of things for speed.
  /etc/passwd m,
  /usr/share/fonts/truetype/**/*.tt[cf] m,
  /usr/share/fonts/**/*.pfb m,
  /usr/share/mime/mime.cache m,
  /usr/share/icons/**/*.cache m,
  owner /{dev,run}/shm/pulse-shm* m,
  owner @{HOME}/.local/share/mime/mime.cache m,
  owner /tmp/** m,

  @{PROC}/sys/kernel/shmmax r,
  owner /{dev,run}/shm/{,.}org.chromium.* mrw,

  /usr/lib/chromium-browser/*.pak mr,
  /usr/lib/chromium-browser/locales/* mr,

  # Noisy
  deny /usr/lib/chromium-browser/** w,

  # Make browsing directories work
  #/ r,
  #/**/ r,
  #Instead of all this I think to open I just need:
  /etc/chromium-browser/policies/recommended/ r,
  /sys/bus/pci/devices/ r,
  /etc/chromium-browser/policies/managed/ r,
  /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,
  

  # Allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/{include,share,src}** r,

   

  # Helpers
  /usr/bin/xdg-open ixr,
  /usr/bin/gnome-open ixr,
  /usr/bin/gvfs-open ixr,
  # TODO: kde, xfce

  # Importing firefox settings (requires 'r' access to @{HOME}/.mozilla/**
  # which is provided by abstractions/ubuntu-browsers.d/user-files).
  #@{PROC}/[0-9]*/oom_adj w,
  #/etc/firefox/profile/bookmarks.html r,
  #owner @{HOME}/.mozilla/** k,

  # Chromium configuration
  owner @{HOME}/.pki/nssdb/* rwk,
  owner @{HOME}/.cache/chromium/ rw,
  owner @{HOME}/.cache/chromium/** rw,
  owner @{HOME}/.cache/chromium/Cache/* mr,
  owner @{HOME}/.config/chromium/ rw,
  owner @{HOME}/.config/chromium/** rwk,
  owner @{HOME}/.config/chromium/**/Cache/* mr,
  owner @{HOME}/.config/chromium/Dictionaries/*.bdic mr,
  owner @{HOME}/.config/chromium/**/Dictionaries/*.bdic mr,

  # Allow transitions to ourself and our sandbox
  /usr/lib/chromium-browser/chromium-browser ix,
  /usr/lib/chromium-browser/chromium-browser-sandbox cx -> chromium_browser_sandbox,

  # TODO: child profile
  /bin/ps Uxr,
  /usr/lib/chromium-browser/xdg-settings Ux,
  /usr/bin/xdg-settings Ux,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.chromium-browser>

profile chromium_browser_sandbox {
    # Be fanatical since it is setuid root and don't use an abstraction
    /lib/libgcc_s.so* mr,
    /lib{,32,64}/libm-*.so* mr,
    /lib/@{multiarch}/libm-*.so* mr,
    /lib{,32,64}/libpthread-*.so* mr,
    /lib/@{multiarch}/libpthread-*.so* mr,
    /lib{,32,64}/libc-*.so* mr,
    /lib/@{multiarch}/libc-*.so* mr,
    /lib{,32,64}/libld-*.so* mr,
    /lib/@{multiarch}/libld-*.so* mr,
    /lib{,32,64}/ld-*.so* mr,
    /lib/@{multiarch}/ld-*.so* mr,
    /lib/tls/*/{cmov,nosegneg}/libm-*.so* mr,
    /lib/tls/*/{cmov,nosegneg}/libpthread-*.so* mr,
    /lib/tls/*/{cmov,nosegneg}/libc-*.so* mr,
    /usr/lib/libstdc++.so* mr,
    /etc/ld.so.cache r,

    # Required for dropping into PID namespace. Keep in mind that until the
    # process drops this capability it can escape confinement, but once it
    # drops CAP_SYS_ADMIN we are ok.
     capability sys_admin,

    # All of these are for sanely dropping from root and chrooting
    capability chown,
    capability fsetid,
    capability setgid,
    capability setuid,
    capability dac_override,
    capability sys_chroot,

    # *Sigh*
    capability sys_ptrace,

    @{PROC}/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/[0-9]*/oom_adj w,

    /usr/bin/chromium-browser r,
    /usr/lib/chromium-browser/chromium-browser Px,
    /usr/lib/chromium-browser/chromium-browser-sandbox r,

    #owner /tmp/** rw,
  }
}

```I've deleted or hashed out all references I could find to allowing access to download folder etc yet I can still save an image there no problem, I don't even see reference to this event in syslog either. I know this profile is in enforce mode however because if I tweak it too hard chrome stops loading alltogether. Could be something to do with the capabilitys?  I dont understand what these are doing...

I want no downloads/uploads whatsoever on this profile and the ability to call no programs like torrents/pdfreaders or anything like that...

---

### Post by Blutkoete on 2011-11-03
I'm learning apparmor myself at the moment, but the included

```
#include <abstractions/ubuntu-browsers.d/chromium-browser>
```

includes again

```
user-files
```

which appears to grant write access to the user's home folder.

---

### Post by Azrael84 on 2011-11-03
Thanks for the reply, but if I remove that chrome wont load at all, is there something else I can do?

---

