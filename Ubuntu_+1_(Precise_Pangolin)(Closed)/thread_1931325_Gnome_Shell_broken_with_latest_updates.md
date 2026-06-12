---
title: "Gnome Shell broken with latest updates"
date: 2012-02-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sgage on 2012-02-25
After doing a bunch of updates this morning, my Gnome Shell crashed. Subsequent attempts to log in result in just the wallpaper - no panel, no overview, no nothing.

Anyone else experiencing this? I didn't see anything in the updates that should be having this effect, but who knows... Gnome Classic and Unity are working normally.

---

### Post by sgage on 2012-02-25
On a hunch, I removed all shell extensions from .local/share/gnome-shell/extensions, and Gnome Shell came right up. I added them back in, one at a time, and it was the "recent items" extension! I didn't know that a trivial little extension like that could crash the whole thing.

And I don't understand why, after it had been working fine for weeks, it just got flakey. Oh well.

---

### Post by ronacc on 2012-02-25
are you using the repo GS or a PPA version ? I have a repo only GS and updating just after your post did not cause my GS to crash after reboot .

edit: I have extensions built from source so the did not update .

---

### Post by sgage on 2012-02-25
> **ronacc said:**
> are you using the repo GS or a PPA version ? I have a repo only GS and updating just after your post did not cause my GS to crash after reboot .

edit: I have extensions built from source so the did not update .

I use the stock GS version from the repos. The extension in question was installed via the extensions.gnome.org website, so not involved with package management and updates.

---

### Post by zika on 2012-02-25
For quite some time I have problem with Gnome-Shell. Lately it does not even start: if I choose GS from greeter I get some Gnome desktop... I'm up-to-date from ricotz PPA...
```
:~$ cat /usr/share/app-install/desktop/gnome-shell:gnome-shell.desktop
[Desktop Entry]
X-AppInstall-Package=gnome-shell
X-AppInstall-Popcon=23081
X-AppInstall-Section=universe

Type=Application
Name=GNOME Shell
Comment=Window management and application launching
Exec=/usr/bin/gnome-shell
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-shell
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.2.2.1
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
NoDisplay=true
``````
:~$ cat /usr/share/applications/gnome-shell.desktop
[Desktop Entry]
Type=Application
Name=GNOME Shell
Comment=Window management and application launching
Exec=/usr/bin/gnome-shell
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-shell
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.3.90
Categories=GNOME;GTK;Core;
OnlyShowIn=GNOME;
NoDisplay=true
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=panel;windowmanager;
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gnome-shell
``````
:~$ cat /usr/share/xsessions/gnome-shell.desktop
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```If I start it either from ~/.Xsession or via ```
gnome-shell --replace
```it is flickering and unstable up to being unusable...
Any suggestions? Other that ```
sudo ppa-purge ppa:ricotz/testing
```what is planned for tomorrow morning... ;)
Update: I was imaptient. I've done ppa-purge and nothing have got better... I (still) do not get GS to start but I get some gnome-session... Once I get GS going it is ustable... I have XorgEdgers and several other PPa's active... Any ideas... It is not (very) important since I spent most of my time in FluxBox or similar... But, I'm (more that anything) curious...
Update: ```
sudo ppa-purge  ppa:xorg-edgers/ppa 
```did not make things any better. One place less to explore...

---

### Post by Harry33 on 2012-02-26
> **zika said:**
> For quite some time I have problem with Gnome-Shell. Lately it does not even start: if I choose GS from greeter I get some Gnome desktop... I'm up-to-date from ricotz PPA...
...
Any suggestions? Other that ```
sudo ppa-purge ppa:ricotz/testing
```what is planned for tomorrow morning... ;)
Update: I was imaptient. I've done ppa-purge and nothing have got better... I (still) do not get GS to start but I get some gnome-session... Once I get GS going it is ustable... I have XorgEdgers and several other PPa's active... Any ideas... It is not (very) important since I spent most of my time in FluxBox or similar... But, I'm (more that anything) curious...
Update: ```
sudo ppa-purge  ppa:xorg-edgers/ppa 
```did not make things any better. One place less to explore...

