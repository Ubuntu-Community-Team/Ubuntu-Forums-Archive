---
title: "Share your AppArmor Profiles"
date: 2008-12-12
forum: Security
---

### Post by bodhi.zazen on 2008-12-12
In order to promote awareness and learning of AppArmor I thought it migh help if we shared our profiles. Hopefully they can be reviewed by experts and help others learn the syntax of an AppArmor Profile.

Here is my Firefox Profile

Firefox version 3.0.4
Ubuntu 9.04 Alpha

> # Last Modified: Thu Dec 11 21:08:14 2008
#include <tunables/global>

/usr/lib/firefox-3.0.4/firefox.sh {
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network dgram,
  network stream,

  /bin/dash rix,
  /bin/grep rix,
  /bin/ps rix,
  /usr/bin/basename rix,
  /usr/lib/firefox-3.0.4/firefox mrix,
  /usr/lib/gamin/gam_server mrix,

  /dev/shm/ r,
  owner /dev/shm/pulse-* rw,
  /etc/ r,
  /etc/firefox-3.0/pref/ r,
  /etc/firefox-3.0/pref/* r,
  /etc/gre.d/ r,
  /etc/gre.d/1.9.0.4.system.conf r,
  /etc/mime.types r,
  /etc/pulse/client.conf r,
  /etc/sound/events/gtk-events-2.soundlist r,
  /etc/xulrunner-1.9/system-greprefs.js r,
  owner /home/** rw,
  owner /home/*/.adobe/ rw,
  owner /home/*/.adobe/** rw,
  owner /home/*/.config/gtk-2.0/** rwk,
  owner /home/*/.macromedia/ w,
  owner /home/*/.macromedia/** rw,
  owner /home/*/.mozilla/** rwk,
  owner /home/*/.pulse-cookie rwk,
  owner /home/*/.pulse/ w,
  owner /home/*/{Desktop,Documents,Downloads}/ rw,
  owner /home/*/{Desktop,Documents,Downloads}/** rw,

  owner /proc/*/maps r,
  /proc/*/mounts/* r,
  owner /proc/*/stat r,
  /proc/version r,
  /usr/local/share/** r,
  /usr/share/** r,
  /var/lib/dbus/machine-id r,

}

Enjoy (and try not to abuse my poor quality profile too much).

---

### Post by PmDematagoda on 2008-12-12
I made a Firefox profile myself, but it never was completed because I wanted to lock it down where-ever access was not necessary, which is really difficult due to specific use-cases of certain users, etc.

Anyway, here's the profile(I know, it hasn't been worked on for a long time):-
```
# Last Modified: Thu Jun 19 08:47:03 2008
#include <tunables/global>
/usr/lib/firefox-3.0/firefox.sh {
  #include <abstractions/base> 
  #include <abstractions/gnome>
  #include <abstractions/fonts>
  network inet,
  network inet6,
  
  /bin/dash rix,
  /etc/gai.conf r,
  /etc/passwd r,
  /etc/nsswitch.conf r,
  /usr/lib/libgconf2-4/gconfd-2 ix,
  /etc/gre.d/* r,
  /etc/gre.d/ r,
  /etc/firefox-3.0/** rw,
  /etc/firefox-3.0/* rw,
  /usr/lib/firefox-3.0/firefox.sh mr,
  /usr/lib/firefox-3.0/** rwix,
  /usr/share/ubufox/** r,
  /usr/share/applications/** r,
  /usr/share/icons/** r,
  #/tmp/** rw,
  #/tmp/ rw,
  /usr/share/myspell/dicts/* r,
  /usr/share/myspell/dicts/ r,
  /usr/share/mime/** r,
  /etc/hosts r,
  /etc/resolv.conf r,

#These are needed if you need to hear any sounds at all.
  /dev/snd/** rw,
  /usr/share/alsa/alsa.conf r,

#To use Gnash, these permissions have to be given.
  /usr/lib/gnash/ m,
  @{HOME}/.gstreamer-0.10/registry.* rw,
  /usr/share/gnash/* r,
  /usr/bin/gtk-gnash mixr,

#The permissions required for Flash 10.
  @{HOME}/.macromedia/** rw,
  @{HOME}/.adobe/** r,
  /usr/lib/locale/en_US.utf8/* r,
  
#Note:- The rule allows Fx to read other processes, this has to be done since Flash absolutely requires this otherwise the browser would crash.  
  @{PROC}/*/maps r,

#The permissions it has within home in order to function as required.
  @{HOME}/Downloads/ rw,
  @{HOME}/Downloads/** rw,
  @{HOME}/.mozilla/firefox/97peui19.default/*.sqlite* rwk,
  @{HOME}/.mozilla/firefox/97peui19.default/** rw,
  @{HOME}/.mozilla/firefox/97peui19.default/ rw,
  @{HOME}/.mozilla/firefox/* rw,
  @{HOME}/.mozilla/firefox/97peui19.default/.parentlock k,
  @{HOME}/.mozilla/extensions/** rw,
  @{HOME}/.config/gtk-2.0/gtkfilechooser.ini* rw,

#Sun Java 6 requires these permissions.
  /usr/lib/jvm/java-6-sun*/jre/** mrix,
  /etc/java-6-sun/* r,
  /etc/java-6-sun/** r,
  @{HOME}/.java/ wr,
  @{HOME}/.java/** wr,
  @{HOME}/.java/deployment/** k,

}

```

Also, this [thread]("http://ubuntuforums.org/showthread.php?t=833839") may be of interest.

Edit:- If you really want a profile that allows the program to work properly in addition to providing good security, then you must do it yourself, and have a good understanding of the inner workings of the program involved. An automatically generated profile is not terrible, but it does tend to allow access to unnecessary resources or files which could be exploited by malware or hackers.

---

### Post by jgoguen on 2008-12-12
I put together a profile for Pidgin and XChat.  The Pidgin profile allows downloading to only a specific folder, and allows uploading from any folder under $HOME, and external applications can't be executed.  The XChat profile doesn't allow downloading or uploading at all, and no external applications.

```
#include <tunables/global>
/usr/bin/pidgin {
    #include <abstractions/base>

    capability sys_ptrace,

    network inet stream,
    network inet dgram,
    network inet6 stream,
    network inet6 dgram,

    owner @{HOME}/** r,
    owner @{HOME}/.aspell* rk,
    owner @{HOME}/.config/enchant/* rk,
    owner @{HOME}/.fonts.conf r,
    owner @{HOME}/.gtk-bookmarks r,
    owner @{HOME}/.ICEauthority r,
    owner @{HOME}/.local/share/mime/* r,
    owner @{HOME}/.Xauthority r,

    owner @{PROC}/*/fd/ r,
    owner @{PROC}/*/maps r,
    owner @{PROC}/*/mounts r,

    /dev/shm/ r,

    /etc/ r,
    /etc/fonts/** r,
    /etc/ssl/certs/ r,
    /etc/gai.conf r,
    /etc/host.conf r,
    /etc/hosts r,
    /etc/nsswitch.conf r,
    /etc/passwd r,
    /etc/pulse/client.conf r,
    /etc/resolvconf/run/resolv.conf r,

    /usr/bin/pidgin r,

    /usr/lib/ r,
    /usr/lib/gtk-*/**.so rm,
    /usr/lib/libvisual-*/**.so rm,
    /usr/lib/pango/**.so rm,
    /usr/lib/pidgin/*.so rm,
    /usr/lib/purple*/*.so rm,

    /usr/local/share/icons/ r,
    /usr/share/fonts/ r,
    /usr/share/fonts/** r,
    /usr/share/gvfs/remote-volume-monitors/ r,
    /usr/share/gvfs/remote-volume-monitors/* r,
    /usr/share/icons/ r,
    /usr/share/icons/** r,
    /usr/share/locale-langpack/** r,
    /usr/share/mime/* r,
    /usr/share/myspell/dicts/ r,
    /usr/share/myspell/dicts/** r,
    /usr/share/pixmaps/ r,
    /usr/share/pixmaps/** r,
    /usr/share/sounds/purple/* r,
    /usr/share/tcltk/** r,
    /usr/share/themes/** r,
    /usr/share/enchant/enchant.ordering r,

    /var/cache/fontconfig/** r,
    /var/lib/aspell/** r,
    /var/lib/defoma/** r,

    owner /tmp/orbit-*/ w,
    /tmp/.ICE-unix/* w,
    /tmp/.X11-unix/* w,
    owner /tmp/pulse-*/* w,

    /var/run/dbus/system_bus_socket w,

    owner @{HOME}/.config/gtk-*/** rw,
    owner @{HOME}/.gnome2/nautilus-sendto/** rw,
    owner @{HOME}/.purple/ rw,
    owner @{HOME}/.purple/** rwk,
    owner @{HOME}/.recently-used* rw,
    owner @{HOME}/Downloads/ rw,
    owner @{HOME}/Downloads/** rw,

    /dev/shm/* rw,
    /dev/tty rw,

    /tmp/ rw,
    /tmp/orbit-*/* w,

    /var/tmp/ rw,

    @{HOME}/.gstreamer*/* ra,

    /usr/bin/gconftool-2 rix,
    /usr/bin/gnome-default-applications-properties ix,
    /usr/bin/gnome-network-preferences ix,
    /usr/bin/launchpad-integration ix,
}
```
I worry that it's a little too permissive, especially around /dev/shm/ and some of the config directories under $HOME.

```
#include <tunables/global>
/usr/bin/xchat {
    #include <abstractions/base>

    network inet stream,
    network inet dgram,
    network inet6 stream,
    network inet6 dgram,

    @{HOME}/ r,
    @{HOME}/.config/** r,
    @{HOME}/.icons/ r,
    @{HOME}/.local/share/icons/ r,
    @{HOME}/.aspell* r,
    @{HOME}/.config/enchant/* rk,
    @{HOME}/.fonts.conf r,
    @{HOME}/.local/share/mime/* r,
    @{HOME}/.Xauthority r,

    @{PROC}/*/mounts r,

    /etc/fonts/** r,
    /etc/host.conf r,
    /etc/hosts r,
    /etc/nsswitch.conf r,
    /etc/passwd r,
    /etc/resolvconf/run/resolv.conf r,

    /usr/bin/xchat r,

    /usr/lib/gtk-*/**.so rm,
    /usr/lib/pango/**.so rm,
    /usr/lib/xchat/plugins/*.so rm,

    /usr/local/share/icons/ r,

    /usr/share/fonts/ r,
    /usr/share/fonts/** r,
    /usr/share/gvfs/remote-volume-monitors/ r,
    /usr/share/icons/ r,
    /usr/share/icons/** r,
    /usr/share/locale-langpack/** r,
    /usr/share/mime/* r,
    /usr/share/myspell/dicts/ r,
    /usr/share/myspell/dicts/** r,
    /usr/share/pixmaps/ r,
    /usr/share/themes/** r,
    /usr/share/enchant/enchant.ordering r,

    /var/cache/fontconfig/** r,
    /var/lib/aspell/** r,
    /var/lib/defoma/** r,

    /tmp/.X11-unix/* w,

    /var/run/dbus/system_bus_socket w,

    @{HOME}/.xchat2/** rwk,

    /usr/bin/launchpad-integration ix,
}
```

---

### Post by teddks on 2008-12-28
I don't suppose there would be a way to write different AppArmor profiles for different Firefox profiles, would there? I would love to limit how much access Firefox has to my system, but I have one profile for anonymous browsing and another for non-anonymous browsing, and obviously have different threat models for both.

---

### Post by bodhi.zazen on 2008-12-28
> **teddks said:**
> I don't suppose there would be a way to write different AppArmor profiles for different Firefox profiles, would there? I would love to limit how much access Firefox has to my system, but I have one profile for anonymous browsing and another for non-anonymous browsing, and obviously have different threat models for both.

Yes it is easy, a bit of a hack really.

Make a hard link

```
sudo ln /usr/bin/firefox-restricted /usr/lib/firefox-3.0.5/firefox.sh
```

Now make an apparmor profile for firefox-restricted

---

### Post by teddks on 2008-12-28
> **bodhi.zazen said:**
> Yes it is easy, a bit of a hack really.

Make a hard link

```
sudo ln /usr/bin/firefox-restricted /usr/lib/firefox-3.0.5/firefox.sh
```

Now make an apparmor profile for firefox-restricted

Ah, alright. Thanks. Will linking to the /usr/bin/firefox link work, as well? I'd like to avoid doing this every version bump...

---

### Post by teddks on 2008-12-28
> **jgoguen said:**
> I put together a profile for Pidgin and XChat.  The Pidgin profile allows downloading to only a specific folder, and allows uploading from any folder under $HOME, and external applications can't be executed.  The XChat profile doesn't allow downloading or uploading at all, and no external applications.

```
#include <tunables/global>
/usr/bin/pidgin {
    #include <abstractions/base>

    capability sys_ptrace,

    network inet stream,
    network inet dgram,
    network inet6 stream,
    network inet6 dgram,

    owner @{HOME}/** r,
    owner @{HOME}/.aspell* rk,
    owner @{HOME}/.config/enchant/* rk,
    owner @{HOME}/.fonts.conf r,
    owner @{HOME}/.gtk-bookmarks r,
    owner @{HOME}/.ICEauthority r,
    owner @{HOME}/.local/share/mime/* r,
    owner @{HOME}/.Xauthority r,

    owner @{PROC}/*/fd/ r,
    owner @{PROC}/*/maps r,
    owner @{PROC}/*/mounts r,

    /dev/shm/ r,

    /etc/ r,
    /etc/fonts/** r,
    /etc/ssl/certs/ r,
    /etc/gai.conf r,
    /etc/host.conf r,
    /etc/hosts r,
    /etc/nsswitch.conf r,
    /etc/passwd r,
    /etc/pulse/client.conf r,
    /etc/resolvconf/run/resolv.conf r,

    /usr/bin/pidgin r,

    /usr/lib/ r,
    /usr/lib/gtk-*/**.so rm,
    /usr/lib/libvisual-*/**.so rm,
    /usr/lib/pango/**.so rm,
    /usr/lib/pidgin/*.so rm,
    /usr/lib/purple*/*.so rm,

    /usr/local/share/icons/ r,
    /usr/share/fonts/ r,
    /usr/share/fonts/** r,
    /usr/share/gvfs/remote-volume-monitors/ r,
    /usr/share/gvfs/remote-volume-monitors/* r,
    /usr/share/icons/ r,
    /usr/share/icons/** r,
    /usr/share/locale-langpack/** r,
    /usr/share/mime/* r,
    /usr/share/myspell/dicts/ r,
    /usr/share/myspell/dicts/** r,
    /usr/share/pixmaps/ r,
    /usr/share/pixmaps/** r,
    /usr/share/sounds/purple/* r,
    /usr/share/tcltk/** r,
    /usr/share/themes/** r,
    /usr/share/enchant/enchant.ordering r,

    /var/cache/fontconfig/** r,
    /var/lib/aspell/** r,
    /var/lib/defoma/** r,

    owner /tmp/orbit-*/ w,
    /tmp/.ICE-unix/* w,
    /tmp/.X11-unix/* w,
    owner /tmp/pulse-*/* w,

    /var/run/dbus/system_bus_socket w,

    owner @{HOME}/.config/gtk-*/** rw,
    owner @{HOME}/.gnome2/nautilus-sendto/** rw,
    owner @{HOME}/.purple/ rw,
    owner @{HOME}/.purple/** rwk,
    owner @{HOME}/.recently-used* rw,
    owner @{HOME}/Downloads/ rw,
    owner @{HOME}/Downloads/** rw,

    /dev/shm/* rw,
    /dev/tty rw,

    /tmp/ rw,
    /tmp/orbit-*/* w,

    /var/tmp/ rw,

    @{HOME}/.gstreamer*/* ra,

    /usr/bin/gconftool-2 rix,
    /usr/bin/gnome-default-applications-properties ix,
    /usr/bin/gnome-network-preferences ix,
    /usr/bin/launchpad-integration ix,
}
```
I worry that it's a little too permissive, especially around /dev/shm/ and some of the config directories under $HOME.


I added this to allow opening URL:

```
/usr/bin/gnome-open Ux,
```

Is that too insecure?

---

### Post by bodhi.zazen on 2008-12-28
First, IMO, nothing is "too insecure" per say, but I would try running with irx rather then Ux

Second, I am not 100 % about the link, it was just a suggestion. I know it works with bash but I have not tried it with firefox.

---

### Post by teddks on 2008-12-29
> **bodhi.zazen said:**
> First, IMO, nothing is "too insecure" per say, but I would try running with irx rather then Ux

Second, I am not 100 % about the link, it was just a suggestion. I know it works with bash but I have not tried it with firefox.

Doesn't work with rix. I suppose I could write a profile for gnome-open, but pidgin's profile is just not good enough. I would need to give pidgin permissions for xdg-open, /etc/orbitrc, and dash, among other things.

As for the link: It seems that making a hard link to a symbolic link just causes it to resolve the symbolic link. Would making a script that called firefox with profile arguments work?

---

### Post by jgoguen on 2008-12-29
Using ix would require gnome-open to be restricted by the same profile as Firefox.  So without giving Firefox access to everything gnome-open needs as well, using ix won't work.  Same goes for any other profile.

---

### Post by bodhi.zazen on 2008-12-29
> **teddks said:**
> Doesn't work with rix. I suppose I could write a profile for gnome-open, but pidgin's profile is just not good enough. I would need to give pidgin permissions for xdg-open, /etc/orbitrc, and dash, among other things.

As for the link: It seems that making a hard link to a symbolic link just causes it to resolve the symbolic link. Would making a script that called firefox with profile arguments work?

Not a script with apparmor profile arguments ...

You can write a script that calls firefox (with irx) and restrict firefox.

And yes, go ahead and call gnome-open with irx, and any other binary it needs (like xdg-open, /etc/orbitrc, and dash) They will all be called, but restricted.

IMO this is better then Ux, which will call the same xdg-open, /etc/orbitrc, and dash (via gnome-open) but in the case of Ux they will run unrestricted, essentially "breaking out" of your apparmor profile.

With apparmor calling these things is not a problem so long as you use irx and they are what you consider "normal functioning" of firefox.

---

### Post by teddks on 2008-12-29
> **bodhi.zazen said:**
> Not a script with apparmor profile arguments ...

You can write a script that calls firefox (with irx) and restrict firefox.

And yes, go ahead and call gnome-open with irx, and any other binary it needs (like xdg-open, /etc/orbitrc, and dash) They will all be called, but restricted.

IMO this is better then Ux, which will call the same xdg-open, /etc/orbitrc, and dash (via gnome-open) but in the case of Ux they will run unrestricted, essentially "breaking out" of your apparmor profile.

With apparmor calling these things is not a problem so long as you use irx and they are what you consider "normal functioning" of firefox.

You're confusing two questions. I have two firefox profiles I use for different purposes. I want different apparmor profiles on them. I was asking if I made a script that called /usr/bin/firefox and provided it with the arguments to access one of those two profiles, would it work. I suppose it would, as firefox would just inherit the other script's profile. Would that override a profile for Firefox, is the question...

As to the other thread of discussion, I don't think ix is better than Ux here, because I have to give Pidgin rights to whatever I want gnome-open to do. gnome-open will eventually call firefox on my system, and if it inherits everything down to that, then I'll be running firefox with Pidgin's limitations. That doesn't seem like a smart policy -- I actually _want_ gnome-open to break out of my Pidgin profile, because it doesn't belong there. I should write a profile for gnome-open, though.

On a side note, does anyone have a profile for Evolution or Totem?

---

### Post by PmDematagoda on 2008-12-30
> **teddks said:**
> You're confusing two questions. I have two firefox profiles I use for different purposes. I want different apparmor profiles on them. I was asking if I made a script that called /usr/bin/firefox and provided it with the arguments to access one of those two profiles, would it work. I suppose it would, as firefox would just inherit the other script's profile. Would that override a profile for Firefox, is the question...

As to the other thread of discussion, I don't think ix is better than Ux here, because I have to give Pidgin rights to whatever I want gnome-open to do. gnome-open will eventually call firefox on my system, and if it inherits everything down to that, then I'll be running firefox with Pidgin's limitations. That doesn't seem like a smart policy -- I actually _want_ gnome-open to break out of my Pidgin profile, because it doesn't belong there. I should write a profile for gnome-open, though.

On a side note, does anyone have a profile for Evolution or Totem?

Firefox doesn't choose the profile it runs with, no application can do that. The profiles are enforced by Apparmor and only Apparmor, if you want to change the profile used when Firefox is to be run, then you need to address the script to remove one profile and add another through Apparmor, which requires root privileges.

For gnome-open, yes, writing a separate profile for it would be better.

About Evolution or Totem, I'll see if I can rustle up profiles for them when I have time:).

A note about Apparmor, it enforces profiles using paths, so if you linked a path to the firefox executable, then the profile that was made for the old path will most likely apply since the real path is still the same.

---

### Post by teddks on 2008-12-30
> **PmDematagoda said:**
> Firefox doesn't choose the profile it runs with, no application can do that. The profiles are enforced by Apparmor and only Apparmor, if you want to change the profile used when Firefox is to be run, then you need to address the script to remove one profile and add another through Apparmor, which requires root privileges.

For gnome-open, yes, writing a separate profile for it would be better.

About Evolution or Totem, I'll see if I can rustle up profiles for them when I have time:).

A note about Apparmor, it enforces profiles using paths, so if you linked a path to the firefox executable, then the profile that was made for the old path will most likely apply since the real path is still the same.

Firefox profile, not Apparmor profile. :)

---

### Post by brandon88tube on 2008-12-30
I'm not using AppArmor yet, but I was looking into it. I wanted to know if anyone had a Transmission profile that they were willing to share. Maybe if I had AppArmor running with a profile I might start using Transmission.

---

### Post by PmDematagoda on 2008-12-30
> **teddks said:**
> Firefox profile, not Apparmor profile. :)

Uhm, I think I just lost you. :)

Could you please explain your situation again please?

---

### Post by teddks on 2008-12-30
> **PmDematagoda said:**
> Uhm, I think I just lost you. :)

Could you please explain your situation again please?

Firefox supports profiles. I have one for normal browsing and one for anonymous browsing. I would like to have one AppArmor profile per Firefox profile, as the two different Firefox profiles have different security needs.

---

### Post by q.dinar on 2009-01-16
hello.
what do they do with /etc/passwd?
what is the difference between r:: and ::r in log?

---

### Post by jgoguen on 2009-01-16
/etc/passwd is often read to get the username associated with a user ID.  When you run **ls -l** in the Terminal, for example, the owner and group of the file is stored as a number, like **1000**.  The ls program will go to /etc/passwd and basically ask "what is the username for user ID 1000".

r:: means that read permissions for user were requested, while ::r means that read permissions for "other" (not user or group) were requested.  If you saw :r: instead, it would mean that read permissions for group were requested.

---

### Post by jgoguen on 2009-01-16
> **teddks said:**
> Firefox supports profiles. I have one for normal browsing and one for anonymous browsing. I would like to have one AppArmor profile per Firefox profile, as the two different Firefox profiles have different security needs.
Firefox accepts the **-P** option, which specifies a name of a profile to use.  If given, Firefox will load that profile.
```
firefox -P <profile name>
```

---

### Post by q.dinar on 2009-01-17
i thought that passwords are stored in /etc/passwd. but it is not so.

now i have been making profile for virtualbox and have searched how to allow "capability"s in log. have found there by searching "capability apparmor.d" in google: [https://help.ubuntu.com/8.04/serverguide/C/apparmor.html](https://help.ubuntu.com/8.04/serverguide/C/apparmor.html) .

i cannot change r for user or group or others in apparmor.d as it does not matter, am i, is it so ? 

sometimes "requested mask" and "denied mask" in log are different, i write to rule which is for more permissions. i have now thought/guessed that "denied .." means which part of permission is needed.

a and w permissions are said incompatible, if they are both i set w. and if there is w i set r also not waiting it appears in log.

why in complain mode only few lines appear after every change of rule and program restart? why all complains do not appear in one run of program?

sudo genprof ... tries to connect to rules repository, and asks many questions, i now choose "finish".

---

### Post by q.dinar on 2009-01-17
in man aparmor.d is written:
"There is no mediation based of port number or protocol beyond tcp, udp, and raw"
so i cannot restrict access to/by certain ip?
can i restrict access of a program but allow other programs as usually with iptables? as i know it is possible.

---

### Post by jgoguen on 2009-01-17
> **q.dinar said:**
> i thought that passwords are stored in /etc/passwd. but it is not so.
Right, passwords are stored in encrypted form in /etc/shadow.  No reason to allow everyone access to read the passwords when all they need is the username :)

> **q.dinar said:**
> i cannot change r for user or group or others in apparmor.d as it does not matter, am i, is it so ?
I think you're right.  You can't tell a program what permissions to ask for.  But you can say "OK, you can have user read only but not group read or other read".  A line like this grants read-only access for user only to home directories:
```
owner @{HOME}/ r,
```> **q.dinar said:**
> sometimes "requested mask" and "denied mask" in log are different, i write to rule which is for more permissions. i have now thought/guessed that "denied .." means which part of permission is needed.
The "requested mask" is what the program wants.  The "denied mask" is what the program isn't getting.  If the request mask is "rmix" and the denied mask is "mx" then it means that the profile allows reading but not mmap() or execute.  Note that I haven't covered what "i" means - it goes along with "x".  Execute permissions are either "ix" (inherit this profile on execute), "Ux" or "ux" (execute with no profile - not recommended!) or "Px" or "px" (execute with the profile for the program).  I'm starting to lean more towards using "ix" wherever possible, but your individual profiles will be larger.  You'll also have more control over what each application actually has access to.

---

### Post by jgoguen on 2009-01-17
> **q.dinar said:**
> in man aparmor.d is written:
"There is no mediation based of port number or protocol beyond tcp, udp, and raw"
so i cannot restrict access to/by certain ip?
can i restrict access of a program but allow other programs as usually with iptables? as i know it is possible.
No, you can't restrict IP addresses using AppArmor.  There's no way to say "only 192.168.100.0/24 can connect".  You would have to use iptables and say "reject from not 192.168.100.0/24 port 8082".  I'm not sure what you mean by restricting an application with iptables though.  You can restrict what network connections may be accepted with iptables, [s]but there's no way to use iptables to say "FreeSWAN may accept connections on port 9021 but not Transmission", and you can't say "MyApp can accept GRE traffic but nothing else can"[/s] (EDIT: Not true, I learned this can be done, see my next post).  You could use AppArmor to say that a program may only access a network using IPv4 UDP, but that's about it.  Do you have a specific scenario?  Maybe we could help you combine AppArmor and iptables to achieve what you want.

---

### Post by q.dinar on 2009-01-18
> The "requested mask" is what the program wants.
yes, i have been mistaken.

> I'm not sure what you mean by restricting an application with iptables though. ... but there's no way to use iptables to say "FreeSWAN may accept connections on port 9021 but not Transmission" 
yes that is other way than blocking application, that that i have seen was blocking by username with what the program runs, i do not know exactly :
[http://danieldegraaf.afraid.org/info/iptables/outfilter](http://danieldegraaf.afraid.org/info/iptables/outfilter) :
```
#!/usr/bin/env iptables-restore
*filter
:FORWARD DROP [0:0]
:INPUT DROP [0:0]
:OUTPUT ACCEPT [0:0]
:loga - [0:0]
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp --dport 80 -j loga
-A loga -j ULOG
-A loga -j ACCEPT
-A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -m owner --uid-owner www-data -j ULOG --ulog-prefix www
-A OUTPUT -m owner --uid-owner www-data -j DROP
-A OUTPUT -m owner --uid-owner root -j ACCEPT
-A OUTPUT -m owner --uid-owner daniel -j ACCEPT
-A OUTPUT -j ULOG --ulog-prefix egress
COMMIT
```

---

### Post by jgoguen on 2009-01-18
What that does there is block any outbound connections not related to an existing session for the specified username.  If you started Firefox as www-data, it would fail to connect to anything.  I've just learned about the --cmd-owner option, which takes a name as a parameter.  It matches if the packet was created by a process matching that command name.  I don't know if it requires a full path (I would imagine so) or if it's enabled in Ubuntu (iptables has to be compiled under a kernel supporting this feature for it to work) but that might allow you to use iptables to restrict an application's network access with iptables.  Which means I stand corrected, there is indeed a way to use iptables to say "FreeSWAN may accept connections on port 9021 but not Transmission" :)

---

### Post by q.dinar on 2009-01-18
hello.
how to make rules for wine and all programs that run with/by wine? would profile created with "sudo genprof wine" cover all {controlled usually by apparmor functions} of all [exe,com] programs that run with wine or just wine components started by that programs excepting their some none-wine direct operations?
> "Ux" or "ux" (execute with no profile - not recommended!) or "Px" or "px" (execute with the profile for the program) this is useful for me, thanks.

---

### Post by jgoguen on 2009-01-18
A profile for /usr/bin/wine would cover all programs started by WINE, even if they're installed under different WINE prefixes.  So if you installed (for example) Starcraft, MS Office 2007, Internet Explorer 6 (IEs4Linux), and World of Warcraft, your AppArmor profile would need to cover all permissions required by all programs.  It would also require maintenance when you install more programs - you would need to make sure the profile gave enough permissions for the installer programs to function, and the profile might require changes to accomodate programs you install later.  genprof only generates an approximate profile, I used it only once and found it was easier for me to just create the profile from scratch each time, or modify an existing profile.

---

### Post by q.dinar on 2009-01-19
i use genprof only to create almost empty file with near 50-100 bytes size. if do not use genprof i do not know for which file make profile and give according name. for example sudo genprof firefox uses file with name like Firefox.sh with "sh" extension file but near that file in its directory there are "firefox" and other executable files.

---

### Post by jgoguen on 2009-01-19
You have a good point there :)

---

### Post by jgoguen on 2009-01-19
Back onto the topic of sharing profiles :)  Here's a profile I've made for Firefox.  It allows downloading only to ~/Downloads/, and it allows uploading from ~/Music/, ~/Pictures/, or ~/Videos/.  It also allows downloading to /tmp/, and PDF files may be opened from Firefox with Evince (the default PDF viewer in GNOME).  The OpenJDK plugin is allowed as the Java plugin.

```
#include <tunables/global>
/usr/lib/firefox-3.0.5/firefox.sh {
    #include <abstractions/base>
    #include <abstractions/gnome>
    #include <abstractions/nameservice>
    #include <abstractions/user-tmp>

##### BEGIN READ-ONLY PERMISSIONS #####
    owner @{HOME}/ r,
    owner @{HOME}/.esd_auth r,
    owner @{HOME}/.icons/ r,
    owner @{HOME}/.local/** r,
    owner @{HOME}/.mozilla/firefox/**.so rm,
    owner @{HOME}/.thumbnails/** r,
    owner @{HOME}/Music/ r,
    owner @{HOME}/Music/** r,
    owner @{HOME}/Pictures/ r,
    owner @{HOME}/Pictures/** r,
    owner @{HOME}/Videos/ r,
    owner @{HOME}/Videos/** r,

    @{PROC}/ r,
    owner @{PROC}/*/fd/ r,
    owner @{PROC}/*/cmdline r,
    owner @{PROC}/*/maps r,
    owner @{PROC}/*/mounts r,
    owner @{PROC}/*/net/** r,
    owner @{PROC}/*/stat r,
    @{PROC}/sys/kernel/pid_max r,
    @{PROC}/uptime r,
    @{PROC}/version r,

    /dev/tty r,

    /etc/ r,
    /etc/firefox-*/pref/ r,
    /etc/firefox-*/pref/* r,
    /etc/gre.d/ r,
    /etc/gre.d/* r,
    /etc/java-6-openjdk/** r,
    /etc/kde4/** r,
    /etc/lsb-release r,
    /etc/pulse/* r,
    /etc/ssl/certs/** r,
    /etc/xulrunner-*/* r,

    /etc/gnome/defaults.list r,
    /etc/kde4rc r,
    /etc/mailcap r,
    /etc/mime.types r,
    /etc/mtab r,
    /etc/sound/events/gtk-events-2.soundlist r,

    /sys/devices/system/cpu/** r,

    /usr/lib/browser-plugins/** rm,
    /usr/lib/firefox-*/**.so rm,
    /usr/lib/jvm/** rm,
    /usr/lib/kde4/**.so rm,

    /usr/local/share/applications/ r,
    /usr/local/share/applications/* r,
    /usr/local/share/mime/** r,

    /usr/share/alsa/** r,
    /usr/share/applications/ r,
    /usr/share/applications/** r,
    /usr/share/evince/** r,
    /usr/share/gvfs/remote-volume-monitors/ r,
    /usr/share/gvfs/remote-volume-monitors/* r,
    /usr/share/icons/**.theme rk,
    /usr/share/java/** r,
    /usr/share/kubuntu-default-settings/** r,
    /usr/share/libthai/** r,
    /usr/share/locale-langpack/** r,
    /usr/share/mime/** r,
    /usr/share/myspell/dicts/ r,
    /usr/share/myspell/dicts/** r,
    /usr/share/ubufox/** r,
##### END READ-ONLY PERMISSIONS #####

##### BEGIN WRITE-ONLY PERMISSIONS #####
    /var/run/cups/cups.sock w,
    /var/run/dbus/system_bus_socket w,
##### END WRITE-ONLY PERMISSIONS #####

##### BEGIN READ-WRITE PERMISSIONS #####
    owner @{HOME}/.config/** rwk,
    owner @{HOME}/.gnome2/accelsevince rw,
    owner @{HOME}/.gnome2/evince/** rw,
    owner @{HOME}/.icedteaplugin/** rw,
    owner @{HOME}/.java/** rwk,
    owner @{HOME}/.kde/** rwk,
    owner @{HOME}/.macromedia/** rw,
    owner @{HOME}/.mozilla/** rwk,
    owner @{HOME}/.recently-used.xbel* rwk,
    owner @{HOME}/Downloads/ rw,
    owner @{HOME}/Downloads/** rw,

    /dev/shm/ rw,
    /dev/shm/* rw,
    /dev/snd/* rw,
##### END READ-WRITE PERMISSIONS #####

##### BEGIN EXECUTE PERMISSIONS #####
    /bin/dash rmix,
    /bin/grep rix,
    /bin/ps rix,
    /bin/readlink rmix,
    /bin/sed rix,

    /usr/bin/basename rix,
    /usr/bin/dirname rix,
    /usr/bin/evince rix,
    /usr/bin/launchpad-integration rix,

    /usr/lib/firefox-*/firefox ix,
    /usr/lib/firefox-*/firefox.sh ix,
    /usr/lib/gamin/gam_server ix,
    /usr/lib/jvm/java-6-openjdk/jre/bin/** rix,
##### END EXECUTE PERMISSIONS #####
}
```

---

### Post by q.dinar on 2009-01-19
> I used it only once and found it was easier for me to just create the profile from scratch each time, or modify an existing profile.
...
You have a good point there :)
how do you choose right name for profile file i.e. right executable file?

---

### Post by jgoguen on 2009-01-19
First, you find the file that is actually executed when you call the command.  That may require following some links.  For example, here's how you would find what to use for Firefox in a Terminal:

[list]
[*]Note that the command used in the menus is **firefox**
[*]Use the **which** command to find where this is: **which firefox**
[*]The output is */usr/bin/firefox*.  See if that's a link: **ls -l /usr/bin/firefox**
[*]The output shows that */usr/bin/firefox* points to firefox-3.0 in the same directory.  See if that's a link: **ls -l /usr/bin/firefox-3.0**
[*]The output shows that */usr/bin/firefox-3.0* points to *../lib/firefox-3.0.5/firefox.sh*.  That means the full path is */usr/lib/firefox-3.0.5/firefox.sh*.  See if that's a link: **ls -l /usr/lib/firefox-3.0.5/firefox.sh**
[*]The output does not point to any other file, so this is the file to use.
[/list]

Now that you know that */usr/lib/firefox-3.0.5/firefox.sh* is the actual file executed to run Firefox, you can construct the name of the AppArmor profile file.  To do this, follow these steps:

[list]
[*]Take the full path name: **/usr/lib/firefox-3.0.5/firefox.sh**
[*]Drop the first slash. This gives: **usr/lib/firefox-3.0.5/firefox.sh**
[*]Convert all remaining slashes to periods.  This gives: **usr.lib.firefox-3.0.5.firefox.sh**
[*]This is the file name for the AppArmor profile
[/list]

When generating the profile, the executable name is the full path you found earlier.

---

### Post by q.dinar on 2009-01-20
hello.
why firefox has asked for these? :
/home/*/.purple/
and
/home/*/.sudo_as_admin_successful
?

---

### Post by q.dinar on 2009-01-20
how to make separate profile for flash player?

---

### Post by jgoguen on 2009-01-20
> **q.dinar said:**
> hello.
why firefox has asked for these? :
/home/*/.purple/
and
/home/*/.sudo_as_admin_successful
?
Is it just asking for read permissions?  I don't know why it's asking for them.  In a full profile, I would deny that, Firefox has no need to access either of those.  I don't believe the profile I posted for Firefox does deny that, but it's still being tweaked.  I posted it as-is hoping a) that someone else would look at it, see something I missed, and post about it, and b) that it would be helpful to someone.

