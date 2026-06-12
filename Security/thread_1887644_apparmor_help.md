---
title: "apparmor help"
date: 2011-11-27
forum: Security
---

### Post by BigCityCat on 2011-11-27
Having problems setting up apparmor profile for firefox. I used sudo aa-genprof firefox. I start the process. Open firefox do all the things I want. Then close firefox. Press S for Scan in the terminal. Allow what I want. Then Save and Finnish. Reload profiles and enforce firefox. Firefox won't open unless I stop apparmor or sudo genprof again. Not sure what I am doing wrong.

---

### Post by Dangertux on 2011-11-27
> **BigCityCat said:**
> Having problems setting up apparmor profile for firefox. I used sudo aa-genprof firefox. I start the process. Open firefox do all the things I want. Then close firefox. Press S for Scan in the terminal. Allow what I want. Then Save and Finnish. Reload profiles and enforce firefox. Firefox won't open unless I stop apparmor or sudo genprof again. Not sure what I am doing wrong.


Generally speaking Firefox is one of the most difficult profiles to generate. It is a very complicated application that demands access to a lot of things.

There is a default profile included for Firefox in /etc/apparmor.d/usr.bin.firefox


in the event you hosed that profile by generating a new one here is a copy of the default Firefox 7.0.1 profile that comes with 11.10. I would recommend making changes to this as opposed to generating a new profile entierly.

```

# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

# We want to confine the binaries that match:
#  /usr/lib/firefox-7.0.1/firefox
#  /usr/lib/firefox-7.0.1/firefox
# but not:
#  /usr/lib/firefox-7.0.1/firefox.sh
/usr/lib/firefox-7.0.1/firefox{,*[^s][^h]} {
  #include <abstractions/audio>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>

  # Addons
  #include <abstractions/ubuntu-browsers.d/firefox>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
  /usr/share/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner /tmp/** m,
  owner /var/tmp/** m,
  /tmp/.X[0-9]*-lock r,

  /etc/timezone r,
  /etc/wildmidi/wildmidi.cfg r,

  # firefox specific
  /etc/firefox*/ r,
  /etc/firefox*/** r,
  /etc/xul-ext/** r,
  /etc/xulrunner-2.0*/ r,
  /etc/xulrunner-2.0*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-7.0.1/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,
  deny /var/cache/fontconfig/ w,
  deny @{HOME}/.local/share/recently-used.xbel r,

  # TODO: investigate
  deny /usr/bin/gconftool-2 x,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-7.0.1/** ixr,
  /usr/bin/basename ixr,
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  /usr/bin/tr ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/mountinfo r,
  @{PROC}/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/task/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,
  owner @{HOME}/.thumbnails/*/*.png r,

  /etc/mtab r,
  /etc/fstab r,

  # Needed for the crash reporter
  owner @{PROC}/[0-9]*/environ r,
  owner @{PROC}/[0-9]*/auxv r,
  /etc/lsb-release r,
  /usr/bin/expr ix,
  /sys/devices/system/cpu/ r,
  /sys/devices/system/cpu/** r,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # per-user firefox configuration
  owner @{HOME}/.{firefox,mozilla}/ rw,
  owner @{HOME}/.{firefox,mozilla}/** rw,
  owner @{HOME}/.{firefox,mozilla}/**/*.{db,parentlock,sqlite}* k,
  owner @{HOME}/.{firefox,mozilla}/plugins/** rm,
  owner @{HOME}/.{firefox,mozilla}/**/plugins/** rm,
  owner @{HOME}/.config/ibus/bus/ w,
  owner @{HOME}/.gnome2/firefox*-bin-* rw,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny /usr/lib/firefox-7.0.1/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  # Miscellaneous (to be abstracted)
  /usr/bin/mkfifo Uxr,    # TODO: investigate
  /bin/ps Uxr,        # TODO: child profile
  /bin/uname Uxr,    # TODO: child profile

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.firefox>
}

```

Hope this helps.

---

### Post by BigCityCat on 2011-11-27
> **Dangertux said:**
> Generally speaking Firefox is one of the most difficult profiles to generate. It is a very complicated application that demands access to a lot of things.

There is a default profile included for Firefox in /etc/apparmor.d/usr.bin.firefox


in the event you hosed that profile by generating a new one here is a copy of the default Firefox 7.0.1 profile that comes with 11.10. I would recommend making changes to this as opposed to generating a new profile entierly.

