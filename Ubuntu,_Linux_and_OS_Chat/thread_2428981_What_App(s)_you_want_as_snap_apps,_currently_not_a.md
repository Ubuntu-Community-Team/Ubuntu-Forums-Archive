---
title: "What App(s) you want as snap apps, currently not available as snap app?"
date: 2019-10-11
forum: Ubuntu, Linux and OS Chat
---

### Post by jasper99 on 2019-10-11
Me

- Virtualbox
- 4K video downloader
- Binreader
- Wine
- Steam
- Gdebi
- dropbox
- synaptic
- Google Chrome
- Vivaldi (browser)

---

### Post by uRock on 2019-10-11
Gdebi and Synaptic as Snaps? Wouldn't that be a slap in the face to their developers.

---

### Post by cruzer001 on 2019-10-11
Snapd is in Synaptics, sounds fair to me:lol:

---

### Post by TheFu on 2019-10-11
I'd like for snapd to be sandboxed where it could not be used without an active, specific, request. No more default pushing of snaps.

---

### Post by Frogs Hair on 2019-10-11
I'd rather not see snaps as default applications ,but have some installed . Only the last three are installed by choice.

```
/dev/loop2      256K  256K     0 100% /snap/gtk2-common-themes/5
/dev/loop1       17M   17M     0 100% /snap/ubuntu-budgie-welcome/145
/dev/loop0       90M   90M     0 100% /snap/core/7713
/dev/loop3       55M   55M     0 100% /snap/core18/1144
/dev/loop6       90M   90M     0 100% /snap/core/7917
/dev/loop7       17M   17M     0 100% /snap/ubuntu-budgie-welcome/144
/dev/loop4       45M   45M     0 100% /snap/gtk-common-themes/1353
/dev/loop8       55M   55M     0 100% /snap/core18/1192
/dev/loop5       43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop9      182M  182M     0 100% /snap/spotify/36
/dev/loop10     220M  220M     0 100% /snap/gimp/189
/dev/loop11     194M  194M     0 100% /snap/mailspring/374



```

---

### Post by P-I H on 2019-10-12
This thread is about snaps, but have you tried flatpaks.
I have these installed on 19.10.
```
p-i@pi-MS-7A34:~$ flatpak list
Name              Application ID                Version    Branch Installation
VidCutter         com.ozmartians.VidCutter      6.0.0.6    stable system
Spotify           com.spotify.Client            1.1.10.546 stable system
Steam             com.valvesoftware.Steam       1.0.0.61   stable system
Freedesktop Plat… org.freedesktop.Platform      18.08.37   18.08  system
Freedesktop Plat… org.freedesktop.Platform      19.08.3    19.08  system
i386              …desktop.Platform.Compat.i386            18.08  system
i386              …desktop.Platform.Compat.i386            19.08  system
default           …edesktop.Platform.GL.default            19.08  system
default           …esktop.Platform.GL32.default            19.08  system
html5-codecs      …esktop.Platform.html5-codecs            18.08  system
openh264          …reedesktop.Platform.openh264            19.08  system
GNOME Boxes       org.gnome.Boxes               3.34.1     stable system
GNOME Applicatio… org.gnome.Platform                       3.32   system
GNOME Applicatio… org.gnome.Platform                       3.34   system
Yaru Gtk Theme    org.gtk.Gtk3theme.Yaru                   3.22   system
KDE Application … org.kde.Platform                         5.12   system
KDE Application … org.kde.Platform                         5.13   system
QGnomePlatform    …PlatformTheme.QGnomePlatform            5.12   system
QGnomePlatform    …PlatformTheme.QGnomePlatform            5.13   system
QGnomePlatform-d… …on.QGnomePlatform-decoration            5.12   system
VLC               org.videolan.VLC              3.0.8      stable system
Kodi              tv.kodi.Kodi                  18.4-Leia  stable system
p-i@pi-MS-7A34:~$
```

---

### Post by TheFu on 2019-10-12
I tried a flatpak.  It was a 900MB download for a 33MB application.  The startup command is complicated. 
```
/usr/bin/flatpak  run com.ozmartians.VidCutter $@
```
It didn't actually work. Just failed with some sort of display error.
Last week, I updated the flatpak, that took about 30 minutes and I was password bombed - forced to fill in my sudo password 3x for each block used in the flatpak. After all that, the program didn't work. Failed with the same error.  I think the developer was assuming kde as the DE.  I don't use any DE.

