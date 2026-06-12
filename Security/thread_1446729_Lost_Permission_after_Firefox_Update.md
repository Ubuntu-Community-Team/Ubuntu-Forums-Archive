---
title: "Lost Permission after Firefox Update"
date: 2010-04-04
forum: Security
---

### Post by donato roque on 2010-04-04
I am unable to open Firefox after recent update to 3.6.2.
I have apparmor in enforce mode for firefox. It works for ff3.6.
Running in terminal it says permission denied.
Anyone experiencing this?  I hate to disable apparmor.  Putting firefox to complain mode doesn't solve it. Thank you for any help.

To mods: Can you please transfer this thread to Security discussion>Apparmor Support Thread?

---

### Post by bodhi.zazen on 2010-04-04
Well, you first need to determine if it is a problem with apparmor.

So I advise you disable apparmor and try firefox from the command line.

If it works we need to look at your apparmor profile and we need more information on how you installed firefox.

If it does not work would you please post the exact error message ?

---

### Post by donato roque on 2010-04-04
When I disable apparmor firefox works.

So I run firefox with apparmor enabled now and this is the error message in the terminal:

> donato@donato-desktop:~$ firefox &
[1] 12228
donato@donato-desktop:~$ /usr/lib/firefox-3.6.2/firefox: 59: dirname: Permission denied
/usr/lib/firefox-3.6.2/firefox: 88: /bin/pwd: Permission denied
/usr/lib/firefox-3.6.2/run-mozilla.sh: 39: dirname: Permission denied
/usr/lib/firefox-3.6.2/firefox-bin: error while loading shared libraries: libxul.so: cannot open shared object file: No such file or directory

I installed firefox through the PPA when it prompted me for the update. ([http://ppa.launchpad.net//mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net//mozillateam/firefox-stable/ubuntu) karmic)

---

### Post by donato roque on 2010-04-04
This is my apparmor profile for firefox.

> # Last Modified: Thu Feb  4 20:42:33 2010
#include <tunables/global>

/usr/lib/firefox-3.6.*/firefox.sh {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/X>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # for sounds
  /etc/sound/ r,
  /etc/sound/** r,

  # firefox specific
  /etc/firefox-3.*/ r,
  /etc/firefox-3.*/** r,
  /etc/xulrunner-1.9*/ r,
  /etc/xulrunner-1.9*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-3.*/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-3.*/** ixr,
  /usr/bin/basename ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,
  capability sys_ptrace,

  /etc/mtab r,
  @{PROC}/[0-9]*/mounts r,
  @{PROC}/[0-9]*/maps r,
  
   # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # allow read and write to all user's files, except explicitly denied ones
  @{HOME}/ r,
  @{HOME}/** rw,
  @{HOME}/Desktop/** rw,
  @{HOME}/Firefox_wallpaper* rw,
  owner /media/** rw,
  owner /mnt/** rw,
  owner /srv/** rw,

  #include <abstractions/private-files>
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,

  # comment this out if using gpg plugin/addons
  audit deny @{HOME}/.gnupg/** mrwkl,

  # per-user firefox configuration
  @{HOME}/.mozilla/ rw,
  @{HOME}/.mozilla/** rw,
  @{HOME}/.mozilla/**/*.sqlite* k,
  @{HOME}/.mozilla/**/.parentlock k,
  @{HOME}/.mozilla/plugins/** rm,
  @{HOME}/.mozilla/**/plugins/** rm,

  # per-user common plugin configuration
  @{HOME}/.icedteaplugin/ rw,
  @{HOME}/.icedteaplugin/** rw,
  @{HOME}/.adobe/ rw,
  @{HOME}/.adobe/** rw,
  @{HOME}/.macromedia/ rw,
  @{HOME}/.macromedia/** rw,
  @{HOME}/.java/ rw,
  @{HOME}/.java/** rwk,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  @{HOME}/.mozilla/**/extensions/** mixr,

  deny /usr/lib/firefox-3.*/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,

  #
  # Plugins/helpers
  #
  @{PROC}/[0-9]*/fd/ r,
  /usr/lib/** rm,
  /bin/bash ixr,
  /bin/dash ixr,
  /bin/grep ixr,
  /bin/ps Uxr,
  /bin/uname Uxr,
  /usr/bin/m4 ixr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer Uxr,
  /var/lib/ r,
  /var/lib/** mr,

  # for maximum plugin/helper compatibility
  #/usr/bin/* Uxr,
  #/usr/lib/*/** ixr,

  #
  # For stricter access, comment out the 'maximum plugin/helper compatibility'
  # lines above and uncomment these
  #

  # evince has its own profile, so change to it
  /usr/bin/evince PUxr,

  # miscellaneous
  #/usr/bin/eog Uxr,
  /usr/bin/gedit Uxr,
  /usr/bin/gimp* Uxr,
  /usr/bin/file-roller Uxr,
  /usr/bin/ooffice Uxr,
  /usr/bin/oocalc Uxr,
  /usr/bin/oodraw Uxr,
  /usr/bin/ooimpress Uxr,
  /usr/bin/oowriter Uxr,
  /usr/bin/gtk-gnash ixr,
  /usr/bin/pulseaudio ixr,

  # totem
  /usr/lib/totem/** ixr,
  /usr/bin/totem-gstreamer Uxr,
  /usr/bin/totem-xine Uxr,
  /usr/bin/totem Uxr,

  # mozplugger
  /etc/mozpluggerrc r,
  /usr/bin/mozplugger-helper Uxr,

  # mplayer plugin
  /etc/mplayerplug-in.conf r,
  /usr/bin/mplayer Uxr,

  # java
  /usr/lib/jvm/java-6-openjdk/jre/bin/java Uxr,
  /etc/java-*-sun/** r,
  /usr/lib/jvm/java-*-sun-1.*/jre/bin/java Uxr,

  # for mailto:
  #include <abstractions/ubuntu-email>
  #include <abstractions/ubuntu-console-email>

  # Terminals for using console applications. These abstractions should ideally
  # have 'ix' to restrct access to what only firefox is allowed to do
  #include <abstractions/ubuntu-gnome-terminal>

  # By default, we won't support launching a terminal program in Xterm or
  # KDE's konsole. It opens up too many unnecessary files for most users.
  # People who need this functionality can uncomment the following:
  ##include <abstractions/ubuntu-xterm>
  ##include <abstractions/ubuntu-konsole>

Thank you.

---

### Post by bodhi.zazen on 2010-04-04
you will need to edit your apparmor profile.

The first few are easy, add

/bin/pwd ixr,

etc to your profile.

You can also use aa-logprof to help.

See the apparmor sticky.

Again, some of this will depend on how you installed firefox (from a ppa ? from mozilla ? )

You can look at my ff profile :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.firefox.firefox](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.firefox.firefox)

---

