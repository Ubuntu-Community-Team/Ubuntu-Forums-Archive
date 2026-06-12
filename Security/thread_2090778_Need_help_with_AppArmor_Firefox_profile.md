---
title: "Need help with AppArmor Firefox profile"
date: 2012-12-03
forum: Security
---

### Post by donsy on 2012-12-03
I'm in the process of learning all I can about AppArmor but in the meantime I need help with an issue with the default usr.bin.firefox profile that came with my Xubuntu 12.04 distribution. I'm posting it here with line numbers:```
     1    # vim:syntax=apparmor
     2    # Author: Jamie Strandboge <jamie@canonical.com>
     3    
     4    # Declare an apparmor variable to help with overrides
     5    @{MOZ_LIBDIR}=/usr/lib/firefox
     6    
     7    #include <tunables/global>
     8    
     9    # We want to confine the binaries that match:
    10    #  /usr/lib/firefox/firefox
    11    #  /usr/lib/firefox/firefox
    12    # but not:
    13    #  /usr/lib/firefox/firefox.sh
    14    /usr/lib/firefox/firefox{,*[^s][^h]} flags=(complain) {
    15      #include <abstractions/audio>
    16      #include <abstractions/cups-client>
    17      #include <abstractions/dbus-session>
    18      #include <abstractions/gnome>
    19      #include <abstractions/nameservice>
    20      #include <abstractions/p11-kit>
    21    
    22      # Addons
    23      #include <abstractions/ubuntu-browsers.d/firefox>
    24    
    25      # for networking
    26      network inet stream,
    27      network inet6 stream,
    28      @{PROC}/[0-9]*/net/if_inet6 r,
    29      @{PROC}/[0-9]*/net/ipv6_route r,
    30      @{PROC}/[0-9]*/net/dev r,
    31      @{PROC}/[0-9]*/net/wireless r,
    32    
    33      # should maybe be in abstractions
    34      /etc/ r,
    35      /etc/mime.types r,
    36      /etc/mailcap r,
    37      /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
    38      /usr/share/xubuntu/applications/defaults.list r,
    39      owner @{HOME}/.local/share/applications/defaults.list r,
    40      owner @{HOME}/.local/share/applications/mimeapps.list r,
    41      owner @{HOME}/.local/share/applications/mimeinfo.cache r,
    42      owner /tmp/** m,
    43      owner /var/tmp/** m,
    44      /tmp/.X[0-9]*-lock r,
    45    
    46      /etc/timezone r,
    47      /etc/wildmidi/wildmidi.cfg r,
    48    
    49      # firefox specific
    50      /etc/firefox*/ r,
    51      /etc/firefox*/** r,
    52      /etc/xul-ext/** r,
    53      /etc/xulrunner-2.0*/ r,
    54      /etc/xulrunner-2.0*/** r,
    55      /etc/gre.d/ r,
    56      /etc/gre.d/* r,
    57    
    58      # noisy
    59      deny @{MOZ_LIBDIR}/** w,
    60      deny /usr/lib/firefox-addons/** w,
    61      deny /usr/lib/xulrunner-addons/** w,
    62      deny /usr/lib/xulrunner-*/components/*.tmp w,
    63      deny /.suspended r,
    64      deny /boot/initrd.img* r,
    65      deny /boot/vmlinuz* r,
    66      deny /var/cache/fontconfig/ w,
    67      deny @{HOME}/.local/share/recently-used.xbel r,
    68    
    69      # TODO: investigate
    70      deny /usr/bin/gconftool-2 x,
    71    
    72      # These are needed when a new user starts firefox and firefox.sh is used
    73      @{MOZ_LIBDIR}/** ixr,
    74      /usr/bin/basename ixr,
    75      /usr/bin/dirname ixr,
    76      /usr/bin/pwd ixr,
    77      /sbin/killall5 ixr,
    78      /bin/which ixr,
    79      /usr/bin/tr ixr,
    80      @{PROC}/ r,
    81      @{PROC}/[0-9]*/cmdline r,
    82      @{PROC}/[0-9]*/mountinfo r,
    83      @{PROC}/[0-9]*/stat r,
    84      owner @{PROC}/[0-9]*/task/[0-9]*/stat r,
    85      @{PROC}/[0-9]*/status r,
    86      @{PROC}/filesystems r,
    87      owner @{HOME}/.thumbnails/*/*.png r,
    88    
    89      /etc/mtab r,
    90      /etc/fstab r,
    91    
    92      # Needed for the crash reporter
    93      owner @{PROC}/[0-9]*/environ r,
    94      owner @{PROC}/[0-9]*/auxv r,
    95      /etc/lsb-release r,
    96      /usr/bin/expr ix,
    97      /sys/devices/system/cpu/ r,
    98      /sys/devices/system/cpu/** r,
    99    
   100      # about:memory
   101      owner @{PROC}/[0-9]*/statm r,
   102      owner @{PROC}/[0-9]*/smaps r,
   103    
   104      # Needed for container to work in xul builds
   105      /usr/lib/xulrunner-*/plugin-container ixr,
   106    
   107      # allow access to documentation and other files the user may want to look
   108      # at in /usr and /opt
   109      /usr/ r,
   110      /usr/** r,
   111      /opt/ r,
   112      /opt/** r,
   113    
   114      # so browsing directories works
   115      / r,
   116      /**/ r,
   117    
   118      # Default profile allows downloads to ~/Downloads and uploads from ~/Public
   119      owner @{HOME}/ r,
   120      owner @{HOME}/Public/ r,
   121      owner @{HOME}/Public/* r,
   122      owner @{HOME}/Downloads/ r,
   123      owner @{HOME}/Downloads/* rw,
   124    
   125      # per-user firefox configuration
   126      owner @{HOME}/.{firefox,mozilla}/ rw,
   127      owner @{HOME}/.{firefox,mozilla}/** rw,
   128      owner @{HOME}/.{firefox,mozilla}/**/*.{db,parentlock,sqlite}* k,
   129      owner @{HOME}/.{firefox,mozilla}/plugins/** rm,
   130      owner @{HOME}/.{firefox,mozilla}/**/plugins/** rm,
   131      owner @{HOME}/.config/ibus/bus/ w,
   132      owner @{HOME}/.gnome2/firefox*-bin-* rw,
   133    
   134      #
   135      # Extensions
   136      # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
   137      # Allow 'x' for downloaded extensions, but inherit policy for safety
   138      owner @{HOME}/.mozilla/**/extensions/** mixr,
   139    
   140      deny @{MOZ_LIBDIR}/update.test w,
   141      deny /usr/lib/mozilla/extensions/**/ w,
   142      deny /usr/lib/xulrunner-addons/extensions/**/ w,
   143      deny /usr/share/mozilla/extensions/**/ w,
   144      deny /usr/share/mozilla/ w,
   145    
   146      # Miscellaneous (to be abstracted)
   147      # Ideally these would use a child profile. They are all ELF executables
   148      # so running with 'Ux', while not ideal, is ok because we will at least
   149      # benefit from glibc's secure execute.
   150      /usr/bin/mkfifo Uxr,  # investigate
   151      /bin/ps Uxr,
   152      /bin/uname Uxr,
   153    
   154      # Site-specific additions and overrides. See local/README for details.
   155      #include <local/usr.bin.firefox>
   156    }
```This profile does not allow the Parole media player to play a .MOV file  directly from Firefox. Instead it suggests that the file be first downloaded. But I noticed that the file is stored in /tmp regardless. So I thought that maybe commenting out lines 42 and 44 may solve the problem, but  I'm a n00b and don't want to screw anything up. So I'm asking for suggestions on how I can modify this profile, or maybe even install a new firefox profile so that Parole is able to play directly from the browser.

