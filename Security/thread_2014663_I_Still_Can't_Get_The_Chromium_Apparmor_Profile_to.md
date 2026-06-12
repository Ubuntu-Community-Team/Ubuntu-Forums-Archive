---
title: "I Still Can't Get The Chromium Apparmor Profile to work!"
date: 2012-07-02
forum: Security
---

### Post by 0011235813 on 2012-07-02
I've always had an issue with this; no matter what I try, everytime I enforce the usr.bin.chromium-browser profile, Chromium won't start. I can see it in the system monitor, and it shows up enforce, but the windows itself doesn't load. I've tried doing what this guy said [here]("https://bugs.launchpad.net/apparmor/+bug/799684") but the bug still does not appear to be fixed in apparmor 2.7. Here is the profile:
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
  # TODO: kde, xfce

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
Any help?

---

### Post by Hungry Man on 2012-07-02
If you're not receiving anything through aa-logprof delete any 'deny' rules.

---

### Post by 0011235813 on 2012-07-02
> **Hungry Man said:**
> If you're not receiving anything through aa-logprof delete any 'deny' rules.

Do you know of any Chromium (or Chrome) profiles that will actually work? Ideally, ones that will allow me to download to specific folders...

---

### Post by Hungry Man on 2012-07-02
Sure. I use a Chrome profile but I haven't actually spent much time making sure it's not full of holes ( could likely keep it more locked down through OWNER tags.) I made these pretty quickly and could likely tighten them more by removing variables.

edit: Actually going through quickly I can see a few issues with this profile in terms of being way too loose. I'll rewrite it later.

> # Last Modified: Wed May 16 23:18:45 2012
#include <tunables/global>

/opt/google/chrome/chrome-sandbox {
  #include <abstractions/base>
  #include <abstractions/ubuntu-konsole>

  capability chown,
  capability dac_override,
  capability fsetid,
  capability setgid,
  capability setuid,
  capability sys_admin,
  capability sys_chroot,
  capability sys_ptrace,



  /etc/ld.so.cache r,
  /home/*/.config/google-chrome/Default/** rwk,
  /home/*/.config/google-chrome/Dictionaries/* r,
  "/home/*/.config/google-chrome/Profile 1/Pepper Data/**" w,
  /home/documents/ r,
  /lib/@{multiarch}/ld-*.so* mr,
  /lib/@{multiarch}/libc-*.so* mr,
  /lib/@{multiarch}/libld-*.so* mr,
  /lib/@{multiarch}/libm-*.so* mr,
  /lib/@{multiarch}/libpthread-*.so* mr,
  /lib/libgcc_s.so* mr,
  /lib/tls/*/{cmov,nosegneg}/libc-*.so* mr,
  /lib/tls/*/{cmov,nosegneg}/libm-*.so* mr,
  /lib/tls/*/{cmov,nosegneg}/libpthread-*.so* mr,
  /lib{,32,64}/ld-*.so* mr,
  /lib{,32,64}/libc-*.so* mr,
  /lib{,32,64}/libld-*.so* mr,
  /lib{,32,64}/libm-*.so* mr,
  /lib{,32,64}/libpthread-*.so* mr,
  /opt/google/** mr,
  /opt/google/chrome/ r,
  /opt/google/chrome/chrome rix,
  /opt/google/chrome/chrome-sandbox r,
  /opt/google/chrome/google-chrome r,
  /opt/google/chrome/nacl_helper_bootstrap px,
  /proc/ r,
  /proc/*/ r,
  /proc/*/fd/ r,
  /proc/*/oom_score_adj w,
  /proc/*/status r,
  /proc/sys/kernel/shmmax r,
  /run/shm/* rw,
  /sys/devices/system/cpu/** r,
  /usr/lib/libstdc++.so* mr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/ r,
  @{PROC}/[0-9]*/fd/ r,
  @{PROC}/[0-9]*/oom_adj w,
  @{PROC}/[0-9]*/oom_score_adj w,
  @{PROC}/[0-9]*/task/[0-9]*/stat r,

}

> # Last Modified: Wed May 16 23:18:45 2012
#include <tunables/global>

