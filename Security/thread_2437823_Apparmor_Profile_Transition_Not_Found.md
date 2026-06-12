---
title: "Apparmor Profile Transition Not Found"
date: 2020-03-01
forum: Security
---

### Post by Magnusmaster on 2020-03-01
I wrote the following profile for /usr/bin/atril:

```
# Last Modified: Sun Mar  1 14:16:31 2020
#include <tunables/global>

/usr/bin/atril {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session-strict>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>

  /etc/fstab r,
  @{HOME}/photorec.ses r,
  /lib/x86_64-linux-gnu/ld-*.so mr,
  /usr/bin/atril mr,
  /usr/bin/caja-sendto cx,
  /usr/bin/caja-sendto mr,
  /usr/bin/yelp cx,
  /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitNetworkProcess cx,
  /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess cx,
  /usr/share/applications/mate-mimeapps.list r,
  /usr/share/atril/icons/ r,
  /usr/share/atril/icons/hicolor/*/actions/ r,
  /usr/share/atril/icons/hicolor/*/mimetypes/ r,
  /usr/share/mate/applications/ r,
  /usr/share/mate/applications/** r,
  /usr/share/poppler/** r,
  @{HOME}/.selected_editor r,
  @{HOME}/.wget-hsts r,
  owner /run/user/*/dconf/user rw,
  owner @{HOME}/ r,
  owner @{HOME}/**/.goutputstream-* rw,
  owner @{HOME}/**/[^.]* rw,
  owner @{HOME}/.bash_history r,
  owner @{HOME}/.dmrc r,
  owner @{HOME}/.goutputstream-* rw,
  owner @{HOME}/.install4j r,
  owner @{HOME}/.lesshst r,
  owner @{HOME}/.local/share/webkitgtk/databases/indexeddb/v* w,
  owner @{HOME}/.local/share/webkitgtk/deviceidhashsalts/*/ r,
  owner @{HOME}/.nvidia-settings-rc r,
  owner @{HOME}/.profile r,
  owner @{HOME}/.xinputrc r,
  owner @{HOME}/.xsession-errors r,
  owner @{HOME}/[^.]* r,
  owner @{HOME}/[^.]* rw,
  owner @{HOME}/[^.]* rw,
  owner @{PROC}/*/cmdline r,
  owner @{PROC}/*/fd/ r,
  owner @{PROC}/*/mountinfo r,
  owner @{PROC}/*/statm r,


  profile /usr/bin/caja-sendto {
    #include <abstractions/audio>
    #include <abstractions/base>
    #include <abstractions/dbus-session-strict>
    #include <abstractions/gnome>

    /lib/x86_64-linux-gnu/ld-*.so mr,
    /usr/bin/caja-sendto mr,
    /usr/share/applications/mate-mimeapps.list r,
    /usr/share/caja-extensions/caja-sendto.ui r,
    /usr/share/mate/applications/ r,
    /usr/share/mate/applications/defaults.list r,
    owner /run/user/*/dconf/user rw,
    owner @{HOME}/.Xauthority r,
    owner @{HOME}/.cache/event-sound-cache.tdb.* rwk,
    owner @{HOME}/.config/dconf/user r,

  }

  profile /usr/bin/yelp {
    #include <abstractions/base>
    #include <abstractions/cups-client>
    #include <abstractions/dbus-strict>
    #include <abstractions/freedesktop.org>
    #include <abstractions/gnome>

    /lib/x86_64-linux-gnu/ld-*.so mr,
    /usr/bin/yelp mr,
    /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess cx,
    /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess mr,
    /usr/share/fonts/** r,
    /usr/share/gnome/help/** r,
    /usr/share/help/C/ r,
    /usr/share/help/C/update-manager/index.docbook r,
    /usr/share/help/es/ r,
    /usr/share/xml/docbook/schema/dtd/** r,
    /usr/share/xml/entities/xml-iso-entities-*/*.ent r,
    /usr/share/yelp-xsl/** r,
    /usr/share/yelp/** r,
    @{PROC}/meminfo r,
    owner @{HOME}/.config/yelp/** r,
    owner @{HOME}/.local/share/webkitgtk/deviceidhashsalts/*/ r,
    owner @{HOME}/.config/dconf/user r,
    owner /proc/*/statm r,
    owner /run/user/*/bus rw,
    owner /run/user/*/dconf/user rw,
    owner @{HOME}/.Xauthority r,

  }

  profile /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitNetworkProcess {
    #include <abstractions/base>
    #include <abstractions/dbus-session-strict>
    #include <abstractions/dbus-strict>

    network netlink raw,

    /lib/x86_64-linux-gnu/ld-*.so mr,
    /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitNetworkProcess mr,
    owner @{HOME}/ r,
    owner @{HOME}/**/[^.]* r,
    owner @{HOME}/.local/share/gvfs-metadata/home r,
    owner @{HOME}/.local/share/gvfs-metadata/home-*.log r,
    owner @{HOME}/[^.]* r,
    owner @{PROC}/*/statm r,

  }

  profile /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess {
    #include <abstractions/base>
    #include <abstractions/gnome>
    #include <abstractions/gstreamer>

    /dev/ r,
    /lib/x86_64-linux-gnu/ld-*.so mr,
    /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess mr,
    owner /run/user/*/bus rw,
    owner /run/user/*/dconf/user rw,
    owner @{HOME}/ r,
    owner @{HOME}/**/[^.]* r,
    owner @{HOME}/.Xauthority r,
    owner @{HOME}/.cache/gstreamer-1.0/registry.x86_64.bin r,
    owner @{HOME}/.config/dconf/user r,
    owner @{HOME}/.local/share/gvfs-metadata/home r,
    owner @{HOME}/.local/share/gvfs-metadata/home-*.log r,
    owner @{HOME}/[^.]* r,
    owner @{PROC}/*/cmdline r,
    owner @{PROC}/*/statm r,

  }
}
```

However, when I load this profile in enforce mode, I get this audit error, despite having the /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess cx rule which should allow it. aa-logprof does not suggest anything to fix it. Any help?
```

Mar  1 15:35:44 myname kernel: [ 7957.320647] audit: type=1400 
audit(1583087744.345:1257): apparmor="DENIED" operation="exec" 
info="profile transition not found" error=-13 
profile="/usr/bin/atril///usr/bin/yelp" 
name="/usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess" 
pid=12373 comm="yelp" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0 
target="/usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess"
```

---

### Post by EuclideanCoffee on 2020-03-01
Before I suggest troubleshooting, did you write the profile as a stand alone or manually?

Generating extensively would be my first step.

[https://doc.opensuse.org/documentation/leap/archive/42.3/security/html/book.security/cha.apparmor.commandline.html#sec.apparmor.commandline.profiling.stand-alone](https://doc.opensuse.org/documentation/leap/archive/42.3/security/html/book.security/cha.apparmor.commandline.html#sec.apparmor.commandline.profiling.stand-alone)

---

### Post by Magnusmaster on 2020-03-01
I used aa-logprof to write the profile but with a lot of manual corrections.

---

### Post by Watonga on 2020-03-18
I tried making an Atril profile based on the Evince profile that comes with AppArmor, but I was getting errors in kern.log similar to yours, related to /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess. These four lines seemed to fix the problem for me:

```

  /lib/x86_64-linux-gnu/ld-2.28.so r,
  /etc/ld.so.preload r,
  /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitNetworkProcess ixr,
  /usr/lib/x86_64-linux-gnu/webkit2gtk-4.0/WebKitWebProcess ixr,
```

---

