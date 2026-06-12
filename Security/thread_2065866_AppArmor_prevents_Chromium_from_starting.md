---
title: "AppArmor prevents Chromium from starting"
date: 2012-10-03
forum: Security
---

### Post by Stonecold1995 on 2012-10-03
I currently have most of my AppArmor profiles on "complain" mode because they interfere with the actual operation of the program.  Especially with Chromium.  When I set the profile to enforce, Chromium simply won't load.  Here's the contents of the profile:
```
# Author: Jamie Strandboge <jamie@canonical.com>
#include <tunables/global>

# We need 'flags=(attach_disconnected)' in newer chromium versions
/usr/lib/chromium-browser/chromium-browser flags=(complain) {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  # This include specifies which ubuntu-browsers.d abstractions to use. Eg, if
  # you want access to productivity applications, adjust the following file
  # accordingly.
  #include <abstractions/ubuntu-browsers.d/chromium-browser>

  # Stuff to get OSSEC to shut the **** up
  /etc/localtime r,

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
  @{PROC}/[0-9]*/task/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/cmdline r,
  owner @{PROC}/[0-9]*/io r,
  owner @{PROC}/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/status r,

  # Newer chromium needs these now
  /sys/devices/pci[0-9]*/**/class r,
  /sys/devices/pci[0-9]*/**/device r,
  /sys/devices/pci[0-9]*/**/irq r,
  /sys/devices/pci[0-9]*/**/resource r,
  /sys/devices/pci[0-9]*/**/vendor r,

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
  / r,
  /**/ r,

  # Allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/{include,share,src}** r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # Helpers
  /usr/bin/xdg-open ixr,
  /usr/bin/gnome-open ixr,
  /usr/bin/gvfs-open ixr,
  /usr/bin/kde-open ixr,
  # TODO: kde (done?), xfce

  # Importing firefox settings (requires 'r' access to @{HOME}/.mozilla/**
  # which is provided by abstractions/ubuntu-browsers.d/user-files).
  @{PROC}/[0-9]*/oom_{,score_}adj w,
  /etc/firefox/profile/bookmarks.html r,
  owner @{HOME}/.mozilla/** k,

  # Chromium configuration
  owner @{HOME}/.pki/nssdb/* rwk,
  owner @{HOME}/.cache/chromium/ rw,
  owner @{HOME}/.cache/chromium/** rw,
  owner @{HOME}/.cache/chromium/Cache/* mr,
  owner @{HOME}/.config/chromium/ mrw,
  owner @{HOME}/.config/chromium/** mrwk,
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

profile chromium_browser_sandbox flags=(complain) {
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
    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/[0-9]*/oom_adj w,
    @{PROC}/[0-9]*/oom_score_adj w,
    @{PROC}/[0-9]*/task/[0-9]*/stat r,

    /usr/bin/chromium-browser r,
    /usr/lib/chromium-browser/chromium-browser Px,
    /usr/lib/chromium-browser/chromium-browser-sandbox r,

    owner /tmp/** rw,
  }
}

```

What do I have to change to allow Chromium to work with enforce mode on?

Also, where can I go to get AppArmor profiles for other applications (like VirtualBox)?

---

### Post by rookcifer on 2012-10-03
Run:

```
sudo aa-logprof
```

Then look at the entries related to Chromium and allow them,  Restart and see if it works.

---