---

### Post by samiux on 2012-12-04
> **donsy said:**
> I'm in the process of learning all I can about AppArmor but in the meantime I need help with an issue with the default usr.bin.firefox profile that came with my Xubuntu 12.04 distribution. I'm posting it here with line numbers:```
     1    # vim:syntax=apparmor
     2    # Author: Jamie Strandboge <jamie@canonical.com>
     3    
     4    # Declare an apparmor variable to help with overrides
     5    @{MOZ_LIBDIR}=/usr/lib/firefox
     6    
     7    #include <tunables/global>
     8    
     9    # We want to confine the binaries that match:
    10    #  /usr/lib/firefox/firefox
    11    #  /usr/lib/firefox/firefox
    12    # but not:
    13    #  /usr/lib/firefox/firefox.sh
    14    /usr/lib/firefox/firefox{,*[^s][^h]} flags=(complain) {
    15      #include <abstractions/audio>
    16      #include <abstractions/cups-client>
    17      #include <abstractions/dbus-session>
    18      #include <abstractions/gnome>
    19      #include <abstractions/nameservice>
    20      #include <abstractions/p11-kit>
    21    
    22      # Addons
    23      #include <abstractions/ubuntu-browsers.d/firefox>
    24    
    25      # for networking
    26      network inet stream,
    27      network inet6 stream,
    28      @{PROC}/[0-9]*/net/if_inet6 r,
    29      @{PROC}/[0-9]*/net/ipv6_route r,
    30      @{PROC}/[0-9]*/net/dev r,
    31      @{PROC}/[0-9]*/net/wireless r,
    32    
    33      # should maybe be in abstractions
    34      /etc/ r,
    35      /etc/mime.types r,
    36      /etc/mailcap r,
    37      /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
    38      /usr/share/xubuntu/applications/defaults.list r,
    39      owner @{HOME}/.local/share/applications/defaults.list r,
    40      owner @{HOME}/.local/share/applications/mimeapps.list r,
    41      owner @{HOME}/.local/share/applications/mimeinfo.cache r,
    42      owner /tmp/** m,
    43      owner /var/tmp/** m,
    44      /tmp/.X[0-9]*-lock r,
    45    
    46      /etc/timezone r,
    47      /etc/wildmidi/wildmidi.cfg r,
    48    
    49      # firefox specific
    50      /etc/firefox*/ r,
    51      /etc/firefox*/** r,
    52      /etc/xul-ext/** r,
    53      /etc/xulrunner-2.0*/ r,
    54      /etc/xulrunner-2.0*/** r,
    55      /etc/gre.d/ r,
    56      /etc/gre.d/* r,
    57    
    58      # noisy
    59      deny @{MOZ_LIBDIR}/** w,
    60      deny /usr/lib/firefox-addons/** w,
    61      deny /usr/lib/xulrunner-addons/** w,
    62      deny /usr/lib/xulrunner-*/components/*.tmp w,
    63      deny /.suspended r,
    64      deny /boot/initrd.img* r,
    65      deny /boot/vmlinuz* r,
    66      deny /var/cache/fontconfig/ w,
    67      deny @{HOME}/.local/share/recently-used.xbel r,
    68    
    69      # TODO: investigate
    70      deny /usr/bin/gconftool-2 x,
    71    
    72      # These are needed when a new user starts firefox and firefox.sh is used
    73      @{MOZ_LIBDIR}/** ixr,
    74      /usr/bin/basename ixr,
    75      /usr/bin/dirname ixr,
    76      /usr/bin/pwd ixr,
    77      /sbin/killall5 ixr,
    78      /bin/which ixr,
    79      /usr/bin/tr ixr,
    80      @{PROC}/ r,
    81      @{PROC}/[0-9]*/cmdline r,
    82      @{PROC}/[0-9]*/mountinfo r,
    83      @{PROC}/[0-9]*/stat r,
    84      owner @{PROC}/[0-9]*/task/[0-9]*/stat r,
    85      @{PROC}/[0-9]*/status r,
    86      @{PROC}/filesystems r,
    87      owner @{HOME}/.thumbnails/*/*.png r,
    88    
    89      /etc/mtab r,
    90      /etc/fstab r,
    91    
    92      # Needed for the crash reporter
    93      owner @{PROC}/[0-9]*/environ r,
    94      owner @{PROC}/[0-9]*/auxv r,
    95      /etc/lsb-release r,
    96      /usr/bin/expr ix,
    97      /sys/devices/system/cpu/ r,
    98      /sys/devices/system/cpu/** r,
    99    
   100      # about:memory
   101      owner @{PROC}/[0-9]*/statm r,
   102      owner @{PROC}/[0-9]*/smaps r,
   103    
   104      # Needed for container to work in xul builds
   105      /usr/lib/xulrunner-*/plugin-container ixr,
   106    
   107      # allow access to documentation and other files the user may want to look
   108      # at in /usr and /opt
   109      /usr/ r,
   110      /usr/** r,
   111      /opt/ r,
   112      /opt/** r,
   113    
   114      # so browsing directories works
   115      / r,
   116      /**/ r,
   117    
   118      # Default profile allows downloads to ~/Downloads and uploads from ~/Public
   119      owner @{HOME}/ r,
   120      owner @{HOME}/Public/ r,
   121      owner @{HOME}/Public/* r,
   122      owner @{HOME}/Downloads/ r,
   123      owner @{HOME}/Downloads/* rw,
   124    
   125      # per-user firefox configuration
   126      owner @{HOME}/.{firefox,mozilla}/ rw,
   127      owner @{HOME}/.{firefox,mozilla}/** rw,
   128      owner @{HOME}/.{firefox,mozilla}/**/*.{db,parentlock,sqlite}* k,
   129      owner @{HOME}/.{firefox,mozilla}/plugins/** rm,
   130      owner @{HOME}/.{firefox,mozilla}/**/plugins/** rm,
   131      owner @{HOME}/.config/ibus/bus/ w,
   132      owner @{HOME}/.gnome2/firefox*-bin-* rw,
   133    
   134      #
   135      # Extensions
   136      # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
   137      # Allow 'x' for downloaded extensions, but inherit policy for safety
   138      owner @{HOME}/.mozilla/**/extensions/** mixr,
   139    
   140      deny @{MOZ_LIBDIR}/update.test w,
   141      deny /usr/lib/mozilla/extensions/**/ w,
   142      deny /usr/lib/xulrunner-addons/extensions/**/ w,
   143      deny /usr/share/mozilla/extensions/**/ w,
   144      deny /usr/share/mozilla/ w,
   145    
   146      # Miscellaneous (to be abstracted)
   147      # Ideally these would use a child profile. They are all ELF executables
   148      # so running with 'Ux', while not ideal, is ok because we will at least
   149      # benefit from glibc's secure execute.
   150      /usr/bin/mkfifo Uxr,  # investigate
   151      /bin/ps Uxr,
   152      /bin/uname Uxr,
   153    
   154      # Site-specific additions and overrides. See local/README for details.
   155      #include <local/usr.bin.firefox>
   156    }
```This profile does not allow the Parole media player to play a .MOV file  directly from Firefox. Instead it suggests that the file be first downloaded. But I noticed that the file is stored in /tmp regardless. So I thought that maybe commenting out lines 42 and 44 may solve the problem, but  I'm a n00b and don't want to screw anything up. So I'm asking for suggestions on how I can modify this profile, or maybe even install a new firefox profile so that Parole is able to play directly from the browser.

