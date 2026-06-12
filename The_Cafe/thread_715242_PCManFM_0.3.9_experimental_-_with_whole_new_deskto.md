---
title: "PCManFM 0.3.9 experimental - with whole new desktop icons and wallpaper support"
date: 2008-03-04
forum: The Cafe
---

### Post by PCMan on 2008-03-04
The old PCManFM 0.3.6.2 stable was released several minutes ago with some fixes. All users are supposed to upgrade.

Today, we have the first public release of the 0.3.9 experimental branch.  You might wonder, what's new in this version, except the new version number. Here is a change log.

[LIST][*]Totally rewrite the desktop icon support. It's much nicer and also faster than the old one.
[*]Drop shadow on desktop item text.
[*]Totally rewrite the wallpaper support. Now there are several different modes: extend, tile, or center the image.
[*]Daemon mode support. Run pcmanfm with -d argument can make pcmanfm a daemon, and it will start much faster later.
[*]Image preview is shown in "Open File" dialog when selecting wallpaper.
[/LIST]

For more detail and download:
[http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)


Besides, I have a small film showing how fast PCManFM and the whole LXDE are on EeePC. The speed is incredible and impressive.

To see is to believe.  (The compressed flv video showed in Flash is poor, please download the original 80 MB video file, if you can)

[http://video.google.com/videoplay?docid=6910499829356532385&hl=en](http://video.google.com/videoplay?docid=6910499829356532385&hl=en)

Your EeePC can be as fast as mine, if you use LXDE.  :-)
We'll have a new release of the whole LXDE recently. Please stay tunned.

Screenshot is a must-have.

[IMG]http://pcman.sayya.org/lxde/desktop_icons.png[/IMG]

---

### Post by eriqjaffe on 2008-03-09
> **PCMan said:**
> The old PCManFM 0.3.6.2 stable was released several minutes ago with some fixes. All users are supposed to upgrade.

Today, we have the first public release of the 0.3.9 experimental branch.  You might wonder, what's new in this version, except the new version number. Here is a change log.

[LIST][*]Totally rewrite the desktop icon support. It's much nicer and also faster than the old one.
[*]Drop shadow on desktop item text.
[*]Totally rewrite the wallpaper support. Now there are several different modes: extend, tile, or center the image.
[*]Daemon mode support. Run pcmanfm with -d argument can make pcmanfm a daemon, and it will start much faster later.
[*]Image preview is shown in "Open File" dialog when selecting wallpaper.
[/LIST]

For more detail and download:
[http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)


Besides, I have a small film showing how fast PCManFM and the whole LXDE are on EeePC. The speed is incredible and impressive.

To see is to believe.  (The compressed flv video showed in Flash is poor, please download the original 80 MB video file, if you can)

[http://video.google.com/videoplay?docid=6910499829356532385&hl=en](http://video.google.com/videoplay?docid=6910499829356532385&hl=en)

Your EeePC can be as fast as mine, if you use LXDE.  :-)
We'll have a new release of the whole LXDE recently. Please stay tunned.

PCMan, I installed the 0.3.9 build last night and am really happy with it, especially running in daemon mode, but I have a question or two...

1) Not a question so much as a possible bug - I'm using PCManFM with Fluxbox, and I'm also using wbar to run a little application launcher.  When I set PCManFM to show a wallpaper, it lays it on top of wbar, rendering it useless.  It doesn't matter what order I load them in, wbar is always in the background.

2) The wallpaper looks as if it were being displayed at a lower bit depth - my system is set to 24-bit, but the wallpaper looks like it's being dithered down, or displayed at 256 colors.  The difference is the same as shown in [a post I made about a different topic](http://ubuntuforums.org/showpost.php?p=4342992&postcount=10), but that gives you an idea of what it looks like.  Any ideas?

Also, are you the same guy who wrote the IETab plugin for Firefox?

---

### Post by kerry_s on 2008-03-09
i'll wait till it get's to debian lenny.

---