### Post by Stonecold1995 on 2012-10-03
Here's some of the entries from syslog:
```
Oct  2 03:21:17 kubuntu kernel: [425135.489547] type=1400 audit(1349173277.164:402134): apparmor="ALLOWED" operation="exec" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser" name="/usr/bin/kdialog" pid=642 comm="Chrome_FileThre" requested_mask="x" denied_mask="x" fsuid=1000 ouid=0 target="/usr/lib/chromium-browser/chromium-browser//null-c2"
Oct  2 03:21:17 kubuntu kernel: [425135.502336] type=1400 audit(1349173277.180:402135): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/lib/chromium-browser/" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502357] type=1400 audit(1349173277.180:402136): apparmor="ALLOWED" operation="open" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/etc/ld.so.cache" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502370] type=1400 audit(1349173277.180:402137): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/etc/ld.so.cache" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502409] type=1400 audit(1349173277.180:402138): apparmor="ALLOWED" operation="open" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/lib/libkfile.so.4.9.1" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502424] type=1400 audit(1349173277.180:402139): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/lib/libkfile.so.4.9.1" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502438] type=1400 audit(1349173277.180:402140): apparmor="ALLOWED" operation="file_mmap" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/lib/libkfile.so.4.9.1" pid=642 comm="kdialog" requested_mask="mr" denied_mask="mr" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502506] type=1400 audit(1349173277.180:402141): apparmor="ALLOWED" operation="open" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/lib/libkio.so.5.9.1" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:17 kubuntu kernel: [425135.502521] type=1400 audit(1349173277.180:402142): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/lib/libkio.so.5.9.1" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.841553] audit_printk_skb: 17247 callbacks suppressed
Oct  2 03:21:22 kubuntu kernel: [425140.841556] type=1400 audit(1349173282.524:407892): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name=2F686F6D652F616C65782F50696374757265732F346368616E20286D697363292F pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Oct  2 03:21:22 kubuntu kernel: [425140.841594] type=1400 audit(1349173282.524:407893): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/share/mime/inode/directory.xml" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.841617] type=1400 audit(1349173282.524:407894): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name=2F686F6D652F616C65782F50696374757265732F346368616E20286D697363292F pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Oct  2 03:21:22 kubuntu kernel: [425140.841652] type=1400 audit(1349173282.524:407895): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/share/mime/inode/directory.xml" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.841678] type=1400 audit(1349173282.524:407896): apparmor="ALLOWED" operation="open" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/share/mime/inode/directory.xml" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.841691] type=1400 audit(1349173282.524:407897): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/share/mime/inode/directory.xml" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.841728] type=1400 audit(1349173282.524:407898): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/usr/share/mime/inode/directory.xml" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.850557] type=1400 audit(1349173282.536:407899): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/etc/localtime" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.884112] type=1400 audit(1349173282.568:407900): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/etc/localtime" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  2 03:21:22 kubuntu kernel: [425140.916514] type=1400 audit(1349173282.600:407901): apparmor="ALLOWED" operation="getattr" parent=8782 profile="/usr/lib/chromium-browser/chromium-browser//null-c2" name="/etc/localtime" pid=642 comm="kdialog" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

I tried fixing it a while back (giving /etc/localtime read permissions), but it didn't work.  Kdialog is repeated in every line apparently.  I tried fixing it by adding the bolded text to the profile, but that didn't work.
```
# Helpers
/usr/bin/xdg-open ixr,
/usr/bin/gnome-open ixr,
/usr/bin/gvfs-open ixr,
**/usr/bin/kde-open ixr,**
```

---

### Post by rookcifer on 2012-10-03
Try:

```
#include <abstractions/base>
```

Put that at the top of the profile.

Also add:

```
/usr/bin/kdialog ixr,
```

Somewhere in the profile.

EDIT: are you using the profile you pasted above?  If so, something isn't right.  Some of the entries in syslog should be covered by the "base" abstraction, which I why I ask.  You may also need to give access to some of the KDE libs, but you need to post me the actual profile you are using first.

---

### Post by 0011235813 on 2012-10-03
I experienced exactly the same problems with Chrome/Chromium: [http://ubuntuforums.org/showthread.php?t=2014663](http://ubuntuforums.org/showthread.php?t=2014663)
Apparently, Hungry Man has his working. I can't figure out for the life of me what I could be doing wrong. I'll check this thread to see if anyone has found a solution, but I doubt it.
In any case, the only advantage apparmor could give you over Chromium's built in sandboxing (as far as I'm aware) is to give you protection if Chromium somehow got root permissions, which is pretty unlikely (there haven't been any Linux exploits of this kind as far as I know).

---

### Post by Hungry Man on 2012-10-03
The benefit is confining the zygote setuid process.

My posted profile is for 64bit Chrome. 32bit needs access to separate librarieS.

---

### Post by Stonecold1995 on 2012-10-03
> **rookcifer said:**
> Try:

```
#include <abstractions/base>
```

Put that at the top of the profile.

Also add:

```
/usr/bin/kdialog ixr,
```

Somewhere in the profile.

EDIT: are you using the profile you pasted above?  If so, something isn't right.  Some of the entries in syslog should be covered by the "base" abstraction, which I why I ask.  You may also need to give access to some of the KDE libs, but you need to post me the actual profile you are using first.

It already has that. #include.  And yes, I'm using the profile pasted above.

I tried adding "/usr/bin/kdialog ixr,", but it didn't open.  Here's the entry from the syslog showing when I set the profile to enforce, tried (and failed) to open Chromium, set it back to complain, and successfully opened Chromium:
```
Oct  3 14:23:36 kubuntu kernel: [48753.157086] type=1400 audit(1349299416.800:77829): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser" pid=14478 comm="apparmor_parser"
Oct  3 14:23:36 kubuntu kernel: [48753.157533] type=1400 audit(1349299416.800:77830): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_java" pid=14478 comm="apparmor_parser"
Oct  3 14:23:36 kubuntu kernel: [48753.157954] type=1400 audit(1349299416.800:77831): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_openjdk" pid=14478 comm="apparmor_parser"
Oct  3 14:23:36 kubuntu kernel: [48753.158014] type=1400 audit(1349299416.800:77832): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" pid=14478 comm="apparmor_parser"
Oct  3 14:23:36 kubuntu kernel: [48753.158277] type=1400 audit(1349299416.800:77833): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//sanitized_helper" pid=14478 comm="apparmor_parser"
Oct  3 14:23:38 kubuntu kernel: [48755.139479] type=1400 audit(1349299418.784:77834): apparmor="DENIED" operation="open" parent=4633 profile="/usr/lib/chromium-browser/chromium-browser" name="/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq" pid=14479 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  3 14:23:38 kubuntu kernel: [48755.146450] type=1400 audit(1349299418.792:77835): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/dev/null" pid=14483 comm="chromium-browse" requested_mask="rw" denied_mask="rw" fsuid=0 ouid=0
Oct  3 14:23:38 kubuntu kernel: [48755.146788] type=1400 audit(1349299418.792:77836): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/proc/14483/status" pid=14483 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  3 14:23:57 kubuntu kernel: [48774.268809] type=1400 audit(1349299437.944:77837): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser" pid=14493 comm="apparmor_parser"
Oct  3 14:23:57 kubuntu kernel: [48774.269290] type=1400 audit(1349299437.944:77838): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_java" pid=14493 comm="apparmor_parser"
Oct  3 14:23:57 kubuntu kernel: [48774.269740] type=1400 audit(1349299437.944:77839): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_openjdk" pid=14493 comm="apparmor_parser"
Oct  3 14:23:57 kubuntu kernel: [48774.269802] type=1400 audit(1349299437.944:77840): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" pid=14493 comm="apparmor_parser"
Oct  3 14:23:57 kubuntu kernel: [48774.270083] type=1400 audit(1349299437.944:77841): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//sanitized_helper" pid=14493 comm="apparmor_parser"
Oct  3 14:23:59 kubuntu kernel: [48775.716332] type=1400 audit(1349299439.392:77842): apparmor="ALLOWED" operation="open" parent=4633 profile="/usr/lib/chromium-browser/chromium-browser" name="/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq" pid=14494 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  3 14:23:59 kubuntu kernel: [48775.721852] type=1400 audit(1349299439.400:77843): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/dev/null" pid=14498 comm="chromium-browse" requested_mask="rw" denied_mask="rw" fsuid=0 ouid=0
Oct  3 14:23:59 kubuntu kernel: [48775.722221] type=1400 audit(1349299439.400:77844): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/proc/14498/status" pid=14498 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  3 14:23:59 kubuntu kernel: [48775.723203] type=1400 audit(1349299439.400:77845): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/proc/1/status" pid=14498 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct  3 14:23:59 kubuntu kernel: [48775.723261] type=1400 audit(1349299439.400:77846): apparmor="ALLOWED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/proc/2/status" pid=14498 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