/opt/google/chrome/google-chrome {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/nvidia>
  #include <abstractions/ubuntu-konsole>
  #include <abstractions/user-tmp>

  deny capability dac_override,
  deny capability dac_read_search,

  capability ipc_lock,
  capability sys_ptrace,

  network inet stream,
  network inet6 stream,

  deny /media/truecrypt1/ r,
  /home/*/Documents/Misc/** r,
  /bin/bash rix,
  /bin/dash rix,
  /bin/grep rix,
  /bin/mkdir rix,
  /bin/mv rix,
  /bin/ps rix,
  /bin/readlink rix,
  /bin/sed rix,
  /bin/touch rix,
  /bin/which rix,
  /dev/ r,
  /dev/video0 r,
  /etc/ati/amdpcsdb.default r,
  /etc/ati/atiogl.xml r,
  /etc/lsb-release r,
  /etc/passwd m,
  /etc/python2.7/sitecustomize.py r,
  owner /home/*/.adobe/** rwk,
  owner /home/*/.cache/dconf/user rwk,
  owner /home/*/.cache/google-chrome/** rwk,
  owner /home/*/.config/autostart/google-chrome.desktop rwk,
  owner /home/*/.config/dconf/user r,
  owner /home/*/.config/google-chrome/ rwk,
  owner /home/*/.config/google-chrome/** rwk,
  /home/*/.fontconfig/** rk,
  owner /home/*/.local/share/applications/* rwk,
  /home/*/.macromedia/** rk,
  /home/*/.mozilla/firefox/** r,
  /home/*/.pki/nssdb/** rwk,
  /home/*/.thumbnails/normal/* r,
  owner /opt/google/** rk,
  owner /opt/google/chrome/* mrk,
  /opt/google/chrome/PepperFlash/* mrk,
  /opt/google/chrome/chrome rix,
  /opt/google/chrome/chrome-sandbox px,
  /opt/google/chrome/google-chrome rix,
  /opt/google/chrome/xdg-settings rix,
  /proc/ r,
  /proc/*/fd/ r,
  /proc/*/io r,
  /proc/*/oom_score_adj w,
  /proc/*/statm r,
  /proc/*/task/ r,
  /proc/ati/major r,
  /proc/sys/kernel/pid_max r,
  /proc/tty/drivers r,
  @{PROC}/[0-9]*/task/[0-9]*/stat r,
  /proc/uptime r,
  /proc/version r,
  /root/.local/share/Trash/files/* rwk,
  /root/.local/share/Trash/files/** rwk,
  /run/shm/* mrw,
  /selinux/ r,
  /sys/bus/pci/devices/ r,
  /sys/devices/** r,
  owner /tmp/** mlk,
  /tmp/** rw,
  /usr/bin/basename rix,
  /usr/bin/cut rix,
  /usr/bin/dirname rix,
  /usr/bin/file-roller rix,
  /usr/bin/gconftool-2 rix,
  /usr/bin/gvfs-open rix,
  /usr/bin/lsb_release rix,
  /usr/bin/mawk rix,
  /usr/bin/nautilus rix,
  /usr/bin/transmission-gtk px,
  /usr/bin/xdg-mime rix,
  /usr/bin/xdg-open rix,
  /usr/bin/xdg-settings rix,
  /usr/include/python2.7/pyconfig.h r,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/python2.7/dist-packages/ r,
  /usr/share/fonts/**/*.pfb m,
  /usr/share/fonts/truetype/**/*.tt[cf] m,
  /usr/share/glib-2.0/schemas/gschemas.compiled r,
  /usr/share/icons/**/*.cache m,
  /usr/share/mime/mime.cache m,
  /usr/share/pyshared/* r,
  owner /{dev,run}/shm/pulse-shm* m,
  owner @{HOME}/ r,
  owner @{HOME}/.local/share/mime/mime.cache m,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{PROC}/[0-9]*/auxv r,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

}

> # Last Modified: Sat Mar 31 04:24:18 2012
#include <tunables/global>

