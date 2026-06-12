---
title: "sudo apt-get install gnome*"
date: 2013-03-12
forum: Ubuntu Development Version
---

### Post by injisera on 2013-03-12
I got ubuntu 13.04 on my laptop which got a 1024x600 screen, the unity bar on the left hand side ruins many sites and annoys the hell out of me, I truly do miss the windows startmenu + everything at bottom + I can easily see that other windows are behind the window I'm currently viewing.

So I did sudo apt-get install gnome-desktop, it didn't do anything at all as far as I could tell so I did a sudo apt-get install gnome* to see if I was missing anything... and then I got _EVERYTHING_ so now it runs some disgusting blue looking thing that I hate even more at 1 fps. so I did ctrl+alt+f1 and logged in and wrote sudo apt-get remove gnome* and now I got no desktop... 

Where do I go from this awful place to a desktop that looks the most like windows(when it comes to the start-menu & keeping _everything_ at bottom)? 

And is there any way of putting the terminal / synaptic / firefox or other ubuntu programs to the desktop? (I am a shortcut person.. shortcuts are supposed to be on the desktop)


Thanks in advance!
- Harry

---

### Post by stinkeye on 2013-03-12
Seriously??? ](*,)
Ubuntu/unity is based on the GNOME desktop.

You ran **sudo apt-get remove gnome***
and your wondering why you have no desktop.
```
**$ sudo apt-get remove gnome***
The following packages will be REMOVED:
  account-plugin-aim account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-identica account-plugin-jabber account-plugin-salut account-plugin-twitter
  account-plugin-windows-live account-plugin-yahoo activity-log-manager-control-center alacarte
  apturl brasero brasero-cdrkit compiz compiz-gnome cuttlefish deja-dup deja-dup-backend-gvfs
  deja-dup-backend-ubuntuone empathy eog evince evolution-data-server firefox-gnome-support
  gambas3-gb-desktop gcalctool gdebi gdm gir1.2-gdata-0.0 gir1.2-gmenu-3.0
  gir1.2-gnomebluetooth-1.0 gir1.2-gnomedesktop-3.0 gir1.2-gnomekeyring-1.0 gir1.2-goa-1.0
  gir1.2-rb-3.0 gir1.2-soup-2.4 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-webkit-3.0
  gkbd-capplet gksu gnome-accessibility-themes gnome-applets gnome-applets-data gnome-bluetooth
  gnome-calculator gnome-contacts gnome-control-center gnome-control-center-data
  gnome-control-center-signon gnome-control-center-unity gnome-desktop3-data gnome-disk-utility
  gnome-font-viewer gnome-games-data gnome-icon-theme gnome-icon-theme-symbolic gnome-keyring
  gnome-mahjongg gnome-media gnome-menus gnome-mines gnome-orca gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-screenshot gnome-session gnome-session-bin
  gnome-session-canberra gnome-session-common gnome-session-fallback gnome-settings-daemon
  gnome-shell-common gnome-sudoku gnome-system-log gnome-system-monitor gnome-terminal
  gnome-terminal-data gnome-tweak-tool gnome-user-guide gnome-user-share gnomine
  gnomishbeige-theme gstreamer0.10-plugins-good gstreamer1.0-plugins-good gvfs-backends gwibber
  gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  humanity-icon-theme i-nex ibus ibus-pinyin ibus-table indicator-bluetooth indicator-datetime
  indicator-power indicator-session language-pack-gnome-en language-pack-gnome-en-base
  language-selector-gnome libbonoboui2-0 libbrasero-media3-1 libebackend-1.2-5
  libedata-book-1.2-15 libedata-cal-1.2-18 libfarstream-0.1-0 libfarstream-0.2-2 libfolks-eds25
  libgdata13 libgksu2-0 libgnome-bluetooth11 libgnome-control-center1 libgnome-desktop-3-4
  libgnome-keyring-common libgnome-keyring0 libgnome-media-profiles-3.0-0 libgnome-menu-3-0
  libgnome2-0 libgnome2-bin libgnome2-canvas-perl libgnome2-common libgnome2-gconf-perl
  libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl libgnomecanvas2-0 libgnomecanvas2-common
  libgnomekbd-common libgnomekbd8 libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgoa-1.0-0 libgweather-3-1 libgwibber-gtk3 libgwibber3
  libp11-kit-gnome-keyring libpam-gnome-keyring libpurple0 libreoffice-gnome librest-0.7-0
  librhythmbox-core6 libsoup-gnome2.4-1 libsyncdaemon-1.0-1 libtelepathy-farstream3
  libtotem-plparser17 libtotem0 light-themes lightdm-remote-session-uccsconfigure
  mcp-account-manager-uoa metacity nautilus nautilus-open-as-root nautilus-sendto
  nautilus-sendto-empathy nautilus-share network-manager-gnome network-manager-pptp-gnome oneconf
  opera policykit-1-gnome python-gnomekeyring python-ubuntu-sso-client
  python-ubuntuone-control-panel rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone
  seahorse shotwell shutter signon-keyring-extension simple-scan software-center ssh-askpass-gnome
  system-config-printer-gnome telepathy-haze telepathy-mission-control-5 thunderbird-gnome-support
  totem totem-mozilla totem-plugins ubuntu-artwork ubuntu-desktop ubuntu-mono
  ubuntu-release-upgrader-gtk ubuntu-sso-client ubuntu-sso-client-qt ubuntu-tweak ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-qt unity unity-asset-pool
  unity-greeter unity-lens-applications unity-lens-photos unity-lens-shopping
  unity-scope-musicstores unity-scope-video-remote unity-tweak-tool update-manager update-notifier
  webaccounts-extension-common xul-ext-webaccounts y-ppa-manager
```

