---
title: "How to make SystemsSettings remeber that RecordActivity should be off?"
date: 2012-12-10
forum: Ubuntu Development Version
---

### Post by zika on 2012-12-10
As above: If I go to SystemSettings>Privacy, toggle Record Activity to off, exit, it should remeber that... Yes?
Well, it does not...
It is like a faulty switch for light in refrigerator, You can check only if You open it...
Well, OK, I found out that it does not by having history in Dash... OK...
To emphasize: I do not ask this because I'm privacy freak, I'm performance freak...

---

### Post by ventrical on 2012-12-10
Iv'e had it off for over a month now. It remembers it here.

Is that what you mean?

---

### Post by ventrical on 2012-12-10
> **zika said:**
> As above: If I go to SystemSettings>Privacy, toggle Record Activity to off, exit, it should remeber that... Yes?
Well, it does not...
It is like a faulty switch for light in refrigerator, You can check only if You open it...
Well, OK, I found out that it does not by having history in Dash... OK...
To emphasize: I do not ask this because I'm privacy freak, I'm performance freak...


Ahhhh .. ok .. gotchya.. sort of like an infinite loop or a shorted switch.

---

### Post by mc4man on 2012-12-10
Works fine here - off is off & stays that way
As far as any history in Dash you have to clear it all or previous will be retained

---

### Post by zika on 2012-12-10
> **mc4man said:**
> Works fine here - off is off & stays that way
As far as any history in Dash you have to clear it all or previous will be retainedKnow that. Cleared all, hecked if empty, tried switch for a couple of dozens of times before I've wrote my post...

---

### Post by mc4man on 2012-12-10
> **zika said:**
> Know that. Cleared all, hecked if empty, tried switch for a couple of dozens of times before I've wrote my post...
Nothing came back here till a restart, then re-activated as you've stated, sounds like a bug, what source not sure
(may take a look at the glib schemas & or overrides

Edit: -re-did with remove all history, disable, delete the complete ~/.local/share/zeitgeist folder
seems to still not show any recent in apps & file lens thru some restarts & log out/ins

Would I be surprised if it showed up again as enabled at some point - no

---

### Post by ventrical on 2012-12-10
Wow .. this is really weird.. FireFox now does not remember that I have read these posts so when I go to the main forum the topic header is still highlighted.

lol :)

---

### Post by zika on 2012-12-11
[https://bugs.launchpad.net/ubuntu/+bug/1088885](https://bugs.launchpad.net/ubuntu/+bug/1088885)

---

### Post by dino99 on 2012-12-11
Ubuntu Privacy, Thats a joke : as everywhere, all is recorded/shared via multiple tools such whoopie/zeitgeist localy but also sent to canonical (known) and NSA/... to know what you have read/seen/send/think/....

Even if you think to be safe via custom debconf settings (official propaganda), the best way to be safe is to drop all the modern communating tools (phone/pc/...) and only use a pencil  :)

[https://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do](https://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do)

---

### Post by zika on 2012-12-11
> **dino99 said:**
> Ubuntu Privacy, Thats a joke : as everywhere, all is recorded/shared via multiple tools such whoopie/zeitgeist localy but also sent to canonical (known) and NSA/... to know what you have read/seen/send/think/....

Even if you think to be safe via custom debconf settings (official propaganda), the best way to be safe is to drop all the modern communating tools (phone/pc/...) and only use a pencil  :)

[https://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do](https://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do)All mentioned are turned off... To write it again: I'm a speed-freak not a privacy-freak (paranoia-type)... I do not mind so much about privacy, but... I do not want to search that database over and over again...

---

### Post by zika on 2012-12-12
Judging by the Launchpad bug I mentioned above, I'm the only one having this &#8222;problem&#8220;...
I'll investigate further to see if I could be to blame...

---

### Post by mc4man on 2012-12-12
From the other day (actually 2) it did return after a cold restart. 
Since then hasn't, the setting has held after doing the same with one add.
disable in SS, disable online, clear history
edit .desktop -  
sudo nano /usr/share/applications/activity-log-manager-ccpanel.desktop
change to  StartupNotify=false

---

### Post by zika on 2012-12-12
> **mc4man said:**
> From the other day (actually 2) it did return after a cold restart. 
Since then hasn't, the setting has held after doing the same with one add.
disable in SS, disable online, clear history
edit .desktop -  
sudo nano /usr/share/applications/activity-log-manager-ccpanel.desktop
change to  StartupNotify=false
That did not work but You've gave me clue how to prove and illustrate what is happening here at my place:
```
:~$ gnome-control-center activity-log-manager

(gnome-control-center:1686): gnome-control-center-unity-WARNING **: testing load

** (gnome-control-center:1686): CRITICAL **: file blacklist-dbus.c: line 772: uncaught error: Error calling StartServiceByName for org.gnome.zeitgeist.Engine: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/zeitgeist-daemon exited with status 21 (g-dbus-error-quark, 25)

(gnome-control-center:1686): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed

** (gnome-control-center:1686): CRITICAL **: alm_files_widget_construct: assertion `blacklist_interface != NULL' failed

(gnome-control-center:1686): GLib-GObject-CRITICAL **: g_object_ref_sink: assertion `G_IS_OBJECT (object)' failed

(gnome-control-center:1686): Gtk-CRITICAL **: gtk_notebook_append_page: assertion `GTK_IS_WIDGET (child)' failed

** (gnome-control-center:1686): CRITICAL **: alm_applications_widget_construct: assertion `blacklist_inter != NULL' failed

(gnome-control-center:1686): GLib-GObject-CRITICAL **: g_object_ref_sink: assertion `G_IS_OBJECT (object)' failed

(gnome-control-center:1686): Gtk-CRITICAL **: gtk_notebook_append_page: assertion `GTK_IS_WIDGET (child)' failed

** (gnome-control-center:1686): CRITICAL **: alm_blacklist_get_incognito: assertion `self != NULL' failed

(gnome-control-center:1686): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-control-center:1686): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-control-center:1686): LibZeitgeist-CRITICAL **: Failed to create proxy for Zeitgeist daemon: Error calling StartServiceByName for org.gnome.zeitgeist.Engine: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/bin/zeitgeist-daemon exited with status 21

