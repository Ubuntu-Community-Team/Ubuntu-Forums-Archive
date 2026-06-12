---
title: "Possible to get Ubuntu to work with lightdm-gtk-greeter?"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-04-10
I know Ubuntu works fine with unity-greeter but I've been working on DE conversions for those who require a non-pae kernel. So far I've only focused on Lubuntu -> Ubuntu and the kernel problem is easy to work-around :cool:

But lightdm is kind of eating my lunch. After adding ubuntu-desktop as long as I leave both it and lubuntu-desktop installed lightdm-gtk-greeter works great to boot either Lubuntu or Ubuntu sessions, but I'm clearly missing something because when I remove Lubuntu and it's components, even though I leave lightdm-gtk-greeter installed, lightdm refuses to load and just displays a low graphics warning.

But if I change "/etc/lightdm/lightdm.conf" to use unity-greeter all is well. Anyway I just wondered if anyone has tried converting Ubuntu to using lightdm-gtk-greeter?

If so they might be able to clue me in and save me a bunch of time sorting this out :D

It's certainly no big deal though, if lightdm-gtk-greeter just doesn't work well with pure Ubuntu then it's easy to convert to unity-greeter.

Thanks in advance.

---

### Post by zika on 2012-04-10
> **kansasnoob said:**
> I know Ubuntu works fine with unity-greeter but I've been working on DE conversions for those who require a non-pae kernel. So far I've only focused on Lubuntu -> Ubuntu and the kernel problem is easy to work-around :cool:

But lightdm is kind of eating my lunch. After adding ubuntu-desktop as long as I leave both it and lubuntu-desktop installed lightdm-gtk-greeter works great to boot either Lubuntu or Ubuntu sessions, but I'm clearly missing something because when I remove Lubuntu and it's components, even though I leave lightdm-gtk-greeter installed, lightdm refuses to load and just displays a low graphics warning.

But if I change "/etc/lightdm/lightdm.conf" to use unity-greeter all is well. Anyway I just wondered if anyone has tried converting Ubuntu to using lightdm-gtk-greeter?

If so they might be able to clue me in and save me a bunch of time sorting this out :D

It's certainly no big deal though, if lightdm-gtk-greeter just doesn't work well with pure Ubuntu then it's easy to convert to unity-greeter.

Thanks in advance.I'm using lightdm-gtk-greeter for more than a month without a glitch...

---

### Post by kansasnoob on 2012-04-10
> **zika said:**
> I'm using lightdm-gtk-greeter for more than a month without a glitch...

Were there any glitches?

Is this pure Ubuntu?

I'm sure I'm overlooking something simple :redface:

---

### Post by Irihapeti on 2012-04-10
I've been using lightdm-gtk greeter with an Openbox install for a while now.

There was an error at one stage that caused it not to appear (had to go to a tty, login and run startx), but it's been fixed.

---

### Post by kansasnoob on 2012-04-10
I'm obviously breaking something but I've tried parsing the dependencies for lightdm-gtk-greeter and I'm not figuring out what I'm doing wrong :(

Once I figure it out I'm sure I'll feel like a total boob :oops:

I've tried the most obvious stuff like "sudo apt-get install --reinstall lightdm-gtk-greeter", same with lightdm itself, and apt-get -f install but I'm just stumped ATM.

The intended unity-greeter works but not lightdm-gtk-greeter :confused:

---

### Post by grahammechanical on 2012-04-10
I am struggling in greater darkness than you. Please let me think this through.

Ubuntu uses lightDM which uses unity-greeter which has a unity-greeter.conf in /etc/lightdm.

You want to use lightdm-gtk-greeter instead of unity-greeter. Do you have a lightdm-gtk-greeter.conf script in /etc/lightdm as well as a unity-greeter.conf?

Also in /usr/share/unity-greeter you will find the logos that the unity-greeter looks for according to unity-greeter.conf.

Do you have a similar folder with icons in it for lightdm-gtk-greeter?

I am just having a blind guess.

Regards.

---

### Post by mc4man on 2012-04-10
Assuming you have it installed, (lightdm-gtk-greeter) you switch to the gtk greeter with

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```

To switch back to unity greeter (assuming you didn't remove which there is no need to

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```

Change is affected thru a restart

---

### Post by kansasnoob on 2012-04-10
> **mc4man said:**
> Assuming you have it installed, (lightdm-gtk-greeter) you switch to the gtk greeter with

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g lightdm-gtk-greeter
```

To switch back to unity greeter (assuming you didn't remove which there is no need to

```
sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```

Change is affected thru a restart

Thank you, I wondered if there weren't an easier way than using a text editor.

I just tried this in a well running Ubuntu Precise and both greeters work fine, so it's definitely something I'm breaking when I run:

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg elementary-icon-theme esound-common galculator gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0 libabiword-2.9 libaudclient2 libaudcore1 libaudiofile1 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libencode-locale-perl libesd0 libexo-1-0 libexo-common libexo-helpers libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1 libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4 libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libmcrypt4 libmenu-cache1 libmowgli2 libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libresid-builder0c2a libsidplay2 libsocket6-perl libtar0 libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libuniconf4.6 liburi-perl libvdpau1 libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1 link-grammar-dictionaries-en lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog python-pysqlite2 python-xklavier scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins system-tools-backends transmission ttf-lyx uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data
```

I just need to keep hammering away until I figure it out ;)

