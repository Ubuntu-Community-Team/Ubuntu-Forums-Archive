---
title: "Yay! Trinity DE (KDE 3.5 fork)."
date: 2013-06-25
forum: Ubuntu, Linux and OS Chat
---

### Post by DisappearingOak on 2013-06-25
Sorry for all the desktop environment threads, but I think I found a really good one. When I started using Linux in '12, I thought all the glory given to old DE's was just because of some old people's nostalgic feelings. But, lately, because of the horrid performance of the new 3d desktops even on my new and adequate hardware (I suspect the radeon driver is total ___ on rs880, and so is catalyst), I've been trying out alternative desktops and I decided to try out Trinity nightly builds (KDE 3.5 fork), and maybe the effect is increased because it has one-time option to set everything to max eye-candy with font smoothing, but it feels like the most coherent and beautiful desktop I've seen. Everything looks seamless and well-stitched. And the confuguration options are all there and not as unintuitive or ugly as kde4. After checking out trinity, I can't understand why people tolerate the new desktops. And also, this thing seems even better than Win XP. I'm surprised why there aren't more developers keeping this project active? No one cares for a coherent, usable desktop? It even has lovely sound effects.

Now I hope the thing will prove stable as I use it. (SolusOS is plan B, but I hope I don't have to go there, all the stable releases had rendering issues and don't know if the latest does or not.) I'm using nightly builds but only because there are no stable packages for raring, it seems. Stable ppa gave me some broken dependency thing. 

Only thing now is to find out how to add some nice window shadows. Maybe I need a different compositor for that? My next few hours is going to be spent adding desktop widgets to the desktop like I see in screenshots with software weirdly named 'Super Karamba' and all. I'm falling for this.

---

### Post by mips on 2013-06-25
Just out of interest sake could you please download this python script [https://github.com/pixelb/scripts/blob/master/scripts/ps_mem.py](https://github.com/pixelb/scripts/blob/master/scripts/ps_mem.py) and run it. I would love to see the memory usage that scrip reports.

Personally I reckon this is a niche project that won't have many adopters, same goes for the old Gnome. Tine to leave the past behind and find alternatives like XFCE, Razor-qt, KLyDE etc which are based on actively developed projects. You might wanna keep and eye on KLyDE if you like KDE.

---

### Post by monkeybrain2012 on 2013-06-25
Yike !This is even more Windows 95-ish than Mate, talk about the king Nosferatu But to each his own. :)

---