** (gnome-control-center:1686): CRITICAL **: alm_blacklist_get_incognito: assertion `self != NULL' failed

** (gnome-control-center:1686): CRITICAL **: alm_blacklist_set_incognito: assertion `self != NULL' failed
```

Now I have to findthat setting alm_blacklist_get_incognito and ...

---

### Post by mc4man on 2012-12-12
Here that command comes up relatively clean 
```
~$ gnome-control-center activity-log-manager

(gnome-control-center:3255): gnome-control-center-unity-WARNING **: testing load

(gnome-control-center:3255): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed

```
Then the panel shows still disabled, ect.

---

### Post by VinDSL on 2012-12-12
> **mc4man said:**
> Here that command comes up relatively clean 
```
~$ gnome-control-center activity-log-manager

(gnome-control-center:3255): gnome-control-center-unity-WARNING **: testing load

(gnome-control-center:3255): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed

```
Then the panel shows still disabled, ect.
I get the same dialog...
```
vindsl@Zuul:~$ gnome-control-center activity-log-manager

(gnome-control-center:494): gnome-control-center-unity-WARNING **: testing load

(gnome-control-center:494): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed

```
But, the panel always shows "Record Activity" is enabled, every time I check...

---

### Post by mc4man on 2012-12-13
> **VinDSL said:**
> I get the same dialog...
```
vindsl@Zuul:~$ gnome-control-center activity-log-manager

(gnome-control-center:494): gnome-control-center-unity-WARNING **: testing load

(gnome-control-center:494): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed

```
But, the panel always shows "Record Activity" is enabled, every time I check...
While I'm going to re-enable soon staying off here with nothing showing in the files lens other than default folders.
Don't think there is is reason it's staying disabled other than that's what it's supposed to do..

(did make me aware of yet another nautilus focus issue - default folders opened from files lens open behind FF & gnome-terminal, unity only

---

### Post by zika on 2012-12-13
> **VinDSL said:**
> I get the same dialog...
```
vindsl@Zuul:~$ gnome-control-center activity-log-manager

(gnome-control-center:494): gnome-control-center-unity-WARNING **: testing load

(gnome-control-center:494): Gtk-CRITICAL **: gtk_box_pack: assertion `gtk_widget_get_parent (child) == NULL' failed

```But, the panel always shows "Record Activity" is enabled, every time I check...Now You're talking... I'm not alone. Go and check the bug report given above ...

---

### Post by zika on 2012-12-13
> **mc4man said:**
> While I'm going to re-enable soon staying off here with nothing showing in the files lens other than default folders.
Don't think there is is reason it's staying disabled other than that's what it's supposed to do..

(did make me aware of yet another nautilus focus issue - default folders opened from files lens open behind FF & gnome-terminal, unity onlySame here...

---

### Post by zika on 2013-01-28
Still no way of making &#8222;RecordActivity>Off&#8220; stick...
Still light in refrigirator on all the time... ;)

---

### Post by manishtech on 2013-06-07
Looks like I found the issue. Due to some weird-ass reason, the application was crashing the daemon to which it connected to. Or maybe the daemon crashes long back before the app started
I reported the bug upstream too

[https://bugs.freedesktop.org/show_bug.cgi?id=65491](https://bugs.freedesktop.org/show_bug.cgi?id=65491)

---

### Post by VinDSL on 2013-06-07
> **manishtech said:**
> I reported the bug upstream [...]
Thanks!

This issue is becoming increasing more important, as time goes by...

EXTRA CREDIT READING:  [http://www.guardian.co.uk/world/2013/jun/06/us-tech-giants-nsa-data](http://www.guardian.co.uk/world/2013/jun/06/us-tech-giants-nsa-data)

---

