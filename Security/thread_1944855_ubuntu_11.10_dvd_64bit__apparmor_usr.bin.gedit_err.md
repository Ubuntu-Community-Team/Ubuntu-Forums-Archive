---
title: "ubuntu 11.10 dvd 64bit  apparmor usr.bin.gedit error"
date: 2012-03-22
forum: Security
---

### Post by oklokl on 2012-03-22
apparmor gedit error.. help..

sudo -i
gedit -> save -> error..

[COLOR=Red](gedit:1023: Gtk-WARNING **: Unable to retrieve the file info for `file:///media/ABC/test': '/media/ABC/test' &#54028;&#51068;&#51032; &#51221;&#48372;&#47484; &#51069;&#45716; &#51473; &#50724;&#47448;: &#44536;&#47088; &#54028;&#51068;&#51060;&#45208; &#46356;&#47113;&#53552;&#47532;&#44032; &#50630;&#49845;&#45768;&#45796;[/COLOR]
error... 

my usr.bin.gedit
```

## &#47588;&#50864; &#50612;&#47140;&#50912;&#45348;&#50836; &#12640;&#12640;.. &#51060;&#44144; &#54616;&#45716;&#45824; &#54616;&#47336; &#51333;&#51068; &#44152;&#47536; &#45712;&#45196; &#51077;&#45768;&#45796; &#12640;&#12640; &#53952;&#47140;&#49436; &#47751;&#48264; &#44256;&#52828;&#51648; &#47784;&#47476;&#44192;&#50612;&#50836;..

## &#46104;&#46020;&#47197; &#51221;&#47532; &#54664;&#45716;&#45824; &#51096; &#51221;&#47532; &#46104;&#50632;&#45716;&#51648; &#47784;&#47476;&#44192;&#45348;&#50836;.. nano&#47196; &#51089;&#50629; &#54644;&#49436; F5 &#54644;&#49436; &#48520;&#47084; &#44256;&#44592; &#54616;&#47732; &#54200;&#54616;&#45908;&#44400;&#50836; &#54028;&#51068;&#51008; vi&#47196; &#54644;&#49436; &#51648;&#50864;&#44256; &#47568;&#51060;&#51424;.. 
## find /usr/lib/*-linux-gnu/pango -name '*.so' > ~/&#47928;&#49436;/gedit.txt &#52286;&#44592;

# Last Modified: Sat Feb  4 04:59:45 2012
#include <tunables/global>

/usr/bin/gedit {
  #include <abstractions/base>
##block
## find /usr/lib/*-linux-gnu/pango -name '*.so' > ~/&#47928;&#49436;/gedit.txt &#52286;&#44592;
#  deny network appletalk, ## ! &#45712;&#45196;&#54364;&#47484; &#51228;&#44144; &#54616;&#49464;&#50836; &#44536;&#47111;&#51648; &#50506;&#51004;&#47732; &#50640;&#47084;..
  deny network dgram, ##&#51064;&#53552;&#45367; &#54596;&#49688;
  deny network inet dgram, ##&#51064;&#53552;&#45367; &#54596;&#49688;
  deny network inet stream,
  deny network inet6 stream,
  deny @{PROC}/[0-9]*/net/if_inet r,
  deny @{PROC}/[0-9]*/net/ipv_route r,
  deny @{PROC}/[0-9]*/net/if_inet6 r,
  deny @{PROC}/[0-9]*/net/ipv6_route r,
  deny network,
  deny network raw,
  deny network rose,
  deny network ax25,
  deny network ipx,
  deny network netrom,
  deny network atmpvc,
  deny network x25,
  deny network bridge,
  deny network netbeui,
  deny network security,
  deny network key,
  deny network ash,
  deny network econet,
  deny network atmsvc,
  deny network sna,
  deny network irda,
  deny network pppox,
  deny network wanpipe,
  deny network seqpacket,
  deny network rdm,
  deny network packet,
  deny network bluetooth,
  deny network icmp,
  deny network tcp,
  deny network udp,
  deny network inet,
  deny network inet6,
  deny network inet tcp,
  deny network inet udp,
  deny network inet6 tcp,
  deny network inet6 udp,

## &#54728;&#50857;
/usr/bin/gedit r,
/usr/bin/dbus-launch ixr,
/usr/lib/d-conf/dconf-service ixr,
/usr/lib/d-conf/dconf-* cx,

/bin/dbus-daemon ixr,
capability dac_override,
capability dac_read_search,
capability sys_resource,
/root/.dbus/session-bus/ rw,
/root/.dbus/session-bus/** rw,
/root/.cache/dconf/user cx,
/root/.cache/dconf/user rw,
/root/.config/gedit/accels rw,
/root/.config/enchant/ r,
/root/.config/enchant/** cxrwk,
/root/.config/dconf/user rw,
/root/.config/dconf/user.* rw,
/root/.local/share/recently-used.xbel rw,
/root/.local/share/recently-used.xbel.** rw,
/home/*/.Xauthority r,
/home/.ecryptfs/*/.*/** rw,
/home/*/** rwl,
owner /home/*/.config/enchant/** rk,
owner /home/*/.config/enchant/ r,
owner /home/*/.config/gedit/accels r,
owner /home/*/.config/dconf/user r,
owner /home/*/.cache/dconf/user r,
owner /home/*/.cache/dconf/user rw,
owner /home/*/.local/share/recently-used.xbel r,
owner /home/*/.config/user-dirs.dirs r,
owner /home/*/.gtk-bookmarks r,
owner /home/*/.local/share/gvfs-metadata/home r,
owner /home/*/.local/share/gvfs-metadata/home-*.log r,
owner /home/*/.local/share/recently-used.xbel rw,
owner /home/*/.local/share/recently-used.xbel.* rw,
owner /home/*/&#47928;&#49436;/** rw,
owner /home/*/&#49324;&#51652;/** rw,
owner /home/*/&#45796;&#50868;&#47196;&#46300;/** rw,
owner /home/*/&#48708;&#46356;&#50724;/** rw,
owner /home/*/&#48148;&#53461;&#54868;&#47732;/** rw,
owner /home/*/&#51020;&#50501;/** rw,
owner /home/*/.config/gedit/accels rw,
owner /home/*/.ICEauthority r,
/media/** rwl,
/run/motd r,
/run/udev/data/** r,
/sys/devices/** r,
/proc/** r,
/etc/ r,
/etc/** r,
/etc/adduser.conf r,
/etc/group r,
/etc/anacrontab r,
/etc/fstab r,
/etc/apg.conf r,
/etc/.pwd.lock r,
/etc/udev/udev.conf r,
/etc/dbus-*/session.d/ r,
/etc/dbus-*/session.conf r,
/etc/resolv.conf r,
/etc/host.conf r,
/etc/fonts/fonts.conf r,
/etc/fonts/conf.d/ r,
/etc/fonts/conf.d/** r,
/etc/fonts/conf.avail/*.* r,
/etc/fonts/conf.d/*.* r,
/etc/nsswitch.conf r,
/etc/passwd r,
/etc/at.deny r,
/etc/bash.bashrc r,
/etc/bash_completion r,
/etc/blkid.conf r,
/etc/brlapi.key r,
/etc/ca-certificates.conf r,
/etc/colord.conf r,
/etc/crontab r,
/etc/crypttab r,
/etc/debconf.conf r,
/etc/debian_version r,
/etc/deluser.conf r,
/etc/environment r,
/etc/fuse.conf r,
/etc/gai.conf r,
/etc/group* r,
/etc/hdparm.conf r,
/etc/hostname r,
/etc/hosts r,
/etc/hosts.allow r,
/etc/hosts.deny r,
/etc/inputrc r,
/etc/insserv r,
/etc/issue r,
/etc/insserv.conf r,
/etc/issue.net r,
/etc/kerneloops.conf r,
/etc/ld.so.conf r,
/etc/legal r,
/etc/lftp.conf r,
/etc/login.defs r,
/var/cache/fontconfig/*.* r,
/var/lib/dbus/machine-id r,
/var/lib/defoma/fontconfig.d/fonts.conf r,
/usr/local/share/fonts/ r,
/usr/lib/*-linux-gnu/pango/*/modules/** r,
/usr/lib/*-linux-gnu/pango/*/modules/pango-basic-fc.so m,
/usr/lib/*-linux-gnu/pango/*/modules/pango-hangul-fc.so m,
/usr/lib/*-linux-gnu/pango/*/modules/*.* r,
/usr/lib/gtk-*/*.*/immodules/im-xim.so m,
/usr/share/dbus-*/services/ r,
/usr/share/dbus-*/*/** r,
/usr/share/myspell/dicts/ r,
/usr/share/fonts/ r,
/usr/share/fonts/** r,
/usr/share/hunspell/** r,
/usr/share/hunspell/ r,
/usr/share/gvfs/remote-volume-monitors/** r,
/usr/share/gvfs/remote-volume-monitors/ r,
/usr/share/gedit/ui/gedit-preferences-dialog.ui r,
/usr/share/themes/Default/gtk-*/gtk-keys.css r,
/usr/share/themes/Ambiance/gtk-*/** r,
/usr/share/themes/Ambiance/gtk-*/** r,
/usr/share/themes/Ambiance/gtk-*/gtk.css r,
/usr/share/themes/Ambiance/gtk-*/gtk-widgets.css r,
/usr/share/themes/Ambiance/gtk-*/apps/gnome-panel.css r,
/usr/share/themes/Ambiance/gtk-*/apps/gnome-terminal.css r,
/usr/share/themes/Ambiance/gtk-*/apps/nautilus.css r,
/usr/share/themes/Ambiance/gtk-*/apps/unity.css r,
/usr/share/themes/Ambiance/gtk-*/settings.ini r,
/usr/share/themes/Ambiance/gtk-*/assets/slider.* r,
/usr/share/themes/Ambiance/gtk-*/assets/slider_* r,
/usr/share/themes/Ambiance/gtk-*/assets/slider_** r,
/usr/share/themes/Ambiance/gtk-*/assets/scrollbar* r,
/usr/share/themes/Ambiance/gtk-*/assets/scrollbar** r,
/usr/share/glib-*/schemas/gschemas.compiled r,
/usr/share/gedit/ui/gedit-ui.xml r,
/usr/share/pixmaps/ r,
/usr/share/applications/gedit.desktop r,
/usr/share/mime/** r,
/usr/share/mime/mime.cache r,
/usr/share/mime/globs2 r,
/usr/share/mime/magic r,
/usr/share/mime/aliases r,
/usr/share/mime/subclasses r,
/usr/share/mime/icons r,
/usr/share/mime/generic-icons r,
/usr/share/mime/text/plain.xml r,
/usr/share/mime/text/** r,
/usr/share/icons/ubuntu-mono-dark/index.theme r,
/usr/share/icons/ubuntu-mono-dark/* r,
/usr/share/icons/ubuntu-mono-dark/*/* r,
/usr/share/icons/Humanity-Dark/index.theme r,
/usr/share/icons/Humanity-Dark/icon-theme.cache r,
/usr/share/icons/Humanity-Dark/* r,
/usr/share/icons/Humanity-Dark/** r,
/usr/share/icons/Humanity-Dark/*/* r,
/usr/share/icons/gnome/index.theme r,
/usr/share/icons/hicolor/index.theme r,
/usr/share/icons/gnome/index.theme r,
/usr/share/icons/ r,
/usr/share/icons/** r,
/usr/share/icons/gnome/icon-theme.cache r,
/usr/share/icons/gnome/** r,
/usr/share/icons/gnome/*/* r,
/usr/share/icons/gnome/*.* r,
/usr/share/icons/hicolor/*.* r,
/usr/share/icons/hicolor/*/* r,
/usr/share/icons/Humanity/index.theme r,
/usr/share/icons/Humanity/icon-theme.cache r,
/usr/share/icons/Humanity/*/* r,
/usr/share/icons/Humanity/*/*/* r,
/usr/share/icons/Humanity/*/*/*.* r,
/usr/share/icons/Humanity/*.* r,
/usr/share/icons/Humanity/** r,
/usr/share/icons/Humanity/actions/16/go-home.svg r,
/usr/share/icons/Humanity/devices/16/drive-harddisk.svg r,
/usr/share/icons/Humanity/places/16/folder.svg r,
/usr/share/icons/Humanity/apps/16/lpi-help.svg r,
/usr/share/icons/Humanity/places/16/folder-documents.svg r,
/usr/share/icons/Humanity/places/16/folder-music.svg r,
/usr/share/icons/Humanity/apps/16/preferences-desktop-locale.svg r,
/usr/share/icons/ubuntu-mono-dark/places/16/user-home.svg r,
/usr/share/gedit/plugins/filebrowser/gedit-file-browser-widget-ui.xml r,
/usr/share/gtksourceview-*/language-specs/** r,
/usr/share/gtksourceview-*/language-specs/ r,
/usr/share/gtksourceview-*/language-specs/* r,
/usr/share/gtksourceview-*/language-specs/*.* r,
/usr/share/icons/DMZ-White/** r,
/usr/share/icons/DMZ-White/cursors/watch r,
/usr/share/icons/DMZ-White/cursor.theme r,
/usr/share/icons/DMZ-White/cursors/hand2 r,
/usr/share/icons/DMZ-White/index.theme r,
/usr/share/icons/DMZ-White/cursors/* r,
/usr/share/gtksourceview-*/styles/ r,
/usr/share/gtksourceview-*/styles/*.* r,
/usr/share/fonts/truetype/** r,
/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf r,
/usr/share/fonts/truetype/unfonts/UnDotum.ttf r,
/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-B.ttf r,
/usr/share/fonts/truetype/ttf-dejavu/*.* r,
/usr/share/fonts/truetype/ubuntu-font-family/UbuntuMono-R.ttf r,
/usr/share/fonts/truetype/ubuntu-font-family/*.* r,
/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-BI.ttf r,
/usr/share/fonts/truetype/unfonts/UnDotumBold.ttf r,
/usr/share/fonts/truetype/unfonts/*.* r,
/usr/share/gedit/ui/gedit-replace-dialog.ui r,
/usr/share/xml/iso-codes/** r,
/usr/share/enchant/enchant.ordering r,
}
```

---

### Post by 0011235813 on 2012-03-23
If you don't mind me asking; why are you trying to apparmor gedit? As far as I'm aware, this application cannot be exploited because it does not execute any code. The only applications that need con-straining are the browser(s),some basic system services which are automatically done when you run
```
sudo apt-get install apparmor-profiles 
```
```
sudo apt-get install apparmor-utils 
```
```
sudo aa-enforce /etc/apparmor.d/* 
```
as well as e-mail clients and social clients like Thunderbird, Skype etc.
Also, potentially LibreOffice, as I hear MS Office is vulnerable to certain exploits, and the same principles could be theoretically applied to LO as well.

---

### Post by oklokl on 2012-03-24
Txt files are infected.
 Is suspected.

 access unknown.
 Txt files are infected.
 Is suspected.

---

### Post by 0011235813 on 2012-03-24
> **oklokl said:**
> Txt files are infected.
 Is suspected.

 access unknown.
 Txt files are infected.
 Is suspected.
That doesn't matter; as I said, even if the text files are "infected" with something, it won't affect gedit as it doesn't execute any code! You can view the infected files all you like but it can't affect your system. 

For any system to be damaged/infected, code must first be executed.

---

### Post by oklokl on 2012-03-24
Thank you. Advice.

Open a specific port
 Malicious downloads.
Open an unknown rootkit infections makes planting.
 Scenarios.

---

### Post by 0011235813 on 2012-03-24
> **oklokl said:**
> Thank you. Advice.

Open a specific port
 Malicious downloads.
Open an unknown rootkit infections makes planting.
 Scenarios.
Your posts are illegible, consider posting in your native language so I can translate and understand you better. 

&#44480;&#54616;&#51032; &#44172;&#49884;&#47932; &#51069;&#44592; &#50612;&#47140;&#50868;&#51060;&#47728;, &#51228;&#44032; &#48264;&#50669;&#54616;&#44256; &#45908; &#51096; &#51060;&#54644;&#54624; &#49688; &#51080;&#46020;&#47197; &#50668;&#47084;&#48516;&#51032; &#47784;&#44397;&#50612;&#47196; &#50732;&#47532;&#45716; &#44163;&#51012; &#44256;&#47140;&#54616;&#49901;&#49884;&#50724;.

---

### Post by bodhi.zazen on 2012-03-25
First you need to post the error message from your logs.

Second, you will need to read about how apparmor works. Your profile is inefficient and full of duplicates and it seems you are trying to debug your profile one file at a time.

---

### Post by oklokl on 2012-03-25
Thank you advise

log no error..

The log is not output. 
Cause will not know.

---