Try to restore with 
```
sudo apt-get install ubuntu-desktop
```

and to be able to choose a gnome2 like session at the greeter...
```
sudo apt-get install gnome-panel
```
Will add 2 entries to the session menu
**gnome classic**.....uses compiz as the window manager.
**gnome classic(no effects)**.....uses metacity as the window manager.

In unity you can just drag applications from the dash on to the desktop.

---

### Post by dino99 on 2013-03-12
@Harry,

you should have tell us which video hardware is used, and some details about your installation: 32/64 bits, which DE used (gnome-classic, unity, ...), and how have you installed ubuntu : thats the minimum to get usefull help.

As you already have used scary commands removing the whole part of your installation, i'm not sure you'll be able to repair it; but you could try anyway:
- boot in recovery mode: hold "shift" key down at the bios end process to get the grub (bootloader) menu
- select the second line (recovery mode)
- select & activate the network
- select "try to repair" line (or so, i dont remember how exactly its named)

if you get the system repaired, then reboot normally, and you will be able to get around the video issue.

---

### Post by injisera on 2013-03-12
I'm sorry I didn't give any more information, I thought it was not necessary because I was fairly certain that some simple sudo-writing would fix it, which it did, THANKS ALOT stinkeye!

---

### Post by serdotlinecho on 2013-03-12
> I got ubuntu 13.04 on my laptop which got a 1024x600 screen, the unity  bar on the left hand side ruins many sites and annoys the hell out of  me, I truly do miss the windows startmenu + everything at bottom + I can  easily see that other windows are behind the window I'm currently  viewing.

So I did sudo apt-get install gnome-desktop, it didn't do anything at  all as far as I could tell so I did a sudo apt-get install gnome* to see  if I was missing anything... and then I got _EVERYTHING_ so now it runs  some disgusting blue looking thing that I hate even more at 1 fps. so I  did ctrl+alt+f1 and logged in and wrote sudo apt-get remove gnome* and  now I got no desktop... 

Where do I go from this awful place to a desktop that looks the most  like windows(when it comes to the start-menu & keeping _everything_  at bottom)? 

And is there any way of putting the terminal / synaptic / firefox or  other ubuntu programs to the desktop? (I am a shortcut person..  shortcuts are supposed to be on the desktop)