In my 64-bit (Nvidia 285GTX with nvidia-current 295.20) I have a fully working gnome-shell (3.3.90).
I use xserver 1.12 with nvidia-current and xserver-xorg-input-evdev from Xorg-edgers. It works very well.
This is a GS from the Ricotz Testing PPA, without any git-versions however.
So I have these:
- clutter 1.9.12 (Gnome3 PPA)
- cogl 1.9.6 (from Gnome3 PPA)
- gnome-shell 3.3.90 (Gnome3 PPA)
- mutter 3.3.90 (Gnome3 PPA)
I have to use gjs 1.31.10+git20120213 (from Ricotz Testing PPA), but that is very near to 1.31.10.
Just bear in mind that you need to have gir1.2-gjs-1.0 installed: otherwise gnome-shell does not start correctly (no panels).
Also I have to use gobject-introspection 1.31.10+git20120221 (from Ricotz Testing PPA).
Then, glib2.0, GTK+3, gnome-themes-standard and pango are from Precise repos. In order to avoid git-versions.

This gnome-shell is no way unstable nor flickering and it starts normally every time from LightDM.

---

### Post by zika on 2012-02-26
> **Harry33 said:**
> In my 64-bit (Nvidia 285GTX with nvidia-current 295.20) I have a fully working gnome-shell (3.3.90).
I use xserver 1.12 with nvidia-current and xserver-xorg-input-evdev from Xorg-edgers. It works very well.
This is a GS from the Ricotz Testing PPA, without any git-versions however.
So I have these:
- clutter 1.9.12
- cogl 1.9.6 (from Gnome3 PPA)
- gnome-shell 3.3.90
- mutter 3.3.90
I have to use gjs 1.31.10+git20120213, but that is very near to 1.31.10.

Then, glib2.0, GTK+3, gobject-introspection, gnome-themes-standard and pango are from Precise repos. In order to avoid git-versions.

This gnome-shell is no way unstable nor flickering and it starts normally every time from LightDM.
I'll have to write all this down and resolve what package is from which PPA. Being sick at the moment (temperature etc.) I have my brain working not on „ondemand“ but on (very) „conservative“... ;)

---

### Post by Harry33 on 2012-02-26
> **zika said:**
> I'll have to write all this down and resolve what package is from which PPA. Being sick at the moment (temperature etc.) I have my brain working not on „ondemand“ but on (very) „conservative“... ;)

Zika, see the additions I made (gir1.2-gjs-1.0).

---

### Post by Harry33 on 2012-02-26
Yes, and one more option to use gnome-shell 3.3.90
here you have no git versions installed:

Totally purge Ricotz Testing PPA and only use Gnome3 PPA.
Then you have these packages:
- gnome-shell 3.3.90
- clutter 1.9.12
- cogl 1.9.6
- mutter 3.3.90
- gjs 1.31.6

All other related packages come from Precise repos:
- gobject introspection 1.31.10
- gnome-themes-standard 3.3.90.1
- gnome-tweak-tool 3.3.4
- glib2.0 2.31.18
- GTK+3 3.3.16
- pango 1.29.5

---

### Post by bmbaker on 2012-02-26
i am running with the ricotz/testing ppa, extensions in .local and in usr/share and everything wking just fine!

---

### Post by zika on 2012-02-26
> **Harry33 said:**
> Zika, see the additions I made (gir1.2-gjs-1.0).
Two things:
1. I do not have gnome-shell-extensions installed. Mistake?
2. At this moment I am under viral infection attack (rising temperature, sore muscles, weak mental status) and a lot if stuf that should be solved on my desk. So GS will have to wait indefinitely. In situations like this OpenBox without anything added or FluxBox is the only environment I'm willing to operate... ;)
I'm sure it will come to place at the time I get better... ;)

---

### Post by Harry33 on 2012-02-26
> **zika said:**
> Two things:
1. I do not have gnome-shell-extensions installed. Mistake?
2. At this moment I am under viral infection attack (rising temperature, sore muscles, weak mental status) and a lot if stuf that should be solved on my desk. So GS will have to wait indefinitely. In situations like this OpenBox without anything added or FluxBox is the only environment I'm willing to operate... ;)
I'm sure it will come to place at the time I get better... ;)

I do not use extensions either.
Hope you get better soon. :)

---

### Post by zika on 2012-02-26
> **Harry33 said:**
> I do not use extensions either.
Hope you get better soon. :)Thank You! What does not kill me, makes me stronger... and older...

---

### Post by apoapo on 2012-03-01
> **Harry33 said:**
> 
Just bear in mind that you need to have gir1.2-gjs-1.0 installed: otherwise gnome-shell does not start correctly (no panels).



That was the fix for me, thanks. Is there any bug to report this missing dependency?

---

### Post by Harry33 on 2012-03-01
> **apoapo said:**
> That was the fix for me, thanks. Is there any bug to report this missing dependency?

That dependency has already been corrected in the Gnome-Shell Testing PPA and also in the Gnome3 Team PPA => package gnome-shell depends on gir1.2-gjs-1.0.

---

