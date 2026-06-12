---
title: "[SOLVED] Trying to build an apparmor profile, and not succeeding"
date: 2008-06-19
forum: Security
---

### Post by PmDematagoda on 2008-06-19
I'm trying to build an Apparmor profile, and I am a newbie at this(you are warned:)), while apparmor_parser accepts the profile it doesn't seem to implement it properly since I'm getting all kinds of rejects and denials in audit for stuff I know I've allowed, here is the profile(it's incomplete):-
```
#include <tunables/global>
/usr/lib/firefox-3.0/firefox.sh flags=(complain) {
  #include <abstractions/base>
  #include <abstractions/gnome>
  #allow access to all networking network

  /bin/dash ix,
  /usr/lib/firefox-3.0/firefox.sh mr,
  /usr/lib/gnash/* rux,
  /usr/lib/firefox-3.0/** rw,
  /home/un/Downloads/** rw,
  /home/un/.mozilla/** rwk,
  /usr/share/icons/** r,
  /tmp/** rw,
  /usr/lib/xulrunner-1.9/** rw,
}

```

Thanks in advance:).

---

### Post by PmDematagoda on 2008-06-19
Ok, I managed to learn something and now the list of denials are decreasing and I think I could handle the stress of fine-tuning the profile:).

One thing that helped me was the really strict cups profile:).

Anyone wanting my new(still incomplete) profile:-
```
#include <tunables/global>
/usr/lib/firefox-3.0/firefox.sh flags=(complain) {
  #include <abstractions/base> 
  #include <abstractions/gnome>
  #include <abstractions/fonts>
  network inet,
  
  /bin/dash ix,
  /usr/lib/firefox-3.0/firefox.sh mr,
  /usr/lib/gnash/* rix,
  /usr/lib/firefox-3.0/** rwix,
  /home/un/Downloads/** rwix,
  /home/un/.mozilla/firefox/97peui19.default/*.sqlite* rwk,
  /home/un/.mozilla/firefox/97peui19.default/** rw,
  /home/un/.mozilla/firefox/97peui19.default/ rw,
  /usr/share/icons/** rix,
  /tmp/** rw,
  /usr/share/mime/** r,
  /usr/lib/xulrunner-1.9/ rix,
  /etc/hosts r,
  /etc/resolv.conf r,
  /usr/share/ubufox/** r,
}
```

---

### Post by PmDematagoda on 2008-06-19
Well, I managed to conjure a profile that allowed me to start and run Firefox while being enforced:-
```
#include <tunables/global>
/usr/lib/firefox-3.0/firefox.sh {
  #include <abstractions/base> 
  #include <abstractions/gnome>
  #include <abstractions/fonts>
  network inet,
  
  /bin/dash rix,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /usr/lib/libgconf2-4/gconfd-2 Ux,
  /etc/gre.d/ r,
  /etc/gre.d/* r,
  /etc/firefox-3.0/** rw,
  /etc/firefox-3.0/* rw,
  /home/un/.mozilla/extensions/** rw,
  /usr/lib/firefox-3.0/firefox.sh mr,
  /usr/lib/gnash/* rix,
  /usr/lib/firefox-3.0/** rwix,
  /home/un/Downloads/ rwix,
  /home/un/Downloads/** rwix,
  /home/un/.mozilla/firefox/97peui19.default/*.sqlite* rwk,
  /home/un/.mozilla/firefox/97peui19.default/** rw,
  /home/un/.mozilla/firefox/97peui19.default/ rw,
  /usr/share/icons/** r,
  /usr/share/applications/** r,
  /home/un/.config/gtk-2.0/gtkfilechooser.ini* rw,
  /tmp/** rw,
  /home/un/.mozilla/firefox/* rw,
  /usr/share/mime/** r,
  /usr/lib/xulrunner-1.9/ rix,
  /etc/hosts r,
  /etc/resolv.conf r,
  /home/un/.mozilla/firefox/97peui19.default/.parentlock k,
  /usr/share/ubufox/** r,
}
```

One thing I deliberately put in there was that Firefox is unable to read my entire home, just the download folder and the .mozilla one.

Anyone got any suggestions as to where I can improve this profile?

---

