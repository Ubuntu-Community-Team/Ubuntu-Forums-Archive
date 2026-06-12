---
title: "Help with xchat AppArmor Profile"
date: 2011-03-16
forum: Security
---

### Post by Soul-Sing on 2011-03-16
After changing xchat log-in, from nickserv ident to sasl via the cap sasl.pl. i am not able to create an apparmor profile for xchat 10.04.
In enforced mode xchat doesn't start.
the profile was based on a profile of bodhi:

# Bodhi.Zazen's current xchat profile
# Please note this for :
# Ubuntu 10.04

## Note: this profile was expanded to include 
## opening links in browsers
## firefox, icecat, chromium, and opera
## totem was included for multimedia

#include <tunables/global>
/usr/bin/xchat {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/ubuntu-gnome-terminal>
  #include <abstractions/nameservice>
  #include <abstractions/python>

  #include <abstractions/private-files>
  audit deny @{HOME}/.ssh/ mrwkl,
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/ mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,

  # comment this out if using gpg plugin/addons
  audit deny @{HOME}/.gnupg/ mrwkl,
  audit deny @{HOME}/.gnupg/** mrwkl,

  /bin/dash ixr,
  /bin/grep ixr,
  /bin/uname ixr,
  /bin/which ixr,
  /etc/chromium-browser/* r,
  /etc/firefox/** r,
  /etc/ld.so.cache r,
  /etc/mime.types r,
  /etc/mtab r,
  /etc/xul-ext/** r,
  /etc/xulrunner-1.9*/ r,
  /etc/xulrunner-1.9*/** r,
  /lib/libc*.so r,
  @{PROC}/filesystems r,
  @{PROC}/*/fd/ r,
  @{PROC}/*/maps r,
  @{PROC}/*/mounts r,
  owner @{HOME}/ r,
  owner @{HOME}/.config/enchant/ rw,
  owner @{HOME}/.config/enchant/* rwk,
  owner @{HOME}/.config/gnome2/** r,
  owner @{HOME}/.config/gnome2_private/** r
  owner @{HOME}/.icons/ r,
  owner @{HOME}/.local/share/** r,
  owner @{HOME}/.mozilla/ rw,  
  owner @{HOME}/.mozilla/** rw,  
  owner @{HOME}/.mozilla/firefox/*/*.sqlite rwk,
  owner @{HOME}/.mozilla/**/.parentlock k,
  owner @{HOME}/.mozilla/plugins/** rm,
  owner @{HOME}/.mozilla/**/plugins/** rm,
  owner @{HOME}/.xchat2/ rw,
  owner @{HOME}/.xchat2/** rw,
  /usr/bin/basename rix,
  /usr/bin/chromium-browser Pxr,
  /usr/bin/dirname ixr,
  /usr/bin/exo-open ixr,
  /usr/bin/expr ixr,
  /usr/bin/firefox Pxr,
  /usr/bin/gnome-open rix,
  /usr/bin/sensible-browser rix,
  /usr/bin/x-www-browser rix,
  /usr/lib/icecat/icecat Pxr,
  /usr/bin/launchpad-integration ixr,
  /usr/bin/opera Pxr,
  /usr/bin/sdg-open ixr,
  /usr/bin/xchat mr,
  /usr/bin/xdg-open ixr,
  /usr/bin/xprop ixr,
  /usr/lib/chromium-browser/* Pxr,
  /usr/lib/firefox-3.6.*/firefox* ixr,
  /usr/lib/gstreamer*/** rix,
  /usr/lib/libgst* mr,
  /usr/lib/libexo-0.3-0/exo-helper-0.3 Uxr,
  /usr/lib/lib*so* mr,
  /usr/lib/mozilla/extensions/** rw,
  /usr/lib/opera/* rixm,
  /usr/lib/totem/totem-plugin-viewer rix,
  /usr/lib/xchat/** mr,
  /usr/lib/xulrunner*/* rmix,
  /usr/share/** r,
  /usr/share/icons/** r,
  /var/lib/dbus/machine-id r,

}


I got in the complain mode: usr/lib/(perl) errors, usr/lib/xchat/perl.so and usr/lib/plugin/perl.so/la

---

### Post by bodhi.zazen on 2011-03-16
I moved your post as you did not post in a support thread.

You will need to post the exact error messages and edit the profile.

---

### Post by Soul-Sing on 2011-03-17
[tag]type=1502 audit(1300339035.125:212):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/File/Glob/Glob.so"
type=1502 audit(1300339035.129:213):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/List/Util/Util.so"
type=1502 audit(1300339035.160:214):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/Time/HiRes/HiRes.so"
type=1502 audit(1300339035.168:215):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/IO/IO.so"
type=1502 audit(1300339035.172:216):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/Fcntl/Fcntl.so"
type=1502 audit(1300339035.176:217):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/Storable/Storable.so"
type=1502 audit(1300339035.212:218):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl/5.10.1/auto/MIME/Base64/Base64.so"
type=1502 audit(1300339035.252:219):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl5/auto/Crypt/OpenSSL/Bignum/Bignum.so"
type=1502 audit(1300339035.336:220):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl5/auto/Math/BigInt/GMP/GMP.so"
type=1502 audit(1300339035.348:221):  operation="file_mmap" pid=3039 parent=1 profile="/usr/bin/xchat" requested_mask="::m" denied_mask="::m" fsuid=1000 ouid=0 name="/usr/lib/perl5/auto/Crypt/Blowfish/Blowfish.so"9[/tag]

---

### Post by rookcifer on 2011-03-17
Try adding this to the profile:

```
/usr/lib/perl* r,
/usr/lib/perl*/** mr,

```

If you still get errors, post back.

---

### Post by Soul-Sing on 2011-03-17
thank you very much, starting fine, no noise.

---