> **q.dinar said:**
> how to make separate profile for flash player?
Do you mean the Flash player plugin for Firefox?  You can't.  You can only make profiles for executables, and the Flash plugin is loaded by Firefox, not executed as its own program.  Whatever Firefox has access to, Flash has access to.  That's the danger and benefit of plugins.  The same goes for any other addon, if I write an addon, and you install it, my addon has access to everything you give Firefox access to.  If you mean a Flash player executable, then you would just make a new profile for that executable, but it wouldn't affect Flash in Firefox.

---

### Post by q.dinar on 2009-01-20
"I don't believe the profile I posted for Firefox does deny that"
that was asked with profile made by me. (i know, you did not said contrary.)
"Do you mean the Flash player plugin for Firefox?"
yes
"You can't. You can only make profiles for executables, and the Flash plugin is loaded by Firefox, not executed as its own program."
hm. but it is separate [binary] executable file as i think. cannot apparmor developers make apparmor to can use separate profiles for them?
"I would deny that" i also have not allowed them.

---

### Post by jgoguen on 2009-01-20
> **q.dinar said:**
> that was asked with profile made by me. (i know, you did not said contrary.)
I'm just saying that my profile doesn't deny it in case someone sees that I said it should be denied and then sees that my profile doesn't deny it.  I'm acknowledging a known "bug" in my profile :)