---

### Post by kansasnoob on 2012-04-10
Just thought to try that command on this Ubuntu where both greeters work:

```
lance@lance-desktop:~$ sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg elementary-icon-theme esound-common galculator gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0 libabiword-2.9 libaudclient2 libaudcore1 libaudiofile1 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libencode-locale-perl libesd0 libexo-1-0 libexo-common libexo-helpers libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1 libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4 libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libmcrypt4 libmenu-cache1 libmowgli2 libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libresid-builder0c2a libsidplay2 libsocket6-perl libtar0 libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libuniconf4.6 liburi-perl libvdpau1 libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1 link-grammar-dictionaries-en lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog python-pysqlite2 python-xklavier scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins system-tools-backends transmission ttf-lyx uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package esound-common is not installed, so not removed
Package gnome-icon-theme-full is not installed, so not removed
Package indicator-status-provider-pidgin is not installed, so not removed
Package libaudiofile1 is not installed, so not removed
Package libcue1 is not installed, so not removed
Package libencode-locale-perl is not installed, so not removed
Package libesd0 is not installed, so not removed
Package libfile-listing-perl is not installed, so not removed
Package libfont-afm-perl is not installed, so not removed
Package libgif4 is not installed, so not removed
Package libglade2-0 is not installed, so not removed
Package libgsf-1-114 is not installed, so not removed
Package libgsf-1-common is not installed, so not removed
Package libgtkspell0 is not installed, so not removed
Package libhtml-form-perl is not installed, so not removed
Package libhtml-format-perl is not installed, so not removed
Package libhtml-parser-perl is not installed, so not removed
Package libhtml-tagset-perl is not installed, so not removed
Package libhtml-tree-perl is not installed, so not removed
Package libhttp-cookies-perl is not installed, so not removed
Package libhttp-daemon-perl is not installed, so not removed
Package libhttp-date-perl is not installed, so not removed
Package libhttp-message-perl is not installed, so not removed
Package libhttp-negotiate-perl is not installed, so not removed
Package libid3tag0 is not installed, so not removed
Package libimlib2 is not installed, so not removed
Package libio-socket-inet6-perl is not installed, so not removed
Package libio-socket-ssl-perl is not installed, so not removed
Package libjavascriptcoregtk-1.0-0 is not installed, so not removed
Package libjpeg-progs is not installed, so not removed
Package libjpeg-turbo-progs is not installed, so not removed
Package liblaunchpad-integration1 is not installed, so not removed
Package libloudmouth1-0 is not installed, so not removed
Package liblwp-mediatypes-perl is not installed, so not removed
Package liblwp-protocol-https-perl is not installed, so not removed
Package libmailtools-perl is not installed, so not removed
Package libnet-http-perl is not installed, so not removed
Package libnet-ssleay-perl is not installed, so not removed
Package libopts25 is not installed, so not removed
Package libpisock9 is not installed, so not removed
Package libsocket6-perl is not installed, so not removed
Package libtidy-0.99-0 is not installed, so not removed
Package libtie-ixhash-perl is not installed, so not removed
Package libtimedate-perl is not installed, so not removed
Package libuniconf4.6 is not installed, so not removed
Package liburi-perl is not installed, so not removed
Package libvdpau1 is not installed, so not removed
Package libwebkitgtk-1.0-0 is not installed, so not removed
Package libwebkitgtk-1.0-common is not installed, so not removed
Package libwvstreams4.6-base is not installed, so not removed
Package libwvstreams4.6-extras is not installed, so not removed
Package libwww-perl is not installed, so not removed
Package libwww-robotrules-perl is not installed, so not removed
Package libxml-parser-perl is not installed, so not removed
Package libxml-twig-perl is not installed, so not removed
Package libxml-xpath-perl is not installed, so not removed
Package libxss1 is not installed, so not removed
Package ntp is not installed, so not removed
Package pidgin is not installed, so not removed
Package pidgin-data is not installed, so not removed
Package pidgin-libnotify is not installed, so not removed
Package wvdial is not installed, so not removed
Package xscreensaver is not installed, so not removed
Package xscreensaver-data is not installed, so not removed
Package abiword is not installed, so not removed
Package abiword-common is not installed, so not removed
Package abiword-plugin-grammar is not installed, so not removed
Package abiword-plugin-mathview is not installed, so not removed
Package ace-of-penguins is not installed, so not removed
Package audacious is not installed, so not removed
Package audacious-plugins is not installed, so not removed
Package audacious-plugins-data is not installed, so not removed
Package blueman is not installed, so not removed
Package chromium-browser is not installed, so not removed
Package chromium-browser-l10n is not installed, so not removed
Package chromium-codecs-ffmpeg is not installed, so not removed
Package elementary-icon-theme is not installed, so not removed
Package galculator is not installed, so not removed
Package gecko-mediaplayer is not installed, so not removed
Package giblib1 is not installed, so not removed
Package gnome-desktop-data is not installed, so not removed
Package gnome-mplayer is not installed, so not removed
Package gnome-system-tools is not installed, so not removed
Package gnome-time-admin is not installed, so not removed
Package gnumeric is not installed, so not removed
Package gnumeric-common is not installed, so not removed
Package gnumeric-doc is not installed, so not removed
Package gpicview is not installed, so not removed
Package guvcview is not installed, so not removed
Package hardinfo is not installed, so not removed
Package leafpad is not installed, so not removed
Package libaacs0 is not installed, so not removed
Package libabiword-2.9 is not installed, so not removed
Package libaudclient2 is not installed, so not removed
Package libaudcore1 is not installed, so not removed
Package libbinio1ldbl is not installed, so not removed
Package libbluray1 is not installed, so not removed
Package libbs2b0 is not installed, so not removed
Package libcddb2 is not installed, so not removed
Package libcolamd2.7.1 is not installed, so not removed
Package libcompfaceg1 is not installed, so not removed
Package libexo-1-0 is not installed, so not removed
Package libexo-common is not installed, so not removed
Package libexo-helpers is not installed, so not removed
Package libfluidsynth1 is not installed, so not removed
Package libfm-data is not installed, so not removed
Package libfm-gtk-data is not installed, so not removed
Package libfm-gtk1 is not installed, so not removed
Package libfm1 is not installed, so not removed
Package libgdome2-0 is not installed, so not removed
Package libgdome2-cpp-smart0c2a is not installed, so not removed
Package libgmlib0 is not installed, so not removed
Package libgmtk0 is not installed, so not removed
Package libgmtk0-data is not installed, so not removed
Package libgoffice-0.8-8 is not installed, so not removed
Package libgoffice-0.8-8-common is not installed, so not removed
Package libgringotts2 is not installed, so not removed
Package libgtkmathview0c2a is not installed, so not removed
Package libguess1 is not installed, so not removed
Package liblink-grammar4 is not installed, so not removed
Package libmcrypt4 is not installed, so not removed
Package libmenu-cache1 is not installed, so not removed
Package libmowgli2 is not installed, so not removed
Package libmpg123-0 is not installed, so not removed
Package libnet-dbus-perl is not installed, so not removed
Package libobrender27 is not installed, so not removed
Package libobt0 is not installed, so not removed
Package libonig2 is not installed, so not removed
Package liboobs-1-5 is not installed, so not removed
Package libots0 is not installed, so not removed
Package libresid-builder0c2a is not installed, so not removed
Package libsidplay2 is not installed, so not removed
Package libtar0 is not installed, so not removed
Package libwebcam0 is not installed, so not removed
Package libwv-1.2-4 is not installed, so not removed
Package libxfce4ui-1-0 is not installed, so not removed
Package libxfce4util-bin is not installed, so not removed
Package libxfce4util-common is not installed, so not removed
Package libxfce4util4 is not installed, so not removed
Package libxfconf-0-2 is not installed, so not removed
Package link-grammar-dictionaries-en is not installed, so not removed
Package lm-sensors is not installed, so not removed
Package lp-solve is not installed, so not removed
Package lubuntu-artwork is not installed, so not removed
Package lubuntu-artwork-12-04 is not installed, so not removed
Package lubuntu-core is not installed, so not removed
Package lubuntu-default-settings is not installed, so not removed
Package lubuntu-desktop is not installed, so not removed
Package lubuntu-icon-theme is not installed, so not removed
Package lubuntu-software-center is not installed, so not removed
Package lxappearance is not installed, so not removed
Package lxappearance-obconf is not installed, so not removed
Package lxinput is not installed, so not removed
Package lxkeymap is not installed, so not removed
Package lxlauncher is not installed, so not removed
Package lxmenu-data is not installed, so not removed
Package lxpanel is not installed, so not removed
Package lxpanel-indicator-applet-plugin is not installed, so not removed
Package lxrandr is not installed, so not removed
Package lxsession is not installed, so not removed
Package lxsession-edit is not installed, so not removed
Package lxshortcut is not installed, so not removed
Package lxtask is not installed, so not removed
Package lxterminal is not installed, so not removed
Package mplayer2 is not installed, so not removed
Package mtpaint is not installed, so not removed
Package obconf is not installed, so not removed
Package openbox is not installed, so not removed
Package openbox-themes is not installed, so not removed
Package osmo is not installed, so not removed
Package pcmanfm is not installed, so not removed
Package pidgin-microblog is not installed, so not removed
Package python-pysqlite2 is not installed, so not removed
Package python-xklavier is not installed, so not removed
Package scrot is not installed, so not removed
Package sylpheed is not installed, so not removed
Package sylpheed-doc is not installed, so not removed
Package sylpheed-i18n is not installed, so not removed
Package sylpheed-plugins is not installed, so not removed
Package system-tools-backends is not installed, so not removed
Package transmission is not installed, so not removed
Package ttf-lyx is not installed, so not removed
Package uvcdynctrl is not installed, so not removed
Package uvcdynctrl-data is not installed, so not removed
Package xfburn is not installed, so not removed
Package xfce-keyboard-shortcuts is not installed, so not removed
Package xfce4-power-manager is not installed, so not removed
Package xfce4-power-manager-data is not installed, so not removed
Package xfconf is not installed, so not removed
Package xfonts-100dpi is not installed, so not removed
Package xpad is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Nothing apparent there ](*,)](*,)](*,)

---

### Post by mc4man on 2012-04-10
The deps for lightdm-gtk-greeter in _Ubuntu_ are quite simple & most likely already installed by default

---

### Post by zika on 2012-04-11
I'm switching between these two greeters just with:
```
:~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
#greeter-session=unity-greeter
#user-session=gnome-classic
...
user-session=cinnamon
autologin-user=........
allow-guest=false
greeter-hide-users=true
```

---

### Post by kansasnoob on 2012-04-11
> **grahammechanical said:**
> I am struggling in greater darkness than you. Please let me think this through.

Ubuntu uses lightDM which uses unity-greeter which has a unity-greeter.conf in /etc/lightdm.

You want to use lightdm-gtk-greeter instead of unity-greeter. Do you have a lightdm-gtk-greeter.conf script in /etc/lightdm as well as a unity-greeter.conf?

Also in /usr/share/unity-greeter you will find the logos that the unity-greeter looks for according to unity-greeter.conf.

Do you have a similar folder with icons in it for lightdm-gtk-greeter?

I am just having a blind guess.

Regards.

I missed this earlier, time to have a look. Many thanks :)

---

### Post by kansasnoob on 2012-04-11
I may have found the problem but I'm multi-tasking because I think many of those w/o PAE support will want a 5 year Ubuntu rather than an 18 month Lubuntu or a 3 year Xubuntu, so I'm combining what I've learned from all of you with what I know about Unity-2D and Classic w/o effects :)

Everything just takes time ............ and animals still need to be fed, the grass and weeds keep growing, and machines (both puter and non-puter) keep breaking :biggrin:

Be patient, I'll get there.

---

