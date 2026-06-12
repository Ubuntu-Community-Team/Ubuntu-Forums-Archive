---
title: "probable bug, possible virus in Gnome on 9.10"
date: 2009-12-26
forum: Security
---

### Post by TheProphetJonah on 2009-12-26
Ok, I've gotten a lot of problems with the media players that have tracebacks to problems in gst.
So I plugged in another distro and am currently running fprot on it. Got a boatload of this in /lib/debug 
> lib/debug/usr/bin/xmlcatalog
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/panel-test-applets
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-cat
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/rhythmbox
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-copy
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/rhythmbox-client
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-info
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-ls
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-monitor
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-mkdir
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-mv
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-rm
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gnomevfs-df
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gdk-pixbuf-csource
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gtk-demo
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/nautilus
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-launch
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/nautilus-file-management-properties
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-xmllaunch
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/nautilus-autorun-software
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-xmlinspect
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/nautilus-connect-server
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/pango-querymodules
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/pango-view
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/totem
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gda-report-test-3.0
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/totem-video-thumbnailer
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/totem-video-indexer
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/totem-audio-preview
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-codec-info-0.10
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-inspect-0.10
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-launch-0.10
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-typefind-0.10
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-xmllaunch-0.10
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-xmlinspect-0.10
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-feedback
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gst-inspect
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/modutil
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gda-inspect-dict-file-3.0
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/pk12util
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/usr/bin/gda-author-dict-file-3.0
[Found possible virus] <Heuristic-90 (not disinfectable)> 

The fprot is still running, but these are, you might notice, all lumped into /usr/ib/debug and a great many of them involve gst.

One of the problems is that Ubuntu Software Center starts, then crashes in seconds. The Exaile and GMerlin media players don't launch at all.