/opt/google/chrome/nacl_helper_bootstrap {
  #include <abstractions/base>


  deny capability dac_override,
  deny capability dac_read_search,
  deny capability chown,
  deny capability fsetid,
  deny capability setgid,
  deny capability setuid,
  deny capability sys_admin,
  deny capability sys_chroot,
  deny capability sys_ptrace,


  /opt/google/chrome/nacl_helper mr,
  /opt/google/chrome/nacl_irt_x86_64.nexe r,
  /run/shm/* mrw,
  /sys/devices/system/cpu/cpu0/** r,
  /tmp/* r,

}

Feel free to edit as you like.

---

### Post by 0011235813 on 2012-07-02
> **Hungry Man said:**
> Sure. I use a Chrome profile but I haven't actually spent much time making sure it's not full of holes ( could likely keep it more locked down through OWNER tags.) I made these pretty quickly and could likely tighten them more by removing variables.

edit: Actually going through quickly I can see a few issues with this profile in terms of being way too loose. I'll rewrite it later.







Feel free to edit as you like.

I assume this profile limits downloads to the "Downloads" folder? If so, would adding: something like ~/Music in @HOME work?

---

### Post by Hungry Man on 2012-07-02
@{HOME}/Downloads/ rwk,
@{HOME}/Downloads/Music rwk,

That's all you need.

You can use an owner tag to limit it to being only able to write to files it owns in those folders.

---

### Post by 0011235813 on 2012-07-02
> **Hungry Man said:**
> @{HOME}/Downloads/ rwk,
@{HOME}/Downloads/Music rwk,

That's all you need.

You can use an owner tag to limit it to being only able to write to files it owns in those folders.

Thanks, I'll get down to it soon.

EDIT:UPDATE: I've got the profile running for Chrome. Here's what I did:
```

sudo -i
cd /etc/apparmor.d
nano opt.google.chrome.chrome-sandbox
#Copied profile
Ctrl+Shift+V
Ctr+X
y
[ENTER]
 nano opt.google.chrome.google-chrome
#same as above, here was the final profile:
# Last Modified: Wed May 16 23:18:45 2012
#include <tunables/global>

/opt/google/chrome/google-chrome {
#include <abstractions/audio>
#include <abstractions/base>
#include <abstractions/bash>
#include <abstractions/cups-client>
#include <abstractions/dbus-session>
#include <abstractions/fonts>
#include <abstractions/freedesktop.org>
#include <abstractions/gnome>
#include <abstractions/nameservice>
#include <abstractions/nvidia>
#include <abstractions/ubuntu-konsole>
#include <abstractions/user-tmp>

deny capability dac_override,
deny capability dac_read_search,

capability ipc_lock,
capability sys_ptrace,

network inet stream,
network inet6 stream,

deny /media/truecrypt1/ r,
/home/*/Documents/Misc/** r,
/bin/bash rix,
/bin/dash rix,
/bin/grep rix,
/bin/mkdir rix,
/bin/mv rix,
/bin/ps rix,
/bin/readlink rix,
/bin/sed rix,
/bin/touch rix,
/bin/which rix,
/dev/ r,
/dev/video0 r,
/etc/ati/amdpcsdb.default r,
/etc/ati/atiogl.xml r,
/etc/lsb-release r,
/etc/passwd m,
/etc/python2.7/sitecustomize.py r,
owner /home/*/.adobe/** rwk,
owner /home/*/.cache/dconf/user rwk,
owner /home/*/.cache/google-chrome/** rwk,
owner /home/*/.config/autostart/google-chrome.desktop rwk,
owner /home/*/.config/dconf/user r,
owner /home/*/.config/google-chrome/ rwk,
owner /home/*/.config/google-chrome/** rwk,
/home/*/.fontconfig/** rk,
owner /home/*/.local/share/applications/* rwk,
/home/*/.macromedia/** rk,
/home/*/.mozilla/firefox/** r,
/home/*/.pki/nssdb/** rwk,
/home/*/.thumbnails/normal/* r,
owner /opt/google/** rk,
owner /opt/google/chrome/* mrk,
/opt/google/chrome/PepperFlash/* mrk,
/opt/google/chrome/chrome rix,
/opt/google/chrome/chrome-sandbox px,
/opt/google/chrome/google-chrome rix,
/opt/google/chrome/xdg-settings rix,
/proc/ r,
/proc/*/fd/ r,
/proc/*/io r,
/proc/*/oom_score_adj w,
/proc/*/statm r,
/proc/*/task/ r,
/proc/ati/major r,
/proc/sys/kernel/pid_max r,
/proc/tty/drivers r,
@{PROC}/[0-9]*/task/[0-9]*/stat r,
/proc/uptime r,
/proc/version r,
/root/.local/share/Trash/files/* rwk,
/root/.local/share/Trash/files/** rwk,
/run/shm/* mrw,
/selinux/ r,
/sys/bus/pci/devices/ r,
/sys/devices/** r,
owner /tmp/** mlk,
/tmp/** rw,
/usr/bin/basename rix,
/usr/bin/cut rix,
/usr/bin/dirname rix,
/usr/bin/file-roller rix,
/usr/bin/gconftool-2 rix,
/usr/bin/gvfs-open rix,
/usr/bin/lsb_release rix,
/usr/bin/mawk rix,
/usr/bin/nautilus rix,
/usr/bin/transmission-gtk px,
/usr/bin/xdg-mime rix,
/usr/bin/xdg-open rix,
/usr/bin/xdg-settings rix,
/usr/include/python2.7/pyconfig.h r,
/usr/lib{,32,64}/** mr,
/usr/local/lib/python2.7/dist-packages/ r,
/usr/share/fonts/**/*.pfb m,
/usr/share/fonts/truetype/**/*.tt[cf] m,
/usr/share/glib-2.0/schemas/gschemas.compiled r,
/usr/share/icons/**/*.cache m,
/usr/share/mime/mime.cache m,
/usr/share/pyshared/* r,
owner /{dev,run}/shm/pulse-shm* m,
owner @{HOME}/ r,
owner @{HOME}/.local/share/mime/mime.cache m,
owner @{HOME}/Downloads/ r,
owner @{HOME}/Downloads/* rw,
owner @{HOME}/Music/* rw
owner @{HOME}/Documents/* rw
owner @{HOME}/Software/* rw
owner @{HOME}/Pictures/* rw
owner @{HOME}/Videos/* rw
owner @{HOME}/Dangerous/* rw
owner @{HOME}/Public/ r,
owner @{HOME}/Public/* r,
owner @{PROC}/[0-9]*/auxv r,
@{PROC}/[0-9]*/net/if_inet6 r,
@{PROC}/[0-9]*/net/ipv6_route r,

}
nano opt.google.chrome.nacl_helper_bootstrap
#same as first
aa-enforce  opt.google.chrome.chrome-sandbox  opt.google.chrome.google-chrome opt.google.chrome.nacl_helper_bootstrap 
#Got this error:
Setting /etc/apparmor.d/opt.google.chrome.chrome-sandbox to enforce mode.
Setting /etc/apparmor.d/opt.google.chrome.google-chrome to enforce mode.
Warning from stdin (line 1): /sbin/apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
AppArmor parser error,  in stdin line 114: syntax error, unexpected TOK_OWNER, expecting TOK_END_OF_RULE