### Post by PCMan on 2008-03-09
> **eriqjaffe said:**
> PCMan, I installed the 0.3.9 build last night and am really happy with it, especially running in daemon mode, but I have a question or two...

1) Not a question so much as a possible bug - I'm using PCManFM with Fluxbox, and I'm also using wbar to run a little application launcher.  When I set PCManFM to show a wallpaper, it lays it on top of wbar, rendering it useless.  It doesn't matter what order I load them in, wbar is always in the background.

2) The wallpaper looks as if it were being displayed at a lower bit depth - my system is set to 24-bit, but the wallpaper looks like it's being dithered down, or displayed at 256 colors.  The difference is the same as shown in [a post I made about a different topic](http://ubuntuforums.org/showpost.php?p=4342992&postcount=10), but that gives you an idea of what it looks like.  Any ideas?

Also, are you the same guy who wrote the IETab plugin for Firefox?
1. The oder of windows is controlled by the window manager. In the program I already request the wm to push the desktop window at bottom, and I also specified proper window hint to tell the wm that this is a desktop window, not a regular one. Other wms like openbox and metacity handle this gracefully. If this is not the case for fluxbox, I think a bug report should be sent to fluxbox developers.

2.I didn't know what's wrong with the wallpaper, and I cannot reproduce this bug, either. Sorry this is currently beyond my knowledge. Maybe someone more familiar with this can help?

3. Yes, I'm the same guy developed the IE Tab plugin for Firefox. The other developer is yuoo2k. We created this Firefox extension/plugin several years ago, when I was still using Windows.

---

### Post by PCMan on 2008-03-09
> **kerry_s said:**
> i'll wait till it get's to debian lenny.
wow, i watched that vid and the whole time i'm thinking "wow, that asus is slow".

i use a debian etch/lenny custom install on a vaio pcg-f430, 450mhz 256mb ram, jwm is my window manager.

but it did make me want to try pcmanfm again, in the past it has always been unstable. well off to try the repo version.

0.3.6 is in debian sid already, but I have no idea when will it get into stable.  However, 0.3.6 is quite stable now. This release is focused on robustness and correctness. Most parts of its core are re-written. So, please give it a try.

---

### Post by kerry_s on 2008-03-09
> **PCMan said:**
> 0.3.6 is in debian sid already, but I have no idea when will it get into stable.  However, 0.3.6 is quite stable now. This release is focused on robustness and correctness. Most parts of its core are re-written. So, please give it a try.

is there a feature to account for toolbars, for desktop icons and can the icons be positioned on the desktop where i want them? i remember the last time i tried to drag icons it gave an error about not being able to move in the same directory. i always have problems with the starting icons(top left corner) always being under my tool bar.

1. i would like the spacing thing like in rox, see pic
2. i want to put the icons where i want them.

---

### Post by wersdaluv on 2008-03-09
Is there a deb? I can't compile it.

```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for SN... configure: error: Package requirements (libstartup-notification-1.0) were not met:

No package 'libstartup-notification-1.0' found

```

---

### Post by eriqjaffe on 2008-03-10
> **PCMan said:**
> 1. The oder of windows is controlled by the window manager. In the program I already request the wm to push the desktop window at bottom, and I also specified proper window hint to tell the wm that this is a desktop window, not a regular one. Other wms like openbox and metacity handle this gracefully. If this is not the case for fluxbox, I think a bug report should be sent to fluxbox developers..Thanks for the quick response - failing a bugfix from the Fluxbox developers, would it be possible to have desktop icons without any wallpaper?  As it stands now, with 0.3.9, it doesn't matter if I have the wallpaper box checked or not, I wind up with wallpaper - that's not quite the behavior I would expect if the wallpaper box isn't checked.  ;)

Ultimately, desktop icons aren't a priority for me, but I would be curious as to how to make this work for me.

Thanks again!

---

### Post by eriqjaffe on 2008-03-11
...just as an update...

I discovered that wbar has an "-above-desktop" switch, which will cause it to appear on top of the PCManFM desktop.  The problem is, as soon as I click anywhere on the desktop that isn't wbar, it drops down behind PCManFM.  Ah, well, it's something.

