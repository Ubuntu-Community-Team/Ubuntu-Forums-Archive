---
title: "Failed to open gnome control center"
date: 2012-11-22
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2012-11-22
After installing the latest updates, I cannot open system settings.

```
serdotlinecho@raring:~$ gnome-control-center
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.

(gnome-control-center:2479): Gtk-WARNING **: GtkAspectFrame does not have a property called position

(gnome-control-center:2479): Gtk-WARNING **: GtkToolItem does not have a property called expand

(gnome-control-center:2479): Gtk-WARNING **: GtkToolItem does not have a property called homogeneous

(gnome-control-center:2479): Gtk-WARNING **: GtkToolbar does not have a property called position

(gnome-control-center:2479): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(gnome-control-center:2479): Gtk-WARNING **: GtkToolbar does not have a property called position

** (gnome-control-center:2479): CRITICAL **: Could not build interface: Error on line 160 char 13: Element 'interface' was closed, but the currently open element is 'child'

(gnome-control-center:2479): Gtk-CRITICAL **: gtk_window_set_application: assertion `GTK_IS_WINDOW (window)' failed

(gnome-control-center:2479): Gtk-CRITICAL **: gtk_bin_get_child: assertion `GTK_IS_BIN (bin)' failed

(gnome-control-center:2479): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-control-center:2479): Gtk-CRITICAL **: gtk_window_present_with_time: assertion `GTK_IS_WINDOW (window)' failed
```

---

### Post by dino99 on 2012-11-22
sudo rm ~/.fonts.conf

.fonfs.conf is gone now on RR, replaced by /fontconfig and .fontconfig.

---

### Post by zika on 2012-11-22
> **dino99 said:**
> sudo rm ~/.fonts.conf

then logout/in, the system will recreate a clean .fonts.conf file
Same here.
I do not think I have ~/.fonts.conf, at least I can not see it...
I've had it on prevoius install that was OO upgraded through time to RR...
Anyhow, SystemSettings are not working with same error:
```
:~$ gnome-control-center 

(gnome-control-center:23479): Gtk-WARNING **: GtkAspectFrame does not have a property called position

(gnome-control-center:23479): Gtk-WARNING **: GtkToolItem does not have a property called expand

(gnome-control-center:23479): Gtk-WARNING **: GtkToolItem does not have a property called homogeneous

(gnome-control-center:23479): Gtk-WARNING **: GtkToolbar does not have a property called position

(gnome-control-center:23479): Gtk-CRITICAL **: gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(gnome-control-center:23479): Gtk-WARNING **: GtkToolbar does not have a property called position

** (gnome-control-center:23479): CRITICAL **: Could not build interface: Error on line 160 char 13: Element 'interface' was closed, but the currently open element is 'child'

(gnome-control-center:23479): Gtk-CRITICAL **: gtk_window_set_application: assertion `GTK_IS_WINDOW (window)' failed

(gnome-control-center:23479): Gtk-CRITICAL **: gtk_bin_get_child: assertion `GTK_IS_BIN (bin)' failed

(gnome-control-center:23479): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-control-center:23479): Gtk-CRITICAL **: gtk_window_present_with_time: assertion `GTK_IS_WINDOW (window)' failed
```

---

### Post by dino99 on 2012-11-22
My  bad, i've answered without browsing the actual folders; of course, .fonfs.conf is gone now on RR, replaced by /fontconfig and .fontconfig.

But i've not your issue on i386 with "proposed" repo activated. Maybe you need to clean old packages/libs/settings (orphans)

---

### Post by zika on 2012-11-22
> **dino99 said:**
> My  bad, i've answered without browsing the actual folders; of course, .fonfs.conf is gone now on RR, replaced by /fontconfig and .fontconfig.

But i've not your issue on i386 with "proposed" repo activated. Maybe you need to clean old packages/libs/settings (orphans)amd_64 here...
If I understood You right, that is done...
The only thing that's left is to try to upgrade to &#8222;proposed&#8220;...
Yes, there is a new gnome-control-center there...
I'll plunge... See You later... ;) Or not... ;)
Bingo, it worked... Thank You...

See also:
[http://ubuntuforums.org/showpost.php?p=12367708&postcount=11](http://ubuntuforums.org/showpost.php?p=12367708&postcount=11)
[http://www.iloveubuntu.net/gnome-control-center-unity-10-landed-ubuntu-1304-non-default](http://www.iloveubuntu.net/gnome-control-center-unity-10-landed-ubuntu-1304-non-default)

---

### Post by jbicha on 2012-11-22
That was fixed with [https://launchpad.net/ubuntu/+source/gnome-control-center/1:3.6.3-0ubuntu4](https://launchpad.net/ubuntu/+source/gnome-control-center/1:3.6.3-0ubuntu4)

And you don't need to use -proposed to get the update.

---

### Post by zika on 2012-11-22
> **jbicha said:**
> That was fixed with [https://launchpad.net/ubuntu/+source/gnome-control-center/1:3.6.3-0ubuntu4](https://launchpad.net/ubuntu/+source/gnome-control-center/1:3.6.3-0ubuntu4)

And you don't need to use -proposed to get the update.It did not come up before I turned proposed on... That is as much as I know... Maybe I was impatient too much, I needed GCC to change some power settings...
As I installed in the meantime gnome-control-center-unuty it is only rhetorical now...

---

### Post by serdotlinecho on 2012-11-22
Doesn't look right to me on my netbook, this new gnome-control-center-unity...

---

### Post by serdotlinecho on 2012-11-23
After installing the latest patch :)

---

### Post by jerrylamos on 2012-11-23
systems settings crashed.  I was trying to start network to connect to hidden wireless WPA secured net.

The preceding replies mention updates which of course won't work because I can't get the internet up because systems settings crashed.

So I tried a 3.7.0-0 to try to report the crash.  Apport crashed, and apport couldn't report an apport crash.

If the only way to get the systems settings bug fixed is updating which requires network running I'm SOL until someone reports the daily build has the fix and I try a new install.

Unless someone has a magic way to start "network" without selecting "system settings" first.  My cli skills on network were never vary good and are now totally rusty.  Maybe someone can help?

---

### Post by ronacc on 2012-11-23
try clicking the network indicator in the top bar it goes directly to network settings. It may not work since it seems to be part of system settings , worth a try though .

---

### Post by serdotlinecho on 2012-11-23
First, you need to know your network interface

```
ifconfig -a
or 
ip address show
```Let's say your interface is wlan0, do some scanning for available wireless network

```
sudo iwlist wlan0 scan
```To connect, try this

```
sudo iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY
```

NETWORK_ID is name of network, And WIRELESS_KEY is the key

then,

```
sudo dhclient wlan0
```

---

### Post by jbicha on 2012-11-23
> **serdotlinecho said:**
> Doesn't look right to me on my netbook, this new gnome-control-center-unity...

What doesn't look right? It has some code to adapt to display better on small screens.

---

### Post by serdotlinecho on 2012-11-23
> What doesn't look right? It has some code to adapt to display better on small screens.All is fine now after latest dist-upgrade. Previously, when I open Appearance, i cannot see Launcher icon size settings(on a netbook). Please look at my attachment on previous post, you will know what i mean>[http://ubuntuforums.org/attachment.php?attachmentid=227583&d=1353640823](http://ubuntuforums.org/attachment.php?attachmentid=227583&d=1353640823)

---