```
Chrome seems to start. 
Gnome system monitor shows it as enforced. Loading pages are working. Downloads to Downloads, Music, Pictures, Videos, Dangerous, and Documents all work.

---

### Post by oklokl on 2012-07-03
Apparmor is a bug(*/etc/init.d/apparmor restart*) Contamination. ->google-chrome Profiles 
This bug.
 This is a bug that only works when you first start.

Apparmor..-> Do not run.  -> -> *#sudo /etc/init.d/apparmor restart*# Do not ever run.
If you need to run the data are contaminated. -> opt.google.chrome.google-chrome
apparmor Profiles 
Contaminated data
 Can not be recovered.
[COLOR=Red]Must be completely rewritten.[/COLOR]

First, please back up your data
#backup
```
mkdir -p ~/test
sudo cp -f /etc/apparmor.d/opt.google.chrome.google-chrome ~/
sudo cp -f /etc/apparmor.d/opt.google.chrome.google-chrome ~/test
```# Point
 # Must be deleted.    king bug.. n,.n
# remove file clean
```
sudo rm -f /etc/apparmor.d/opt.google.chrome.google-chrome
sudo /etc/init.d/apparmor restart
```# edit
```
sudo nano ~/opt.google.chrome.google-chrome
```# my Core
```
/sys/devices/system/cpu/cpu*/cpufreq/* r,
/dev/null rw,
/proc/*/** r,
```# you core
```
owner @{HOME}/Downloads/ rwk,
owner @{HOME}/Downloads/** rwk,
owner @{HOME}/Downloads/Music rwk,
owner @{HOME}/Downloads/Music/** rwk,
``````
sudo cp -f ~/opt.google.chrome.google-chrome /etc/apparmor.d
sudo /etc/init.d/apparmor restart
```*#sudo /etc/init.d/apparmor restart*#- > If you already use.
Write a completely new ...

 ```
sudo rm -f /etc/apparmor.d/opt.google.chrome.google-chrome
sudo /etc/init.d/apparmor restart
```new file write and..
copy you file.. -> /etc/apparmor.d

and..
sudo /etc/init.d/apparmor restart


[opt.google.chrome.chrome-sandbox] This issue is bogus.
 Bogus log

I find this problem ... It took a long time



If you have used.  */etc/init.d/apparmor restart*
 Due to a bug

 May seem normal.  ->file.. opt.google.chrome.google-chrome
 but.. Is not normal.
remove file..



If you modify the same way as above normal.
 Work without any problem.

When you modify the same applies to normal again.
The first problem is that if the program works.

---

### Post by 0011235813 on 2012-07-03
> **oklokl said:**
> Apparmor is a bug(*/etc/init.d/apparmor restart*) Contamination. ->google-chrome Profiles 
This bug.
 This is a bug that only works when you first start.

Apparmor..-> Do not run.  -> -> *#sudo /etc/init.d/apparmor restart*# Do not ever run.
If you need to run the data are contaminated. -> opt.google.chrome.google-chrome
apparmor Profiles 
Contaminated data
 Can not be recovered.
[COLOR=Red]Must be completely rewritten.[/COLOR]

First, please back up your data
#backup
```
mkdir -p ~/test
sudo cp -f /etc/apparmor.d/opt.google.chrome.google-chrome ~/
sudo cp -f /etc/apparmor.d/opt.google.chrome.google-chrome ~/test
```# Point
 # Must be deleted.    king bug.. n,.n
# remove file clean
```
sudo rm -f /etc/apparmor.d/opt.google.chrome.google-chrome
sudo /etc/init.d/apparmor restart
```# edit
```
sudo nano ~/opt.google.chrome.google-chrome
```# my Core
```
/sys/devices/system/cpu/cpu*/cpufreq/* r,
/dev/null rw,
/proc/*/** r,
```# you core
```
owner @{HOME}/Downloads/ rwk,
owner @{HOME}/Downloads/** rwk,
owner @{HOME}/Downloads/Music rwk,
owner @{HOME}/Downloads/Music/** rwk,
``````
sudo cp -f ~/opt.google.chrome.google-chrome /etc/apparmor.d
sudo /etc/init.d/apparmor restart
```*#sudo /etc/init.d/apparmor restart*#- > If you already use.
Write a completely new ...

 ```
sudo rm -f /etc/apparmor.d/opt.google.chrome.google-chrome
sudo /etc/init.d/apparmor restart
```new file write and..
copy you file.. -> /etc/apparmor.d

and..
sudo /etc/init.d/apparmor restart


[opt.google.chrome.chrome-sandbox] This issue is bogus.
 Bogus log