The problem comes out as Gstreamer and gst faults. I've got the error logs for Exaile and Software Center saved on the Ubuntu installation, I'll post them as soon as I get done with fprot.Thanks for looking, and for my friends (and strangers too, it doesn't really matter) in the Commonwealth nations, Happy Boxing day.

---

### Post by TheProphetJonah on 2009-12-26
That looks simply awful, I know. I just used the gpm function and grabbed a lump of the reports on the Terminal.

There's about 300 of them total.

The last one detected is : 
[Found possible virus] <Heuristic-90 (not disinfectable)>     /media/hda4/usr/lib/debug/sbin/ldconfig.real

That was about 20 minutes ago, more or less and the program is still running..

---

### Post by TheProphetJonah on 2009-12-26
OK, final tally from fpscan...


Results:

Files: 312274
Skipped files: 0
MBR/boot sectors checked: 0
Objects scanned: 584806
Infected objects: 283
Files with errors: 5
Disinfected: 0

And as promised, a small portion of the error log from Ubuntu itself. Note that it starts with two networking alarms. One repetitive from Firefox and one from Evolution.

> evolution-alarm-notify-Message:  Fri Dec 25 17:00:00 2009

Torbutton logger online
[12-26 02:30:11] Torbutton NOTE: Skipping no location: chrome://browser/content/browser.xul
[12-26 02:30:16] Torbutton NOTE: Conflict between noncrashed and normal_exit states.. Assuming crash but no session restore..
[12-26 02:30:16] Torbutton NOTE: Crash detected, attempting recovery
[12-26 02:30:16] Torbutton NOTE: Restoring cookie status
[12-26 02:30:16] Torbutton NOTE: Loading non-tor jar after crash
[12-26 02:30:17] Torbutton NOTE: Restoring tor state
Torbutton logger online
[12-26 02:32:24] Torbutton NOTE: Skipping no location: chrome://browser/content/browser.xul
[12-26 02:32:29] Torbutton NOTE: Conflict between noncrashed and normal_exit states.. Assuming crash but no session restore..
[12-26 02:32:29] Torbutton NOTE: Crash detected, attempting recovery
[12-26 02:32:29] Torbutton NOTE: Restoring cookie status
[12-26 02:32:29] Torbutton NOTE: Loading non-tor jar after crash
[12-26 02:32:30] Torbutton NOTE: Restoring tor state
Torbutton logger online
[12-26 03:20:47] Torbutton NOTE: Skipping no location: chrome://browser/content/browser.xul
[12-26 03:20:52] Torbutton NOTE: Conflict between noncrashed and normal_exit states.. Assuming crash but no session restore..
[12-26 03:20:52] Torbutton NOTE: Crash detected, attempting recovery
[12-26 03:20:52] Torbutton NOTE: Restoring cookie status
[12-26 03:20:52] Torbutton NOTE: Loading non-tor jar after crash
[12-26 03:20:53] Torbutton NOTE: Restoring tor state
INFO    : Loading Exaile 0.3.0.1...
INFO    : Loading settings...
Traceback (most recent call last):
  File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 53, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 90, in __init__
    self.__init()
  File "/usr/lib/exaile/xl/main.py", line 116, in __init
    self.__show_splash()
  File "/usr/lib/exaile/xl/main.py", line 241, in __show_splash
    import xlgui
  File "/usr/lib/exaile/xlgui/__init__.py", line 46, in <module>
    from xlgui import devices, guiutil, icons, prefs, queue
  File "/usr/lib/exaile/xlgui/prefs/__init__.py", line 46, in <module>
    from xlgui.prefs import playlists_prefs, osd_prefs
  File "/usr/lib/exaile/xlgui/prefs/osd_prefs.py", line 42, in <module>
    from xlgui import osd
  File "/usr/lib/exaile/xlgui/osd.py", line 31, in <module>
    from xlgui.main import PlaybackProgressBar
  File "/usr/lib/exaile/xlgui/main.py", line 31, in <module>
    import gst, logging
  File "/usr/lib/python2.6/dist-packages/gst-0.10/gst/__init__.py", line 193, in <module>
    from _gst import *
RuntimeError: can't initialize module gst: Error re-scanning registry , child terminated by signal

(software-center:4013): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:4013): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:4013): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:4013): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:4013): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:4013): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:4013): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:4013): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:4013): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:4013): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:4013): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:4013): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:4013): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:4013): GStreamer-WARNING **: adding type gint multiple times

(software-center:4013): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:4013): GStreamer-WARNING **: adding type glong multiple times

(software-center:4013): GStreamer-WARNING **: adding type guint multiple times

(software-center:4013): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:4013): GStreamer-WARNING **: adding type gulong multiple times
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by infinitejones on 2009-12-26
I often find that googling error messages works wonders, so I googled some of yours and this is what I found:

