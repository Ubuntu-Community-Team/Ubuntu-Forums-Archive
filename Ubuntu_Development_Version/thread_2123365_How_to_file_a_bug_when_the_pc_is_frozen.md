---
title: "How to file a bug when the pc is frozen?"
date: 2013-03-07
forum: Ubuntu Development Version
---

### Post by jerrylamos on 2013-03-07
Runs along fine for 15 minutes or an hour or two then screen freezes.  Ctrl-Alt-F1 screen goes to black with a non-blinking underline at top left corner.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"
Linux Aspire1 3.8.0-11-generic #20-Ubuntu SMP Tue Mar 5 20:33:22 UTC 2013 i686 i686 i686 GNU/Linux

Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

HP 20" LED 1600x900 

Nothing in /var/crash.

Nothing useful in Xorg.0.log

.xsession-errors last two lines:

(update-notifier:1988): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed
(update-notifier:1988): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

no idea if these lines are relevant.

Any ideas or suggestions or how to file a bug when the pc is frozen solid?

Whoops, happened again this morning, browsing plus apport trying to report a bug then wham everything froze no Ctrl-Alt-F2.
.xseesion-errors:
** (gnome-screensaver:1803): WARNING **: screensaver already running in this session
(update-notifier:1990): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed
(update-notifier:1990): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(update-notifier:1990): GLib-GIO-CRITICAL **: g_mount_can_eject: assertion `G_IS_MOUNT (mount)' failed
(update-notifier:1990): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (nm-applet:1605): WARNING **: (nm-access-point.c:357):nm_access_point_connection_valid: runtime check failed: (ap_freq > 0)
(process:2194): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed

/var/crash:
whoopsie 8165002 Mar  8 08:06 _usr_bin_compiz.1000.crash

Let me see if apport can file a bug....+bug/1152605

---

### Post by jerrylamos on 2013-03-08
Whoops, 3.8.0-11 froze again.  Rebooted now in endless "logon" "enter password" loop.

Recovery mode same thing.  "enter password", enter the password, repeat.

I assume the install is screwed?

This is LTS.  Always have an LTS around....

Any clue on how to get out of this?

---

### Post by zika on 2013-03-08
> **jerrylamos said:**
> Whoops, 3.8.0-11 froze again.  Rebooted now in endless "logon" "enter password" loop.

Recovery mode same thing.  "enter password", enter the password, repeat.

I assume the install is screwed?

This is LTS.  Always have an LTS around....

Any clue on how to get out of this?
Did You try creating .xinitrc and using startx(xinit)?
Where do You get stuck?

---

### Post by dino99 on 2013-03-08
Looks like you have a mix of glibc packages (genuine+ppa), as i remember having seen a change about "g_mount_can_eject: assertion " a few days ago.

---

### Post by jerrylamos on 2013-03-08
> **zika said:**
> Did You try creating .xinitrc and using startx(xinit)?
Where do You get stuck?
I'm running along with some Firefox tabs open when suddenly the screen stops, except for cursor.

If I do a Ctrl-Alt-F2 I can log in and do a 
sudo startx
which gets me right back where I was.
I did a find on raring 3.8.0-11 for .xinitrc and didn't find any.

Ubuntu wiki says something about
sudo /etc/init.d/gdm start
I think raring is using lightdm?

I didn't get anywhere doing 
sudo service lightdm restart
or any combination of such commands.

Right now raring is stuck in login "enter password" password "enter password" password ...... ad nauseum.  BTW, it's supposed to log in automatically.

I'm doing a zsync for a re-install....it's a March 7 install updated daily since.  linux images have been changing one after another.

---

### Post by zika on 2013-03-08
> **jerrylamos said:**
> I'm running along with some Firefox tabs open when suddenly the screen stops, except for cursor.

If I do a Ctrl-Alt-F2 I can log in and do a 
sudo startx
which gets me right back where I was.
I did a find on raring 3.8.0-11 for .xinitrc and didn't find any.

Ubuntu wiki says something about
sudo /etc/init.d/gdm start
I think raring is using lightdm?

I didn't get anywhere doing 
sudo service lightdm restart
or any combination of such commands.

Right now raring is stuck in login "enter password" password "enter password" password ...... ad nauseum.  BTW, it's supposed to log in automatically.

I'm doing a zsync for a re-install....it's a March 7 install updated daily since.  linux images have been changing one after another.
startx is not supposed to be used with sudo. You've now closed the door to use it without sudo. If You want to use it without root level, erase .Xauthority in ~...
To use startx(or xinit) You have to create .xnitrc or .Xsession and put there what You want to start in X...

---

### Post by jerrylamos on 2013-03-08
> **jerrylamos said:**
> I'm running along with some Firefox tabs open when suddenly the screen stops, except for cursor.

Right now raring is stuck in login "enter password" password "enter password" password ...... ad nauseum.  BTW, it's supposed to log in automatically.

I'm doing a zsync for a re-install....it's a March 7 install updated daily since.  linux images have been changing one after another.
Something must have gotten screwed up.  Did a new zsync and a new install ran for a couple hours O.K.

---

### Post by thomassisson on 2013-04-16
Nothing here answers the original question, "How to file a bug when the pc is frozen?"

Somewhere there should be information on where or how to file a bug aside from running an application on the system containing a bug!
 
If you can answer the question, please answer it.<snip>

---

### Post by cariboo on 2013-04-16
> **thomassisson said:**
> Nothing here answers the original question, "How to file a bug when the pc is frozen?"

Somewhere there should be information on where or how to file a bug aside from running an application on the system containing a bug!
 
If you can answer the question, please answer it.<snip>

If you want an answer to your question, without discussion, this may not be the place for you. [Ask Ubuntu]("http://askubuntu.com/") is the place to go, if you have no interest in discussion.

---