I find this problem ... It took a long time



If you have used.  */etc/init.d/apparmor restart*
 Due to a bug

 May seem normal.  ->file.. opt.google.chrome.google-chrome
 but.. Is not normal.
remove file..



If you modify the same way as above normal.
 Work without any problem.

When you modify the same applies to normal again.
The first problem is that if the program works.

Sorry, but I don't seem to understand what you're trying to say. Is there some sort of bug with Chrome when restrating apparmor? Please, I'm confused... Perhaps English is not your native language? It's not mine either, but I'm afraid I don't speak Korean. Do you have anyone that can help you translate?

---

### Post by oklokl on 2012-07-03
profile -> Is changed due to a bug
Chromium

Only occurs once.

You must remove the faulty file.
and..
sudo /etc/init.d/apparmor restart
and..
And create a new profile(opt.google.chrome.google-chrome)
 Insert  
and..
 sudo /etc/init.d/apparmor restart

See the command above.
 Answers can be found.

---

### Post by 0011235813 on 2012-07-08
I can't seem to get the opt.google.chrome.google-chrome profile to enforce. I get:
```


Setting /etc/apparmor.d/opt.google.chrome.google-chrome to enforce mode.
Warning from stdin (line 1): /sbin/apparmor_parser: cannot use or update cache, disable, or force-complain via stdin
AppArmor parser error,  in stdin line 114: syntax error, unexpected TOK_OWNER, expecting TOK_END_OF_RULE

```
Here is line 1 and line 114:
```

#Line 1
# Last Modified: Wed May 16 23:18:45 2012
#Line 114
owner @{HOME}/Documents/* rw

```
Any ideas?

---

### Post by Hungry Man on 2012-07-08
It needs a comma after rw.

---

### Post by 0011235813 on 2012-07-09
> **Hungry Man said:**
> It needs a comma after rw.

Done that, it enforces now, but when I try to open Chrome, it says it can't see the data files and asks for a re-install. It only works on complain mode. Here is the profile:
```

# Last Modified: Wed May 16 23:18:45 2012
#include <tunables/global>

/opt/google/chrome/google-chrome flags=(complain) {
#include <abstractions/audio>
#include <abstractions/base>
#include <abstractions/bash>
#include <abstractions/cups-client>
#include <abstractions/dbus-session>
#include <abstractions/fonts>
#include <abstractions/freedesktop.org>
#include <abstractions/gnome>
#include <abstractions/nameservice>
#include <abstractions/nvidia>
#include <abstractions/ubuntu-konsole>
#include <abstractions/user-tmp>

deny capability dac_override,
deny capability dac_read_search,

capability ipc_lock,
capability sys_ptrace,

network inet stream,
network inet6 stream,

deny /media/truecrypt1/ r,
/home/*/Documents/Misc/** r,
/bin/bash rix,
/bin/dash rix,
/bin/grep rix,
/bin/mkdir rix,
/bin/mv rix,
/bin/ps rix,
/bin/readlink rix,
/bin/sed rix,
/bin/touch rix,
/bin/which rix,
/dev/ r,
/dev/video0 r,
/etc/ati/amdpcsdb.default r,
/etc/ati/atiogl.xml r,
/etc/lsb-release r,
/etc/passwd m,
/etc/python2.7/sitecustomize.py r,
owner /home/*/.adobe/** rwk,
owner /home/*/.cache/dconf/user rwk,
owner /home/*/.cache/google-chrome/** rwk,
owner /home/*/.config/autostart/google-chrome.desktop rwk,
owner /home/*/.config/dconf/user r,
owner /home/*/.config/google-chrome/ rwk,
owner /home/*/.config/google-chrome/** rwk,
/home/*/.fontconfig/** rk,
owner /home/*/.local/share/applications/* rwk,
/home/*/.macromedia/** rk,
/home/*/.mozilla/firefox/** r,
/home/*/.pki/nssdb/** rwk,
/home/*/.thumbnails/normal/* r,
owner /opt/google/** rk,
owner /opt/google/chrome/* mrk,
/opt/google/chrome/PepperFlash/* mrk,
/opt/google/chrome/chrome rix,
/opt/google/chrome/chrome-sandbox px,
/opt/google/chrome/google-chrome rix,
/opt/google/chrome/xdg-settings rix,
/proc/ r,
/proc/*/fd/ r,
/proc/*/io r,
/proc/*/oom_score_adj w,
/proc/*/statm r,
/proc/*/task/ r,
/proc/ati/major r,
/proc/sys/kernel/pid_max r,
/proc/tty/drivers r,
@{PROC}/[0-9]*/task/[0-9]*/stat r,
/proc/uptime r,
/proc/version r,
/root/.local/share/Trash/files/* rwk,
/root/.local/share/Trash/files/** rwk,
/run/shm/* mrw,
/selinux/ r,
/sys/bus/pci/devices/ r,
/sys/devices/** r,
owner /tmp/** mlk,
/tmp/** rw,
/usr/bin/basename rix,
/usr/bin/cut rix,
/usr/bin/dirname rix,
/usr/bin/file-roller rix,
/usr/bin/gconftool-2 rix,
/usr/bin/gvfs-open rix,
/usr/bin/lsb_release rix,
/usr/bin/mawk rix,
/usr/bin/nautilus rix,
/usr/bin/transmission-gtk px,
/usr/bin/xdg-mime rix,
/usr/bin/xdg-open rix,
/usr/bin/xdg-settings rix,
/usr/include/python2.7/pyconfig.h r,
/usr/lib{,32,64}/** mr,
/usr/local/lib/python2.7/dist-packages/ r,
/usr/share/fonts/**/*.pfb m,
/usr/share/fonts/truetype/**/*.tt[cf] m,
/usr/share/glib-2.0/schemas/gschemas.compiled r,
/usr/share/icons/**/*.cache m,
/usr/share/mime/mime.cache m,
/usr/share/pyshared/* r,
owner /{dev,run}/shm/pulse-shm* m,
owner @{HOME}/ r,
owner @{HOME}/.local/share/mime/mime.cache m,
owner @{HOME}/Downloads/ r,
owner @{HOME}/Downloads/* rw,
owner @{HOME}/Music/* rw,
owner @{HOME}/Documents/* rw,
owner @{HOME}/Software/* rw,
owner @{HOME}/Pictures/* rw,
owner @{HOME}/Videos/* rw,
owner @{HOME}/Dangerous/* rw,
owner @{HOME}/Public/ r,
owner @{HOME}/Public/* r,
owner @{PROC}/[0-9]*/auxv r,
@{PROC}/[0-9]*/net/if_inet6 r,
@{PROC}/[0-9]*/net/ipv6_route r,

}

```
What could be wrong?
I found the problem in this log:
```

Jul  9 16:21:17 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  332.836468] type=1400 audit(1341847277.761:64): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/theme_resources_standard.pak" pid=3347 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:17 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  332.836597] type=1400 audit(1341847277.761:65): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/ui_resources_standard.pak" pid=3347 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:17 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  332.838089] type=1400 audit(1341847277.761:66): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/locales/en-GB.pak" pid=3347 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:24 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  339.818803] type=1400 audit(1341847284.740:67): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/chrome.pak" pid=3437 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:24 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  339.819293] type=1400 audit(1341847284.740:68): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/theme_resources_standard.pak" pid=3437 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:24 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  339.819378] type=1400 audit(1341847284.740:69): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/ui_resources_standard.pak" pid=3437 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:24 manuela-HP-Pavilion-dm1-Notebook-PC kernel: [  339.820856] type=1400 audit(1341847284.744:70): apparmor="DENIED" operation="open" parent=1 profile="/opt/google/chrome/google-chrome" name="/opt/google/chrome/locales/en-GB.pak" pid=3437 comm="chrome" requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
Jul  9 16:21:35 manuela-HP-Pavilion-dm1-Notebook-PC kernel:

```
It seems to be denying /opt/google/chrome/theme_resources_standard.pak (theme?) and various other .pak files. I also have extensions installed, coule this be affecting it?