### Post by PmDematagoda on 2008-06-20
I cleaned the profile up and extended the functionality a bit, but unfortunately I've hit a bit of a wall, here is the profile:-
```
#include <tunables/global>
/usr/lib/firefox-3.0/firefox.sh {
  #include <abstractions/base> 
  #include <abstractions/gnome>
  #include <abstractions/fonts>
  network inet,
  network inet6,
  
  /bin/dash rix,
  /etc/gai.conf r,
  /etc/nsswitch.conf r,
  /etc/passwd r,
  /usr/lib/libgconf2-4/gconfd-2 Ux,
  /etc/gre.d/* r,
  /etc/gre.d/ r,
  /etc/firefox-3.0/** rw,
  /etc/firefox-3.0/* rw,
  /usr/lib/firefox-3.0/firefox.sh mr,
  /usr/lib/firefox-3.0/** rwix,
  /usr/share/ubufox/** r,
  /usr/share/applications/** r,
  /usr/share/icons/** r,
  /tmp/** rw,
  /tmp/ rw,
  /usr/share/myspell/dicts/ r,
  /usr/share/mime/** r,
  /usr/lib/xulrunner-1.9/ rix,
  /etc/hosts r,
  /etc/resolv.conf r,

#To use Gnash, these permissions have to be given.
  /usr/lib/gnash/ ix,
  @{HOME}/.gstreamer-0.10/registry.* rw,
  /usr/share/gnash/* r,
  /usr/bin/gtk-gnash mixr,

#The permissions required for Flash 10.
  @{HOME}/.macromedia/** rw,
  @{HOME}/.adobe/** r,
  /usr/lib/locale/en_US.utf8/* r,
  /dev/snd/** rw,
#Note:- The rule allows Fx to read other processes, this has to be done since Flash absolutely requires this otherwise the browser would crash.  
[COLOR="Red"]**  @{PROC}/** r,**[/COLOR]

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
}

#The below profile is required when viewing flash files.
/usr/bin/gtk-gnash {
#include<abstractions/gnome>
}
```

The problem is the red line, I know it isn't a serious thing, but I was wondering if it is possible to set it up in such a way that the path would be the current process of Firefox since that is what the path is.

---

