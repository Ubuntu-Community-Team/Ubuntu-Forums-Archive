---
title: "AppArmor Deny"
date: 2011-09-01
forum: Security
---

### Post by duke.tim on 2011-09-01
Summary: The goal here was to block network access to two programs, ping, and respectivly , chromium-browser. Using the deny network, statement works in ping yet does not in chromium; thus chromium connects to the internet regardless (which is unwanted).

So from what I understood from the man page and various websites is that in an AppArmor profile you can use the deny statment to prevent a program from using a rule.

> When there is no corresponding rule for a resource, AppArmor will block access to the resource and log it. When there is a rule in the policy, access is allowed to the resource without logging. The following modifiers can be prepended to a rule to change this behavior: deny: explicitly deny, without logging

So for example using ping with this profile
```
# Last Modified: 
#include <tunables/global>

/bin/ping {
  #include <abstractions/base>
  #include <abstractions/nameservice>


  capability net_raw,
  network inet,
  deny network,
  

}
```

I can easily block the program ping from accessing network resources 

> duke@duke-VirtualBox:/etc/apparmor.d$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


Yet when the same deny statement is applied to a program such as chromium

```
# Author: Jamie Strandboge <jamie@canonical.com>
#include <tunables/global>

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
  audit deny network,
  audit deny network inet stream,
  deny network inet6 stream,
  deny @{PROC}/[0-9]*/net/if_inet6 r,
  deny @{PROC}/[0-9]*/net/ipv6_route r,
  deny capability net_raw,

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

  # Needed for the crash reporter
  owner @{PROC}/[0-9]*/auxv r,

  # chromium mmaps all kinds of things for speed.
  /etc/passwd m,
  /usr/share/fonts/truetype/**/*.tt[cf] m,
  /usr/share/fonts/**/*.pfb m,
  /usr/share/mime/mime.cache m,
  /usr/share/icons/**/*.cache m,
  owner /dev/shm/pulse-shm* m,
  owner @{HOME}/.local/share/mime/mime.cache m,
  owner /tmp/** m,

  @{PROC}/sys/kernel/shmmax r,
  owner /dev/shm/{,.}org.chromium.* mrw,

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
  @{PROC}/[0-9]*/oom_adj w,
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
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/[0-9]*/oom_adj w,

    /usr/bin/chromium-browser r,
    /usr/lib/chromium-browser/chromium-browser Px,
    /usr/lib/chromium-browser/chromium-browser-sandbox r,

    owner /tmp/** rw,
  }
}
```

It doesn't work (I also tried a simplified version via aa-genprof)

This is what is says in the log
> ep  1 14:59:57 duke-VirtualBox kernel: [10886.227562] type=1400 audit(1314914397.667:178184): apparmor="ALLOWED" operation="recvmsg" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" pid=9933 comm="chromium-browse" laddr=10.0.2.15 lport=38112 faddr=64.18.21.1 fport=80 family="inet" sock_type="stream" protocol=6
Sep  1 14:59:57 duke-VirtualBox kernel: [10886.232363] type=1400 audit(1314914397.671:178185): apparmor="ALLOWED" operation="recvmsg" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" pid=9933 comm="chromium-browse" laddr=10.0.2.15 lport=36916 faddr=194.7.155.81 fport=80 family="inet" sock_type="stream" protocol=6
Sep  1 14:59:57 duke-VirtualBox kernel: [10886.232856] type=1400 audit(1314914397.671:178186): apparmor="ALLOWED" operation="recvmsg" parent=1 profile="/usr/lib/chromium-browser/chromium-browser" pid=9933 comm="chromium-browse" laddr=10.0.2.15 lport=56718 faddr=69.171.228.14 fport=443 family="inet" sock_type="stream" protocol=6


---

### Post by bodhi.zazen on 2011-09-02
Your profile is in complain mode 

> /usr/lib/chromium-browser/chromium-browser **[color=darkred][size=2]flags=(complain)[/color]**[/size]

You need to put it into enforcing mode ;)

---

### Post by duke.tim on 2011-09-02
Thanks for taking the time to check all of that out. 8-[... I kinda feel stupid now :lolflag:

---

### Post by bodhi.zazen on 2011-09-02
> **duke.tim said:**
> Thanks for taking the time to check all of that out. 8-[... I kinda feel stupid now :lolflag:

No problem, I have made similar mistakes countless times.

This is why it helps to post error messages and in your case the config file ;)

Sometimes it just takes a second set of eyes

---