Thanks in advance!
- Harry

I'm using Unity on netbook(1024x600) with unity launcher is set to autohide and i can live with it.
Clearly, Unity or Gnome-shell is not for you, based on your preferences. If you want something like windows xp-ish with start menu, applications shortcuts on the desktop and tasklist/taskbar on the bottom panel, then, I suggest you to try xubuntu or lubuntu. Or if you want something eyecandy and more modern desktop, you can install cinnamon desktop:

```
~&#10095; apt-cache search cinnamon
cinnamon - Innovative and comfortable desktop
cinnamon-common - Innovative and comfortable desktop (Common data files)
cinnamon-dbg - Innovative and comfortable desktop (Debugging symbols)
gir1.2-muffin-3.0 - GObject introspection data for Muffin
libmuffin-dev - lightweight window and compositing manager (development files)
libmuffin0 - lightweight window and compositing manager (shared library)
muffin - lightweight window and compositing manager
muffin-common - lightweight window and compositing manager (data files)
muffin-dbg - lightweight window and compositing manager (debugging symbols)
~&#10095; sudo apt-get install cinnamon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cinnamon-common gir1.2-accountsservice-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-muffin-3.0 gir1.2-polkit-1.0
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs libgjs0c libmozjs185-1.0 libmuffin0 muffin-common
The following NEW packages will be installed:
  cinnamon cinnamon-common gir1.2-accountsservice-1.0 gir1.2-clutter-1.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0
  gir1.2-gconf-2.0 gir1.2-gdesktopenums-3.0 gir1.2-gkbd-3.0 gir1.2-json-1.0 gir1.2-muffin-3.0 gir1.2-polkit-1.0
  gir1.2-upowerglib-1.0 gir1.2-xkl-1.0 gjs libgjs0c libmozjs185-1.0 libmuffin0 muffin-common
0 upgraded, 19 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,985 kB of archives.
After this operation, 20.3 MB of additional disk space will be used.
Do you want to continue [Y/n]?
```

---

### Post by jerrylamos on 2013-03-12
> ```
sudo apt-get install gnome-panel
```
Will add 2 entries to the session menu
**gnome classic**.....uses compiz as the window manager.
**gnome classic(no effects)**.....uses metacity as the window manager.
In unity you can just drag applications from the dash on to the desktop.
2 thoughts:
1.  How much different is this than Gnome Remix?  I suspect a lot with unity lurking in the background...

2. I've got a couple 16:9 displays, either 1366x768 or 1600x900 depending on which test pc I'm on, so I've got a lot more width to spare than height.
I'd rather lose some space sideways than up and down.  

Actually with "Appearance > behavior > hide" most of the time I don't lose width either.

I've also got a test pc with 1280x1024 so I might rather lose height on that one.  

What I do mind is loss of all the applets with very handy "applications" "system" and "preference" applets.  Maybe I can try gnome-panel vs. gnome remix when/if I get energetic.  Since gnome-remix seems to be getting some energy I might try it on a spare partition.  Now if I had a handy "internet video" benchmark.....

Running gnome I delete the bottom panel so I have a top gnome panel which with my chosen applets is a WHOLE lot more useful than Unity's top panel with no way to put chosen applets up there, as far as I know....

---

### Post by injisera on 2013-03-12
In order for me to get cinnamon, do I have to do "sudo apt-get remove ubuntu-desktop" and then write "sudo apt-get install cinnamon"?

(I rather ask than try... don't want to walk in the dark again)

---

### Post by dino99 on 2013-03-12
you already have marked that thread as SOLVED, thats good, so dont spam it with something else: open a new thread into the good subforum: general or updates; here its only for testing u+1, and not about basic questions.

---

### Post by cole.mickens on 2013-03-12
In terms of this topic itself, it would be a reminder to not blindly run commands on your machine. For example, if hundreds of packages are about to be removed, it might be worth considering what those packages are and mentally asking "Hm, should this be purging a ton of important stuff" before hitting Enter...

---