---

### Post by Dawa on 2008-03-16
is there any way to get the 'Computer' and 'Trash' icons on the desktop with PCManFM?  it's the only thing i miss from nautilus  :)

---

### Post by PCMan on 2008-03-17
> **Dawa said:**
> is there any way to get the 'Computer' and 'Trash' icons on the desktop with PCManFM?  it's the only thing i miss from nautilus  :)
Currently, no, but supporting Trash is already planned.

---

### Post by sonnet on 2008-03-22
is this file manager lighter than Thunar and XFE?

---

### Post by PCMan on 2008-03-22
> **sonnet said:**
> is this file manager lighter than Thunar and XFE?

That depends
Generally it's lighter than thunar but heavier than xfe.
However, the i18n support of xfe is poor. Besides, it doesn't support themes, and the default look & feel is Win 95 style. The mime-type handling is worse in xfe, too, and its handling is not standard-compliant.
Thunar is better in many places, but pcmanfm owns tabs, and some parts of pcmanfm are faster than thunar. In addition, pcmanfm with desktop icon support turned on is definitely lighter than thunar + xfdesktop under xfce.

---

### Post by sonnet on 2008-03-24
the main problem of pcmanfm it seems to me that it lacks volume automount capabilities, are you going to implement that?

---

### Post by picpak on 2008-03-24
I compiled 0.3.9.10 into a deb last night. I also have lxpanel if anyone wants it (I found it too buggy for me).

---

### Post by eriqjaffe on 2008-03-25
I'm really liking PCManFM 3.9.1, but I have a question...

When I right-click on some files (.pngs, in particular), "Open with..." lists some applications multiple times:

```
GPicView Image Viewer
--------------------
gimp
mirage
gpicview
feh
feh
Mirage
Opera
GIMP Image Editor
--------------------
Open with another program
```

How can I get rid of extraneous entries?  Are the MIME type stored in a file somewhere?

---

### Post by picpak on 2008-03-25
Try running

```
sudo update-mime-database /usr/share/mime
sudo update-desktop-database
```

The readme says to add these to the postinst scripts, but I don't know how to do that when building with checkinstall.

---

### Post by eriqjaffe on 2008-03-26
> **picpak said:**
> Try running

```
sudo update-mime-database /usr/share/mime
sudo update-desktop-database
```

The readme says to add these to the postinst scripts, but I don't know how to do that when building with checkinstall.Thanks, I'll give those a go tomorrow and see if it improves matters.

edit:  Nope, no change.

---

### Post by webaake on 2008-04-04
Whooa! It's definately faster than 0.3.6 !!!


Thanks pcman!

---

### Post by newb1e on 2008-04-18
hi,

where can I get the libstartup-notification-1.0?

thanks!

---

### Post by Kiri on 2008-04-18
> **wersdaluv said:**
> Is there a deb? I can't compile it.

```
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
checking for SN... configure: error: Package requirements (libstartup-notification-1.0) were not met:

No package 'libstartup-notification-1.0' found

```


I'm having this problem too

---

### Post by webaake on 2008-04-18
Check in synaptic for something like;
libstartup-notification-dev-xxx.

Hope it helps...

---

### Post by Kiri on 2008-04-18
Thanks. I actually ended up using a deb:

[http://www.getdeb.net/release.php?id=2374]("http://www.getdeb.net/release.php?id=2374")

---

### Post by newb1e on 2008-04-18
> **webaake said:**
> Check in synaptic for something like;
libstartup-notification-dev-xxx.

Hope it helps...

thank:)
This new version is much better than the one I had before:popcorn:
Although I miss the drag & drop on desktop (drag & drop among tabs is fine)
Can it display icons (not thumbnails) of image files? I don't really need that, just want to know:)
And can it show hidden files:confused:

PS: uhm, and how can I update the wallpaper?:confused:

---

### Post by eriqjaffe on 2008-04-18
> **newb1e said:**
> And can it show hidden files:confused:Hidden files can be shown by pressing CTRL-H.

---