It left the older version of the updated block behind, though no other flatpak is referencing those blocks.

I am not impressed, but I don't have enough knowledge.  When tools like this are new, a short "do this" info summary would be helpful at the start of every command.  I was missing the 
```
flatpak uninstall --unused
```
to clean up unreferenced blocks.  Good thing they didn't call the option, I don't know, autoclean.

---

### Post by makitso on 2019-10-12
My most recent experience with snap was not so good.  I installed fileZilla via snap and when I tried to set the default editor to gedit it would not let fileZilla access the /usr folder.  
Seems snap is not allowed to launch applications.

---

### Post by TheFu on 2019-10-12
> **makitso said:**
> My most recent experience with snap was not so good.  I installed fileZilla via snap and when I tried to set the default editor to gedit it would not let fileZilla access the /usr folder.  
Seems snap is not allowed to launch applications.

Exactly.  Try to upload a file from /tmp/ as well.  Or to download from a snap to /tmp/.  Good luck with that.

snaps almost always break existing integrations by default.  They should install and run in "monitor mode" to see what integrations the user needs, then setup permissions to allow those integrations.  Perhaps in the next 5 yrs, that will be possible as snaps eventually mature and become production ready.

I'm sorry. Didn't mean to be this involved in this thread.  I'll go away now.

---

### Post by PaulW2U on 2019-10-12
> **makitso said:**
> I installed fileZilla via snap and when I tried to set the default editor to gedit it would not let fileZilla access the /usr folder.
Did you realise that the FileZilla snap hasn't progressed past the beta stage of development? That may not have been obvious if you installed using the Ubuntu Software application but your attention is drawn to that fact when installing from the command line.
```
paul@n1644:~$ sudo snap install filezilla
[sudo] password for paul: 
error: snap "filezilla" is not available on stable but is available to install on the following
       channels:

       beta       snap install --beta filezilla
       edge       snap install --edge filezilla

       Please be mindful pre-release channels may include features not completely tested or
       implemented. Get more information with 'snap info filezilla'.

```
The developer might still be trying to work around any such limitations before the snap is released to the stable channel.

Edit: See [https://forum.snapcraft.io/t/filezilla-cant-access-certain-binaries-with-strict-confinement/11491](https://forum.snapcraft.io/t/filezilla-cant-access-certain-binaries-with-strict-confinement/11491). There are ways around such problems.  :)

---

### Post by deadflowr on 2019-10-12
> **jasper99 said:**
> Me

- Virtualbox
- 4K video downloader
- Binreader
- Wine
- Steam
- Gdebi
- dropbox
- synaptic
- Google Chrome
- Vivaldi (browser)

See: [https://forum.snapcraft.io/t/snap-wishlist-suggestions-wanted/567]("https://forum.snapcraft.io/t/snap-wishlist-suggestions-wanted/567")

---

### Post by VMC on 2019-10-12
> **TheFu said:**
> I'd like for snapd to be sandboxed where it could not be used without an active, specific, request. No more default pushing of snaps.
Absolutely! I want nothing to do with Snaps or Flaps. Give me **apt** only and I will be happy.

---

### Post by Tadaen_Sylvermane on 2019-10-13
Agreed. Part of the whole Linux draw for me is shared libraries which the current Apt provides nicely. Without that, might as well go back to Windows... desktop anyway. To be fair though, I'm not entirely against them either. Some type of universal packaging mechanism is going to be required if anyone ever expects the big software providers to bring stuff to linux. Thinking Adobe, Triple A games, and any number of other software's that people rely on that keep them using Windows.

---

### Post by lammert-nijhof on 2019-10-13
Snaps run in a kind of container for security and it is not allowed to launch 'unknown' applications nor malware.

---

### Post by VMC on 2019-10-13
> **lammert-nijhof said:**
> Snaps run in a kind of container for security and it is not allowed to launch 'unknown' applications nor malware.
When's the last time you got a malware running APT? Me. Never.

---

### Post by mc4man on 2019-10-16
> **VMC said:**
> When's the last time you got a malware running APT? Me. Never.
That ' snap provides security ... idea' seems over-extended.
The use and anticipated use of snaps themselves  created the need to confine snaps as many are  3rd party prop with no available/review-able  source code.

---