---

### Post by rookcifer on 2012-10-04
Add these:

```
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,
/dev/null rw,
/proc/[0-9]*/status r,
```

Then run: 

```
sudo apparmor_parser -r usr.bin.chromium-browser
```

Restart chrome and see if it opens.

---

### Post by Stonecold1995 on 2012-10-04
It didn't open.

```
Oct  4 04:06:23 kubuntu kernel: [98046.114532] type=1400 audit(1349348783.173:96608): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser" pid=10664 comm="apparmor_parser"
Oct  4 04:06:23 kubuntu kernel: [98046.114936] type=1400 audit(1349348783.173:96609): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_java" pid=10664 comm="apparmor_parser"
Oct  4 04:06:23 kubuntu kernel: [98046.115339] type=1400 audit(1349348783.173:96610): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_openjdk" pid=10664 comm="apparmor_parser"
Oct  4 04:06:23 kubuntu kernel: [98046.115396] type=1400 audit(1349348783.173:96611): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" pid=10664 comm="apparmor_parser"
Oct  4 04:06:23 kubuntu kernel: [98046.115639] type=1400 audit(1349348783.173:96612): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//sanitized_helper" pid=10664 comm="apparmor_parser"
Oct  4 04:07:12 kubuntu kernel: [98095.560272] type=1400 audit(1349348832.693:96613): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser" pid=10714 comm="apparmor_parser"
Oct  4 04:07:12 kubuntu kernel: [98095.560684] type=1400 audit(1349348832.693:96614): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_java" pid=10714 comm="apparmor_parser"
Oct  4 04:07:12 kubuntu kernel: [98095.561076] type=1400 audit(1349348832.693:96615): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_openjdk" pid=10714 comm="apparmor_parser"
Oct  4 04:07:12 kubuntu kernel: [98095.561132] type=1400 audit(1349348832.693:96616): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" pid=10714 comm="apparmor_parser"
Oct  4 04:07:12 kubuntu kernel: [98095.561371] type=1400 audit(1349348832.693:96617): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//sanitized_helper" pid=10714 comm="apparmor_parser"
Oct  4 04:07:14 kubuntu kernel: [98097.641960] type=1400 audit(1349348834.777:96618): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/dev/null" pid=10719 comm="chromium-browse" requested_mask="rw" denied_mask="rw" fsuid=0 ouid=0
Oct  4 04:07:14 kubuntu kernel: [98097.642268] type=1400 audit(1349348834.777:96619): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/proc/10719/status" pid=10719 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

---

### Post by rookcifer on 2012-10-04
OK, add the lines I provided you to the "chromium-sandbox" profile and see if that works.  That's the child profile near the bottom of the profile.

---

### Post by Stonecold1995 on 2012-10-04
> **rookcifer said:**
> OK, add the lines I provided you to the "chromium-sandbox" profile and see if that works.  That's the child profile near the bottom of the profile.

Didn't work.
```
Oct  4 15:59:13 kubuntu kernel: [140752.914566] type=1400 audit(1349391553.582:100911): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser" pid=26566 comm="apparmor_parser"
Oct  4 15:59:13 kubuntu kernel: [140752.914970] type=1400 audit(1349391553.582:100912): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_java" pid=26566 comm="apparmor_parser"
Oct  4 15:59:13 kubuntu kernel: [140752.915336] type=1400 audit(1349391553.582:100913): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//browser_openjdk" pid=26566 comm="apparmor_parser"
Oct  4 15:59:13 kubuntu kernel: [140752.915393] type=1400 audit(1349391553.582:100914): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" pid=26566 comm="apparmor_parser"
Oct  4 15:59:13 kubuntu kernel: [140752.915643] type=1400 audit(1349391553.586:100915): apparmor="STATUS" operation="profile_replace" name="/usr/lib/chromium-browser/chromium-browser//sanitized_helper" pid=26566 comm="apparmor_parser"
Oct  4 15:59:15 kubuntu kernel: [140755.078365] type=1400 audit(1349391555.750:100916): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox" name="/proc/26578/status" pid=26578 comm="chromium-browse" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
```

```
# Author: Jamie Strandboge <jamie@canonical.com>
#include <tunables/global>