---

### Post by Hungry Man on 2012-07-09
Does anything come up with aa-logprof? 

It's probably whining about some file permission issue in which case the easiest solution is:

1) Copy your Default folder
2) Past it to some other folder
3) Delete original
4) Copy and paste it back

---

### Post by 0011235813 on 2012-07-09
> **Hungry Man said:**
> Does anything come up with aa-logprof? 

It's probably whining about some file permission issue in which case the easiest solution is:

1) Copy your Default folder
2) Past it to some other folder
3) Delete original
4) Copy and paste it back

aa-logprof turns up nothing, in fact, everytime I switch to the terminal, Chrome closes itself. 

Tried that, still doesn't open. Maybe there is a conflict between plugins? Themes? Extensions? New version that requires some extra files? Should I try disabling extensions? Uninstalling them? Change the gtk+ theme?

EDIT: Now Chrome doesn't even show in the launcher when I open it up, using Chromium. How does anyone deal with this program?!!

---

### Post by vasa1 on 2012-07-09
Why is the thread **Solved**? You can go back to Thread Tools and _un_Solve it.

---

### Post by 0011235813 on 2012-07-09
> **vasa1 said:**
> Why is the thread **Solved**? You can go back to Thread Tools and _un_Solve it.

I thought it was solved but apparently apparmor doesn't like my profile very much. Or maybe Chrome is the culprit, IDK.

---

### Post by Hungry Man on 2012-07-09
Strange issue. Maybe build the profile from scratch - if you're on the beta you might need a lot of new rights because of some new APIs introduced for webcam and device access.

---

### Post by 0011235813 on 2012-07-10
> **Hungry Man said:**
> Strange issue. Maybe build the profile from scratch - if you're on the beta you might need a lot of new rights because of some new APIs introduced for webcam and device access.