> **q.dinar said:**
> hm. but it is separate [binary] executable file as i think. cannot apparmor developers make apparmor to can use separate profiles for them?
If you're using the flash player plugin from Adobe, it's not a separate executable.  It's a shared object file that gets loaded by Firefox.  I sincerely hope that I'm wrong though, I think it would be nice if AppArmor would restrict plugins.  Just because I trust Firefox to have write access to ~/Downloads/ doesn't mean I want Flash doing the same thing.

---

### Post by teddks on 2009-01-20
> **q.dinar said:**
> hello.
why firefox has asked for these? :
/home/*/.purple/
and
/home/*/.sudo_as_admin_successful
?

Probably asked for the .purple stuff for aim:// and irc:// and other urls that are registered to Pidgin. sudo_as_admin_successful might be for AptURL?

---

### Post by q.dinar on 2009-01-24
hello.
xchat asks for /home/*/.recently-used.xbel . what is that, why xchat wants it, i looked into it, i have thought it is written with what file opened with what program.
also i see wine asks something though [i thought] it is off, i looked in system monitor and see "winbind"s by root.
wine asks for:
... operation="capable" name="dac_override" ... profile="/usr/bin/wine"
... operation="capable" name="dac_read_search" ... profile="/usr/bin/wine"
... operation="inode_mkdir" requested_mask="w::" denied_mask="w::" fsuid=0 name="/root/.wine/" ... profile="/usr/bin/wine"

25th jan. 14:44 gmt: [AppArmor Support Thread](http://ubuntuforums.org/showthread.php?t=1049698) thread(topic) appeared for this type of questions.

---

### Post by Bachstelze on 2009-03-24
AA profile for iroffer:

```

# AppArmor profile for iroffer v1.4.b03
#
# This AppArmor profile assumes the bot's configuration,
# PID, state and log files are stored in ~/xdcc/, and the
# files served for download are stored in ~/xdcc/files/.
#
#include <tunables/global>

/usr/bin/iroffer {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  owner /home/*/xdcc/*.config r,
  owner /home/*/xdcc/*.log* wl,
  owner /home/*/xdcc/*.pid w,
  owner /home/*/xdcc/*.{state,state.tmp,state\~} rwl,
  owner /home/*/xdcc/files/** rw,
  /usr/bin/iroffer r,

}
```

---

### Post by Thelasko on 2009-03-25
I discovered a [Brainstorm page]("http://brainstorm.ubuntu.com/idea/18369/") to improve the default profiles on AppArmor, I figured the people on this thread might be interested.

---

### Post by q.dinar on 2009-04-03
1st april icecast2 stopped to log anything. somehow only today i have noticed that and looked in syslog and indeed there apparmor reports about it.
there is in apparmor config file for icecast2:
/var/log/icecast2/error.log a,
/var/log/icecast2/access.log a,
i have just thought that this is wrong and changed them to "w" and reloaded this profile and tried to open stream url with player and closed it and have seen that icecast2 has logged it. without other complains logged by apparmor. then i think: why it did work before? why it did not need "w" permission? even several gzipped log files are created. (they are created by special daemon >10th of april, 2009: probably not daemon but cron job.<.)... hm! i have just wanted to check when i created icecast2 profiles and wanted to look in syslog archives and have found that old files are not there!
and i have thought why it has started to log to log file when it has not been restarted?
and i have thought why it should need "w" permission? and have edited it back to "a". and reloaded the profile again and it does not write and complains in syslog again.

---

### Post by bodhi.zazen on 2009-04-03
probably needs permissions or ra

I would append (a) rather then write (w) a log file.

If you are getting error messages, it helps to post them.

If you need advice

sudo aa-logprof

---

### Post by q.dinar on 2009-04-03
i have restarted apparmor and icecast2 and ices2 and checked with player and it works now.

[QUOTE="bodhi.zazen"]probably needs permissions or ra[/QUOTE]
it asked for "w":
Apr  4 01:20:54 linux2009 kernel: [146893.162337] type=1503 audit(1238793654.348:1392): operation="file_permission" requested_mask="w::" denied_mask="w::" fsuid=116 name="/var/log/icecast2/access.log" pid=5481 profile="/usr/bin/icecast2"

and as i have just looked to copy this i have seen in syslog that even though it started to append to log file now, it still has complained one line:
Apr  4 02:21:07 linux2009 kernel: [150506.656194] type=1503 audit(1238797267.844:1426): operation="file_permission" requested_mask="w::" denied_mask="w::" fsuid=116 name="/var/log/icecast2/access.log" pid=5529 profile="/usr/bin/icecast2"

and many complain lines are written about ices2:
Apr  4 02:21:14 linux2009 kernel: [150512.820144] type=1503 audit(1238797274.008:1437): operation="file_permission" requested_mask="w::" denied_mask="w::" fsuid=1000 name="/var/log/ices/ices.log" pid=5487 profile="/usr/bin/ices2"
and
Apr  4 02:21:14 linux2009 kernel: [150512.826378] type=1503 audit(1238797274.012:1438): operation="socket_create" family="inet" sock_type="dgram" protocol=0 pid=5487 profile="/usr/bin/ices2"
lines.
ices2 also has only "a" permission to its log file.

---

### Post by bodhi.zazen on 2009-04-03
In general, if it is working, nothing more needs to be done.

AA is noisy in the logs and, IMO , not everything logged needs to be fixed.

---

### Post by q.dinar on 2009-04-03
i had forgotten [AppArmor Support Thread](http://ubuntuforums.org/showthread.php?t=1049698).

---

### Post by rileinc on 2009-04-17
```
# Last Modified: Thu Apr 30 13:10:28 2009
#include <tunables/global>

/usr/lib/firefox-3.0.10/firefox.sh flags=(complain) {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>

  network dgram,
  network stream,


  /bin/dash rix,
  /usr/bin/basename rix,
  /usr/lib/firefox-3.0.10/firefox rix,

  owner /dev/shm/pulse-shm-* w,
  /etc/mime.types r,
  owner /home/*/ r,
  owner /home/*/.Xauthority r,
  owner /home/*/.adobe/Flash_Player/AssetCache/ r,
  owner /home/*/.adobe/Flash_Player/AssetCache/** rw,
  owner /home/*/.config/gtk-2.0/* rw,
  owner /home/*/.gtk-bookmarks r,
  owner /home/*/.macromedia/ r,
  owner /home/*/.macromedia/** r,
  owner /home/*/.mozilla/extensions/*/ r,
  owner /home/*/.mozilla/firefox/*.default/ r,
  owner /home/*/.mozilla/firefox/*.default/** rwk,
  owner /home/*/.mozilla/firefox/profiles.ini r,
  owner /home/*/.mozilla/plugins/libflashplayer.so mr,
  owner /home/*/.recently-used.xbel r,
  owner /home/*/Desktop/ r,
  owner /home/*/Desktop/** ra,
  /mnt/ r,
  /mnt/** r,
  /mnt/Backup/Others/Firefox/Ubuntu/** ra,
  /mnt/Incoming/Incoming/** ra,
  owner /proc/*/mounts r,
  /proc/cpuinfo r,
  /usr/share/** r,

}
```
Just doing a test drive :)
Please make suggestions on how I can improve the profile [(in the AA support thread).](http://ubuntuforums.org/showthread.php?t=1049698&page=4)

---

### Post by rookcifer on 2009-06-14
My profile for the newly released Firefox-3.0.11.  You will notice that I do not use the macros.  I have found that if I do, they tend to be ignored (not sure why).  But overall, this profile works well (I use KDE but have Gnome libs installed).  Firefox has quit complaining no matter what I do with the browser.

```
# Last Modified: Sun Jun 14 05:30:44 2009
#include <tunables/global>

/usr/lib/firefox-3.0.11/firefox.sh {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>
  #include <abstractions/nvidia>
  #include <abstractions/user-tmp>

  capability sys_ptrace,


  deny /etc/fstab r,
  deny /home/*/.bash* rw,
  deny /home/*/.gnupg/* rw,
  deny /home/*/.ssh/* rw,

  /bin/dash rix,
  /bin/grep rix,
  /bin/ls mrix,
  /bin/ps rix,
  /bin/sed rix,
  /bin/uname rix,
  /bin/which rix,
  /dev/ r,
  /dev/shm/ r,
  owner /dev/shm/* rw,
  /dev/zero mrw,
  /etc/ r,
  /etc/X11/cursors/* r,
  /etc/default/apport r,
  /etc/firefox-3.0/pref/ r,
  /etc/firefox-3.0/pref/** r,
  /etc/gre.d/ r,
  /etc/gre.d/** r,
  /etc/java-6-openjdk/** r,
  /etc/kde4/kdeglobals r,
  /etc/kde4rc r,
  /etc/lsb-release r,
  /etc/mailcap r,
  /etc/mime.types r,
  /etc/mplayer/* r,
  /etc/openoffice/soffice.sh r,
  /etc/pulse/client.conf r,
  /etc/sound/events/gtk-events-2.soundlist r,
  /etc/ssl/certs/java/cacerts r,
  /etc/xulrunner-1.9/* r,
  owner /home/*/ r,
  owner /home/*/.cache/ rwk,
  owner /home/*/.cache/gnome-mplayer/plugin/ rw,
  owner /home/*/.cache/gnome-mplayer/plugin/** rw,
  owner /home/*/.config/Trolltech.conf rk,
  owner /home/*/.config/gtk-2.0/ rw,
  owner /home/*/.config/qtcurve.gtk-icons rw,
  owner /home/*/.config/transmission/lock rwk,
  owner /home/*/.gnome2/ rw,
  owner /home/*/.gnome2/accels/ rw,
  owner /home/*/.gnome2_private/ rw,
  owner /home/*/.icedteaplugin/* rw,
  owner /home/*/.kde/share/apps/kpdf/ rw,
  owner /home/*/.kde/share/apps/okular/ rw,
  owner /home/*/.kde/share/apps/okular/** rw,
  owner /home/*/.kde/share/config/ w,
  owner /home/*/.kde/share/config/* rw,
  owner /home/*/.kde/share/config/kdeglobals k,
  owner /home/*/.kde/share/icons/KDE4CrystalDiamondIcons_1.1_Kubuntu/** rw,
  owner /home/*/.macromedia/Flash_Player/** rw,
  owner /home/*/.mozilla/firefox/** rwk,
  owner /home/*/.netx/ rw,
  owner /home/*/.pulse-cookie rwk,
  owner /home/*/.pulse/ rw,
  owner /home/*/.recently-used.xbel* rwk,
  /home/*/.selected_editor r,
  owner /home/*/Desktop/* rw,
  owner /home/*/Download/** rw,
  owner /home/*/Pictures/** rw,
  owner /home/.mozilla/{firefox*,plugins,extensions}/ rw,
  owner /home/.mozilla/{firefox*,plugins,extensions}/** mrwk,
  owner /home/*/** r,
  owner /home/*/.config/Trolltech.conf rwk,
  /proc/ r,
  /proc/*/cmdline r,
  owner /proc/*/fd/ r,
  owner /proc/*/mounts r,
  /proc/*/net/if_inet6 r,
  /proc/*/net/ipv6_route r,
  /proc/*/stat r,
  /proc/*/status r,
  /proc/cpuinfo r,
  /proc/meminfo r,
  /proc/sys/kernel/pid_max r,
  /proc/tty/drivers r,
  /proc/uptime r,
  /proc/version r,
  /sys/devices/system/cpu/ r,
  /usr/bin/basename rix,
  /usr/bin/dcop rix,
  /usr/bin/dirname rix,
  /usr/bin/env rix,
  /usr/bin/gconftool-2 rix,
  /usr/bin/gnome-mplayer rix,
  /usr/bin/kde4-config rix,
  /usr/bin/mencoder rix,
  /usr/bin/mplayer rix,
  /usr/bin/okular rix,
  /usr/bin/ps2pdf rix,
  /usr/bin/setarch rix,
  /usr/bin/soffice r,
  /usr/bin/stat rix,
  /usr/bin/transmission rix,
  /usr/lib/firefox-3.0.11/firefox rix,
  /usr/lib/jvm/java-6-openjdk/jre/bin/java rix,
  /usr/lib/kde4/libexec/drkonqi rix,
  /usr/lib/nspluginwrapper/i386/linux/npviewer* rix,
  /usr/lib/openoffice/* r,
  /usr/lib/openoffice/** rix,
  /usr/lib/ure/bin/javaldx rix,
  /usr/lib{,32,64}/** mr,
  /usr/share/ghostscript/8.64/Resource/Init/gs_init.ps r,
  /usr/share/java/* r,
  /usr/share/javazi/ r,
  /usr/share/javazi/** r,
  /usr/share/kde4/* r,
  /usr/share/kde4/** r,  
  /usr/share/kubuntu-default-settings/kde4-profile/default/share/** r,
  /usr/share/libthai/* r,
  /usr/share/myspell/** r,
  /usr/share/zoneinfo/ r,
  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so mr,

}

```

---

### Post by Barriehie on 2009-06-17
Hello Everyone,
I finally got tired/curious about the apparmor warnings at boot time so I've since discovered what this is all about and think it's pretty neat... although, I've yet to fully understand the profile files.  I'll be working on one for opera so we'll see how that goes.  So far if I enable it it won't even start!  Guess that's pretty safe.  :D

To bodhi.zazen: Discovered your Intro and web page of profiles and appreciate the efforts.

I've been running Ubuntu for a bit over a year now and maybe know enough to give back to the community. (bet I still have lots of reading though!)

Barrie

---

### Post by rookcifer on 2009-06-18
Would anyone post the default Jaunty CUPS apparmor profile here?  I deleted mine (long story).  Reinstalling apparmor does not reinstall the cups profile, nor does installing the extra profiles.

Thanks.

---

### Post by unutbu on 2009-06-18
rookcifer, I don't have Jaunty installed, or I would pastebin it for you. However, you should be able to regenerate it by reinstalling the cups package:
```
% dpkg -S /etc/apparmor.d/usr.sbin.cupsd
cups: /etc/apparmor.d/usr.sbin.cupsd
```

---

### Post by movieman on 2009-09-18
SVN server, usr.bin.svnserve:
```
#include <tunables/global>

/usr/bin/svnserve {
  #include <abstractions/base>

  network inet stream,
  network inet6 dgram,
  network inet6 stream,


  /etc/gai.conf r,
  /tmp/** rwk,
  /var/tmp/** rwk,
  /usr/bin/svnserve r,
  /var/run/svnserve/* rwk,

  # Repository
  /var/lib/SVN/** rwk,
}
```

Update the repository directory as required for your system. I'm not sure why it apparently wants IPv6 UDP services but not IPv4?

---

### Post by movieman on 2009-09-18
Racoon ISAKMP service, usr.sbin.racoon:

```
#include <tunables/global>

/usr/sbin/racoon {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability net_admin,

  network key raw,

  /etc/racoon/** r,
  /proc/*/net/ r,
  /proc/*/net/unix r,
  /usr/sbin/racoon r,
  /var/run/racoon.pid rwk,
  /var/run/racoon/* rwk,

}
```

---

### Post by movieman on 2009-09-18
Zabbix:

usr.sbin.zabbix_agentd:
```
/usr/sbin/zabbix_agentd {
  #include <abstractions/base>

  capability setgid,
  capability setuid,

  network inet stream,


  /bin/cat rix,
  /bin/dash rix,
  /bin/grep rix,
  /bin/hostname rix,
  /bin/uname rix,
  /etc/group r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/zabbix/zabbix_agentd.conf r,
  /etc/inetd.conf r,
  /etc/services r,
  /etc/gai.conf r,
  /bin/* r,
  /sbin/* r,
  /usr/bin/* r,
  /usr/sbin/* r,
  /boot/* r,
  /var/log/zabbix-agent/* ra,
  /var/run/zabbix-agent/* rwk,
  /proc/ r,
  /proc/*/cmdline r,
  /proc/*/mounts r,
  /proc/*/net/dev r,
  /proc/*/status r,
  /proc/cmdline r,
  /proc/loadavg r,
  /proc/sys/** r,
  /tmp/zabbix/* r,
  /usr/bin/gawk rix,
  /usr/bin/wc rix,
  /usr/bin/who rix,
  /usr/sbin/zabbix_agentd r,
  /var/run/utmp rk,

}
```

I'm sure you can provoke the agent into accessing more files on the system to monitor other stats, but so far I haven't seen it try to do so.

Note that I use /tmp/zabbix to dump the output of some cron jobs which the agent later scans to update various stats; you may not need it.

usr.sbin.zabbix_server:
```
#include <tunables/global>

/usr/sbin/zabbix_server {
  #include <abstractions/base>


  capability setgid,
  capability setuid,

  network inet stream,
  network inet6 dgram,


  /etc/gai.conf r,
  /etc/group r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/services r,
  /etc/zabbix/zabbix_server.conf r,
  /usr/sbin/zabbix_server r,
  /var/log/zabbix-server/* ra,
  /var/run/zabbix-server/* rwk,
  /usr/share/mysql/charsets/* r,
  /usr/share/snmp/mibs/* r,

}
```

---

### Post by bodhi.zazen on 2009-09-18
thank you for posting those [movieman]("http://ubuntuforums.org/member.php?u=511464")

---

### Post by rookcifer on 2009-09-25
Here's my current Firefox 3.5.2 profile:

```
# Last Modified: Thu Sep 24 05:34:56 2009
#include <tunables/global>

/usr/lib/firefox-3.5.2/firefox.sh {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>
  #include <abstractions/nvidia>
  #include <abstractions/perl>


  deny capability sys_ptrace,

  deny / r,
  deny owner /home/*/.ICEauthority r,
  deny owner /home/*/.Xauthority r,
  deny owner /home/*/.bash** rw,
  deny owner /home/*/.dmrc rw,
  deny owner /home/*/.dvdcss/ rw,
  deny owner /home/*/.gnupg/ rw,
  deny owner /home/*/.pki/ rw,
  deny owner /home/*/.recently-used.xbel r,
  deny owner /home/*/.ssh/ rw,
  deny owner /home/*/ r,
  deny owner /home/*/.VirtualBox/ rw,
  
  /bin/dash mrix,
  /bin/grep rix,
  /bin/ps rix,
  /bin/sed rix,
  /bin/uname rix,
  /bin/which rix,
  /dev/shm/ r,
  owner /dev/shm/* a,
  /dev/zero mrw,
  /etc/ r,
  /etc/X11/cursors/* r,
  /etc/default/apport r,
  /etc/firefox-3.5/** r,
  /etc/fstab r,
  /etc/gre.d/ r,
  /etc/gre.d/1.9.1.4pre.system.conf r,
  /etc/kde4/kdeglobals r,
  /etc/kde4rc r,
  /etc/mailcap r,
  /etc/mime.types r,
  /etc/mplayer/input.conf r,
  /etc/mplayer/mplayer.conf r,
  /etc/pulse/client.conf r,
  /etc/sound/events/* r,
  /etc/xulrunner-1.9.1/* r,
  owner /home/*/.adobe/ r,
  owner /home/*/.adobe/Flash_Player/*/ r,
  owner /home/*/.cache/ r,
  owner /home/*/.cache/* rwk,
  owner /home/*/.cache/gnome-mplayer/*/ rw,
  owner /home/*/.cache/gnome-mplayer/plugin/* rw,
  owner /home/*/.cache/gnome-mplayer/plugin/*/ w,
  owner /home/*/.config/ r,
  owner /home/*/.config/* r,
  owner /home/*/.config/Trolltech.conf rwk,
  owner /home/*/.config/gtk-2.0/* rw,
  owner /home/*/.config/qtcurve.gtk-icons rw,
  owner /home/*/.dbus/ r,
  owner /home/*/.directory r,
  owner /home/*/.esd_auth r,
  owner /home/*/.fontconfig/* r,
  owner /home/*/.gconf/ r,
  owner /home/*/.gconfd/ r,
  owner /home/*/.gtkrc-2.0-kde4 r,
  owner /home/*/.gvfs/ r,
  owner /home/*/.icedteaplugin/ r,
  owner /home/*/.kde/ r,
  owner /home/*/.kde/share/apps/kpdf/ w,
  owner /home/*/.kde/share/apps/okular/* rw,
  owner /home/*/.kde/share/apps/okular/*/ w,
  owner /home/*/.kde/share/apps/okular/docdata/* w,
  owner /home/*/.kde/share/config/ w,
  owner /home/*/.kde/share/config/gtkrc-2.0 r,
  owner /home/*/.kde/share/config/kdeglobals rk,
  owner /home/*/.kde/share/config/okular* rw,
  owner /home/*/.kde/share/icons/** rw,
  owner /home/*/.local/ r,
  owner /home/*/.local/share/mime/mime.cache r,
  owner /home/*/.macromedia/ r,
  owner /home/*/.macromedia/*/ r,
  owner /home/*/.macromedia/Flash_Player/** rw,
  owner /home/*/.marble/ r,
  owner /home/*/.mozilla/ r,
  owner /home/*/.mozilla/extensions/*/ r,
  owner /home/*/.mozilla/firefox-3.5/** mrwk,
  owner /home/*/.mozilla/firefox/** r,
  owner /home/*/.mplayer/ r,
  owner /home/*/.mplayer/* rw,
  owner /home/*/.nvidia-settings-rc r,
  owner /home/*/.profile r,
  owner /home/*/.pulse-cookie r,
  owner /home/*/.pulse/ rw,
  owner /home/*/.qt/ r,
  owner /home/*/.sudo_as_admin_successful r,
  owner /home/*/.thumbnails/ r,
  owner /home/*/.thumbnails/normal/* r,
  owner /home/*/.update-manager-core/ r,
  owner /home/*/.xine/ r,
  owner /home/*/.xsession-errors r,
  owner /home/*/{Desktop,download}/ rw,
  owner /home/*/{Desktop,download}/** rw,
  owner /home/*/{Documents,Pictures}/ r,
  owner /home/*/{Documents,Pictures}/** ra,
  /proc/ r,
  /proc/*/cmdline r,
  owner /proc/*/fd/ r,
  owner /proc/*/maps r,
  owner /proc/*/mounts r,
  /proc/*/stat r,
  /proc/*/status r,
  owner /proc/*/task/ r,
  /proc/cpuinfo r,
  /proc/meminfo r,
  /proc/stat r,
  /proc/sys/kernel/pid_max r,
  /proc/tty/drivers r,
  /proc/uptime r,
  /proc/version r,
  /sys/devices/system/cpu/ r,
  /usr/bin/basename rix,
  /usr/bin/dcop rix,
  /usr/bin/gnome-mplayer rix,
  /usr/bin/kde4-config rix,
  /usr/bin/mencoder rix,
  /usr/bin/mplayer rix,
  /usr/bin/okular rix,
  /usr/bin/perl rix,
  /usr/bin/ps2pdf rix,
  /usr/bin/setarch rix,
  /usr/bin/transmission px,
  /usr/lib/firefox-3.5.2/firefox-3.5 rix,
  /usr/lib/firefox-3.5.2/firefox.sh rix,
  /usr/lib/kde4/libexec/drkonqi rix,
  /usr/lib/nspluginwrapper/i386/linux/npviewer rix,
  /usr/lib/nspluginwrapper/i386/linux/npviewer.bin rix,
  /usr/lib{,32,64}* mr,
  /usr/lib{,32,64}/** mr,
  /usr/share/kde4/apps/okular/* r,
  /usr/share/kde4/apps/okular/**/ r,
  /usr/share/kde4/config/kdebug.areas r,
  /usr/share/kde4/config/kdebugrc r,
  /usr/share/kde4/config/ui/ui_standards.rc r,
  /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/kdeglobals r,
  /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/oxygenrc r,
  /usr/share/libthai/* r,
  /usr/share/myspell/dicts/ r,
  /usr/share/myspell/dicts/* r,
  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so mr,

}
```

This profile allows for just about every typical browser usage scenario: mplayer plugins, Flash, PDF viewing, Java plugins, spell check, and opening torrent trackers in Transmission.  Also, please note this profile is for Firefox on **Kubuntu**.

I would like feedback on my deny policies.  Firefox tries to read just about the whole /home directory and, as you can see, I have denied quite a few of these directories and it still seems to function just fine.  I would also like feedback on /proc.  Does FF really need access to all of these /proc directories?

Yes, I realize I did not use the macros @{HOME}, etc.  For some reason if I use them, AppArmor does not recognize them in my profile.  Perhaps I need to adjust the tunables and/or globals file, but I haven't gotten around to it (though I figured these variables should already be defined).

---

### Post by bodhi.zazen on 2009-09-25
Firefox is a difficult profile. Many people expect different things from Firefox, from browsing, to media to reading documents to web page development to email.

Your profile looks fine, the main thing I do is allow full access to home , then limit what FF does not need, such as ~/.ssh (it is easier to allow all and deny a few then allow specific access to all teh .config files in $HOME).

Also, FYI, there is now a profile for Firefox in 9.10. So I am looking at modifying the default profile more then maintaining my own. Again Firefox is difficult to maintain as the various directories keep changing.

---

### Post by q.dinar on 2009-12-24
i attach /etc/apparmor.d content as it was when i have installed new ubuntu 9.10 , there are profiles that worked with ubuntu 9.04 and ubuntu 8.10 .

2009-12-25 9:58 utc+3 :
most useful profiles there i think these:
usr.bin.icecast2
usr.bin.ices2
usr.bin.konqueror
usr.bin.pidgin
usr.bin.psi
usr.bin.totem-gstreamer
usr.bin.transmission
usr.bin.wine
usr.bin.xchat
usr.lib.firefox-3.0.15.firefox.sh
usr.sbin.dancer-ircd
usr.sbin.ejabberd
usr.share.virtualbox.VBox.sh
except them there are usr.bin.gajim and usr.bin.gossip but i have not used them much enough, just tried. and there is home.dinar-q.doc.phpcmdl.test2.php for testing a command line php script. and there are backup files of firefox since usr.lib.firefox-3.0.6.firefox.sh~ .
10:12 utc+3: to [#60](http://ubuntuforums.org/showpost.php?p=8554963&postcount=60) : i also had thought about that but was lazy and thought may be will write that later.
2009-12-25 16:38 utc+3: md5sum: e0f10e74e04a50f58f815e53200c9759

---

### Post by jgoguen on 2009-12-24
> **q.dinar said:**
> i attach /etc/apparmor.d content as it was when i have installed new ubuntu 9.10 , there are profiles that worked with ubuntu 9.04 and ubuntu 8.10 .
Could you please list what profiles you have in the archive? Also, posting profiles present on an installed system isn't incredibly useful.  Posting your modifications to those profiles, or posting new profiles, now that's useful :)

Thanks!

---

### Post by rookcifer on 2009-12-25
Here are a few of my AppArmor profiles.  All of these work on 9.10, and all work without throwing any errors after several months of use.

Amarok 2.2.1 profile. (Note: I use OSS and not ALSA/Phonon)

```
#include <tunables/global>                            

/usr/bin/amarok {
  #include <abstractions/X>
  #include <abstractions/audio>
  #include <abstractions/base> 
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/mysql>          
  #include <abstractions/nameservice>    
  #include <abstractions/private-files>  
  #include <abstractions/private-files-strict>
  #include <abstractions/samba>               
  #include <abstractions/user-tmp>            


  /dev/oss/oss_hdaudio0/* w,
  /dev/zero mrw,            
  /etc/default/apport r,    
  /etc/fstab r,             
  /etc/kde4rc r,            
  /etc/mysql/* r,
  /etc/mysql/** r,
  owner /home/** rwkl,
  owner /home/*/ r,
  owner /proc/*/status r,
  owner /proc/*/task/ r,
  /proc/filesystems r,  
  /sys/devices/system/cpu/ r,
  /usr/bin/amarok r,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/lib*so* mr,
  /usr/share/fonts/ r,
  /usr/share/kde4/apps/amarok/ r,
  /usr/share/kde4/apps/amarok/** r,
  /usr/share/kde4/apps/desktoptheme/** r,
  /usr/share/kde4/config/* r,
  /usr/share/kde4/services/* r,
  /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/* r,
  /usr/share/locale-langpack/ r,
  /usr/share/locale/ r,
  /usr/share/xine/**/ r,

}
```

My Kopete profile:

```
#include <tunables/global>                           