I think you need a QuickTime plugin (if any) for Firefox and Parole Media Player if the player can play via browser instead of changing the default Firefox Apparmor profile file.

Samiux

---

### Post by donsy on 2012-12-04
> **samiux said:**
> I think you need a QuickTime plugin (if any) for Firefox and Parole Media Player if the player can play via browser instead of changing the default Firefox Apparmor profile file.

Samiux

I forgot to mention in my original post that after I disabled the firefox profile it works just fine from the browser. This would indicate to me that no extra plugin is required.

---

### Post by samiux on 2012-12-04
> **donsy said:**
> I forgot to mention in my original post that after I disabled the firefox profile it works just fine from the browser. This would indicate to me that no extra plugin is required.

If it is related to /tmp, the line 42 should be looking like this :

```
owner /tmp/** rwk,
```

Samiux

---

### Post by donsy on 2012-12-04
> **samiux said:**
> If it is related to /tmp, the line 42 should be looking like this :

```
owner /tmp/** rwk,
```Samiux

[SIZE=3]Thanks. It worked![/SIZE]

---

### Post by donsy on 2013-01-20
Update: 

It really DIDN'T work. I failed to put usr.bin.firefox in enforce mode. But this apparently did work:
Between lines 79 and 80 I added```
/usr/bin/parole ixr,
```Would appreciate advice on if this presents a security vulnerability or not. Thanks.

---

### Post by samiux on 2013-01-20
> **donsy said:**
> Update: 

It really DIDN'T work. I failed to put usr.bin.firefox in enforce mode. But this apparently did work:
Between lines 79 and 80 I added```
/usr/bin/parole ixr,
```Would appreciate advice on if this presents a security vulnerability or not. Thanks.

No.

---