Googling [gstreamer "adding type" "multiple times"]("http://www.google.com.au/search?q=gstreamer+%22adding+type%22+%22multiple+times%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") gives this link: [http://answers.launchpad.net/ubuntu/+source/software-center/+question/92521]("http://answers.launchpad.net/ubuntu/+source/software-center/+question/92521"), which looks like a solved bug so I'd suggest scrolling down to the posts from 2009-12-04 and trying what they're suggesting.

Googling ["can't initialize module gst: Error re-scanning registry , child terminated by signal"]("http://www.google.com.au/search?q=%22can%27t+initialize+module+gst%3A+Error+re-scanning+registry+%2C+child+terminated+by+signal%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a") bring us to this Ubuntu Forums posting: [URL="http://ubuntuforums.org/showthread.php?t=705533"]
http://ubuntuforums.org/showthread.php?t=705533[/URL], which also discusses a few possible solutions.

So I'd say it's some kind of already-known bug (or a combination of bugs) rather than a virus, because as we all know, [for all practical purposes Linux (of which Ubuntu is a subset) can't get infected by a virus]("http://www.gnu.org/fun/jokes/evilmalware.html"). I'd say it's much more likely that F-Prot is throwing false positives.

Try the solutions discussed in the links I posted and let us know how you get on!

---

### Post by TheProphetJonah on 2009-12-27
OK I did the first suggested one, [from the Gnome app-install issue]("http://ubuntuforums.org/showthread.php?t=705533"). (more than 18 months old and archived) > sudo -s
apt-get remove gnome-app-install
and got 
> Building dependency tree       
Reading state information... Done
Package gnome-app-install is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 kdevelop-data libflac++6 festlex-cmu festlex-poslex
  festvox-kallpc16k libsvnqt6 festival linux-headers-2.6.31-14-generic
  libestools1.2 lcov
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
root@figpucker:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  festival festlex-cmu festlex-poslex festvox-kallpc16k kdevelop-data lcov
  libestools1.2 libflac++6 libsvnqt6 linux-headers-2.6.31-14
  linux-headers-2.6.31-14-generic
0 upgraded, 0 newly installed, 11 to remove and 32 not upgraded.
After this operation, 104MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 344982 files and directories currently installed.)
Removing festvox-kallpc16k ...
Removing festlex-poslex ...
Removing festlex-cmu ...
Removing festival ...
Removing kdevelop-data ...
Removing lcov ...
Removing libestools1.2 ...
Removing libflac++6 ...
Removing libsvnqt6 ...
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@figpucker:~# 


So I would assume that the software-center app was renamed somewhere in the past 2 years.

I'll do the other apt-get procedures and see what happens next. 

I sort of figured it wasn't a virus, although f-prot reacted to them. Probably just had something to do with the 2.6.31-14 kernel headers being in the wrong place.(as in, still installed) I also ran chkrootkit and got exactly nothing wrong on that. 

I DID pick up a rootkit once, just before installing Ubuntu, on a Puppy distribution. Which has no passwords. Big security issue there. So I know from experience that not all malware is "virus" but (importantly) it sure is as destructive as a virus.
I also have no problems at all vis-a-vis browsing and networking. THE big bad boy Trojan that's going around is one that puts up a fake Windows Security Update notice, runs a fake scan while encrypting all your files, then charges you $50 yankee money to get your files back. AND I'm actually getting a few jobs out of it, people paying to have it scrubbed off their drives. I charge like not even a days pay, and make allowances for the fact that people don't have much money anymore. They don't always hit the rich folks with it.

That also isn't a virus, so I simplify when I'm talking to DOS addicts.
There's been reports that it has hit Mac and Linux systems, but all it does on any *nix filesystem is make the user laugh at a WinPopup appearing on your screen claiming to be from Microsux.
So far, so good.

One of the first suggestions in the linked-in thread was to check Python to see if it's installed right. Which, there's some Python games I tried to get to run, installed them off Software Center, no go. I'll check that part later too.

---

### Post by rookcifer on 2009-12-27
I don't know why people even waste their time with rootkit scanners.  The whole notion that a scanner can defeat an attacker who has root access to the machine is ludicrous.  The scanner itself can be altered by the attacker.  He can manipulate it so that it will return a clean bill of health.  

If you want a better way to detect any unauthorized changes, then you should use an IDS like AIDE.  Or better yet, don't have your box cracked in the first place.

---

### Post by TheProphetJonah on 2009-12-27
Still, naught. Since it's more annoyance than danger and really frustrating when I try anything I only do it in fits and starts. It is a comfort to realize that it's a bug and not malware. And that other people, more skilled than myself, are debugging it.

As for rootkits, that's the pure beauty of starting from a CD. Since, as you pointed out, there's no such thing as a trusted partition.
Plus when fighting a determined enemy, it makes sense to use every tool available.

Especially the free ones.

When I do the scans I always start with Microsoft partitions, too. By now, that's a reflex.

I tell my customers that Windows itself is a virus.:P

There's far worse dangers now. Like a computer you can lose in your pocket. There was a story on NBC the other day of a woman whose iPhone was stolen and had all her business transactions and information on it.

---

### Post by judge jankum on 2009-12-27
Someone would almost need hand trucks to get one of my old dinosaurs lol"

---