/usr/bin/kopete {
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/kde>  
  #include <abstractions/nameservice>
  #include <abstractions/private-files>
  #include <abstractions/private-files-strict>

  /etc/default/apport r,
  /etc/kde4rc r,
  owner @{HOME}/*/** rwlk,
  /proc/filesystems r,
  /proc/meminfo r,
  /proc/stat r,
  /proc/sys/crypto/* r,
  /usr/lib{,32,64}/** mr,
  /usr/share/emoticons/ r,
  /usr/share/enchant/* r,
  /usr/share/kde4/apps/kabc/** r,
  /usr/share/kde4/apps/khtml/** r,
  /usr/share/kde4/apps/kopete** r,
  /usr/share/kde4/config/** r,
  /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/* r,
  /usr/share/myspell/dicts/ r,
  /usr/share/myspell/dicts/* r,

}
```

My Kvirc profile:

```
#include <tunables/global>

/usr/bin/kvirc {
  #include <abstractions/fonts>
  #include <abstractions/kde>
  #include <abstractions/nameservice>
  #include <abstractions/private-files>
  #include <abstractions/private-files-strict>


  audit deny @{HOME}/Documents/ rwk,
  audit deny @{HOME}/Downloads/ rwk,

  /etc/default/apport r,
  /etc/kde4rc r,
  owner /home/*/** rwk,
  /proc/stat r,
  /usr/bin/kfmclient rix,
  /usr/share/kde4/config/* r,
  /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/* r,
  /usr/share/kvirc/** r,

}
```


My Transmission profile:

```
#include <tunables/global>                                 

/usr/bin/transmission {
  #include <abstractions/X>
  #include <abstractions/base>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/private-files>
  #include <abstractions/private-files-strict>


  /etc/kde4rc r,
  owner /home/*/ r,
  owner /home/*/** rwk,
  owner /proc/*/cmdline r,
  owner /proc/*/fd/ r,
  /proc/*/net/route r,
  /proc/filesystems r,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/lib*so* mr,
  /usr/share/fonts/ r,

}
```

---

### Post by q.dinar on 2009-12-25
empathy profile:
```
#include <tunables/global>