I'll live with JavaScript turned off then. Crazed program, at least with no JS, it won't matter because there are no exploits on web pages without JS or plugins, I'll guess I'll just have to deal with the inconvenience :(

Thank you for the help anyway.

---

### Post by Hungry Man on 2012-07-10
You can still be exploited without Javascript/ plugins through text rendering vulnerabilities (rare, but there was one not so long ago.)

My Chrome profile's working for me, idk

---

### Post by 0011235813 on 2012-07-12
> **Hungry Man said:**
> You can still be exploited without Javascript/ plugins through text rendering vulnerabilities (rare, but there was one not so long ago.)

My Chrome profile's working for me, idk

Possibly, but in the end, the most it's going to end up doing is screwing with my home directory, which is backed up daily. My only concern is passwords, I wonder if there is a program that will encrypt Chrome passwords. And anyway, password-stealing type exploits can't be prevented by apparmor anyway.

---

### Post by Hungry Man on 2012-07-12
I suggest LastPass, which is what I use.

---

### Post by 0011235813 on 2012-07-13
> **Hungry Man said:**
> I suggest LastPass, which is what I use.

Same. But it's really a cloud based password manager. I can't believe Chrome doesn't have password encryption like Opera and Firefox.

---

### Post by Hungry Man on 2012-07-13
It does. 
 It's encrypted with either your GMail password or your passphrase. On Windows it's encrypted on disk with your Windows Login password and it decrypts when you log in.

LastPass does all of its encryption locally as well as server side, which is why I use it. It's stored on their servers but even if they're hacked I have absolutely nothing to worry about.

---

### Post by 0011235813 on 2012-07-14
> **Hungry Man said:**
> It does. 
 It's encrypted with either your GMail password or your passphrase. On Windows it's encrypted on disk with your Windows Login password and it decrypts when you log in.

LastPass does all of its encryption locally as well as server side, which is why I use it. It's stored on their servers but even if they're hacked I have absolutely nothing to worry about.
Uhm... Not quite. What you're mentioning is the Account Sign in feature of Chrome, which does indeed ** only encrypt passwords  by default on the server side** and can be set to encrypt everything, **but not locally on your computer!**. This means that if a website were to compromise Chrome, it could potentially steal the passwords, because they are in fact stored in plaintext [http://support.google.com/chrome/bin/answer.py?hl=en&answer=2390059&topic=1693469&ctx=topic:](http://support.google.com/chrome/bin/answer.py?hl=en&answer=2390059&topic=1693469&ctx=topic:)
> 
How do I stop syncing to my Google Account, while keeping my bookmarks and other browsing data on my computer?

You can disconnect your Google Account from Chrome and stop syncing with your computer. By disconnecting your Google Account, you won&#8217;t lose the data stored on your computer or in your Google Account. However, any future changes you make on your computer will not be reflected on other computers that you&#8217;ve signed in to Chrome on. Learn how to disconnect your Google Account from Chrome
> 
When you sign in to Chrome and enable sync, Chrome keeps your information secure by using a passphrase to encrypt your synced data. By default, Chrome uses your Google Account password as the passphrase, but you can choose to use a custom encryption passphrase instead. This custom passphrase is stored on your computer and isn&#8217;t sent to Google.


*Note: The last bit is also important to notice, because a website can also get your whole account passphrase if you use that and could again decrypt and read everything in your account.*

As for the CryptProtectData API in Windows, that still decrypts it on login (and thus does not protect from web-based threats of password-stealing) and anyway, can't the attacker just look at the Windows password on the computer via Live session, store it, copy the passwords from Chrome, go to another machine, make a Windows VM with the same account details, copy the passwords into Chrome's folder, and voila?

---

### Post by Hungry Man on 2012-07-14
[http://gregoryszorc.com/blog/2012/04/08/comparing-the-security-and-privacy-of-browser-syncing/](http://gregoryszorc.com/blog/2012/04/08/comparing-the-security-and-privacy-of-browser-syncing/)

> The default behavior is for Chrome to encrypt your passwords before uploading them to the server.

Nothing you quoted disagrees with what I've said. In fact, the bit about the passphrase stored on your computer and not their servers enforces that you're the one holding the encryption key and you're the one doing the encryption.

If your Chrome is compromised and they do gain access to the passwords (they'd have to move to a sandbox that has access to this, the renderer is where you'll find exploits most of the time and it has no read access) the reason it would lhave access is, just as with the Firefox master password, your passwords *have* to be decrypted at some point.

> As for the CryptProtectData API in Windows, that still decrypts it on login (and thus does not protect from web-based threats of password-stealing) and anyway, can't the attacker just look at the Windows password on the computer via Live session, store it, copy the passwords from Chrome, go to another machine, make a Windows VM with the same account details, copy the passwords into Chrome's folder, and voila?
If they have the password they could simply log into the Windows computer.

A master password protects only against this attack, really.

---

### Post by 0011235813 on 2012-07-14
> **Hungry Man said:**
> [http://gregoryszorc.com/blog/2012/04/08/comparing-the-security-and-privacy-of-browser-syncing/](http://gregoryszorc.com/blog/2012/04/08/comparing-the-security-and-privacy-of-browser-syncing/)



Nothing you quoted disagrees with what I've said. In fact, the bit about the passphrase stored on your computer and not their servers enforces that you're the one holding the encryption key and you're the one doing the encryption.

If your Chrome is compromised and they do gain access to the passwords (they'd have to move to a sandbox that has access to this, the renderer is where you'll find exploits most of the time and it has no read access) the reason it would lhave access is, just as with the Firefox master password, your passwords *have* to be decrypted at some point.


If they have the password they could simply log into the Windows computer.

A master password protects only against this attack, really.
Yeah, the whole point I was trying to make isn't that Chrome doesn't encrypt the passwords on the server when you sign in to your account, it's that a JavaScript/plugin/whatever exploit could read the passwords on the machine. For example, let's say I made a site with some malicious JavaScript and I successfully managed to exploit Chromium. I could then tell it to upload ~/.config/chromium/Default/Web Data to [ftp://malicious.evil.hacker/your-passwords](ftp://malicious.evil.hacker/your-passwords) and hey presto, I could see al the passwords with something like sqliteman.  

Yeah, I didn't think of that. I wonder why they bother with CryptProtectData? It wouldn't help the encrypted passwords if the master password to decrypt them is stored in plain text in c:\windows\system32\configure\sam. Stupid. Stupid.

EDIT: Sorry, I should have mentioned specifically I was referring to locally stored passwords, I thought it would have been evident when I mentioned files in my /home directory and concern over passwords.

---

### Post by Hungry Man on 2012-07-14
> For example, let's say I made a site with some malicious JavaScript and I successfully managed to exploit Chromium. I could then tell it to upload ~/.config/chromium/Default/Web Data to [ftp://malicious.evil.hacker/your-passwords](ftp://malicious.evil.hacker/your-passwords) and hey presto, I could see al the passwords with something like sqliteman. 
Not really. If it were a Java exploit sure. But a Javascript exploit will be held in the JAvascript sandbox, which on Windows runs at Untrusted integrity. That means it has no read/ write access.

>  I wonder why they bother with CryptProtectData
Because without your Windows ID password they can't get in unless I'm missing something.

Although there might be a way around that if it's stored in plaintext.

Either way, I suggest LAstPass lol

---

### Post by 0011235813 on 2012-07-15
> **Hungry Man said:**
> Not really. If it were a Java exploit sure. But a Javascript exploit will be held in the JAvascript sandbox, which on Windows runs at Untrusted integrity. That means it has no read/ write access.
 
 
Because without your Windows ID password they can't get in unless I'm missing something.
 
Although there might be a way around that if it's stored in plaintext.
 
Either way, I suggest LAstPass lol
 The scenario was hypothetical of course, but I think the Chrome/Chromium developers are giving their sandbox a little too much credit, treating it as if it were unbreakable and thus being sloppy in other departments like password protection which browsers like Firefox and Opera all employ. 


Not to bash LastPass, but it seems a bit strange that one would require to use a third-party extension to do something as simple as keep your passwords safe

---

### Post by Hungry Man on 2012-07-15
ACtually the Chromium developers are working on a password management system that's far more ambitious than a simple master password - it's an entire LastPass-type system but with Google's servers.

It's been in the works for about two months now and it's already showing some features (like password generation.)

I agree that it would be nice to not have to use a 3rd party extension. But if their new management system works as well we won't have to.

As for the Chrome sandbox I think the credit is well deserved. Bypassing it on Windows is incredibly difficult - bypassing it on Linux is way harder and, with the proper configuration, really just not feasible for any cost-effective attack (and by "proper configuration" I'm talking about grsecurity kernels with hardened chroots etc on a 3.5 kernel) but, of course, it's not invincible.

That's not super on topic though. The point is for an attacker to see your password file they need at least one 'hop' to a higher privileged sandbox.

---

### Post by 0011235813 on 2012-07-15
> **Hungry Man said:**
> ACtually the Chromium developers are working on a password management system that's far more ambitious than a simple master password - it's an entire LastPass-type system but with Google's servers.

It's been in the works for about two months now and it's already showing some features (like password generation.)

I agree that it would be nice to not have to use a 3rd party extension. But if their new management system works as well we won't have to.

As for the Chrome sandbox I think the credit is well deserved. Bypassing it on Windows is incredibly difficult - bypassing it on Linux is way harder and, with the proper configuration, really just not feasible for any cost-effective attack (and by "proper configuration" I'm talking about grsecurity kernels with hardened chroots etc on a 3.5 kernel) but, of course, it's not invincible.

That's not super on topic though. The point is for an attacker to see your password file they need at least one 'hop' to a higher privileged sandbox.
I was under the impression the Chrome developers weren't interested because "it provides a false sense of security" but apparently not. Good to hear.

Now I'm using Opera next, because for some reason the Chrome version of FVD doesn't work properly, and Firefox is too slow for my liking [-(

---

### Post by Hungry Man on 2012-07-15
The false sense of security would come with a simple MP. This system is designed to actually be secure throughout.

---