### Post by chrisccoulson on 2008-06-23
Very interesting, and thank you for sharing this. I've been using Apparmor to sandbox Firefox for quite a while now, so I'll share my profile with you too, in the hope that you might find it semi-useful. If you have any questions, feel free to ask.
```
# Last Modified: Fri Jun 20 22:03:44 2008
#include <tunables/global>
/usr/lib/firefox-3.0/firefox.sh {
  #include <abstractions/apport>
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/cups-client>
  #include <abstractions/dbus>
  #include <abstractions/fonts-custom>
  #include <abstractions/freedesktop.org-custom>
  #include <abstractions/gnome-custom>
  #include <abstractions/nameservice>
  #include <abstractions/python>
  #include <abstractions/user-download-custom>
  #include <abstractions/user-read>
  #include <abstractions/user-tmp>

  capability sys_ptrace,

  /bin/dash ix,
  /bin/grep ixr,
  /bin/ps ixr,
  /bin/sed ixr,
  /bin/uname Ux,
  /bin/which Ux,
  /dev/shm/ r,
  /dev/shm/pulse-shm-* rw,
  /etc/X11/cursors/* r,
  /etc/firefox-3.0/** r,
  /etc/fstab r,
  /etc/gnome/defaults.list r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,
  /etc/java-6-openjdk/** r,
  /etc/mailcap r,
  /etc/mime.types r,
  /etc/mplayer/input.conf r,
  /etc/mplayer/mplayer.conf r,
  /etc/mplayerplug-in.conf r,
  /etc/pulse/* r,
  /etc/sound/events/gtk-events-2.soundlist r,
  @{PROC}/ r,
  @{PROC}/*/cmdline r,
  @{PROC}/*/environ r,
  @{PROC}/*/fd/ r,
  @{PROC}/*/maps r,
  @{PROC}/*/mounts r,
  @{PROC}/*/stat r,
  @{PROC}/*/status r,
  @{PROC}/meminfo r,
  @{PROC}/net/* r,
  @{PROC}/sys/kernel/pid_max r,
  @{PROC}/tty/drivers r,
  @{PROC}/uptime r,
  @{PROC}/version r,
  /sys/devices/system/cpu/ r,
  /usr/bin/deluge Px,
  /usr/bin/env ixr,
  /usr/bin/eog Ux,
  /usr/bin/evince Ux,
  /usr/bin/evolution Px,
  /usr/bin/file-roller Ux,
  /usr/bin/gconftool-2 ixr,
  /usr/bin/gpg ixr,
  /usr/bin/lsb_release ixr,
  /usr/bin/mplayer ixr,
  /usr/bin/python2.5 ix,
  /usr/bin/screem Ux,
  /usr/bin/seahorse-tool ixr,
  /usr/bin/setarch ixr,
  /usr/lib/firefox-3.0/firefox ixr,
  /usr/lib/firefox-3.0/firefox.sh mr,
  /usr/lib/jvm/java-6-openjdk/jre/bin/pluginappletviewer ixr,
  /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/gcjwebplugin.so mr,
  /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so mr,
  /usr/lib/mozilla/plugins/mplayerplug-in-qt.so mr,
  /usr/lib/mozilla/plugins/mplayerplug-in-rm.so mr,
  /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so mr,
  /usr/lib/mozilla/plugins/mplayerplug-in.so mr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer ixr,
  /usr/lib/nspluginwrapper/i386/linux/npviewer.bin ixr,
  /usr/lib32/Adobe/Reader8/bin/acroread Ux,
  /usr/lib32/gtk-2.0/2.10.0/engines/* mr,
  /usr/lib32/pango/1.6.0/modules/* mr,
  /usr/share/locale-langpack/** r,
  /usr/share/ubufox/* r,
  /usr/share/ubufox/**/ r,
  /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so mr,
  @{HOME}/.ICEauthority r,
  @{HOME}/.Xauthority r,
  @{HOME}/.adobe/ w,
  @{HOME}/.adobe/Flash_Player/ w,
  @{HOME}/.adobe/Flash_Player/** rw,
  @{HOME}/.config/user-dirs.dirs r,
  @{HOME}/.cups/* r,
  @{HOME}/.gcjwebplugin/ w,
  @{HOME}/.gcjwebplugin/** rw,
  @{HOME}/.gnupg r,
  @{HOME}/.gnupg/*.gpg r,
  @{HOME}/.gstreamer-0.10/registry.*.xml r,
  @{HOME}/.gtkrc-2.0-gnome-color-chooser r,
  @{HOME}/.local/share/applications/ r,
  @{HOME}/.local/share/applications/* r,
  @{HOME}/.macromedia/ w,
  @{HOME}/.macromedia/Flash_Player/ w,
  @{HOME}/.macromedia/Flash_Player/** rw,
  @{HOME}/.mailcap r,
  @{HOME}/.mcop/random-seed rw,
  @{HOME}/.mcoprc r,
  @{HOME}/.mime.types r,
  @{HOME}/.mozilla/ w,
  @{HOME}/.mozilla/default/ rw,
  @{HOME}/.mozilla/default/** rw,
  @{HOME}/.mozilla/extensions/ rw,
  @{HOME}/.mozilla/extensions/** rw,
  @{HOME}/.mozilla/firefox/ rw,
  @{HOME}/.mozilla/firefox/** krw,
  @{HOME}/.mozilla/plugins/ rw,
  @{HOME}/.mozilla/plugins/** rw,
  @{HOME}/.mplayer/ w,
  @{HOME}/.mplayer/config rw,
  @{HOME}/.pulse-cookie krw,
  @{HOME}/.thumbnails/** r,
  @{HOME}/dwhelper/ w,
  @{HOME}/dwhelper/* w,
}
```

For completeness, I have quite a few custom abstractions too.

abstractions/apport:
```
# vim:syntax=apparmor

  /var/crash/* rw,
```

abstractions/fonts-custom:
```
# vim:syntax=apparmor

  #include <abstractions/fonts>

  @{HOME}/.fonts.conf			r,
```

abstractions/freedesktop.org-custom:
```
# vim:syntax=apparmor

  #include <abstractions/freedesktop.org>


  @{HOME}/.icons/                 r,
  @{HOME}/.icons/**		  r,
  @{HOME}/.recently-used.xbel*    rw,
  @{HOME}/.local/share/icons/ 	  r,
  @{HOME}/.local/share/icons/**   r,
  /opt/share/icons/ 		  r,
  /opt/share/icons/**		  r,
  /opt/share/pixmaps/ 		  r,
  /opt/share/pixmaps/**		  r,
```

abstractions/gnome-custom:
```
# vim:syntax=apparmor

#include <abstractions/fonts-custom>
#include <abstractions/freedesktop.org-custom>
#include <abstractions/gnome>

  @{HOME}/.themes/		  r,
  @{HOME}/.themes/**		  r,
  @{HOME}/.config/gtk-2.0/gtkfilechooser.ini rw,
  @{HOME}/.config/gtk-2.0/gtkfilechooser.ini* rw,
  @{HOME}/.fonts/fonts.cache-* rwl, 
  @{HOME}/.gtkrc-2.0-gnome-color-chooser r,
```