/usr/bin/empathy {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/base>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/X>
  #include <abstractions/dbus>

/proc/filesystems r,
@{HOME}/.gstreamer-*/** r,
/usr/lib/libvisual-*/** m,
/usr/share/empathy/** r,
@{HOME}/.gstreamer-*/registry.i486.bin.* w,
@{HOME}/.config/Empathy/** rw,
/usr/share/telepathy/** r,
@{HOME}/.gstreamer-*/registry.i486.bin w,
@{HOME}/.cache/telepathy/ w,
@{HOME}/.cache/telepathy/** rw,
/usr/share/enchant/** r,
/usr/share/myspell/** r,
/usr/share/xml/** r,
@{HOME}/.local/share/Empathy/ w,
@{HOME}/.local/share/Empathy/** rw,
@{HOME}/.config/enchant/ rw,
@{HOME}/.config/enchant/** rw,
@{PROC}/[0-9]*/fd/ r,
/usr/lib/firefox-3.5.*/firefox.sh Uxr,
}
```
2009-12-27 11:23 utc+3 : don't bother about "...firefox.sh Uxr," , it has not profile and runs other binary file which has profile and that runs confined.

---

### Post by q.dinar on 2009-12-26
for ejabberd profiles for 2 files, they both run when ejabberd is started:
```
#include <tunables/global>
/usr/sbin/ejabberd {
#include <abstractions/base>
/usr/sbin/ejabberd r,
/etc/default/ejabberd r,
/usr/lib/erlang/bin/erl ix,
/bin/sed ix,
/usr/lib/erlang/** ix,
/proc/filesystems r,
/sys/devices/system/cpu/ r,
/bin/dash ix,
/var/log/ejabberd/** wr,
/var/lib/ejabberd/** wr,
/sys/devices/system/cpu/** r,
#include <abstractions/nameservice>
/etc/ejabberd/** r,
/var/lib/ejabberd/ r,
/usr/lib/ejabberd/** mr,
/var/www/muclogs/** wr,
}
```edit /var/www/muclogs/** as you need
```
#include <tunables/global>
/usr/sbin/ejabberdctl {
#include <abstractions/base>
/usr/sbin/ejabberdctl r,
/etc/default/ejabberd r,
/bin/date ix,
/usr/lib/erlang/bin/erl ix,
/bin/sed ix,
/usr/lib/erlang/** ix,
/proc/filesystems r,
/sys/devices/system/cpu/ r,
/bin/dash ix,
#include <abstractions/nameservice>
/sys/devices/system/cpu/** r,
@{HOME}/erl_crash.dump wr,
/var/lib/ejabberd/** wr,
@{HOME}/.erlang.cookie wr,
}
```other things may appear except @{HOME}/.erlang.cookie wr, if you run ejabberdctl from terminal, i have not used it much.
/etc/init.d/ejabberd :
```
#include <tunables/global>
/etc/init.d/ejabberd {
#include <abstractions/base>
/etc/init.d/ejabberd r,
/etc/default/ejabberd r,
/bin/su ix,
capability dac_override,
capability dac_read_search,
/usr/bin/expr ix,
/bin/sleep ix,
/var/run/utmp rk,
#include <abstractions/nameservice>
/etc/login.defs r,
/etc/pam.d/* r,
/lib/security/** mr,
/etc/shells r,
/proc/filesystems r,
capability setgid,
/etc/shadow r,
/etc/security/** r,
capability setuid,
/etc/environment r,
/etc/default/locale r,
/bin/dash ix,
/usr/sbin/ejabberdctl Px,
/usr/sbin/ejabberd Px,
}
```

---

### Post by bodhi.zazen on 2009-12-26
Thank you for posting your profiles.

My 2c would be that you take the time to keep your profile organized =)

Not that I am perfect at this either , but it makes it difficult to read and debug if the profile is not is some semblance of order.

In general :

1. Includes first.
2. capabilities second.
3. System files next, alphabetical order (/etc/foo before @{PROC} before /tmp before /var
4. @{HOME} last , again in alphabetical order.

One very general consideration, IMO one of the main uses of apparmor is to limit access to files in $HOME. System files are already "protected" by permissions, but $HOME is wide open.

I typically limit access to things such as ~/.ssh ~/.bashrc and only allow downloads to certain locations, such as ~/Downloads In fact, I usually review 

/etc/apparmor.d/abstractions/private-files

Then of course
#include <abstractions/private-files>

=)

The other consideration is to not only limit access to only what is needed, but also to quiet down the logs.

Ideally apparmor would only log Abnormal activity. If say firefox is filling the log with errors because you denied access to /proc/ , while it may work, it is harder to then detect aberrant behavior =)

My uptime is only 5 days now, but no errors from apparmor in my log with "normal activity" so that is nice also.

To do this I 

tail -F /var/log/messages

then run say firefox, do normal activities, and try to quiet down the logs as much as possible.

---

### Post by q.dinar on 2009-12-27
```
#include <tunables/global>

/usr/bin/psi {
  #include <abstractions/base>

/usr/bin/psi r,
/etc/fonts/fonts.conf r,
/var/cache/fontconfig/*-x86.cache-2 r,
/usr/share/fonts/ r,
/tmp/.X11-unix/X* w,

/etc/fonts/conf.d/ r,
@{HOME}/.Xauthority r,

#birinci taraz

/etc/fonts/conf.avail/*.conf r,

/var/lib/defoma/fontconfig.d/fonts.conf r,
#@{HOME}/.config/Trolltech.conf rw,
/tmp/.ICE-unix/* w,
#@{HOME}/.psi/ w,

@{HOME}/.config/Trolltech.conf rwk,
@{HOME}/.ICEauthority r,
/etc/ssl/certs/ca-certificates.crt r,
#@{HOME}/.psi/*/ w,
/usr/share/icons/** r,

#@{HOME}/.psi/*/ wr,
#@{HOME}/.psi/*/*/ wr,
/usr/share/fonts/** r,

#@{HOME}/.psi/*/*/*/ rw,
/etc/nsswitch.conf r,
#/etc/passwd r,
#@{HOME}/.psi/caps.xml rw,
/usr/share/X11/XKeysymDB r,
#@{HOME}/.psi/profiles/*/*.xml rw,
#@{HOME}/.psi/*.xml rw,
#@{HOME}/.psi/psirc a,

#@{HOME}/.psi/psirc rwk,

/etc/resolv.conf r,
/etc/host.conf r,
/etc/hosts r,
network dgram,

/usr/bin/lsb_release ix,
/etc/debian_version r,

#/usr/share/psi/certs/ r,
network stream,

#/usr/share/psi/certs/* r,

#/usr/bin/sox ix,

/usr/bin/sox mrix,

/usr/share/psi/** r,

/usr/bin/python2.5 ix,

#/usr/share/alsa/alsa.conf r,

/usr/share/alsa/** r,
#/dev/snd/controlC0 r,

/etc/pulse/** r,
/dev/shm/ r,
#/dev/shm/pulse-shm-* a,
/tmp/pulse-*/native w,
/dev/snd/controlC0 rw,

/dev/shm/pulse-shm-* wr,

@{HOME}/.psi/** rw,
@{HOME}/.psi/ rw,
/usr/share/psi/ r,

@{HOME}/.psi/psirc rwk,

#ubuntu 9.10
/etc/fonts/conf.d/** r,
/var/run/gdm/** r,
/etc/passwd r,
/tmp/orbit-*/** wr,
/proc/filesystems r,
/usr/share/themes/** r,
/usr/lib/pango/** mr,
/usr/lib/gtk-2.0/** mr,
/usr/local/share/icons/ r,
/usr/share/icons/ r,
/usr/share/pixmaps/ r,
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/mime/** r,
#include <abstractions/dbus>
/usr/share/gvfs/remote-volume-monitors/** r,
/usr/share/pyshared/** r,
/usr/local/lib/** r,
/etc/python*/** r,
/usr/bin/lsb_release r,
/etc/lsb-release r,
/bin/dash ix,
/usr/bin/aplay ix,
@{HOME}/.pulse-cookie rwk,
}
```

---

### Post by rookcifer on 2009-12-27
q.dinar,

As bodhi said, your profiles are a mess.  The best way to generate a profile is to use 

```
sudo aa-genprof <app>
```

and then allow genprof to automatically generate the basic profile template.  This will keep everything in order.  From there you can use *aa-logprof* (which is broken in 9.10) or just use *tail -f*.

One thing you should do is install auditd.  This will make it *much* easier to read AppArmor logs, as they will all be stored in /var/log/audit and not in /var/log/messages.  One of the AppArmor developers said that he recommends it be done this way.

---

### Post by q.dinar on 2009-12-28
i have posted my profiles as they were at me. they are not complete mess , not random , requests for files are in order that they appear during start of application, and then during stop and use. i would sort that requests by type and alphabet if there were to many lines, but there is not too many , but i agree it is harder to you because not you made it , and easier for me because i remember it because i made it. and i had not need much to change my profiles, and if i want to check whether rule for a file is already there to edit it i can just press Ctrl+F and find that. and i agree that it is easier to find that if they are sorted. but topic is "share your apparmor profiles", there were not such restriction to post only well formatted profiles. i can do not post such profiles at all, i myself do not enough need for myself that they are well-formatted yet.

---

### Post by jgoguen on 2009-12-28
While it's true that there's no requirement to only post well-formatted profiles, it would be courteous to do so anyway.  For only your use, of course put your profiles however you want, you need to be able to easily work with them.  But here, where you're sharing profiles, people are much more likely to read, use and even help improve your profiles if they can easily read it.  And sometimes, formatting things well can help reveal things you can do to make your profile easier to read even for yourself, or reveal things you were doing that may not have been the most efficient or even unnecessary.  It's also a lot easier to work with the same profile you're posting.  

Yes, you're free to post your profiles formatted as you wish, but for exactly the same reason others are allowed to suggest different ways of formatting, so please try not to get too upset with it.  The reason for standards are so people can easily work together and new people can easily see what's going on without lots of (re-)training.  To you, it makes perfect sense, but to most other people it doesn't, and it's other people you should to consider when sharing profiles or asking for help.  You don't have to, it's just nice if you do.

---

### Post by running_rabbit07 on 2010-01-07
Has anyone created a strong profile for [COLOR=DarkOrange][Mozilla Prism]("http://prism.mozilla.com/") [/COLOR]and/or [COLOR=DarkOrange]ggl-gtk[/COLOR](Google Widgets) and/or [COLOR=DarkOrange]VirtualBox[/COLOR], yet? I use it for Facebook only. Now that I am on a role with getting AppArmor strengthened, I don't want to use programs without a profile.

Thanks

---

### Post by q.dinar on 2010-01-08
[http://ubuntuforums.org/showpost.php?p=8551897&postcount=59](http://ubuntuforums.org/showpost.php?p=8551897&postcount=59) - there is profile for virtualbox in ubuntu 9.04 , probably you need to add several rules to it if use in 9.10.

---

### Post by running_rabbit07 on 2010-01-08
Cool thanks, I'll check it out.

---

### Post by bodhi.zazen on 2010-01-08
Just as a FYI, I host some aa profiles on my server. As I see there is renewed interest, please feel free to look at the profiles as well.

If anyone would like, I am accepting profiles from the community as well, send me an PM if you are interested in contributing.

[http://bodhizazen.net/aa-profiles/](http://bodhizazen.net/aa-profiles/)

---

### Post by running_rabbit07 on 2010-01-08
Bodhi, I have quite a few of yours installed. Thanks for sharing them.

---

### Post by q.dinar on 2010-01-14
```
#include <tunables/global>

/usr/bin/xchat-gnome {
  #include <abstractions/base>
/proc/filesystems r,
  #include <abstractions/nameservice>
/var/run/gdm/auth-for-*-*/database r,
/usr/share/themes/** r,
/etc/gnome-vfs-2.0/modules/ r,
@{HOME}/.ICEauthority r,
/tmp/orbit-*/linc-*-*-* wr,
/etc/sound/** r,
@{HOME}/.xchat2/ wr,
/usr/share/xchat-gnome/** r,
/etc/gnome-vfs-2.0/modules/** r,
@{HOME}/.xchat2/** wr,
/etc/fonts/** r,
/var/cache/fontconfig/*-x86.cache-2 r,
/usr/share/fonts/ r,
/usr/share/fonts/** r,
/usr/lib/pango/** mr,
/var/lib/defoma/fontconfig.d/** r,
/usr/share/icons/** r,
/usr/local/share/icons/ r,
/usr/share/icons/ r,
@{HOME}/.config/enchant/ r,
/usr/share/enchant/** r,
/usr/share/pixmaps/ r,
/usr/share/myspell/dicts/ r,
/var/lib/aspell/** r,
/usr/share/myspell/dicts/** r,
/usr/lib/gtk-2.0/** mr,
@{HOME}/.esd_auth r,
/var/lib/dbus/machine-id r,
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/gvfs/remote-volume-monitors/** r,
/usr/share/mime/** r,
@{HOME}/.gnome2/accels/xchat-gnome wr,
@{HOME}/.recently-used.xbel rw,
@{HOME}/.gtk-bookmarks r,
@{HOME}/.config/user-dirs.dirs r,
@{HOME}/.config/gtk-2.0/gtkfilechooser.ini r,
/dev/tty rw,
/usr/share/xml/iso-codes/** r,
/usr/lib/xchat-gnome/** mr,
@{HOME}/.recently-used.xbel.* wr,
/home/ r,
/usr/share/libthai/** r,
/proc/*/fd/ r,
/usr/bin/xprop ix,
/usr/lib/firefox-3.5.*/firefox.sh PUx,








}
```

---

### Post by q.dinar on 2010-01-26
open office :
```
# min qdb yazam
#include <tunables/global>