### Post by DisappearingOak on 2013-06-25
Yikes indeed. I thought it looked too good to be true. After a little use, it started crashing like crazy, so I installed Ubuntu LTS and installed the stable version of the PPA, but that too... crashes, even the panel crashed. :(

Hmm, I'm unlucky, I guess. There's KDE 3.5 in one of ROSA releases and OpenSuse (I think), so I'm gonna go search for that. This is too good to give up without a fight though.

Maybe the Trinity has customizations, because it didn't look much like Windows 95 (except the menu, but I like the classic menu, and this one even has search). It looked better than XP to me, with some of the included themes like Keramik, etc. And also really nice font hinting.

I think it supports Compiz also (or seemed like that from the options) so I'm going to use it to composite the desktop, when I find a supported kde3 distro.

---

### Post by ssam on 2013-06-25
> **mips said:**
> Personally I reckon this is a niche project that won't have many adopters, same goes for the old Gnome. Tine to leave the past behind and find alternatives like XFCE, Razor-qt, KLyDE etc which are based on actively developed projects. You might wanna keep and eye on KLyDE if you like KDE.

Mate and trinity seem to be roughly as active as XFCE (the ohloh stats are a bit out of date, but you can compare the 30 day and 12 month stats). Also they are based on code that has had far wider use and testing than XFCE (seen as KDE3 and GNOME2 were default desktops on major distros for many years).

[https://www.ohloh.net/p/compare?project_0=Trinity+Desktop+Environment&project_1=MATE+%28desktop+environment%29&project_2=Xfce+%28Core%29](https://www.ohloh.net/p/compare?project_0=Trinity+Desktop+Environment&project_1=MATE+%28desktop+environment%29&project_2=Xfce+%28Core%29)

---

### Post by DisappearingOak on 2013-06-25
> **mips said:**
> Just out of interest sake could you please download this python script [https://github.com/pixelb/scripts/blob/master/scripts/ps_mem.py](https://github.com/pixelb/scripts/blob/master/scripts/ps_mem.py) and run it. I would love to see the memory usage that scrip reports.

Personally I reckon this is a niche project that won't have many adopters, same goes for the old Gnome. Tine to leave the past behind and find alternatives like XFCE, Razor-qt, KLyDE etc which are based on actively developed projects. You might wanna keep and eye on KLyDE if you like KDE.

I found a workaround for panel crashes, so I'm running it again. If anything else starts crashing then I am out.

```
 Private + Shared = RAM used    Program

 96.0 KiB +   8.0 KiB = 104.0 KiB       start_kdeinit
124.0 KiB +  15.0 KiB = 139.0 KiB       cat
180.0 KiB +  25.5 KiB = 205.5 KiB       atd
212.0 KiB +  14.0 KiB = 226.0 KiB       startkde
208.0 KiB +  27.0 KiB = 235.0 KiB       irqbalance
212.0 KiB +  37.0 KiB = 249.0 KiB       upstart-socket-bridge
232.0 KiB +  47.0 KiB = 279.0 KiB       hald-addon-acpi
252.0 KiB +  45.0 KiB = 297.0 KiB       upstart-udev-bridge
272.0 KiB +  43.0 KiB = 315.0 KiB       cron
292.0 KiB +  25.0 KiB = 317.0 KiB       acpid
112.0 KiB + 215.5 KiB = 327.5 KiB       tsak (2)
312.0 KiB +  45.5 KiB = 357.5 KiB       rtkit-daemon
336.0 KiB +  36.5 KiB = 372.5 KiB       dbus-launch
364.0 KiB +  16.5 KiB = 380.5 KiB       ssh-agent
324.0 KiB +  75.0 KiB = 399.0 KiB       hald-addon-input
332.0 KiB +  70.0 KiB = 402.0 KiB       hald-addon-cpufreq
392.0 KiB +  44.5 KiB = 436.5 KiB       dnsmasq
408.0 KiB +  71.5 KiB = 479.5 KiB       hald-runner
456.0 KiB +  93.5 KiB = 549.5 KiB       gvfsd
556.0 KiB +  52.0 KiB = 608.0 KiB       bluetoothd
600.0 KiB +  64.5 KiB = 664.5 KiB       plymouth-upstart-bridge
340.0 KiB + 376.5 KiB = 716.5 KiB       kdeinit
496.0 KiB + 267.0 KiB = 763.0 KiB       http
620.0 KiB + 168.0 KiB = 788.0 KiB       hald-addon-storage (2)
520.0 KiB + 322.5 KiB = 842.5 KiB       avahi-daemon (2)
676.0 KiB + 173.0 KiB = 849.0 KiB       kwrapper
744.0 KiB + 111.0 KiB = 855.0 KiB       gvfs-gphoto2-volume-monitor
856.0 KiB +  23.0 KiB = 879.0 KiB       dhclient
804.0 KiB + 144.0 KiB = 948.0 KiB       gvfs-afc-volume-monitor
644.0 KiB + 395.5 KiB =   1.0 MiB       kdm (2)
  1.0 MiB +  53.0 KiB =   1.0 MiB       rsyslogd
876.0 KiB + 261.0 KiB =   1.1 MiB       at-spi-bus-launcher
980.0 KiB + 185.5 KiB =   1.1 MiB       gvfs-fuse-daemon
976.0 KiB + 204.0 KiB =   1.2 MiB       getty (6)
  1.2 MiB + 145.5 KiB =   1.3 MiB       modem-manager
  1.3 MiB +  66.5 KiB =   1.3 MiB       init
  1.1 MiB + 235.0 KiB =   1.4 MiB       gvfs-gdu-volume-monitor
972.0 KiB + 477.5 KiB =   1.4 MiB       sudo (2)
988.0 KiB + 500.5 KiB =   1.5 MiB       kaccess
  1.0 MiB + 512.0 KiB =   1.5 MiB       kdmtsak
  1.2 MiB + 312.5 KiB =   1.5 MiB       zeitgeist-daemon
  1.1 MiB + 503.5 KiB =   1.6 MiB       udisks-daemon (2)
  1.5 MiB + 119.0 KiB =   1.6 MiB       gconfd-2
  1.3 MiB + 252.0 KiB =   1.6 MiB       polkitd
  1.2 MiB + 423.5 KiB =   1.6 MiB       gconf-helper
  1.2 MiB + 563.0 KiB =   1.7 MiB       klauncher
  1.3 MiB + 411.5 KiB =   1.7 MiB       deja-dup-monitor
  1.5 MiB + 262.5 KiB =   1.8 MiB       console-kit-daemon
  1.5 MiB + 361.5 KiB =   1.9 MiB       dbus-daemon (2)
  1.5 MiB + 433.0 KiB =   1.9 MiB       zeitgeist-datahub
  1.4 MiB + 556.5 KiB =   2.0 MiB       ksmserver
  1.0 MiB + 998.0 KiB =   2.0 MiB       kio_file (2)
864.0 KiB +   1.2 MiB =   2.0 MiB       dcopserver
  1.8 MiB + 243.0 KiB =   2.1 MiB       aspell
  1.6 MiB + 604.5 KiB =   2.2 MiB       udevd (3)
  1.7 MiB + 513.0 KiB =   2.2 MiB       whoopsie
  1.9 MiB + 524.0 KiB =   2.4 MiB       cupsd
  2.1 MiB + 383.0 KiB =   2.5 MiB       zeitgeist-fts
  2.3 MiB + 269.5 KiB =   2.6 MiB       NetworkManager
  2.3 MiB + 872.5 KiB =   3.1 MiB       kio_uiserver
  3.0 MiB + 107.0 KiB =   3.1 MiB       hald
  2.8 MiB + 480.5 KiB =   3.3 MiB       kdialogd3
  2.8 MiB + 943.5 KiB =   3.7 MiB       knotify
  3.5 MiB + 709.5 KiB =   4.2 MiB       kwin
  3.8 MiB + 714.5 KiB =   4.5 MiB       klipper
  3.7 MiB + 852.5 KiB =   4.6 MiB       pulseaudio
  3.4 MiB +   1.5 MiB =   4.9 MiB       notification-daemon-tde
  4.2 MiB +   1.3 MiB =   5.5 MiB       konsole
  3.8 MiB +   1.9 MiB =   5.7 MiB       kdesktop_lock
  4.7 MiB +   1.2 MiB =   5.9 MiB       kmix
  4.3 MiB +   1.9 MiB =   6.1 MiB       kded
  5.6 MiB +   2.0 MiB =   7.7 MiB       katapult
  6.6 MiB +   1.1 MiB =   7.7 MiB       bash (2)
  6.8 MiB +   1.1 MiB =   7.9 MiB       colord
  7.6 MiB + 772.0 KiB =   8.4 MiB       krandrtray
  7.9 MiB +   1.2 MiB =   9.1 MiB       artsd
  7.5 MiB +   1.7 MiB =   9.2 MiB       konqueror
 10.0 MiB +  90.5 KiB =  10.1 MiB       plymouthd [updated]
 14.6 MiB +   1.7 MiB =  16.3 MiB       kicker
 15.3 MiB +   1.7 MiB =  17.0 MiB       kdesktop
 19.9 MiB +   1.0 MiB =  20.9 MiB       adept_notifier
 46.5 MiB + 333.5 KiB =  46.8 MiB       apt-get
 47.0 MiB + 654.0 KiB =  47.6 MiB       Xorg
---------------------------------
                        327.8 MiB
=================================


```

---

### Post by mips on 2013-06-25
Thanks. That's not very 'light' if i could put it that way. Honestly though it would have lower memory usage. Use to love KDE3.5 back in the day ;)

---

### Post by ssam on 2013-06-25
> **mips said:**
> Thanks. That's not very 'light' if i could put it that way. Honestly though it would have lower memory usage. Use to love KDE3.5 back in the day ;)

You wouldn't have plymouthd, colord, pulseaudio, zeitgeist and deja-dup-monitor running back in the day. does one need artsd and pulseaudio running?

Also apt-get is listed, so I guess the script was run will apt was checking for updates.

---

### Post by DisappearingOak on 2013-06-25
> **ssam said:**
> You wouldn't have plymouthd, colord, pulseaudio, zeitgeist and deja-dup-monitor running back in the day. does one need artsd and pulseaudio running?

Also apt-get is listed, so I guess the script was run will apt was checking for updates.

Hmm, yes, I think I was installing something from apt in Konsole.

It hasn't crashed, but not all of my apps run properly. The GTK ones, it complains about GTK 2.x and 3.x library mixtures and what not, so I'm going to resign myself to using another DE for now. It did leave a pleasant feelings in my mind though.. the lovely, fun, colourful keramik theme, the nice calendar which maximizes, the great serene sound effects (we are so advanced now that we don't have sounds anymore. might as well become deaf altogether), the wonderful animations when you click on icons, the really nice image blending effects like "hue shift". Where is all that in KDE4?

[BEGIN RANT] Why can't we just have human-friendly user interfaces anymore? Even Windows 7 has gone on the wrong path. Looking at KDE plasma makes me feel sick. It is so ugly. Do we really need dratted pixel perfect SVGs for everything? What was wrong with fun colourful UIs? Can anyone actually read anything on plasma's transparent panels and widgets, whatever theme, without tearing out their eyeballs? Yuck. [END]

Hehe.

---

### Post by mastablasta on 2013-06-26
> **DisappearingOak said:**
> [BEGIN RANT] Why can't we just have human-friendly user interfaces anymore? Even Windows 7 has gone on the wrong path. Looking at KDE plasma makes me feel sick. It is so ugly. Do we really need dratted pixel perfect SVGs for everything? What was wrong with fun colourful UIs? Can anyone actually read anything on plasma's transparent panels and widgets, whatever theme, without tearing out their eyeballs? Yuck. [END]


i don't see anything horrible in new KDE (except maybe kickstarter). you can modify it to make it more colourful if that is what you want. 

who says you need transparent widnows and panels and such? i've turned off all unnecessary and useless desktop effects.

---

