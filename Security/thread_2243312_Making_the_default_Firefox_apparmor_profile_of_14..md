---
title: "Making the default Firefox apparmor profile of 14.04 more restrictive"
date: 2014-09-07
forum: Security
---

### Post by linuxyogi on 2014-09-07
Hi,

This is the default FF apparmor profile of 14.04.

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
  #include <abstractions/p11-kit>

  # Addons
  #include <abstractions/ubuntu-browsers.d/firefox>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/wireless r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
  /etc/xfce4/defaults.list r,
  /usr/share/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner /tmp/** m,
  owner /var/tmp/** m,
  /tmp/.X[0-9]*-lock r,
  /etc/udev/udev.conf r,
  # Doesn't seem to be required, but noisy. Maybe allow 'r' for 'b*' if needed.
  # Possibly move to an abstraction if anything else needs it.
  deny /run/udev/data/** r,

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
  /sys/devices/pci[0-9]*/**/uevent r,
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

  # about:memory
  owner @{PROC}/[0-9]*/statm r,
  owner @{PROC}/[0-9]*/smaps r,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # allow access to documentation and other files the user may want to look
  # at in /usr and /opt
  /usr/ r,
  /usr/** r,
  /opt/ r,
  /opt/** r,

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
  owner @{HOME}/.gnome2/firefox*-bin-* rw,
  owner @{HOME}/.cache/mozilla/{,firefox/} rw,
  owner @{HOME}/.cache/mozilla/firefox/** rw,
  owner @{HOME}/.cache/mozilla/firefox/**/*.sqlite k,

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
  /usr/bin/mkfifo Uxr,  # investigate
  /bin/ps Uxr,
  /bin/uname Uxr,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.firefox>
}


```


This is a custom made profile for Transmission-gtk given to me by a member.

> **Lars Noodén said:**
> Here's what I got for Ubuntu 14.04 beta.  It probably works for 12.04.

```

#include <tunables/global>

