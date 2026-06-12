---
title: "Need Assistance with AppArmor Profiling Issue"
date: 2012-03-21
forum: Security
---

### Post by sktd on 2012-03-21
I’m  profiling Firefox11. I can never get it to work, in enforce mode,  without problems. I keep running it, then running aa-logprof to make  corrections to the profile. Then I go into Edit A Profile (in YaST) to  look at the changes and I see some weird entries at the beginning of the  profile. They are as follows:
  
[+] ^null-15
[+] ^null-1e
[+] ^null-27
[+] ^null-32
[+] ^null-d
  
And  it keeps making these things. I think this is why I keep having  problems. Each time it creates one of the entries, it has a new name. I  thought I’d try highlighting the first entry ([+] ^null-15) and doing an  edit of the entry and set it to [+] ^null-*, but when I highlighted the  entry and clicked the Edit Entry button, it was like it took me into  another file that was full of entries of its own.
  
Any idea on what I can do to resolve this?

---

### Post by oklokl on 2012-03-21
bug[URL="http://www.makelinux.net/man/5/A/apparmor.d"]..
[/URL]
[URL="http://www.makelinux.net/man/5/A/apparmor.d"]
[/URL]
[http://www.makelinux.net/man/5/A/apparmor.d](http://www.makelinux.net/man/5/A/apparmor.d)


[http://en.opensuse.org/SDB:AppArmor_geeks](http://en.opensuse.org/SDB:AppArmor_geeks)


[http://ubuntuforums.org/showthread.php?t=1941480](http://ubuntuforums.org/showthread.php?t=1941480)


[http://ubuntuforums.org/showthread.php?t=1380553](http://ubuntuforums.org/showthread.php?t=1380553)



sudo -i

sudo apt-get install apparmor-utils apparmor-profiles

usr.bin.firefox

cp -rf /etc/apparmor.d/usr.bin.firefox /home/*/Download
chown -Rh *User_Name* /home/*/Download

/home/*/Download/usr.bin.firefox ->gedit

echo "" > /etc/apparmor.d/usr.bin.firefox
cat /home/*/Download/usr.bin.firefox > /etc/apparmor.d/usr.bin.firefox

sudo aa-enforce usr.bin.firefox

sudo /etc/init.d/apparmor restart


```
# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

# We want to confine the binaries that match:
#  /usr/lib/firefox-11.0/firefox
#  /usr/lib/firefox-11.0/firefox
# but not:
#  /usr/lib/firefox-11.0/firefox.sh
/usr/lib/firefox-11.0/firefox{,*[^s][^h]} {
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
  deny /usr/lib/firefox-11.0/** w,
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
  /usr/lib/firefox-11.0/** ixr,
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

  deny /usr/lib/firefox-11.0/update.test w,
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


null-* r,
null-* rw,
null-* rm,
null-* ra,
null-* w,
null-* a,
null-* m,

---