abstractions/user-download-custom:
```
# vim:syntax=apparmor

  @{HOME}/Desktop/		rw,
  @{HOME}/Desktop/**   		krwl,
  @{HOME}/Download/		rw,
  @{HOME}/Download/**		krwl,
```

abstractions/user-read:
```
# vim:syntax=apparmor

  @{HOME}/[a-zA-Z0-9]*/ r,
  @{HOME}/[a-zA-Z0-9]*/** r,
  / r,
  /bin/ r,
  /bin/** r,
  @{HOMEDIRS}/ r,
  @{HOME}/ r,
  /lib/ r,
  /lib/** r,
  /lib32/ r,
  /lib32/** r,
  /media/ r,
  /media/** r,
  /misc/ r,
  /misc/** r,
  /mnt/ r,
  /mnt/** r,
  /opt/ r,
  /opt/** r,
  /sbin/ r,
  /sbin/** r,
  /usr/ r,
  /usr/** r,

```

This profile has evolved quite a lot through Gutsy using FF2 and now on Hardy using FF3. Basically, I let FF read most directories in their entirety except for /boot, /dev, /etc, /initrd, /proc, /srv, /sys, /var and any hidden directories in my home folder. This ensures FF has no access to most personal information whilst ensuring that the open/save dialogs still behave in a relatively sane manner, and FF is still largely useful and functional. I only allow FF to write to my desktop, a dedicated download folder or any temporary locations (/tmp, @{HOME}/tmp, /var/tmp).

If you've got other apps you want to profile, feel free to ask - as I may already have done it.

---

### Post by PmDematagoda on 2008-06-28
Thanks for that information chrisccoulson, sorry for the late reply:). But doesn't your profile look a bit over the top(no offense meant), but the fact is that you are providing(seemingly) unnecessary permissions for Firefox by allowing it to read  quite a lot of files it really does not need. Ah, and by the way, all those proc permissions aren't required from my experience since Flash only requires /proc/pid/maps:). Also I created two more profiles for Transmission, Pidgin and Skype(with a Novell profile for a pretty woeful base).

Firefox:-
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