/usr/bin/transmission-gtk {
  #include <abstractions/base>
  #include <abstractions/gnome>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network inet stream,
  network inet6 stream,

  owner /.Trash-*/ w,

  owner @{HOME}/.Xauthority r,
  owner @{HOME}/.cache/transmission/ w,
  owner @{HOME}/.cache/transmission/** rw,
  owner @{HOME}/.config/dconf/user r,
  owner @{HOME}/.config/gtk-3.0/bookmarks r,
  owner @{HOME}/.config/transmission/ w,
  owner @{HOME}/.config/transmission/** rw,
  owner @{HOME}/.config/user-dirs.dirs r,
  owner @{HOME}/.local/share/Trash/files/* w,
  owner @{HOME}/.local/share/Trash/info/* rw,
  owner @{HOME}/.local/share/applications/ r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner @{HOME}/.local/share/gvfs-metadata/home r,
  owner @{HOME}/.local/share/gvfs-metadata/home-*.log r,
  owner @{HOME}/.local/share/gvfs-metadata/root r,
  owner @{HOME}/.local/share/gvfs-metadata/root-*.log r,
  owner @{HOME}/.local/share/mime/mime.cache r,
  owner @{HOME}/.local/share/recently-used.xbel rw,
  owner @{HOME}/.local/share/recently-used.xbel.* rw,
  owner @{HOME}/Downloads/** r, 
  owner @{HOME}/Downloads/** rw,

  @{PROC}/*/fd/ r,
  @{PROC}/*/mountinfo r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/wireless r,
  @{PROC}/net/ipv6_route r,
  @{PROC}/net/route r,
  @{PROC}/sys/kernel/random/uuid r,

}

```




As you can see ^^ there is not a single **[COLOR=#ff0000]deny[/COLOR]** entry in the above profile. Transmission is allowed access to only those areas of the filesystem without which it cannot function. As you can see from my pic below it working pretty effectively. Here I am trying to browse the filesystem with Transmission's File > open >PCManFM

[IMG]http://s17.postimg.org/svywgtnj3/Selection_018.png[/IMG]




But when when I try to do the same thing with FF (in enforce mode) apparmor is not denying access. In fact I can browse the entire filesystem with FF. I may not have write write permissions coz only root can write in those area but thats the basic security with Linux. 

[IMG]http://s22.postimg.org/h7y6ns0lt/Selection_019.png[/IMG]

```
$ sudo aa-status
apparmor module is loaded.
47 profiles are loaded.
23 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/bin/transmission-gtk
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser//browser_java
   /usr/lib/chromium-browser/chromium-browser//browser_openjdk
   /usr/lib/chromium-browser/chromium-browser//sanitized_helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox{,*[^s][^h]}
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_java
   /usr/lib/firefox/firefox{,*[^s][^h]}//browser_openjdk
   /usr/lib/firefox/firefox{,*[^s][^h]}//sanitized_helper
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
24 profiles are in complain mode.
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/chromium-browser/chromium-browser//chromium_browser_sandbox
   /usr/lib/chromium-browser/chromium-browser//lsb_release
   /usr/lib/chromium-browser/chromium-browser//xdgsettings
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/{sbin/traceroute,bin/traceroute.db}
   /{usr/,}bin/ping
5 processes have profiles defined.
4 processes are in enforce mode.
   /sbin/dhclient (1150) 
   /usr/lib/firefox/firefox{,*[^s][^h]} (1887) 
   /usr/sbin/cupsd (691) 
   /usr/sbin/ntpd (1450) 
1 processes are in complain mode.
   /usr/sbin/dnsmasq (1200) 
0 processes are unconfined but have a profile defined.


```


Dont you think the FF apparmor profile is working at all ?

---

### Post by Lars Noodén on 2014-09-08
I'm not sure how the FF profile is supposed to work with firefox.sh and firefox both.  However, the existing profile does explicitly allow read access to the whole file system:

```

  # so browsing directories works
  / r,
  /**/ r,

```

:( 

As you can see, it's not very tightened down.  However, there is also the question of what all do you want to allow the browser to do?  A profile for basic web surfing will probably be quite different than one that can allow adding add-ons, watching video, listening to audio, etc.

---

### Post by linuxyogi on 2014-09-08
> **Lars Noodén said:**
> I'm not sure how the FF profile is supposed to work with firefox.sh and firefox both.  However, the existing profile does explicitly allow read access to the whole file system:

```

  # so browsing directories works
  / r,
  /**/ r,

```

:( 

As you can see, it's not very tightened down.  However, there is also the question of what all do you want to allow the browser to do?  A profile for basic web surfing will probably be quite different than one that can allow adding add-ons, watching video, listening to audio, etc.

Yes, I noticed those permissions too. God knows what this profile does. I also tried testing the "deny" entries by trying to open those files with Firefox. Sometimes it works meaning apparmor stop and sometimes I can open those files (Ex:in /boot).

When I am boot I am getting crash report pretty regularly related apparmor but they are not about FF.

[This is a profile]("http://ubuntuforums.org/showthread.php?t=1814567&page=2") given to me by bodhi.zazen but this profile is for a standalone FF (downloaded from Mozilla's website).

Very few people can actually learn Apparmor. I tried, progressed a bit then gave up.

---

### Post by vasa1 on 2014-09-08
> Keep in mind a couple of things:
1. The goal of the firefox apparmor profile is not to protect the user from herself, but instead to add a layer of protection against *firefox* executing code and launching other attacks. Due to a number of factors, not least of which usability and development time, the firefox profile will run many helper applications unconfined.

2. Users expect to be able to download and upload files, as well as access those files on removable media. Also, these lines apply to directories only:
  / r,
  /**/ r,

3. The profile explicitly denies read/write access to sensitive files via the priate abstraction and write access to ~/bin (which is in the user's PATH).

All of these things combined does improve the security stance of firefox, by effectively making it run within a sandbox. That said, it is recognized that security minded people and enterprise users will want to make the profile less general purpose and further restrict firefox, which is why the profile is shipped in /etc as a configuration file. It is planned that Ubuntu 10.10 will make it easier to fine browser profiles.

For more information on the design of the profile, please see [https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile](https://wiki.ubuntu.com/SecurityTeam/Specifications/Karmic/AppArmorFirefoxProfile)from [this bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/592121/comments/2")

---

### Post by Lars Noodén on 2014-09-08
Apparmor is much more complex than systrace, but for some reason(s) the latter was not chosen by Ubuntu.  However, the real problems here are the sample profile and the complexity of what Firefox *might* do.  Since the browser can do nearly anything, a universal profile ends up allowing about everything.  The default profile has a lot of #includes and these seem to allow quite a bit.  It's also hard to work in an active home directory, since FF needs to be able to set up files and directories when initializing a new user account.  

What subset of FF capabilities do you want AA to keep and what subset do you want to block?

---

### Post by linuxyogi on 2014-09-08
@Vasa1

But they must understand that a home user may also want extra security. IMHO they should at least provide another set of profiles which are more restrictive.


> **Lars Noodén said:**
> Apparmor is much more complex than systrace, but for some reason(s) the latter was not chosen by Ubuntu.  However, the real problems here are the sample profile and the complexity of what Firefox *might* do.  Since the browser can do nearly anything, a universal profile ends up allowing about everything.  The default profile has a lot of #includes and these seem to allow quite a bit.  It's also hard to work in an active home directory, since FF needs to be able to set up files and directories when initializing a new user account.  

What subset of FF capabilities do you want AA to keep and what subset do you want to block?

I want to restrict FF to only those parts of / without which it cannot function. Read or write access as per need. 

Same in case of the home folder. Other than that only read/write access to ~/Downloads so that FF cannot read or write to any files or folder that I have created or which are there by default like ~/Music, ~/Documents, etc.

---

### Post by vasa1 on 2014-09-08
@Linuxyogi, I played around with Apparmor quite a bit in late 2011: A good way to learn about it is to make your own profile. I had made profiles for Firefox and Seamonkey (both of which were not from the software center and were installed in my home folder), Google Chrome and Privoxy.

There's a guide somewhere here by bodhi.zazen on how to make your own profile. If I find the link I'll post it.

---

### Post by linuxyogi on 2014-09-08
@Vasa

aa-genprof of 14.04 doesn't work. Creating a new profile won't be possible.

---

### Post by vasa1 on 2014-09-08
> **linuxyogi said:**
> @Vasa

aa-genprof of 14.04 doesn't work. Creating a new profile won't be possible.Wow! Any idea why?

This: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1319829](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1319829) ?

---

### Post by linuxyogi on 2014-09-08
Yes. Really frustrating. After I found that I went to #apparmor on Freenode. They told me the fix will be added to 14.10.

---

### Post by vasa1 on 2014-09-08
According to [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1319829/comments/15](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1319829/comments/15) it should appear in 14.04 eventually.

---

### Post by linuxyogi on 2014-09-08
Okay. Then he must have said 14.04 then. Actually I went to that channel thinking everybody must be making profiles all day there in the holy city of apparmor. 

But unfortunately the only one who answered was not using 14.04 so it was quite frustrating.

---

### Post by Lars Noodén on 2014-09-08
Here's one that is more restrictive but has some rough edges.  I'm not proficient with apparmor or firefox.  The profile seems to work well enough to do downloads and I tested it with HTML5 videos on Youtube.  

```

#include <tunables/global>

/usr/lib/firefox/firefox {
  #include <abstractions/base>
  #include <abstractions/lightdm>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network inet stream,
  network inet6 stream,

  owner @{HOME}/.Xauthority r,

  owner @{HOME}/.cache/ rw,
  owner @{HOME}/.cache/mozilla/{,firefox/} rw,
  owner @{HOME}/.cache/mozilla/firefox/** rw,
  owner @{HOME}/.cache/mozilla/firefox/**/*.sqlite k,

  owner @{HOME}/.mozilla/ rw,
  owner @{HOME}/.mozilla/** rw,
  owner @{HOME}/.mozilla/**/*.{db,parentlock,sqlite}* k,

  owner @{HOME}/.local/share/unity-webapps/ rw,
  owner @{HOME}/.local/share/unity-webapps/* rw,
  owner @{HOME}/.local/share/unity-webapps/availableapps-v2.db rwk,

  owner @{HOME}/.config/dconf/user r,
  owner @{HOME}/.config/user-dirs.dirs r,

  owner @{HOME}/.dbus/ rw,
  owner @{HOME}/.dbus/session-bus/ rw,
  owner @{HOME}/.dbus/session-bus/* rwl,

  owner @{HOME}/.gconf/ r,
  owner @{HOME}/.config/gtk-3.0/ r,
  owner @{HOME}/.config/gtk-3.0/bookmarks r,

  owner @{HOME}/Downloads/ rw,
  owner @{HOME}/Downloads/** rw,

  @{PROC}/*/fd/ r,
  @{PROC}/*/mountinfo r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/wireless r,
  @{PROC}/net/ipv6_route r,
  @{PROC}/net/route r,
  @{PROC}/sys/kernel/random/uuid r,

}


```

Unfortunately it still allows read access to much of the system.  There's not much that can be done about that, I think.  But most of the user directories, except for ~/Downloads, are blocked.  

It might be that two profiles are needed, one slightly looser for the initialization of Firefox and its add-ons.  Then another more restrictive one with more read-only options for regular use.  This one should work even when starting a fresh Firefox profile.

---

### Post by linuxyogi on 2014-09-08
I did

```
cd /etc/apparmor.d
```

```
sudo aa-enforce usr.bin.firefox
```

```
sudo /etc/init.d apparmor reload
```

Then tried browsing my home folder with FF, all files and folders are accessible. 

```
$ sudo aa-status
apparmor module is loaded.
16 profiles are loaded.
16 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/firefox/firefox
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/sbin/cupsd
   /usr/sbin/ntpd
   /usr/sbin/tcpdump
0 profiles are in complain mode.
4 processes have profiles defined.
3 processes are in enforce mode.
   /sbin/dhclient (1023) 
   /usr/sbin/cupsd (907) 
   /usr/sbin/ntpd (1405) 
0 processes are in complain mode.
1 processes are unconfined but have a profile defined.
   /usr/lib/firefox/firefox (1427) 


```


```
$ sudo aa-enforce usr.bin.firefox /usr/bin/firefox 
Setting /etc/apparmor.d/usr.bin.firefox to enforce mode.
Profile for /usr/lib/firefox/firefox.sh not found, skipping

```

---

### Post by Lars Noodén on 2014-09-08
I'm pretty sure you also have to quit and re-run Firefox after applying the changes to apparmor.  That's what I have been doing to test the profile.

---

### Post by linuxyogi on 2014-09-08
> **Lars Noodén said:**
> I'm pretty sure you also have to quit and re-run Firefox after applying the changes to apparmor.  That's what I have been doing to test the profile.

I did that earlier after enforcing the profile but for some reason it didn't work. This time I closed FF then disabled the profile then enforced it again, reloaded apparmor and now it works.

/boot is completely blocked. Only ~/Download has rw. That's awesome !  

But how did you manage to create this profile coz aa-genprof is broken in 14.04.

Thanks a lot ! [IMG]http://s3.postimg.org/s9iat7ytr/step0001.jpg[/IMG]

---

### Post by Lars Noodén on 2014-09-08
Yes, aa-genprof is broken. 

I started by stripping down the one I made for transmission, removing the pieces that were obviously transmission-specific, and then set apparmor to enforce.  

I had an extra window up with *tail -f /var/log/syslog | grep -P 'DENIED.*name="[^"]*"'* running in it, to collect and highlight the errors.  Then in another window, I had a line in bash to remove the firefox profile directories, reload the apparmor profile and then launch firefox. Each time I ran the browser, I addressed the first new error that popped up in syslog.  Repeat dozens of times.  

If you look at the profile, there are still some other directories writeable but mostly it is strapped down.  If you look at the errors in syslog, there are a few still, but they don't seem to affect the performance and would open more directories for writing.  So I left them unaddressed.  

The big breakthrough was finding web pages that pointed to /usr/lib/firefox/firefox.  Maybe that's not right but it gives the appearance of working.

---

