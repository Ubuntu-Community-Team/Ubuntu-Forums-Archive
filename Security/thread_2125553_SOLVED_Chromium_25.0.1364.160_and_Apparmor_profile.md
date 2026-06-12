---
title: "SOLVED Chromium 25.0.1364.160 and Apparmor profile for chromium-browser"
date: 2013-03-14
forum: Security
---

### Post by maglinu on 2013-03-14
Since the recent update of Chromium to Version 25.0.1364.160 Ubuntu 12.04 I haven't been able to get it to launch with its Apparmor profile set to Enforce. Set it to Complain and all is well.

Before I start trying to fiddle with the profile (which I am reluctant to do since it is straight out of the Ubuntu repository and it may well prove beyond me to do so anyway), I thought I'd ask if anyone else has seen the same behaviour?

TIA

---

### Post by maglinu on 2013-03-14
Perhaps if I rephrase the question.

Is anyone now successfully opening Chromium 25.0.1364.160 with the apparmor profile for chromium-browser in enforce mode? 

I'm now failing to do so on two different machines.

---

### Post by nomenkultur on 2013-03-14
same... I came here looking for a new profile I could download and load

 if you edit yours to make it work please share

---

### Post by maglinu on 2013-03-14
Thanks for the response.

Now I know it's not just me.

I'm not sure if it's really necessary anyway, since seccomp sandbox is now enabled by default in chromium.

I'll have a look at kern.log and see if I can find anything that some bright people here might be able to use to tell me how to modify the profile.

---

### Post by maglinu on 2013-03-15
If any apparmor experts out there would like to take a look, this is the kern.log output for the chromium-browser block by apparmor:
 apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" name="/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0/block/sda/sda1/size" pid=3596 comm="Chrome_FileThre" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

---

### Post by maglinu on 2013-03-15
> **nomenkultur said:**
> same... I came here looking for a new profile I could download and load

 if you edit yours to make it work please share

Have a look here:

[http://ubuntuforums.org/showthread.php?t=2065866](http://ubuntuforums.org/showthread.php?t=2065866)

Doesn't look easy!

---

### Post by maglinu on 2013-03-15
I think this is perhaps a bug that is already reported.
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1154164](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1154164)
with a patch hopefully on the way.

---

### Post by nomenkultur on 2013-03-16
> **maglinu said:**
> 

I'm not sure if it's really necessary anyway, since seccomp sandbox is now enabled by default in chromium.


I'd rather have the sandbox activated in the system than in the browser.


 Have you tried loading this profile? the guy in that thread you linked says it works

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

---

### Post by maglinu on 2013-03-16
No it looked a bit too specific to me.

I'd rather try to make my own changes - but unfortunately I get no output from sudo aa-logprof, and I can't figure out what to actually add based on the syslog complaints.

I think seccomp is a system (kernel) function rather than a browser function by the way. Any process running under seccomp is sent the sigkill command by the kernel if it attempts any system calls other than exit, sigreturn, read and write.

I read somewhere that it doesn't offer some protection that apparmor does though.

---

### Post by maglinu on 2013-03-17
Much to my surprise, I fixed it! 

All I did was add the block line to the profile in what looked like an obvious place - in my case under # Newer chromium needs these now

/sys/devices/pci0000:00/0000:00:14.1/host4/target4:0:0/4:0:0:0/block/sda/sda1/size r,

Now it runs sweetly in enforce mode:)

Course I'd feel a lot happier if I knew why it worked!

Edit - also works with:
/sys/devices/pci[0-9]*/**/size r,

which looks a lot neater, and consistent with the other entries.

---

### Post by nomenkultur on 2013-03-17
maligne cna you copy and paste your chromium profile here or upload it to wherever ?

---

### Post by maglinu on 2013-03-17
Here is the profile as I now have it on my machine. 
The two lines I have added are in red. The first is needed for it to open. The second just stops it complaining.

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


  # Networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,


  # Should maybe be in abstractions
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/mtab r,
  /etc/xdg/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,


  @{PROC}/[0-9]*/fd/ r,
  @{PROC}/filesystems r,
  @{PROC}/ r,
  @{PROC}/[0-9]*/task/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/cmdline r,
  owner @{PROC}/[0-9]*/io r,
  @{PROC}/[0-9]*/smaps r,
  owner @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/statm r,
  owner @{PROC}/[0-9]*/status r,


  # Newer chromium needs these now
  /etc/udev/udev.conf r,
[COLOR=#ff0000]  /sys/devices/pci[0-9]*/**/size r,[/COLOR]
[COLOR=#ff0000]  /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq r,[/COLOR]
  /sys/devices/pci[0-9]*/**/class r,
  /sys/devices/pci[0-9]*/**/device r,
  /sys/devices/pci[0-9]*/**/irq r,
  /sys/devices/pci[0-9]*/**/resource r,
  /sys/devices/pci[0-9]*/**/vendor r,
  /sys/devices/pci[0-9]*/**/removable r,
  /sys/devices/pci[0-9]*/**/uevent r,
  # This is requested, but doesn't seem to actually be needed so deny for now
  deny /run/udev/data/** r,


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


  /bin/ps Uxr,
  /usr/lib/chromium-browser/xdg-settings Cxr -> xdgsettings,
  /usr/bin/xdg-settings Cxr -> xdgsettings,


  profile xdgsettings {
    #include <abstractions/base>
    #include <abstractions/bash>
    #include <abstractions/gnome>


    /bin/dash ixr,


    /usr/bin/xdg-settings r,
    /usr/lib/chromium-browser/xdg-settings r,
    /usr/share/applications/*.desktop r,


    # Checking default browser
    /bin/grep ixr,
    /bin/readlink ixr,
    /bin/sed ixr,
    /bin/which ixr,
    /usr/bin/basename ixr,
    /usr/bin/cut ixr,


    # Setting the default browser
    /bin/mkdir ixr,
    /bin/mv ixr,
    /bin/touch ixr,
    /usr/bin/dirname ixr,
    /usr/bin/gconftool-2 ix,
    /usr/bin/mawk ixr,
    /usr/bin/xdg-mime ixr,
    owner @{HOME}/.local/share/applications/ w,
    owner @{HOME}/.local/share/applications/mimeapps.list* rw,
  }


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
    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/[0-9]*/oom_adj w,
    @{PROC}/[0-9]*/oom_score_adj w,
    @{PROC}/[0-9]*/status r,
    @{PROC}/[0-9]*/task/[0-9]*/stat r,


    /usr/bin/chromium-browser r,
    /usr/lib/chromium-browser/chromium-browser Px,
    /usr/lib/chromium-browser/chromium-browser-sandbox r,


    /dev/null rw,


    owner /tmp/** rw,
  }
}
```

---