#The below profile is required when viewing flash files through Gnash.
/usr/bin/gtk-gnash {
#include<abstractions/gnome>
}
```

Transmission:-
```
# Last Modified: Fri Jun 20 09:55:31 2008
#include <tunables/global>
/usr/bin/transmission {
  #include <abstractions/base>
  #include <abstractions/gnome>
network inet,
  /usr/bin/transmission mr,
  "@{HOME}/Downloads/**" rw,
  @{HOME}/.transmission/** rw,
  @{HOME}/.transmission/gtk/lock k,
  @{HOME}/.transmission/ rw,
  /etc/hosts r,
  /etc/resolv.conf r,
}
```

Pidgin:-
```
# Last Modified: Fri Jun 20 09:42:54 2008
#include <tunables/global>
/usr/bin/pidgin {
  #include <abstractions/base>
  #include <abstractions/gnome>
network inet,
  /usr/lib/purple-2/* mr,
  /usr/bin/pidgin mr,
  /etc/hosts r,
  /etc/resolv.conf r,
  @{HOME}/.purple/* wr,
  @{HOME}/.purple/** wr,
  /usr/bin/gconftool-2 ix,
  /usr/bin/gnome-open ix, 
 /usr/lib/pidgin/* mr,
  @{HOME}/pidgindownloads/** rw,
 @{HOME}/pidgindownloads/ rw,
 @{HOME}/ r,
 /usr/share/sounds/purple/* r,
 /home/pramod/.purple/ wr,
 /usr/lib/libgconf2-4/gconfd-2 Ux,
 #/dev/shm/** rw,
 /var/run/dbus/system_bus_socket rw,
}
```

Skype(which was based on a rather lax Novell profile):-
```
# Last Modified: Fri Jun 20 07:34:08 2008
# REPOSITORY: http://apparmor.test.opensuse.org/backend/api draglor 53
#include <tunables/global>
/usr/bin/skype {
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/fonts>
  #include <abstractions/nameservice>

  /usr/lib/kde4/lib/kde4/plugins/imageformats/* mr,
  /home/*/.Skype/ rw,
  /home/*/.Skype/** krw,
  @{HOME}/.Xauthority r,
  /home/*/.config/Trolltech.conf kr,
  /home/*/.fontconfig/* r,
  /tmp/.ICE-unix/* w,
  /tmp/.X11-unix/X0 w,
  /usr/bin/skype mr,
  /usr/lib/qt4/plugins/iconengines/ r,
  /usr/lib/qt4/plugins/imageformats/ r,
  /usr/lib/qt4/plugins/imageformats/*.so mr,
  /usr/lib/qt4/plugins/inputmethods/ r,
  /usr/share/X11/locale/** r,
  /usr/share/icons/** r,
  /usr/share/skype/sounds/*.wav kr,
  /var/cache/libx11/compose/* r,
  /dev/snd/** rm,
}
```

---

### Post by chrisccoulson on 2008-06-28
It's not as complex as it looks. I find that FF tries to access more than just /proc/pid/maps under /proc, hence the extra entries. That could be a plugin or extension that I use which does that though. Also, there are a lot of entries that allow me to download things like images, PDF's, archives and other documents and open them directly with an application of choice using Firefox's own dialog (eog, evince, file-roller, Openoffice) etc, without having the click 'Save As' and then open the file manually. My aim is to sandbox and protect my files as much as possible without Apparmor being too obstructive to work flow.

I also try to avoid having logs which are flooded with Apparmor stuff.

Also, there are entries to allow plugins such as Flash, Java and other media plugins to function correctly (this is the reason I allow access to certain hidden folders in my home folder). And I also allow Firefox to create new profile folders (~/.mozilla, ~/.adobe etc), so that it doesn't fail when a fresh user launches it for the first time (when the profile folders don't exist yet). You might find that if you create a new user, Firefox won't work from them because it doesn't have permissions to create the ~/.mozilla folder with your Apparmor profile.

The abstractions I listed are common between a lot of my profiles, and aren't unique to Firefox. I allow read access to most folders on the filesystem which aren't likely to contain personal or sensitive information so that the open/save dialog functions sanely (and I do this with any application that uses an open/save dialog). The only things I deny access to (and then explicitly open up access for files where necessary) are /boot, /dev, /etc, /proc, /sys and /var.

I have a profile for Pidgin (a bit shorter than the one for Firefox):
```
# Last Modified: Fri Jun 20 22:03:44 2008
#include <tunables/global>
/usr/bin/pidgin {
  #include <abstractions/apport>
  #include <abstractions/aspell>
  #include <abstractions/base>
  #include <abstractions/bash>
  #include <abstractions/consoles>
  #include <abstractions/dbus>
  #include <abstractions/fonts-custom>
  #include <abstractions/freedesktop.org-custom>
  #include <abstractions/gnome-custom>
  #include <abstractions/nameservice>
  #include <abstractions/user-download-custom>
  #include <abstractions/user-read>
  #include <abstractions/user-tmp>

  /bin/dash ix,
  /bin/which ixr,
  /dev/shm/ r,
  /dev/shm/pulse-shm-* rw,
  /etc/X11/cursors/* r,
  /etc/pulse/client.conf r,
  @{PROC}/*/fd/ r,
  @{PROC}/*/mounts r,
  /tmp/orbit-*/bonobo-activation-register.lock klrw,
  /usr/bin/gconftool-2 ixr,
  /usr/bin/gnome-default-applications-properties Ux,
  /usr/bin/gnome-network-preferences Ux,
  /usr/bin/gnome-open ixr,
  /usr/bin/launchpad-integration ixr,
  /usr/bin/pidgin mr,
  /usr/bin/sensible-browser ixr,
  /usr/bin/xdg-open ixr,
  /usr/lib/firefox-3.0*/firefox.sh Px,
  /usr/lib/firefox-3.0/firefox.sh Px,
  /usr/lib/pidgin/* mr,
  /usr/lib/purple-2/* mr,
  @{HOME}/.ICEauthority r,
  @{HOME}/.Xauthority r,
  @{HOME}/.aspell.en.prepl kr,
  @{HOME}/.aspell.en.pws kr,
  @{HOME}/.face r,
  @{HOME}/.gnome2/nautilus-sendto/pidgin_buddies_online w,
  @{HOME}/.gnome2/nautilus-sendto/spool/ r,
  @{HOME}/.gstreamer-0.10/registry.*.xml r,
  @{HOME}/.gstreamer-0.10/registry.*.xml.* w,
  @{HOME}/.pulse-cookie rw,
  @{HOME}/.purple/ w,
  @{HOME}/.purple/** rw,
}
```

---