/usr/lib/openoffice/program/soffice {
  #include <abstractions/base>
/etc/openoffice/soffice.sh r,
/usr/bin/stat ix,
/bin/uname ix,
/usr/bin/dirname ix,
/usr/bin/basename ix,
/proc/filesystems r,
/usr/lib/ure/bin/javaldx ix,
#/usr/lib/openoffice/basis3.1/program/pagein ix,
/usr/lib/openoffice/basis*/program/* ix,
/sys/devices/system/cpu/ r,
/etc/nsswitch.conf r,
/etc/passwd r,
@{HOME}/.openoffice.org/ rw,
@{HOME}/.openoffice.org/** rw,
#/var/lib/openoffice/basis3.1/program/services.rdb r,
/var/lib/openoffice/** rk,
/usr/lib/openoffice/program/*.bin ix,
/bin/dash ix,
/usr/lib/ure/lib/*.so m,
/etc/openoffice/ r,
/etc/openoffice/** r,
/var/run/gdm/auth-for-*-*/database r,
/usr/share/themes/** r,
/usr/bin/gconftool-2 ix,
/var/spool/openoffice/** rkw,
/usr/lib/ure/share/misc/types.rdb kr,
/tmp/*.tmp rwk,
@{HOME}/.execooo* wrm,
/etc/fonts/** r,
/tmp/orbit-*/linc-*-*-* wr,
/usr/lib/openoffice/** k,
/var/cache/fontconfig/** r,
/usr/share/fonts/ r,
/usr/local/share/fonts/ r,
/usr/share/fonts/** r,
/usr/local/share/fonts/** r,
/usr/lib/ure/share/misc/services.rdb k,
/tmp/.execooo* wrm,
/var/lib/defoma/fontconfig.d/** r,
/usr/lib/pango/**/*.so m,
/tmp/OSL_PIPE_1000_SingleOfficeIPC_* wr,
/tmp/ r,
/tmp/*.tmp/ wrk,
/usr/share/icons/** r,
/usr/lib/gtk-2.0/**/*.so m,
@{HOME}/.ICEauthority r,
/usr/bin/paperconf ix,
/etc/services ix,
#network inet stream,
#network inet6 stream,
/tmp/virtual-*.*/ r,
/tmp/*.tmp/*.tmp wrk,
/etc/papersize r,
/etc/services r,
#@{HOME}/.mozilla/ r,
@{HOME}/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ r,
@{HOME}/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/** r,
/home/MYSISTER/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/** w,
@{HOME}/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/ r,
@{HOME}/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/** r,
/home/MYSISTER/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/** w,
"@{HOME}/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/" r,
"@{HOME}/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/**" r,
"/home/MYSISTER/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/**" w,
/ r,
/{mnt,media}/ r,
/{mnt,media}/*/ r,
/{mnt,media}/*/**/ r,
/{mnt,media}/*/**/*.{doc,DOC,rtf,RTF,txt,TXT,odt,ODT,docx,DOCX,html,HTML,htm,HTM,xml,XML} rw,
@{HOME}/.recently-used wrk,
#saqlaw
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/gvfs/remote-volume-monitors/** r,
@{HOME}/.recently-used.xbel* rw,
/etc/fstab r,
/proc/*/mounts r,
@{HOME}/.gtk-bookmarks r,
/usr/local/share/icons/ r,
/usr/share/icons/ r,
/usr/share/pixmaps/ r,
/usr/local/share/icons/** r,
/usr/share/icons/** r,
/usr/share/pixmaps/** r,
@{HOME}/.config/gtk-2.0/gtkfilechooser.ini* rw,
/usr/share/mime/* r,
@{HOME}/.config/user-dirs.dirs r,
@{HOME}/ r,
@{HOME}/* r,





}

```
warning: open office tries to connect to internet and read .mozilla directory.
in this profile i have not made directory to write yet in home directory, but all files writable for my sister in some directories in her home directory.
and this can complain for additional files if you run open office first time.

---

### Post by q.dinar on 2010-01-26
```
# min qdb yazam
#include <tunables/global>

/usr/bin/gimp-2.* {
  #include <abstractions/base>
/proc/filesystems r,
/etc/nsswitch.conf r,
/etc/passwd r,
@{HOME}/.gimp-2.*/ wr,
@{HOME}/.gimp-2.*/** wr,
@{HOME}/.gegl-0.0/** r,
/usr/lib/babl-0.0/*.so m,
/usr/lib/gegl-0.0/*.so m,
/var/run/gdm/auth-for-*-*/database r,
/usr/share/themes/** r,
/etc/gimp/** r,
/usr/share/gimp/** r,
/etc/fonts/** r,
/var/cache/fontconfig/** r,
/usr/share/fonts/ r,
/usr/share/fonts/** r,
/usr/lib/pango/** m,
/var/lib/defoma/fontconfig.d/** r,
@{HOME}/.fontconfig/** rw,
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/gvfs/remote-volume-monitors/** r,
@{HOME}/.recently-used.xbel r,
/usr/lib/gimp/2.0/plug-ins/script-fu ix,
/usr/share/icons/** r,
/usr/share/icons/ r,
/usr/lib/gtk-2.0/** m,
/usr/local/share/icons/ r,
/usr/local/share/icons/** r,
/usr/share/pixmaps/ r,
/usr/share/pixmaps/** r,
/usr/share/mime/* r,
@{HOME}/ r,
@{HOME}/&#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080;/ r,
@{HOME}/&#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080;/** r,
@{HOME}/&#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080;/gimpocon/ rw,
@{HOME}/&#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080;/gimpocon/** rw,
/home/MYSISTER/&#1050;&#1072;&#1088;&#1090;&#1080;&#1085;&#1082;&#1080;/** rw,
@{HOME}/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/ r,
@{HOME}/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/** r,
/home/MYSISTER/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/** rw,
@{HOME}/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ r,
@{HOME}/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/** r,
/home/MYSISTER/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/** rw,
"@{HOME}/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/" r,
"@{HOME}/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/**" r,
"/home/MYSISTER/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/**" rw,
@{HOME}/&#1052;&#1091;&#1079;&#1099;&#1082;&#1072;/ r,
@{HOME}/&#1052;&#1091;&#1079;&#1099;&#1082;&#1072;/** r,
/home/MYSISTER/&#1052;&#1091;&#1079;&#1099;&#1082;&#1072;/** rw,
@{HOME}/.gtk-bookmarks r,
@{HOME}/.config/user-dirs.dirs r,
@{HOME}/.config/gtk-2.0/gtkfilechooser.ini* rw,
@{HOME}/.xsession-errors r,
@{HOME}/* r,
@{HOME}/.thumbnails/** rw,
/usr/lib/gimp/2.0/plug-ins/* ix,
@{HOME}/.recently-used.xbel* rw,














}
```

---

### Post by q.dinar on 2010-01-26
file and directory comparer "meld"
warning: this profile does not allow to save modified files
```
#aftoro qdb
#include <tunables/global>
/usr/bin/meld {
#include <abstractions/base>
#include <abstractions/python>
/usr/bin/python2.6 ix,
/usr/bin/meld r,
/proc/filesystems r,
/etc/nsswitch.conf r,
/etc/passwd r,
/var/run/gdm/auth-for-*-*/database r,
/usr/share/themes/** r,
/etc/gnome-vfs-2.0/modules/ r,
/etc/gnome-vfs-2.0/modules/** r,
/usr/share/meld/** r,
/etc/apt/apt.conf.d/ r,
/tmp/orbit-*/linc-*-*-* wr,
/etc/fonts/** r,
/var/cache/fontconfig/*-x86.cache-* r,
/usr/share/fonts/ r,
/usr/share/fonts/** r,
/usr/lib/pango/**/*.so mr,
/var/lib/defoma/fontconfig.d/** r,
/usr/share/icons/** r,
/usr/local/share/icons/** r,
/usr/share/pixmaps/** r,
/usr/local/share/icons/ r,
/usr/share/icons/ r,
/usr/share/pixmaps/ r,
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/gvfs/remote-volume-monitors/** r,
/usr/share/mime/** r,
/usr/lib/gtk-2.0/**/*.so mr,
/ r,
/**/ r,
@{HOME}/.recently-used.xbel rw,
@{HOME}/.gtk-bookmarks r,
@{HOME}/.config/user-dirs.dirs r,
@{HOME}/.config/gtk-2.0/gtkfilechooser.ini rw,
@{HOME}/.xsession-errors r,
@{HOME}/.gpilotd.pid r,
#@{HOME}/erl_crash.dump r,
@{HOME}/.recently-used.xbel.* wr,
@{HOME}/.esd_auth r,
@{HOME}/.pulse-cookie r,
@{HOME}/.ICEauthority r,
#@{HOME}/.sudo_as_admin_successful r,
#@{HOME}/.gksu.lock r,
#@{HOME}/.bash_history r,
#@{HOME}/.erlang.cookie r,
#@{HOME}/.mysql_history r,
@{HOME}/.dmrc r,
@{HOME}/* r,
@{HOME}/.config/gtk-2.0/gtkfilechooser.ini.* rw,
@{HOME}/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/ r,
@{HOME}/&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1099;/** r,
@{HOME}/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/ r,
@{HOME}/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;/** r,
/usr/share/gtksourceview-2.0/** r,





}
```

---

### Post by q.dinar on 2010-01-26
addition to usr.bin.passwd from apparmor profiles package ...doc.. extra directory:
```
# for ubuntu 9.10, added by qdb
/etc/.pwd.lock kr,
/proc/filesystems r,
/var/run/utmp rkw,
/etc/nshadow rw,
capability fsetid,
capability setuid,
/usr/bin/gnome-keyring-daemon PUx,
```

---

### Post by q.dinar on 2010-05-24
all my current apparmor profiles: [http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/) . for ubuntu 9.10 . these are real, loaded profiles.
new profiles among them:
[usr.bin.skype](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.skype)
[usr.bin.zekr](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.zekr)
[usr.sbin.PootleServer](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.sbin.PootleServer)
[etc.init.d.pootle](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/etc.init.d.pootle)
[usr.bin.rhythmbox](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.rhythmbox)
[usr.bin.ghex2](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.ghex2)
[usr.bin.liveice](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.liveice)
[usr.bin.icecast](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.icecast)
[usr.bin.darkice](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.darkice)
[usr.bin.emacs23-x](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.emacs23-x)
profiles that i had not said here:
[usr.lib.apache2.mpm-worker.apache2](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.lib.apache2.mpm-worker.apache2)
[usr.bin.omegat](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.omegat)
[usr.bin.cronolog](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.cronolog)
[usr.bin.awffull](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.awffull)

add at 15:59 utc+4 :
this site now works only from 6:55 till 23:55 utc+4 .

---

### Post by bodhi.zazen on 2010-05-24
> **q.dinar said:**
> all my current apparmor profiles: [http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/](http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/) . for ubuntu 9.10 . these are real, loaded profiles.
new profiles among them:
[usr.bin.skype]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.skype")
[usr.bin.zekr]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.zekr")
[usr.sbin.PootleServer]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.sbin.PootleServer")
[etc.init.d.pootle]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/etc.init.d.pootle")
[usr.bin.rhythmbox]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.rhythmbox")
[usr.bin.ghex2]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.ghex2")
[usr.bin.liveice]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.liveice")
[usr.bin.icecast]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.icecast")
[usr.bin.darkice]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.darkice")
[usr.bin.emacs23-x]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.emacs23-x")
profiles that i had not said here:
[usr.lib.apache2.mpm-worker.apache2]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.lib.apache2.mpm-worker.apache2")
[usr.bin.omegat]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.omegat")
[usr.bin.cronolog]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.cronolog")
[usr.bin.awffull]("http://qdb.tmf.org.ru/9.10_ubuntu_apparmor_profillaro/usr.bin.awffull")

add at 15:59 utc+4 :
this site now works only from 6:55 till 23:55 utc+4 .

If you would like, send me your profiles (zip or tar ball) and I will post them on my server. IMO it helps to keep these things in one location and it does not sound as if your server is up 24/7 .

I will PM you my e-mail.

---

### Post by tlu on 2010-05-25
[This]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/561564") bug on launchpad confirms what I observed on my machine. How can I modify the Firefox profile to make Flashgot work?

---

### Post by bodhi.zazen on 2010-05-25
> **tlu said:**
> [This]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/561564") bug on launchpad confirms what I observed on my machine. How can I modify the Firefox profile to make Flashgot work?

You will need to look at the logs

/var/log/messages

And edit the firefox profile

See the apparmor thread for details.

[Introduction to AppArmor]("http://ubuntuforums.org/showthread.php?t=1008906")

---

### Post by tlu on 2010-05-25
> **bodhi.zazen said:**
> You will need to look at the logs

/var/log/messages[/QUOTE

There I find the following entries:

```
type=1502 audit(1274795059.417:103643):  operation="open" pid=6693 parent=6692 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-59" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.xxxxx.Default_20User/flashgot.fgt"

type=1502 audit(1274795059.417:103644):  operation="mknod" pid=6695 parent=6693 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-59" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.xxxxx.Default_20User/flashgot.sh.test"

type=1502 audit(1274795059.417:103645):  operation="open" pid=6695 parent=6693 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-59" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.xxxxx.Default_20User/flashgot.sh.test"
```

[quote]And edit the firefox profile

I'm not quite sure how. I understand that Flashgot performs a test with every FF start for the available download managers and writes to the tmp folder. So a rule may look like

@{HOME}/tmp/** w

IMHO, but isn't that already covered by 

owner @{HOME}/** w

???

---

### Post by bodhi.zazen on 2010-05-25
> **tlu said:**
> [QUOTE=bodhi.zazen;9357827]You will need to look at the logs

/var/log/messages[/QUOTE

There I find the following entries:

```
type=1502 audit(1274795059.417:103643):  operation="open" pid=6693 parent=6692 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-59" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.xxxxx.Default_20User/flashgot.fgt"

type=1502 audit(1274795059.417:103644):  operation="mknod" pid=6695 parent=6693 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-59" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.xxxxx.Default_20User/flashgot.sh.test"

type=1502 audit(1274795059.417:103645):  operation="open" pid=6695 parent=6693 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-59" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.xxxxx.Default_20User/flashgot.sh.test"
```

I'm not quite sure how. I understand that Flashgot performs a test with every FF start for the available download managers and writes to the tmp folder. So a rule may look like

@{HOME}/tmp/** w

IMHO, but isn't that already covered by 

owner @{HOME}/** w

???

Well, those errors are for a "null" , so something was denied x access , thus the "null".

You will need to either wait for a fix or debug the profile. To debug the profile, the following commands often help

1. tail -F /var/log/messages

2. aa-logprof

3. Put firefox into complain mode.

Close and restart firefox, browse web pages, and debug errors as they occur in the logs.

I can not debug the profile for you unless you post

1. your current firefox profile

2. **ALL** the logs, not a snippits or partial logs.

Please keep in mind , we are all volunteers, so we may not have time to do this for you.

---

### Post by bapoumba on 2010-05-26
Ping bodhi :)
[http://ubuntuforums.org/showpost.php?p=9365820&postcount=2](http://ubuntuforums.org/showpost.php?p=9365820&postcount=2)

---

### Post by bodhi.zazen on 2010-05-26
> **bapoumba said:**
> Ping bodhi :)
[http://ubuntuforums.org/showpost.php?p=9365820&postcount=2](http://ubuntuforums.org/showpost.php?p=9365820&postcount=2)

I am honored, thank you for highlighting Security =)

---

### Post by tlu on 2010-05-27
Okay, here we go.:)

> **bodhi.zazen said:**
> 

Well, those errors are for a "null" , so something was denied x access , thus the "null".

You will need to either wait for a fix or debug the profile. To debug the profile, the following commands often help

1. tail -F /var/log/messages

2. aa-logprof

3. Put firefox into complain mode.

Close and restart firefox, browse web pages, and debug errors as they occur in the logs.

Done.

> I can not debug the profile for you unless you post

1. your current firefox profile

```
# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

#include <tunables/global>

/usr/lib/firefox-3.6.5pre/firefox-*bin flags=(complain) {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/fonts>
  #include <abstractions/freedesktop.org>
  #include <abstractions/gnome>
  #include <abstractions/kde>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/X>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/timezone r,
  /etc/wildmidi/wildmidi.cfg r,
  /etc/xdg/xubuntu/applications/defaults.list r,
  /usr/bin/dbus-launch ixr,
  /usr/bin/scim Ux,
  /usr/bin/scim-bridge Ux,
  /usr/bin/apport-bug Ux,
  /usr/local/lib{,32,64}/*.so* mr,
  /usr/lib/gstreamer0.10/gstreamer-0.10/gst-plugin-scanner ix,
  /usr/bin/apturl Uxr,

  # firefox specific
  /etc/firefox*/ r,
  /etc/firefox*/** r,
  /etc/xul-ext/** r,
  /etc/xulrunner-1.9*/ r,
  /etc/xulrunner-1.9*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny /usr/lib/firefox-3.6.5pre/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,

  # These are needed when a new user starts firefox and firefox.sh is used
  /usr/lib/firefox-3.6.5pre/** ixr,
  /usr/bin/basename ixr,
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  /usr/bin/tr ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,

  /etc/mtab r,
  /etc/fstab r,

  # allow access to documentation and other files the user may want to look
  # at in /usr
  /usr/ r,
  /usr/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # allow read and write to all user's files, except explicitly denied ones
  @{HOME}/ r,
  @{HOME}/** r,
  owner @{HOME}/** w,
  owner @{HOME}/Desktop/** r,

  # removable media and filesystems
  /media/** r,
  /mnt/** r,
  /srv/** r,
  owner /media/** w,
  owner /mnt/** w,
  owner /srv/** w,

  #include <abstractions/private-files>
  audit deny @{HOME}/.ssh/** mrwkl,
  audit deny @{HOME}/.gnome2_private/** mrwkl,

  # comment this out if using gpg plugin/addons
  audit deny @{HOME}/.gnupg/** mrwkl,

  # per-user firefox configuration
  owner @{HOME}/.mozilla/ rw,
  owner @{HOME}/.mozilla/** rw,
  owner @{HOME}/.mozilla/**/*.sqlite* k,
  owner @{HOME}/.mozilla/**/.parentlock k,
  owner @{HOME}/.mozilla/plugins/** rm,
  owner @{HOME}/.mozilla/**/plugins/** rm,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny /usr/lib/firefox-3.6.5pre/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  #
  # Plugins/helpers
  #
  @{PROC}/[0-9]*/fd/ r,
  /usr/lib/** rm,
  /bin/bash ixr,
  /bin/dash ixr,
  /bin/grep ixr,
  /bin/sed ixr,
  /bin/ps Uxr,
  /bin/uname Uxr,
  /usr/bin/gnome-codec-install Uxr,
  /usr/bin/m4 ixr,
  /usr/bin/mkfifo Uxr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer Uxr,
  /usr/bin/pulseaudio ixr,
  /var/lib/ r,
  /var/lib/** mr,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # for maximum plugin/helper compatibility
  #/usr/bin/* Uxr,
  #/usr/lib/*/** ixr,

  #
  # For stricter access, comment out the 'maximum plugin/helper compatibility'
  # lines above and uncomment these
  #

  # for PDFs
  owner @{HOME}/.adobe/** rw,
  /opt/Adobe/Reader9/bin/acroread Uxr,
  /opt/Adobe/Reader9/** r,
  /usr/bin/evince PUxr,
  /usr/bin/okular Uxr,

  # Image viewers
  /usr/bin/eog Uxr,
  /usr/bin/gimp* Uxr,

  # Openoffice.org
  /usr/bin/ooffice Uxr,
  /usr/bin/oocalc Uxr,
  /usr/bin/oodraw Uxr,
  /usr/bin/ooimpress Uxr,
  /usr/bin/oowriter Uxr,
  /usr/lib/openoffice/program/soffice Uxr,

  # Multimedia
  #include <abstractions/ubuntu-media-players>
  owner @{HOME}/.macromedia/** rw,
  /opt/real/RealPlayer/mozilla/nphelix.so rm,

  # Bittorrent clients
  #include <abstractions/ubuntu-bittorrent-clients>

  # Archivers
  /usr/bin/ark Uxr,
  /usr/bin/file-roller Uxr,
  /usr/bin/xarchiver Uxr,

  # Text editors (It's All Text [https://addons.mozilla.org/en-US/firefox/addon/4125])
  /usr/bin/emacsclient.emacs-snapshot Uxr,
  /usr/bin/emacsclient.emacs22 Uxr,
  /usr/bin/gedit Uxr,
  /usr/bin/vim.gnome Uxr,
  /usr/bin/leafpad Uxr,
  /usr/bin/mousepad Uxr,

  # Mozplugger
  /etc/mozpluggerrc r,
  /usr/bin/mozplugger-helper Uxr,

  # Java
  @{HOME}/.java/deployment/deployment.properties k,
  /etc/java-*/ r,
  /etc/java-*/** r,
  /usr/lib/jvm/java-6-openjdk/jre/bin/java cx -> firefox_openjdk,
  /usr/lib/jvm/java-*-sun-1.*/jre/bin/java{,_vm} cx -> firefox_java,
  /usr/lib/jvm/java-*-sun-1.*/jre/lib/*/libnp*.so cx -> firefox_java,
  /usr/lib/j2*-ibm/jre/bin/java cx -> firefox_java,

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

  # Miscellaneous (to be abstracted)
  /usr/bin/nautilus Uxr,
  /usr/bin/thunar Uxr,
  /usr/bin/liferea-add-feed Uxr,


  #
  # Child profiles
  #

  # Profile for the supported OpenJDK in Ubuntu. This doesn't require the
  # unfortunate workarounds of the proprietary Javas, so have a separate
  # profile.
profile firefox_openjdk flags=(complain) {
    #include <abstractions/base>
    #include <abstractions/fonts>
    #include <abstractions/gnome>
    #include <abstractions/kde>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/user-tmp>
    #include <abstractions/private-files-strict>

    network inet stream,
    network inet6 stream,
    @{PROC}/[0-9]*/net/if_inet6 r,
    @{PROC}/[0-9]*/net/ipv6_route r,

    /etc/java-*/ r,
    /etc/java-*/** r,
    /etc/lsb-release r,
    /etc/ssl/certs/java/* r,
    /etc/timezone r,

    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/filesystems r,
    /sys/devices/system/cpu/ r,
    /sys/devices/system/cpu/** r,
    /usr/share/** r,
    /var/lib/dbus/machine-id r,

    /usr/bin/env ix,
    /usr/lib/jvm/java-6-openjdk/jre/bin/java ix,
    /usr/lib/jvm/java-6-openjdk/jre/lib/i386/client/classes.jsa m,

    # Why would java need this?
    deny /usr/bin/gconftool-2 x,

    owner @{HOME}/ r,
    owner @{HOME}/** rwk,
  }

  # Profile for commercial Javas. These need workarounds to work right (eg
  # Sun's forcing of an executable stack (LP: #535247)).
profile firefox_java flags=(complain) {
    #include <abstractions/base>
    #include <abstractions/fonts>
    #include <abstractions/gnome>
    #include <abstractions/kde>
    #include <abstractions/nameservice>
    #include <abstractions/ssl_certs>
    #include <abstractions/user-tmp>
    #include <abstractions/private-files-strict>

    network inet stream,
    network inet6 stream,
    @{PROC}/[0-9]*/net/if_inet6 r,
    @{PROC}/[0-9]*/net/ipv6_route r,

    /etc/java-*/ r,
    /etc/java-*/** r,
    /etc/lsb-release r,
    /etc/ssl/certs/java/* r,
    /etc/timezone r,

    @{PROC}/[0-9]*/ r,
    @{PROC}/[0-9]*/fd/ r,
    @{PROC}/filesystems r,
    /sys/devices/system/cpu/ r,
    /sys/devices/system/cpu/** r,
    /usr/share/** r,
    /var/lib/dbus/machine-id r,

    /usr/bin/env ix,
    /usr/lib/jvm/java-*-sun-1.*/jre/bin/java{,_vm} ix,
    /usr/lib/jvm/java-*-sun-1.*/jre/lib/i386/client/classes.jsa m,
    /usr/lib/j2*-ibm/jre/bin/java ix,

    # noisy, can't write here anyway
    deny /etc/.java/ w,
    deny /etc/.java/** w,

    deny /usr/bin/gconftool-2 x,

    owner @{HOME}/ r,
    owner @{HOME}/** rwk,

    # These are seriously unfortunate, but required due to LP: #535247
    /etc/passwd m,
    owner @{HOME}/.java/**/cache/** m,
    owner /tmp/** m,
    /usr/lib{,32,64}/jvm/**/*.jar mr,
    /usr/share/fonts/** m,
  }
}

```

2. **ALL** the logs, not a snippits or partial logs.
```
May 27 19:27:53 HANNIBAL kernel: [ 4615.385020] __ratelimit: 171 callbacks suppressed
May 27 19:27:53 HANNIBAL kernel: [ 4615.385023] type=1502 audit(1274981273.799:2833):  operation="exec" pid=3863 parent=3862 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a"
May 27 19:27:53 HANNIBAL kernel: [ 4615.386674] type=1502 audit(1274981273.799:2834):  operation="open" pid=3863 parent=3862 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 27 19:27:53 HANNIBAL kernel: [ 4615.386701] type=1502 audit(1274981273.799:2835):  operation="open" pid=3863 parent=3862 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 27 19:27:53 HANNIBAL kernel: [ 4615.386713] type=1502 audit(1274981273.799:2836):  operation="file_mmap" pid=3863 parent=3862 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 27 19:27:53 HANNIBAL kernel: [ 4615.386945] type=1502 audit(1274981273.799:2837):  operation="open" pid=3863 parent=3862 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"
May 27 19:27:53 HANNIBAL kernel: [ 4615.387076] type=1502 audit(1274981273.799:2838):  operation="mknod" pid=3864 parent=3863 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 27 19:27:53 HANNIBAL kernel: [ 4615.387096] type=1502 audit(1274981273.799:2839):  operation="open" pid=3864 parent=3863 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 27 19:27:53 HANNIBAL kernel: [ 4615.387111] type=1502 audit(1274981273.799:2840):  operation="open" pid=3864 parent=3863 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="::wc" denied_mask="::wc" fsuid=1000 ouid=0 name="/dev/null"
May 27 19:27:53 HANNIBAL kernel: [ 4615.387264] type=1502 audit(1274981273.799:2841):  operation="exec" pid=3865 parent=3864 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/bin/which" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a//null-4b"
May 27 19:27:53 HANNIBAL kernel: [ 4615.387502] type=1502 audit(1274981273.799:2842):  operation="open" pid=3865 parent=3864 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a//null-4b" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 27 19:34:20 HANNIBAL kernel: [ 5002.259512] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37988 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:20 HANNIBAL kernel: [ 5002.309759] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37990 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:20 HANNIBAL kernel: [ 5002.319601] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37989 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:20 HANNIBAL kernel: [ 5002.337848] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37992 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:21 HANNIBAL kernel: [ 5002.767097] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37993 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:21 HANNIBAL kernel: [ 5003.073328] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37995 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:21 HANNIBAL kernel: [ 5003.094728] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37998 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:21 HANNIBAL kernel: [ 5003.330665] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37996 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:21 HANNIBAL kernel: [ 5003.361158] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=37999 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:34:22 HANNIBAL kernel: [ 5003.822960] [UFW BLOCK] IN=eth0 OUT= MAC=00:1d:7d:ad:8f:1a:00:0f:b5:c9:9f:54:08:00 SRC=63.245.209.92 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=52 ID=0 DF PROTO=TCP SPT=443 DPT=38000 WINDOW=0 RES=0x00 RST URGP=0 
May 27 19:36:31 HANNIBAL kernel: [ 5133.520769] __ratelimit: 171 callbacks suppressed
May 27 19:36:31 HANNIBAL kernel: [ 5133.520773] type=1502 audit(1274981791.935:2900):  operation="exec" pid=4117 parent=4116 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523085] type=1502 audit(1274981791.935:2901):  operation="open" pid=4117 parent=4116 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523124] type=1502 audit(1274981791.935:2902):  operation="open" pid=4117 parent=4116 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523140] type=1502 audit(1274981791.935:2903):  operation="file_mmap" pid=4117 parent=4116 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523471] type=1502 audit(1274981791.935:2904):  operation="open" pid=4117 parent=4116 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523665] type=1502 audit(1274981791.935:2905):  operation="mknod" pid=4118 parent=4117 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523693] type=1502 audit(1274981791.935:2906):  operation="open" pid=4118 parent=4117 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523714] type=1502 audit(1274981791.935:2907):  operation="open" pid=4118 parent=4117 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="::wc" denied_mask="::wc" fsuid=1000 ouid=0 name="/dev/null"
May 27 19:36:31 HANNIBAL kernel: [ 5133.523937] type=1502 audit(1274981791.935:2908):  operation="exec" pid=4119 parent=4118 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/bin/which" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56//null-57"
May 27 19:36:31 HANNIBAL kernel: [ 5133.524555] type=1502 audit(1274981791.939:2909):  operation="open" pid=4119 parent=4118 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-56//null-57" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
```


> Please keep in mind , we are all volunteers, so we may not have time to do this for you.

I understand that, and I appreciate your work!

---

### Post by bodhi.zazen on 2010-05-27
Do you see the "null" in those logs ?
 
May 27 19:27:53 HANNIBAL kernel: [ 4615.385023] type=1502 audit(1274981273.799:2833):  operation="exec" pid=3863 parent=3862 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt" name2="**/usr/lib/firefox-3.6.5pre/firefox-*bin//null-4a**"

I emphasized that one ^^

When firefox calls an program, such as /bin/sh or /bin/foo, if your apparmor profile denies access, all the rest of the calls are denied and labeled "null"

so "firefox-*bin//null-xx"

The null profile will give all sorts of errors, these are all red herrings.

You need to fix the original execution denial, the one that triggered all those nulls.

Since you have not posted that, I can not fix your problem as you have not posted the original denial, the one that triggered all those nulls.

---

### Post by bodhi.zazen on 2010-05-27
Furthermore, your profile is not in complain mode, so if you are having a problem, it is not due to apparmor.

---

### Post by tlu on 2010-05-28
> **bodhi.zazen said:**
> 
You need to fix the original execution denial, the one that triggered all those nulls.

Since you have not posted that, I can not fix your problem as you have not posted the original denial, the one that triggered all those nulls.

Thanks, bodhi.zazen. Here's the complete output:
```
tail -F /var/log/messages
May 28 13:12:59 HANNIBAL kernel: [ 4516.753204] type=1502 audit(1275045179.837:246):  operation="open" pid=3728 parent=3727 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753216] type=1502 audit(1275045179.837:247):  operation="file_mmap" pid=3728 parent=3727 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753445] type=1502 audit(1275045179.837:248):  operation="open" pid=3728 parent=3727 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753575] type=1502 audit(1275045179.837:249):  operation="mknod" pid=3730 parent=3728 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753594] type=1502 audit(1275045179.837:250):  operation="open" pid=3730 parent=3728 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753608] type=1502 audit(1275045179.837:251):  operation="open" pid=3730 parent=3728 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::wc" denied_mask="::wc" fsuid=1000 ouid=0 name="/dev/null"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753768] type=1502 audit(1275045179.837:252):  operation="exec" pid=3731 parent=3730 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/bin/which" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-49"
May 28 13:12:59 HANNIBAL kernel: [ 4516.754015] type=1502 audit(1275045179.837:253):  operation="open" pid=3731 parent=3730 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-49" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 28 13:27:40 HANNIBAL sudo: pam_sm_authenticate: Called
May 28 13:27:40 HANNIBAL sudo: pam_sm_authenticate: username = [tlu]
^C
tlu@HANNIBAL:~$ sudo aa-logprof
Reading log entries from /var/log/messages.
Updating AppArmor profiles in /etc/apparmor.d.
tlu@HANNIBAL:~$ tail -F /var/log/messages
May 28 13:12:59 HANNIBAL kernel: [ 4516.753204] type=1502 audit(1275045179.837:246):  operation="open" pid=3728 parent=3727 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753216] type=1502 audit(1275045179.837:247):  operation="file_mmap" pid=3728 parent=3727 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753445] type=1502 audit(1275045179.837:248):  operation="open" pid=3728 parent=3727 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753575] type=1502 audit(1275045179.837:249):  operation="mknod" pid=3730 parent=3728 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753594] type=1502 audit(1275045179.837:250):  operation="open" pid=3730 parent=3728 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753608] type=1502 audit(1275045179.837:251):  operation="open" pid=3730 parent=3728 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::wc" denied_mask="::wc" fsuid=1000 ouid=0 name="/dev/null"
May 28 13:12:59 HANNIBAL kernel: [ 4516.753768] type=1502 audit(1275045179.837:252):  operation="exec" pid=3731 parent=3730 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/bin/which" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-49"
May 28 13:12:59 HANNIBAL kernel: [ 4516.754015] type=1502 audit(1275045179.837:253):  operation="open" pid=3731 parent=3730 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-49" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 28 13:27:40 HANNIBAL sudo: pam_sm_authenticate: Called
May 28 13:27:40 HANNIBAL sudo: pam_sm_authenticate: username = [tlu]
May 28 13:32:47 HANNIBAL kernel: [ 5704.841463] __ratelimit: 171 callbacks suppressed
May 28 13:32:47 HANNIBAL kernel: [ 5704.841467] type=1502 audit(1275046367.925:311):  operation="exec" pid=4179 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54"
May 28 13:32:47 HANNIBAL kernel: [ 5704.843740] type=1502 audit(1275046367.925:312):  operation="open" pid=4179 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 28 13:32:47 HANNIBAL kernel: [ 5704.843779] type=1502 audit(1275046367.925:313):  operation="open" pid=4179 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:32:47 HANNIBAL kernel: [ 5704.843796] type=1502 audit(1275046367.925:314):  operation="file_mmap" pid=4179 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:32:47 HANNIBAL kernel: [ 5704.844125] type=1502 audit(1275046367.929:315):  operation="open" pid=4179 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"
May 28 13:32:47 HANNIBAL kernel: [ 5704.844312] type=1502 audit(1275046367.929:316):  operation="mknod" pid=4180 parent=4179 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 28 13:32:47 HANNIBAL kernel: [ 5704.844347] type=1502 audit(1275046367.929:317):  operation="open" pid=4180 parent=4179 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.sh.test"
May 28 13:32:47 HANNIBAL kernel: [ 5704.844368] type=1502 audit(1275046367.929:318):  operation="open" pid=4180 parent=4179 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="::wc" denied_mask="::wc" fsuid=1000 ouid=0 name="/dev/null"
May 28 13:32:47 HANNIBAL kernel: [ 5704.844599] type=1502 audit(1275046367.929:319):  operation="exec" pid=4181 parent=4180 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/bin/which" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-55"
May 28 13:32:47 HANNIBAL kernel: [ 5704.845427] type=1502 audit(1275046367.929:320):  operation="open" pid=4181 parent=4180 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-55" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 28 13:36:14 HANNIBAL kernel: [ 5911.790337] __ratelimit: 171 callbacks suppressed
May 28 13:36:14 HANNIBAL kernel: [ 5911.790341] type=1502 audit(1275046574.873:378):  operation="exec" pid=4207 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot-1.fgt" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60"
May 28 13:36:14 HANNIBAL kernel: [ 5911.793490] type=1502 audit(1275046574.877:379):  operation="open" pid=4207 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/etc/ld.so.cache"
May 28 13:36:14 HANNIBAL kernel: [ 5911.793529] type=1502 audit(1275046574.877:380):  operation="open" pid=4207 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:36:14 HANNIBAL kernel: [ 5911.793546] type=1502 audit(1275046574.877:381):  operation="file_mmap" pid=4207 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/lib/tls/i686/cmov/libc-2.11.1.so"
May 28 13:36:14 HANNIBAL kernel: [ 5911.793872] type=1502 audit(1275046574.877:382):  operation="open" pid=4207 parent=4178 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot-1.fgt"
May 28 13:36:14 HANNIBAL kernel: [ 5911.794003] type=1502 audit(1275046574.877:383):  operation="open" pid=4210 parent=4207 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/dev/null"
May 28 13:36:14 HANNIBAL kernel: [ 5911.794125] type=1502 audit(1275046574.877:384):  operation="exec" pid=4210 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60" requested_mask="::x" denied_mask="::x" fsuid=1000 ouid=0 name="/usr/bin/kget" name2="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61"
May 28 13:36:14 HANNIBAL kernel: [ 5911.818437] type=1502 audit(1275046574.902:385):  operation="open" pid=4210 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/usr/lib/libkdeui.so.5.4.0"
May 28 13:36:14 HANNIBAL kernel: [ 5911.818453] type=1502 audit(1275046574.902:386):  operation="file_mmap" pid=4210 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="::mr" denied_mask="::mr" fsuid=1000 ouid=0 name="/usr/lib/libkdeui.so.5.4.0"
May 28 13:36:14 HANNIBAL kernel: [ 5911.818523] type=1502 audit(1275046574.902:387):  operation="open" pid=4210 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/usr/lib/libkio.so.5.4.0"
May 28 13:36:20 HANNIBAL kernel: [ 5917.701743] __ratelimit: 5838 callbacks suppressed
May 28 13:36:20 HANNIBAL kernel: [ 5917.701746] type=1502 audit(1275046580.786:2334):  operation="truncate" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/home/tlu/.kde/share/apps/kget/transfers.kgt"
May 28 13:36:20 HANNIBAL kernel: [ 5917.701798] type=1502 audit(1275046580.786:2335):  operation="open" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/.kde/share/apps/kget/transfers.kgt"
May 28 13:36:21 HANNIBAL kernel: [ 5918.283662] type=1502 audit(1275046581.367:2336):  operation="unlink" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="d::" denied_mask="d::" fsuid=1000 ouid=1000 name="/home/tlu/.kde/share/apps/kget/checksumsearch/0"
May 28 13:36:21 HANNIBAL kernel: [ 5918.288437] type=1502 audit(1275046581.373:2337):  operation="mknod" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/tmp/ksocket-tlu/kgetNu4211.slave-socket"
May 28 13:36:21 HANNIBAL kernel: [ 5918.288469] type=1502 audit(1275046581.373:2338):  operation="open" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="rwc::" denied_mask="rwc::" fsuid=1000 ouid=1000 name="/tmp/ksocket-tlu/kgetNu4211.slave-socket"
May 28 13:36:21 HANNIBAL kernel: [ 5918.288504] type=1502 audit(1275046581.373:2339):  operation="unlink" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="d::" denied_mask="d::" fsuid=1000 ouid=1000 name="/tmp/ksocket-tlu/kgetNu4211.slave-socket"
May 28 13:36:21 HANNIBAL kernel: [ 5918.288549] type=1502 audit(1275046581.373:2340):  operation="mknod" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="c::" denied_mask="c::" fsuid=1000 ouid=1000 name="/tmp/ksocket-tlu/kgetNu4211.slave-socket"
May 28 13:36:21 HANNIBAL kernel: [ 5918.311708] type=1502 audit(1275046581.393:2341):  operation="unlink" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="d::" denied_mask="d::" fsuid=1000 ouid=1000 name="/tmp/ksocket-tlu/kgetNu4211.slave-socket"
May 28 13:36:23 HANNIBAL kernel: [ 5920.056800] type=1502 audit(1275046583.142:2342):  operation="truncate" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/var/tmp/kdecache-tlu/kpc/kde-icon-cache.updated"
May 28 13:36:23 HANNIBAL kernel: [ 5920.056826] type=1502 audit(1275046583.142:2343):  operation="open" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/var/tmp/kdecache-tlu/kpc/kde-icon-cache.updated"
May 28 13:36:35 HANNIBAL kernel: [ 5932.823483] __ratelimit: 9 callbacks suppressed
May 28 13:36:35 HANNIBAL kernel: [ 5932.823487] type=1502 audit(1275046595.905:2347):  operation="truncate" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/var/tmp/kdecache-tlu/kpc/kde-icon-cache.updated"
May 28 13:36:35 HANNIBAL kernel: [ 5932.823505] type=1502 audit(1275046595.905:2348):  operation="open" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/var/tmp/kdecache-tlu/kpc/kde-icon-cache.updated"
May 28 13:36:41 HANNIBAL kernel: [ 5938.321409] type=1502 audit(1275046601.406:2349):  operation="truncate" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="w::" denied_mask="w::" fsuid=1000 ouid=1000 name="/home/tlu/.kde/share/apps/kget/transfers.kgt"
May 28 13:36:41 HANNIBAL kernel: [ 5938.321475] type=1502 audit(1275046601.406:2350):  operation="open" pid=4211 parent=1 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61" requested_mask="wc::" denied_mask="wc::" fsuid=1000 ouid=1000 name="/home/tlu/.kde/share/apps/kget/transfers.kgt"
```

> Furthermore, your profile is not in complain mode, so if you are having a problem, it is not due to apparmor. 

Sorry, but according to aa-status it's definitely in complain mode:

```
sudo aa-status
apparmor module is loaded.
108 profiles are loaded.
11 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/mysqld-akonadi
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession
97 profiles are in complain mode.
   /bin/ping
   /sbin/klogd
   /sbin/syslog-ng
   /sbin/syslogd
   /usr/lib/dovecot/deliver
   /usr/lib/dovecot/dovecot-auth
   /usr/lib/dovecot/imap
   /usr/lib/dovecot/imap-login
   /usr/lib/dovecot/managesieve-login
   /usr/lib/dovecot/pop3
   /usr/lib/dovecot/pop3-login
   /usr/lib/firefox-3.6.5pre/firefox-*bin
   /usr/lib/firefox-3.6.5pre/firefox-*bin//firefox_java
   /usr/lib/firefox-3.6.5pre/firefox-*bin//firefox_openjdk
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-25
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-26
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-27
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-28
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-29
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-2a
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-2b
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-2c
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-2d
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-2e
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-24//null-2f
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-31
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-32
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-33
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-34
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-35
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-36
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-37
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-38
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-39
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-3a
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-30//null-3b
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-3d
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-3e
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-3f
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-40
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-41
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-42
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-43
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-44
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-45
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-46
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-3c//null-47
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-49
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-4a
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-4b
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-4c
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-4d
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-4e
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-4f
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-50
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-51
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-52
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-48//null-53
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-55
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-56
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-57
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-58
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-59
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-5a
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-5b
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-5c
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-5d
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-5e
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-54//null-5f
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-60
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-63
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-64
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-65
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-66
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-67
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-68
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-69
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-6a
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-6b
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-6c
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-62//null-6d
   /usr/sbin/avahi-daemon
   /usr/sbin/dnsmasq
   /usr/sbin/dovecot
   /usr/sbin/identd
   /usr/sbin/mdnsd
   /usr/sbin/nmbd
   /usr/sbin/nscd
   /usr/sbin/smbd
   /usr/sbin/traceroute
6 processes have profiles defined.
2 processes are in enforce mode :
   /sbin/dhclient3 (1226) 
   /usr/sbin/cupsd (1974) 
4 processes are in complain mode.
   /usr/lib/firefox-3.6.5pre/firefox-*bin (4241) 
   /usr/lib/firefox-3.6.5pre/firefox-*bin//null-60//null-61 (4211) 
   /usr/sbin/avahi-daemon (1154) 
   /usr/sbin/avahi-daemon (1159) 
0 processes are unconfined but have a profile defined.

```

---

### Post by bodhi.zazen on 2010-05-28
> **tlu said:**
> Thanks, bodhi.zazen. Here's the complete output:


Well, you are in quite a tizzy I see.

You really need to start over.

1. Stop firefox.

2. Reload apparmor

```
sudo service apparmor stop
sudo service apparmor start
```

That will clear out all those null profiles.

3. You need to understand what you are doing as I think you are missing the point. As I keep telling you, a null profile is generated when the apparmor denies execute access to something. 

In complain mode, access is allowed, but the process is then named null something. For example, you have a long list, 

/usr/lib/firefox-3.6.5pre/firefox-*bin//null-24

See the null-24 ?

Apparmor will generate a denial for everything "/usr/lib/firefox-3.6.5pre/firefox-*bin//null-24" tries to access.

You do not debug "/usr/lib/firefox-3.6.5pre/firefox-*bin//null-24" , you fix the initial denial that caused "/usr/lib/firefox-3.6.5pre/firefox-*bin//null-24" to be created.

So you have to look up in your logs to the last denial that does not contain a "null". Fix that denial, and the nulls will go away.

This elaborate procedure is to "help" debugging apparmor profiles, but in practice, it is of little help at all, and as you can see, causes more confusion.

You do not "debug" anything with a "//null-xx" in the name, you have to debug the initial denial that caused the null.

As with previous posts, you are not posting the initial denial. Your posts keep getting longer, but I do not think you understand what to look for.

Please:

1. Do not post long logs like that. They do not help and only clutter your posts.

2. Do not post any log message that contains a null profile. They clutter your post and do not help at all.


Now, open a terminal. Enter:

```
tail -F /var/log/messages
```

Watch this terminal for errors.

With your firefox apparmor in complain mode, open firefox. If firefox is not working, apparmor is not the problem -> go debug firefox or whatever addon or plugin that is broken.

If firefox works, close firefox, and debug any denials you received in the "tail -F /var/log/messages" terminal.

Keep repeating until you have managed all the denials.

Then put the firefox profile into enforcing mode and try to start firefox.

Post any denial you do not understand, but do not post any denial with a null profile in it.

---

### Post by tlu on 2010-05-29
Thanks for your detailed response!

> **bodhi.zazen said:**
> 

1. Stop firefox.

2. Reload apparmor

```
sudo service apparmor stop
sudo service apparmor start
```

Done.

> So you have to look up in your logs to the last denial that does not contain a "null". Fix that denial, and the nulls will go away.
...

If firefox works, close firefox, and debug any denials you received in the "tail -F /var/log/messages" terminal.

In complain mode I didn't get **any** log entry without the "null".


> Then put the firefox profile into enforcing mode and try to start firefox.

Post any denial you do not understand, but do not post any denial with a null profile in it.

After switching to enforce mode I got the following log (now without the "null"):

```
May 29 12:25:16 HANNIBAL kernel: [ 1587.419979] __ratelimit: 171 callbacks suppressed
May 29 12:25:16 HANNIBAL kernel: [ 1587.419981] type=1505 audit(1275128716.952:375):  operation="profile_replace" pid=4012 name="/usr/lib/firefox-3.6.5pre/firefox-*bin"
May 29 12:25:16 HANNIBAL kernel: [ 1587.420171] type=1505 audit(1275128716.956:376):  operation="profile_replace" pid=4012 name="/usr/lib/firefox-3.6.5pre/firefox-*bin//firefox_java"
May 29 12:25:16 HANNIBAL kernel: [ 1587.420302] type=1505 audit(1275128716.956:377):  operation="profile_replace" pid=4012 name="/usr/lib/firefox-3.6.5pre/firefox-*bin//firefox_openjdk"
May 29 12:25:48 HANNIBAL kernel: [ 1619.060824] type=1503 audit(1275128748.596:378):  operation="exec" pid=4037 parent=4036 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"
```

---

### Post by bodhi.zazen on 2010-05-29
THAT'S IT !!!!

> May 29 12:25:48 HANNIBAL kernel: [ 1619.060824] type=1503 audit(1275128748.596:378):  operation="exec" pid=4037 parent=4036 profile="/usr/lib/firefox-3.6.5pre/firefox-*bin" requested_mask="x::" denied_mask="x::" fsuid=1000 ouid=1000 name="/home/tlu/tmp/flashgot.ho87hudj.Default_20User/flashgot.fgt"

You need to allow execution of flashgot, add this:

```
owner @{HOME}/tul/tmp/flashgot.*/flashgot* rix,
```

restart apparmor ...

Try to start firefox again. See if there are additional denials (there may well be) and fix those as well.

It is possible the "flashgot.*" may need to be slightly adjusted, perhaps

@{HOME}/tul/tmp/flashgot.*.*/* rix,

Or you may need to add m or k ;)

Watch the logs ...

---

### Post by tlu on 2010-05-29
> **bodhi.zazen said:**
> THAT'S IT !!!!

Yes, indeed, it is!

> You need to allow execution of flashgot, add this:

```
owner @{HOME}/tul/tmp/flashgot.*/flashgot* rix,
```

I added that (without the /tul - obviously a typo of yours ;)  ) and that fixes the problem. No more denials.

Thanks a lot, bodhi.zazen !

---

### Post by bodhi.zazen on 2010-05-29
Alrighty then, hope you learned a little about apparmor :twisted:

---

### Post by q.dinar on 2010-06-01
hello
there is [AppArmor Support Thread](http://ubuntuforums.org/showthread.php?t=1049698)
you should write such support discussion there, i think.

---

### Post by cprofitt on 2010-06-01
Very nice thread -- is there a good guide you guys can point to in regards to setting up profiles.

---

### Post by bodhi.zazen on 2010-06-01
> **cprofitt said:**
> Very nice thread -- is there a good guide you guys can point to in regards to setting up profiles.

[http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html](http://www.linuxtopia.org/online_books/opensuse_guides/apparmor_guide/index.html)

It has much SUSE specific content, which can be ignored with impunity.

It is incomplete in some areas, especially how to debug profiles.

But it is the best single guide I know, from there, as with all things, it come with use.

If you use apparmor it takes about 2-3 hours of time for it to all click (hint toggle between complain and enforce mode, "tail -F /var/log/messages").

---

### Post by BkkBonanza on 2010-09-05
@Bodhi,

I tried out a couple profiles from your site's repo. Wireshark and Skype. I think Wireshark worked well except a minor change for usb devices ("/dev/usbmon? r," if you even use it for watching usb traffic).

But Skype has changed a fair bit since that one was created. This nasty program  wants to get to all sorts of system info and you can't enforce against it without the program not starting. I ended up enabling the things it wanted.

The one thing I wanted to ask about is why it wants "m" access to the /etc/passwd file. I know the passwords aren't stored there now but I'm just curious what use it has for looking at the "accounts list" and related info.

Along with denying access to the /var/lib/dbus/machine-id file, I'd much prefer it not look at those files. But that doesn't appear to be an usable option.

Anyway, I updated my own copy of the skype profile to work with 10.4 and Skype 2.1 and if anyone wants it I could post it here.

---

### Post by bodhi.zazen on 2010-09-05
It is amazing what some of these applications access !!!

Aye, those profiles are "templates" to get started, glad you found them helpful.

---

### Post by rileinc on 2010-09-19
Just sharing what I added to get Gmail voice & video chat working on Firefox (as of 3.6.x):

# Gmail voice & video
/opt/google/talkplugin/** rm,
/opt/google/talkplugin/GoogleTalkPlugin Uxr,
/dev/nvidiactl rw,
/dev/nvidia0 rw,
/dev/zero m,
/proc/interrupts r,

Maybe slightly different if you have an ATI/AMD video card.

I'm not quite sure why the plugin needs to access "/dev/zero" and "/proc/interrupts". Can someone enlighten me?

---

### Post by CandidMan on 2011-03-10
Here's an archive of all of my profiles so far, I'm sure there are a lot of redundant lines in there. Mainly due to the fact that I've mixed and matched profiles and used apparmor-utils

Feel free to pick them apart :D

---

### Post by Shiangtao on 2011-03-14
Thank you very much @CandidMan

---

### Post by DanneStrat on 2011-03-19
Hi.

I recently finished my transmission

profile for ubuntu 10.10 so I thought 

I would leave it here for all of 

you who want to confine transmission.

Tested for Transmission 2.04 (11151)

This profile gives you read and write access

to the ~Desktop and ~Downloads directory. 

You should also be able to copy

magnet links from your torrents to clipboard.

Just put it in enforce mode and try it out.

Enjoy!

> # DanneStrat's transmission profile for
# Ubuntu 10.10

#include <tunables/global>

/usr/bin/transmission {
  #include <abstractions/base>

  
  audit deny /home/.ssh/ mrwkl,
  audit deny /home/.ssh/** mrwkl,
  audit deny /home/.gnome2_private/ mrwkl,
  audit deny /home/.gnome2_private/** mrwkl,



  /etc/fonts/** r,
  /etc/gai.conf r,
  /etc/gnome/defaults.list r,
  /etc/group r,
  /etc/host.conf r,
  /etc/hosts r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /proc/*/fd/ r,
  /proc/*/mounts r,
  /tmp/orbit-*/linc* rw,
  /usr/bin/nautilus rix,
  /usr/lib/pango/1.6.0/modules/pango-basic-fc.so m,
  /usr/share/ r,
  /usr/share/** r,
  /var/cache/fontconfig/* r,
  /var/lib/defoma/fontconfig.d/fonts.conf r,
  /var/run/gdm/auth-for-*/database r,
  /var/run/resolvconf/resolv.conf r,

  /home/ r,
  /home/** r,
  /home/*/.cache/transmission/favicons/** rw,
  /home/*/.config/gtk-2.0/gtkfilechooser.ini rw,
  /home/*/.config/gtk-2.0/gtkfilechooser.ini* rw,
  /home/*/.config/transmission/blocklist.tmp rw,
  /home/*/.config/transmission/blocklists/* rw,
  /home/*/.config/transmission/dht.dat* rw,
  /home/*/.config/transmission/lock rwk,
  /home/*/.config/transmission/resume/** rw,
  /home/*/.config/transmission/settings.json rw,
  /home/*/.config/transmission/settings.json* rw,
  /home/*/.config/transmission/stats.json w,
  /home/*/.config/transmission/stats.json* rw,
  /home/*/.config/transmission/torrents/** rw,
  /home/*/.local/share/Trash/files/** w,
  /home/*/.local/share/Trash/info/** rw,
  /home/*/.recently-used* rw,
  /home/*/Downloads/** rw,
  /home/*/Desktop/** rw,

}


---

### Post by DanneStrat on 2011-03-31
Here is my profile for qbittorrent (tested with v. 2.7.1 on ubuntu 10.10)

> # DanneStrat's qbittorrent profile for
# ubuntu 10.10


#include <tunables/global>

/usr/bin/qbittorrent {
  #include <abstractions/base>



  /bin/dash r,
  /etc/fonts/** r,
  /etc/gai.conf r,
  /etc/gnome-vfs-2.0/modules/ r,
  /etc/gnome-vfs-2.0/modules/** r,
  /etc/gnome/defaults.list r,
  /etc/group r,
  /etc/host.conf r,
  /etc/hosts r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /etc/python2.6/** r,
  /etc/xdg/Trolltech.conf rk,
  /proc/*/fd/ r,
  /proc/*/mounts r,
  /tmp/orbit-*/linc* rw,
  /tmp/qtsingleapp* rwk,
  /usr/bin/gnome-open rix,
  /usr/bin/nautilus rix,
  /usr/bin/python2.6 rix,
  /usr/bin/xdg-open rix,
  /usr/lib/pango/1.6.0/modules/pango-basic-fc.so m,
  /usr/lib/python2.6/lib-dynload/_json.so m,
  /usr/local/lib/python2.6/dist-packages/ r,
  /usr/local/lib/python2.6/dist-packages/** r,
  /usr/share/applications/defaults.list r,
  /usr/share/applications/mimeinfo.cache r,
  /usr/share/applications/nautilus.desktop r,
  /usr/share/applications/nautilus-folder-handler.desktop r,
  /usr/share/fonts/** r,
  /usr/share/GeoIP/** r,
  /usr/share/gnome/applications/mimeinfo.cache r,
  /usr/share/gvfs/remote-volume-monitors/ r,
  /usr/share/gvfs/remote-volume-monitors/** r,
  /usr/share/icons/ r,
  /usr/share/icons/** rk,
  /usr/share/mime/mime.cache r,
  /usr/share/pixmaps/ r,
  /usr/share/pixmaps/** r,
  /usr/share/pyshared/** r,
  /usr/share/qt4/** r,
  /usr/share/themes/** r,
  /usr/share/X11/** r,
  /var/cache/fontconfig/** r,
  /var/lib/defoma/fontconfig.d/fonts.conf r,
  /var/run/gdm/auth-for-** r,
  /var/run/resolvconf/resolv.conf r,

  /home/ r,
  /home/** r,
  /home/*/.cache/qBittorrent/** rw,
  /home/*/.config/gtk-2.0/gtkfilechooser.ini rw,
  /home/*/.config/gtk-2.0/gtkfilechooser.ini* rw,
  /home/*/.config/qBittorrent/** rwk,
  /home/*/.config/Trolltech.conf rk,
  /home/*/.config/user-dirs.dirs r,
  /home/*/.gtk-bookmarks r,
  /home/*/.local/share/data/qBittorrent/** rw,
  /home/*/.recently-used.xbel r,
  /home/*/.thumbnails/** r,
  /home/*/Desktop/** rw,
  /home/*/Downloads/** rw,
  

}

---

### Post by oldmankit on 2011-05-02
> **BkkBonanza said:**
> @Bodhi,

I tried out a couple profiles from your site's repo. Wireshark and Skype. I think Wireshark worked well except a minor change for usb devices ("/dev/usbmon? r," if you even use it for watching usb traffic).

But Skype has changed a fair bit since that one was created. This nasty program  wants to get to all sorts of system info and you can't enforce against it without the program not starting. I ended up enabling the things it wanted.

The one thing I wanted to ask about is why it wants "m" access to the /etc/passwd file. I know the passwords aren't stored there now but I'm just curious what use it has for looking at the "accounts list" and related info.

Along with denying access to the /var/lib/dbus/machine-id file, I'd much prefer it not look at those files. But that doesn't appear to be an usable option.

Anyway, I updated my own copy of the skype profile to work with 10.4 and Skype 2.1 and if anyone wants it I could post it here.

That sounds interesting.  It's a shame there isn't an open-source skype.  But I'm stuck with it...I need it to make lots of international calls to landlines etc...

I'd like to see your skype profile if you don't mind posting it.  I've just installed Natty.  Does a lot need to be changed in apparmor profiles when upgrading Ubuntu?

---

### Post by DanneStrat on 2011-05-25
I recently made a midori profile for Lucid.(tested with midori 0.3.6)

Here it is:

> # DanneStrat's midori profile for
# Ubuntu 10.04

#include <tunables/global>

/usr/bin/midori {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/ubuntu-konsole>

  capability sys_ptrace,

  
  /bin/dash rix,
  /bin/grep rix,
  /bin/ps rix,
  /dev/shm/ r,
  /dev/shm/pulse-shm* rw,
  /etc/java-6-openjdk/** r,
  /etc/pulse/client.conf r,
  /etc/ssl/certs/ca-certificates.crt r,
  /etc/xdg/midori/extensions/libadblock.so/config r,
  /etc/xdg/midori/search r,
  /proc/ r,
  /proc/*/cmdline r,
  /proc/*/fd/ r,
  /proc/*/stat r,
  /proc/*/status r,
  /proc/sys/kernel/pid_max r,
  /proc/tty/drivers r,
  /proc/uptime r,
  /proc/version r,
  /sys/devices/system/cpu/ r,
  /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so m,
  /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so m,
  /usr/lib/jvm/java-6-openjdk/jre/bin/java rix,
  /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so m,
  /usr/lib/pango/1.6.0/modules/pango-*.so m,
  /usr/share/alsa/** r,
  /usr/share/applications/ r,
  /usr/share/applications/** r,
  /usr/share/enchant/* r,
  /usr/share/gvfs/remote-volume-monitors/ r,
  /usr/share/gvfs/remote-volume-monitors/** r,
  /usr/share/hunspell/** r,
  /usr/share/javascript/** r,
  /usr/share/libthai/** r,
  /usr/share/midori/** r,
  /usr/share/nvidia-current/** r,
  /usr/share/themes/** r,
  /usr/share/webkit-1.0/** r,
  /var/lib/dbus/machine-id r,

  /home/ r,
  /home/** r,
  /home/*/.cache/midori/** rw,
  /home/*/.config/enchant/*.dic rwk,
  /home/*/.config/enchant/*.exc rwk,
  /home/*/.config/gtk-2.0/gtkfilechooser.ini rw,
  /home/*/.config/gtk-2.0/gtkfilechooser.ini** rw,
  /home/*/.config/midori/** rwk,
  /home/*/.local/share/webkit/icondatabase/** rwk,
  /home/*/.macromedia/Flash_Player/#SharedObjects/*/** rw,
  /home/*/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/** rw,
  /home/*/.pulse-cookie rwk,
  /home/*/Desktop/** rw,
  /home/*/Downloads/** rw,

  
}

With this profile loaded you can only download files to your "Desktop" and 

"downloads" directory. Also you will not be able to open files with

external applications directly.

---

### Post by BigCityCat on 2011-11-27
Having problems setting up apparmor profile for firefox. I used sudo aa-genprof firefox. I start the process. Open firefox do all the things I want. Then close firefox. Press S for Scan in the terminal. Allow what I want. Then Save and Finnish. Reload profiles and enforce firefox. Firefox won't open unless I stop apparmor or sudo genprof again. Not sure what I am doing wrong.

---

### Post by DanneStrat on 2011-11-27
> **BigCityCat said:**
> Having problems setting up apparmor profile for firefox. I used sudo aa-genprof firefox. I start the process. Open firefox do all the things I want. Then close firefox. Press S for Scan in the terminal. Allow what I want. Then Save and Finnish. Reload profiles and enforce firefox. Firefox won't open unless I stop apparmor or sudo genprof again. Not sure what I am doing wrong.

I can try to help you with this, but could you make a separate thread and post the link here? This way we keep this profile-share thread clean. ;)
I have a suscription on this thread btw, so I will notice when new stuff gets posted.

---

### Post by bodhi.zazen on 2011-11-28
> **BigCityCat said:**
> Having problems setting up apparmor profile for firefox. I used sudo aa-genprof firefox. I start the process. Open firefox do all the things I want. Then close firefox. Press S for Scan in the terminal. Allow what I want. Then Save and Finnish. Reload profiles and enforce firefox. Firefox won't open unless I stop apparmor or sudo genprof again. Not sure what I am doing wrong.

1. Firefox is a large and complex application, and thus it is not a good one to start with.

2. There is already an apparmor profile for firefox, why not use or modify that one ?

3. To debug firefox you would need to post the errors you are getting in your logs.

---

### Post by jhansonxi on 2011-12-03
> **BigCityCat said:**
> Having problems setting up apparmor profile for firefox. I used sudo aa-genprof firefox. I start the process. Open firefox do all the things I want. Then close firefox. Press S for Scan in the terminal. Allow what I want. Then Save and Finnish. Reload profiles and enforce firefox. Firefox won't open unless I stop apparmor or sudo genprof again. Not sure what I am doing wrong.I tried that and had the same result.  It probably failed because /usr/bin/firefox is not the main binary, only a shell script.  Look in /etc/apparmor.d/disable for a link to the old firefox profile and delete it (the link).  Then look for the new profile in /etc/apparmor.d (check the date) and move it out or delete it.

---

### Post by zmago on 2012-02-01
Here is my profile for Skype in ubuntu 11.10
You can also check it on my blog: [https://eternalwalkabout.wordpress.com/2012/02/01/ubuntu-11-10-skype-apparmor-profile/](https://eternalwalkabout.wordpress.com/2012/02/01/ubuntu-11-10-skype-apparmor-profile/)

Cheers! :p
------
#include <tunables/global>

/usr/bin/skype {

	#include <abstractions/base>
	#include <abstractions/user-tmp>
	#include <abstractions/audio>
	#include <abstractions/nameservice>
	#include <abstractions/ssl_certs>
	#include <abstractions/fonts>
	#include <abstractions/X>
	#include <abstractions/freedesktop.org>
	#include <abstractions/kde>


	/usr/bin/skype mr,
	/opt/skype/skype pix,
	/opt/skype/** kmr,
	/usr/share/fonts/X11/** m,

	@{PROC}/*/net/arp r,
	@{PROC}/sys/kernel/ostype r,
	@{PROC}/sys/kernel/osrelease r,

	/dev/ r,
	/dev/tty rw,
        /dev/snd/* mrw,
        /dev/shm/ r,
        /dev/shm/pulse-shm-* mrw,
	/etc/pulse/client.conf r,
	/dev/pts/* rw,
	/dev/video* mrw,

	@{HOME}/.Skype/ rw,
	@{HOME}/.Skype/** krw,
	/usr/share/skype/** kmr,
	/usr/share/skype/sounds/*.wav kr,

	deny @{HOME}/.mozilla/ r,
	deny @{PROC}/[0-9]*/fd/ r,
	deny @{PROC}/[0-9]*/task/ r,
	deny @{PROC}/[0-9]*/task/** r,

}

---