```

# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

# We want to confine the binaries that match:
#  /usr/lib/firefox-7.0.1/firefox
#  /usr/lib/firefox-7.0.1/firefox
# but not:
#  /usr/lib/firefox-7.0.1/firefox.sh
/usr/lib/firefox-7.0.1/firefox{,*[^s][^h]} {
  #include <abstractions/audio>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>

  # Addons
  #include <abstractions/ubuntu-browsers.d/firefox>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
  /usr/share/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner /tmp/** m,
  owner /var/tmp/** m,
  /tmp/.X[0-9]*-lock r,

  /etc/timezone r,
  /etc/wildmidi/wildmidi.cfg r,

  # firefox specific
  /etc/firefox*/ r,
  /etc/firefox*/** r,
  /etc/xul-ext/** r,
  /etc/xulrunner-2.0*/ r,
  /etc/xulrunner-2.0*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-7.0.1/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,
  deny /var/cache/fontconfig/ w,
  deny @{HOME}/.local/share/recently-used.xbel r,

  # TODO: investigate
  deny /usr/bin/gconftool-2 x,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-7.0.1/** ixr,
  /usr/bin/basename ixr,
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  /usr/bin/tr ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/mountinfo r,
  @{PROC}/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/task/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,
  owner @{HOME}/.thumbnails/*/*.png r,

  /etc/mtab r,
  /etc/fstab r,

  # Needed for the crash reporter
  owner @{PROC}/[0-9]*/environ r,
  owner @{PROC}/[0-9]*/auxv r,
  /etc/lsb-release r,
  /usr/bin/expr ix,
  /sys/devices/system/cpu/ r,
  /sys/devices/system/cpu/** r,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # per-user firefox configuration
  owner @{HOME}/.{firefox,mozilla}/ rw,
  owner @{HOME}/.{firefox,mozilla}/** rw,
  owner @{HOME}/.{firefox,mozilla}/**/*.{db,parentlock,sqlite}* k,
  owner @{HOME}/.{firefox,mozilla}/plugins/** rm,
  owner @{HOME}/.{firefox,mozilla}/**/plugins/** rm,
  owner @{HOME}/.config/ibus/bus/ w,
  owner @{HOME}/.gnome2/firefox*-bin-* rw,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny /usr/lib/firefox-7.0.1/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  # Miscellaneous (to be abstracted)
  /usr/bin/mkfifo Uxr,    # TODO: investigate
  /bin/ps Uxr,        # TODO: child profile
  /bin/uname Uxr,    # TODO: child profile

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.firefox>
}

```

Hope this helps.

Okay but the version of firefox now is currently 8.0. Is that a problem? Also can you tell me the process I would use to allow citrix through the default profile? Do I put firefox into complain mode then use it for a while then put it into enforce mode? Not sure how to do it.

---

### Post by Dangertux on 2011-11-27
> **BigCityCat said:**
> Okay but the version of firefox now is currently 8.0. Is that a problem? Also can you tell me the process I would use to allow citrix through the default profile? Do I put firefox into complain mode then use it for a while then put it into enforce mode? Not sure how to do it.

Not sure if the version is different  for 8 than 7.0.1 -- however the profile is installed with Firefox, if it is hosed (you should verify that first). You can reinstall the profile by reinstalling Firefox.

That being said about the citrix question it is highly dependent on your configuration, you may have to create a hat for Citrix you may not. But generally putting the profile into complain mode then debugging it is the best way to go for complicated applications. 

If you haven't checked this out you should -- it's very helpful for creating Apparmor profiles : [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by BigCityCat on 2011-11-27
I was able to get back to the default firefox 8 profile but I need help allowing citrix webclient firefox plugin though apparmor.

---

### Post by BigCityCat on 2011-11-27
> **Dangertux said:**
> Not sure if the version is different  for 8 than 7.0.1 -- however the profile is installed with Firefox, if it is hosed (you should verify that first). You can reinstall the profile by reinstalling Firefox.

That being said about the citrix question it is highly dependent on your configuration, you may have to create a hat for Citrix you may not. But generally putting the profile into complain mode then debugging it is the best way to go for complicated applications. 

If you haven't checked this out you should -- it's very helpful for creating Apparmor profiles : [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

okay I will take a look at it. I was able to get citrix working before by doing sudo aa-genprof firefox but when firefox was updated to 8 citrix stopped working and the way I used the first time is not working anymore.

---

### Post by BigCityCat on 2011-11-27
apparmor sucks lol. Really dont want to read a manual to figure it out.

---

### Post by Dangertux on 2011-11-27
> **BigCityCat said:**
> apparmor sucks lol. Really dont want to read a manual to figure it out.

If you post the original way you had it, it might help.

---

