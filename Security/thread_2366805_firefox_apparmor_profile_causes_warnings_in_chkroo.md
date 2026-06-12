---
title: "firefox apparmor profile causes warnings in chkrootkit, why?"
date: 2017-07-22
forum: Security
---

### Post by thehighhat-q on 2017-07-22
I modifed the usr.bin.firefox apparmor profile to further lock down firefox.

Some mods might be incorrect, but for the most part it prevents firefox from getting access to stuff it does not need.

But oddly enough, when set to enforce, whenever chkrootkit is run, the chkutmp displays a bunch of unprintable characters.

so... here is the apparmor profile.  what is wrong here?    why would it cause chkrootkit to complain?  thoughts?

```

# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

# Declare an apparmor variable to help with overrides
@{MOZ_LIBDIR}=/usr/lib/firefox

#include <tunables/global>

# We want to confine the binaries that match:
#  /usr/lib/firefox/firefox
#  /usr/lib/firefox/firefox
# but not:
#  /usr/lib/firefox/firefox.sh
/usr/lib/firefox/firefox{,*[^s][^h]} {
  #include <abstractions/audio>
  #include <abstractions/cups-client>
  # TODO: finetune this for required accesses
  #include <abstractions/dbus>
  #include <abstractions/dbus-accessibility>
  #include <abstractions/dbus-session>
  #include <abstractions/gnome>
  #include <abstractions/ibus>
  #include <abstractions/nameservice>
  #include <abstractions/openssl>
  #include <abstractions/p11-kit>

  # Addons

###  disabling defaults; too many locations
###  #include <abstractions/ubuntu-browsers.d/firefox>

  # for networking
  network inet stream,
### requires network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
### disable network inet6 routing
### @{PROC}/[0-9]*/net/ipv6_route r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/wireless r,

  # should maybe be in abstractions
###  disable global reading  /etc
###  /etc/ r,
  /etc/mime.types r,
###  disable 
deny /etc/mailcap r,
  /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
  /etc/xfce4/defaults.list r,
  /usr/share/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner /tmp/** m,
  owner /var/tmp/** m,
  owner /{,var/}run/shm/shmfd-* rw,
  /tmp/.X[0-9]*-lock r,
  /etc/udev/udev.conf r,
  # Doesn't seem to be required, but noisy. Maybe allow 'r' for 'b*' if needed.
  # Possibly move to an abstraction if anything else needs it.

### disable device file access
###  deny /run/udev/data/** r,

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
  deny @{MOZ_LIBDIR}/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,
  deny /var/cache/fontconfig/ w,
  deny @{HOME}/.local/share/recently-used.xbel r,
### disable user 
deny @{HOME}/.local/share/gvfs-metadata/home r,

  # TODO: investigate
  deny /usr/bin/gconftool-2 x,

  # These are needed when a new user starts firefox and firefox.sh is used
  @{MOZ_LIBDIR}/** ixr,
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
  @{PROC}/sys/vm/overcommit_memory r,
  /sys/devices/pci[0-9]*/**/uevent r,
### disable system device iteration
deny /sys/devices/pci[0-9]*/**/config r,
  /sys/devices/platform/**/uevent r,
  /sys/devices/pci*/**/{busnum,idVendor,idProduct} r,

### no 
deny /usr/bin/nvidia* rx,
deny @{PROC}/modules r,
deny @{PROC}/*/net/arp mrw,

###  why does ff want this?
###  /etc/mtab r,
###  /etc/fstab r,

  # Needed for the crash reporter
### reject access to these
###  owner @{PROC}/[0-9]*/environ r,
###  owner @{PROC}/[0-9]*/auxv r,
###  /etc/lsb-release r,
###  /usr/bin/expr ix,
###  /sys/devices/system/cpu/ r,
  /sys/devices/system/cpu/** r,

  # about:memory
  owner @{PROC}/[0-9]*/statm r,
  owner @{PROC}/[0-9]*/smaps r,

  # Needed for container to work in xul builds
### disable global plugins ; forgot why i did this
###  /usr/lib/xulrunner-*/plugin-container ixr,

  # allow access to documentation and other files the user may want to look
  # at in /usr and /opt
  /usr/ r,
  /usr/** r,
### stay out of local blobs 
###  /opt/ r,
###  /opt/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
### restrict user file access to only the Download folder
###  owner @{HOME}/ r,
###  owner @{HOME}/Public/ r,
###  owner @{HOME}/Public/* r,
deny @{HOME}/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # per-user firefox configuration
  owner @{HOME}/.{firefox,mozilla}/ rw,
  owner @{HOME}/.{firefox,mozilla}/** rw,
  owner @{HOME}/.{firefox,mozilla}/**/*.{db,parentlock,sqlite}* k,
  owner @{HOME}/.{firefox,mozilla}/plugins/** rm,
  owner @{HOME}/.{firefox,mozilla}/**/plugins/** rm,
  owner @{HOME}/.gnome2/firefox*-bin-* rw,
  owner @{HOME}/.cache/mozilla/{,firefox/} rw,
  owner @{HOME}/.cache/mozilla/firefox/** rw,
  owner @{HOME}/.cache/mozilla/firefox/**/*.sqlite k,
### too noisy
deny @{HOME}/.cache/* r,
deny  @{HOME}/**/*thumbnails*/** r,
deny  @{HOME}/.thumbnails/** r,
deny  @{HOME}/.config/gtk-3.0/ r,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny @{MOZ_LIBDIR}/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  # Miscellaneous (to be abstracted)
  # Ideally these would use a child profile. They are all ELF executables
  # so running with 'Ux', while not ideal, is ok because we will at least
  # benefit from glibc's secure execute.
### do not allow the system to be probed
###  /usr/bin/mkfifo Uxr,  # investigate
###  /bin/ps Uxr,
###  /bin/uname Uxr,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.firefox>

### fix broken renderer; ff will not start w/o this
owner /run/shm/org.chromium.* rw,

### dconf denied
deny /run/user/*/dconf/user rwx,
deny /home/*/.config/dconf/user rwx,

### deny access to these
deny /etc/passwd r,
deny /etc/group  r,

}

```

---

### Post by HermanAB on 2017-07-23
Well, why are you running chrootkit?  It is not particularly useful...

---

### Post by thehighhat-q on 2017-07-23
chkrootkit is in official repo.

it is a security tool described as being useful for identifying signs of a rootkit.

that being said, do you have any insights into why the contents of /var/run/utmp are affected by this firefox apparmor profile.

---

### Post by thehighhat2 on 2017-08-05
also want to point out that on debian 9, firefox does not trigger the same warnings.  although, chromium does.

Did some more digging.  Firefox ESR is very different under the hood that more common version.  Ubuntu does not use ESR.  The ESR builds to not have the same utmp behavior.

---