# We need 'flags=(attach_disconnected)' in newer chromium versions
/usr/lib/chromium-browser/chromium-browser {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  # This include specifies which ubuntu-browsers.d abstractions to use. Eg, if
  # you want access to productivity applications, adjust the following file
  # accordingly.
  #include <abstractions/ubuntu-browsers.d/chromium-browser>

  # Stuff to get OSSEC to shut the **** up
  /etc/localtime r,
  /usr/bin/kdialog ixr,
  /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,

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
  @{PROC}/[0-9]*/task/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/cmdline r,
  owner @{PROC}/[0-9]*/io r,
  owner @{PROC}/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/status r,

  # Newer chromium needs these now
  /sys/devices/pci[0-9]*/**/class r,
  /sys/devices/pci[0-9]*/**/device r,
  /sys/devices/pci[0-9]*/**/irq r,
  /sys/devices/pci[0-9]*/**/resource r,
  /sys/devices/pci[0-9]*/**/vendor r,

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
  / r,
  /**/ r,

  # Allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/{include,share,src}** r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # Helpers
  /usr/bin/xdg-open ixr,
  /usr/bin/gnome-open ixr,
  /usr/bin/gvfs-open ixr,
  /usr/bin/kde-open ixr,
  # TODO: kde (done?), xfce

  # Importing firefox settings (requires 'r' access to @{HOME}/.mozilla/**
  # which is provided by abstractions/ubuntu-browsers.d/user-files).
  @{PROC}/[0-9]*/oom_{,score_}adj w,
  /etc/firefox/profile/bookmarks.html r,
  owner @{HOME}/.mozilla/** k,

  # Chromium configuration
  owner @{HOME}/.pki/nssdb/* rwk,
  owner @{HOME}/.cache/chromium/ rw,
  owner @{HOME}/.cache/chromium/** rw,
  owner @{HOME}/.cache/chromium/Cache/* mr,
  owner @{HOME}/.config/chromium/ mrw,
  owner @{HOME}/.config/chromium/** mrwk,
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
    # More stuff to get OSSEC to shut the **** up
    [b]/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,
    /dev/null rw,[/b]

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
    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/[0-9]*/oom_adj w,
    @{PROC}/[0-9]*/oom_score_adj w,
    @{PROC}/[0-9]*/task/[0-9]*/stat r,

    /usr/bin/chromium-browser r,
    /usr/lib/chromium-browser/chromium-browser Px,
    /usr/lib/chromium-browser/chromium-browser-sandbox r,

    owner /tmp/** rw,
  }
}

```

---

### Post by rookcifer on 2012-10-05
You need to read the logs and add rules manually.  You need to add the /proc/[0-9]*/status line to the sandbox profile first.  From there you're just going to have to read logs and keep adding rules until Chromium starts.

I had to do the same thing when I used Chromium.

---

### Post by Stonecold1995 on 2012-10-08
Thanks, I think I've got the hang of AppArmor now.

```
# Author: Jamie Strandboge <jamie@canonical.com>
#include <tunables/global>

# We need 'flags=(attach_disconnected)' in newer chromium versions
/usr/lib/chromium-browser/chromium-browser {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  # This include specifies which ubuntu-browsers.d abstractions to use. Eg, if
  # you want access to productivity applications, adjust the following file
  # accordingly.
  #include <abstractions/ubuntu-browsers.d/chromium-browser>

  # Stuff to get OSSEC to shut the **** up
  /etc/localtime r,
  /usr/bin/kdialog ixr,
  /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,
  @{PROC}/[0-9]*/statm r,
  /etc/mtab r,
  @{HOME}/.kde/share/config/kdeglobals k,
  /etc/xdg/Trolltech.conf kr,
  /etc/udev/udev.conf r,
  /etc/fstab r,
  /usr/bin/testparm.samba3 ixr,
  /usr/bin/net.samba3 ixr,
  /usr/bin/man ixr,

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
  @{PROC}/[0-9]*/task/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/cmdline r,
  owner @{PROC}/[0-9]*/io r,
  owner @{PROC}/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/status r,

  # Newer chromium needs these now
  /sys/devices/pci[0-9]*/**/class r,
  /sys/devices/pci[0-9]*/**/device r,
  /sys/devices/pci[0-9]*/**/irq r,
  /sys/devices/pci[0-9]*/**/resource r,
  /sys/devices/pci[0-9]*/**/vendor r,

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
  / r,
  /**/ r,

  # Allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/{include,share,src}** r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # Helpers
  /usr/bin/xdg-open ixr,
  /usr/bin/gnome-open ixr,
  /usr/bin/gvfs-open ixr,
  /usr/bin/kde-open ixr,
  # TODO: kde (done?), xfce

  # Importing firefox settings (requires 'r' access to @{HOME}/.mozilla/**
  # which is provided by abstractions/ubuntu-browsers.d/user-files).
  @{PROC}/[0-9]*/oom_{,score_}adj w,
  /etc/firefox/profile/bookmarks.html r,
  owner @{HOME}/.mozilla/** k,

  # Chromium configuration
  owner @{HOME}/.pki/nssdb/* rwk,
  owner @{HOME}/.cache/chromium/ rw,
  owner @{HOME}/.cache/chromium/** rw,
  owner @{HOME}/.cache/chromium/Cache/* mr,
  owner @{HOME}/.config/chromium/ mrw,
  owner @{HOME}/.config/chromium/** mrwk,
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
    # More stuff to get OSSEC to shut the **** up
    /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,
    /dev/null rw,
    @{PROC}/[0-9]*/status r,

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
    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/[0-9]*/oom_adj w,
    @{PROC}/[0-9]*/oom_score_adj w,
    @{PROC}/[0-9]*/task/[0-9]*/stat r,

    /usr/bin/chromium-browser r,
    /usr/lib/chromium-browser/chromium-browser Px,
    /usr/lib/chromium-browser/chromium-browser-sandbox r,

    owner /tmp/** rw,
  }
}

```

This seems to be working for me.  So far no problems!

---

### Post by litiform on 2012-10-12
I took a look at AppArmor, but it is tough to learn!

---

