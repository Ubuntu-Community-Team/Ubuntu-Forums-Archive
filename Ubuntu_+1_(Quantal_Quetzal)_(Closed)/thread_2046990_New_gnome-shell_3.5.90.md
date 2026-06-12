---
title: "New gnome-shell_3.5.90"
date: 2012-08-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-24
Just noticed gnome-shell_3.5.90 is available from the Gnome-Shell Testing PPA.
However, that version is build against gdm.
Also I found this eplanation:

> === GNOME-Shell 3.5.90+ / Gdm 3.5.90+ ===
Make sure you are actually runing Gdm 3.5.5+ while using this newer Shell version.
Gdm is a runtime dependency as well. Running it with Lightdm or Kdm will give you an incomplete or even broken experience!

So, it may take a while until gnome-shell is upgraded into 3.5.90 in QQ repos.

---

### Post by Harry33 on 2012-08-31
Will gnome-shell_3.5.90 ever be uploaded into QQ official repos (universe)?
New gnome-shell needs new gdm too.
But we already have gdm_3.5.90 in QQ repos (also in universe) now.
And gdm depends on gnome-shell.

---

### Post by jbicha on 2012-08-31
Harry, the problem is that GNOME Shell just doesn't depend on gdm, but depends on gdm being the default display manager, and there's no good way to enforce that. It affects other distros but it's far more obvious on Ubuntu where every image uses lightdm now.

I've opened a [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=683060") about this regression. I'm hesitant to upload gnome-shell 3.5.90 to Ubuntu (or even the GNOME3 PPA) until the bug is resolved.

---

### Post by Harry33 on 2012-08-31
> **jbicha said:**
> Harry, the problem is that GNOME Shell just doesn't depend on gdm, but depends on gdm being the default display manager, and there's no good way to enforce that. It affects other distros but it's far more obvious on Ubuntu where every image uses lightdm now.

I've opened a [bug]("https://bugzilla.gnome.org/show_bug.cgi?id=683060") about this regression. I'm hesitant to upload gnome-shell 3.5.90 to Ubuntu (or even the GNOME3 PPA) until the bug is resolved.

Thank you Jeremy for this explanation.

---

### Post by Starks on 2012-08-31
3.5.90 is on Rico's PPA. The new tray is sexy.

---

### Post by Harry33 on 2012-09-01
> **Starks said:**
> 3.5.90 is on Rico's PPA. The new tray is sexy.
  
You have gdm installed for sure, but do you still use lightdm as default?

---

### Post by 3vi1 on 2012-09-01
Jasper's comments in that thread don't look promising.

For a desktop that appears to be bleeding user-share at an incredible rate, you'd think they'd try to make it easier for non-gnome3-hardcore to use their desktop.  Maybe this is an attempt to try to lock people into GDM?  :confused:

---

### Post by jerrylamos on 2012-09-01
Gnome shell didn't run for me with lightdm.  Kinda screwed up by then so I just re-installed Ubuntu, gdm, gnome shell.

For me gnome shell uses 2 horizontal lines on my 1366x768, so I use lxde which combines the 2 lines into one leaves the other line  for my applications.  Previous ubuntu I could delete the bottom panel line but didn't see how to do it with 12.10 gnome shell.

I'm not into the internals of linux, you do have a choice of gdm & gnome shell or lightdm and lxde  or xfce or kubuntu or unity or mint or whatever.

---

### Post by Harry33 on 2012-09-07
So, now we have gnome-shell 3.5.91 in QQ repos.
And, it depends on gdm, which now must be installed.

---

### Post by sgage on 2012-09-07
> **Harry33 said:**
> So, now we have gnome-shell 3.5.91 in QQ repos.
And, it depends on gdm, which now must be installed.

I went ahead and upgraded Gnome Shell, and ineed it brought in gdm. Working quite well, I must say.

---

### Post by VinDSL on 2012-09-07
> **sgage said:**
> I went ahead and upgraded Gnome Shell, and ineed it brought in gdm. Working quite well, I must say.
Interesting!

Did you select GDM as your default display manager, or LightDM?

I choose LightDM.  Unity works quite well, but GS doesn't have any panels -- just a blank desktop.


**Gnome-Shell**...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-sep-2012-1.png")[/INDENT]


**Unity**...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-sep-2012-2.png")[/INDENT]

---

### Post by jbicha on 2012-09-07
VinDSL, could you check your .xsession-errors?

Did you have gnome-shell extensions enabled before? If that's your problem, you can check with
```
dconf dump /org/gnome/shell/
```

and unenable the extensions with
```
dconf reset /org/gnome/shell/enabled-extensions
```

---

### Post by sammiev on 2012-09-07
> **VinDSL said:**
> Interesting!

Did you select GDM as your default display manager, or LightDM?

I choose LightDM.  Unity works quite well, but GS doesn't have any panels -- just a blank desktop.


**Gnome-Shell**...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-sep-2012-1.png")[/INDENT]ar. 


**Unity**...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-sep-2012-2.png")[/INDENT]

I selected LightDM on update and had no problems at all. Like the new so far, fast to say the least. :)

---

### Post by VinDSL on 2012-09-07
> **jbicha said:**
> VinDSL, could you check your .xsession-errors?
Can't see any errors, out of the ordinary. Just the usual suspects... font stuff, a Nautilus error here 'n there, nothing exciting.

> **jbicha said:**
> Did you have gnome-shell extensions enabled before? If that's your problem, you can check with
```
dconf dump /org/gnome/shell/
```
Seems like I lose all my shell extensions, ever time I update, so I gave up re-installing/re-enabling them a long time ago.  LoL!

That said, I ran the above command, and all it reported was a theme that hasn't worked, ever since when -- didn't even realize it was still installed.  

> **jbicha said:**
> and unenable the extensions with
```
dconf reset /org/gnome/shell/enabled-extensions
```
I logged into GS (in same session) after running the above, to no avail. Then, I rebooted... and still no panels.

No big deal.  I'm just curious why GS is working for others, but not for me.  It's usually the other way around.  ;)

---

### Post by sgage on 2012-09-08
> **VinDSL said:**
> Interesting!

Did you select GDM as your default display manager, or LightDM?

I choose LightDM.  Unity works quite well, but GS doesn't have any panels -- just a blank desktop.


**Gnome-Shell**...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-sep-2012-1.png")[/INDENT]


**Unity**...
[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-sep-2012-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-sep-2012-2.png")[/INDENT]

I selected gdm - the new Gnome Shell requires it not just to be installed, but to actually be running. That's why it's not working properly for you...

---

### Post by VinDSL on 2012-09-08
> **sgage said:**
> I selected gdm - the new Gnome Shell requires it not just to be installed, but to actually be running. That's why it's not working properly for you...
Okay, tried it.  Nothing.  No difference.

The GDM login screen looks more pleasant, these days.  Last time I used it, it looked like Gnome 2.

Here's my GS dump...

```
vindsl@Zuul:~$ dconf dump /org/gnome/shell/
[/]
command-history=['r']
favorite-apps=['chromium-browser.desktop', 'firefox.desktop', 'thunderbird.desktop', 'opera-next-browser.desktop', 'synaptic.desktop', 'nautilus.desktop', 'gnome-terminal.desktop', 'banshee.desktop', 'guayadeque.desktop']
saved-session-presence=0

[extensions/user-theme]
name='GnomishBeige'

[overrides]
button-layout=':minimize,maximize,close'
```

Doesn't look like that's the prob.

Hrm...

Oh, well, this too shall pass.

---

### Post by sgage on 2012-09-08
> **VinDSL said:**
> Okay, tried it.  Nothing.  No difference.

The GDM login screen looks more pleasant, these days.  Last time I used it, it looked like Gnome 2.

Here's my GS dump...

```
vindsl@Zuul:~$ dconf dump /org/gnome/shell/
[/]
command-history=['r']
favorite-apps=['chromium-browser.desktop', 'firefox.desktop', 'thunderbird.desktop', 'opera-next-browser.desktop', 'synaptic.desktop', 'nautilus.desktop', 'gnome-terminal.desktop', 'banshee.desktop', 'guayadeque.desktop']
saved-session-presence=0

[extensions/user-theme]
name='GnomishBeige'

[overrides]
button-layout=':minimize,maximize,close'
```

Doesn't look like that's the prob.

Hrm...

Oh, well, this too shall pass.

Sometimes deleting ~/.local/share/gnome-shell gets things working again...

---

### Post by Harry33 on 2012-09-08
> **VinDSL said:**
> Okay, tried it.  Nothing.  No difference.
The GDM login screen looks more pleasant, these days.  Last time I used it, it looked like Gnome 2.
....


Well VinDSL, we have here the same issue.
Gnome-shell_3.5.91 is not working here either: no panels, just the background.

Here is how I did it.

First I had a fully working GS_3.5.4 with LightDM. No issues.
Then I installed Gdm_3.5.91 and chose Gdm as default DM and then purged LightDM.
Still, no problems, everything works fine.
Gdm has a small and nice black login screen in the center of the desktop.

Then I upgraded GS_3.5.4 to 3.5.91.
Now, the Gdm login screen is grey and it fills the entire desktop.
And GS has no panels.

After rebooting I am able to open the Gnome Classic DE and downgrade to GS_3.5.4 and everything is working again.


It may be GS_3.5.91 needs to have a certain package installed (compared to 3.5.4), even it does not depend on it. And I do not have it.

---

### Post by pressureman on 2012-09-08
I'm running a fully up to date quantal (GS 3.5.91), with no GS PPAs configured, and it seems to be working ok here. I saw GDM get pulled in as a dependency, but I opted to keep using lightdm. Log in is fine, however screen lock doesn't work - the error message "cannot connect to GDM; screen lock disabled" pops up. The "screensaver" does work however, showing the date and time (which looks quite nice).

---

### Post by sgage on 2012-09-08
> **pressureman said:**
> I'm running a fully up to date quantal (GS 3.5.91), with no GS PPAs configured, and it seems to be working ok here. I saw GDM get pulled in as a dependency, but I opted to keep using lightdm. Log in is fine, however screen lock doesn't work - the error message "cannot connect to GDM; screen lock disabled" pops up. The "screensaver" does work however, showing the date and time (which looks quite nice).

How do you turn on the screensaver?

---

### Post by paul_in_london on 2012-09-08
Just tried this out ( don't often log into GS).

Was able to start a GS session from lightdm, but almost nothing worked.

The screen would start to darken almost instantly and then remain dark until I moved the mouse. I could start a terminal by clicking on the icon, but then I couldn't give the terminal window focus. Similarly, I could start system settings, but after the settings window appeared clicking on any of the icons did nothing.

Ok I thought - maybe it's something to do with this apparent dependency on gdm (which is annoying because I prefer to use lightdm). So I changed my default display manager to gdm, but this made no difference - same behaviour when the GS session was launched from gdm. Weird.

```
paul@quantal-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.5.91+git20120907.c866b0db-0ubuntu1~12.10~ricotz0
  Candidate: 3.5.91+git20120907.c866b0db-0ubuntu1~12.10~ricotz0
  Version table:
 *** 3.5.91+git20120907.c866b0db-0ubuntu1~12.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     3.5.91-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
paul@quantal-64:~$
```

```
paul@quantal-64:~$ cat .xsession-errors.old                                                                                                                                                                                                   
org.gtk.vfs.MountTracker.listMountableInfo call failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker (g-dbus-error-quark, 19)
p11-kit: duplicate configured module: gnome-keyring.module: /usr/lib/x86_64-linux-gnu/pkcs11/gnome-keyring-pkcs11.so

(gnome-settings-daemon:4753): color-plugin-WARNING **: There is no colord server available

(gnome-panel:4774): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion `accelerator != NULL' failed

** (gnome-panel:4774): WARNING **: Unable to parse mouse modifier '(null)'


(gnome-panel:4774): Gtk-CRITICAL **: gtk_accelerator_parse_with_keycode: assertion `accelerator != NULL' failed

** (gnome-panel:4774): WARNING **: Unable to parse mouse modifier '(null)'

Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

(gnome-panel:4774): Gtk-WARNING **: no parent (nil) is not realized but child GtkPlug 0xfc52b0 is realized
gnome-session[4686]: WARNING: Application 'gnome-panel.desktop' killed by signal 11
gnome-session[4686]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
gnome-session[4686]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed

(gnome-sound-applet:4790): Gdk-CRITICAL **: gdk_error_trap_pop_internal: assertion `trap != NULL' failed

(gnome-settings-daemon:4753): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-settings-daemon:4753): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-sound-applet:4790): Gdk-WARNING **: gnome-sound-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:4784): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

gm-notify: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.

(gnome-screensaver:5365): Gdk-WARNING **: gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:4788): Gdk-WARNING **: nautilus: Fatal IO error 0 (Success) on X server :0.


** (zeitgeist-datahub:5364): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
paul@quantal-64:~$
```

Back to lightdm and gnome classic!

EDIT: that may not actually be the right log because I had a problem with the first gnome classic session I started after I switched back to lightdm.

---

### Post by pressureman on 2012-09-08
> **sgage said:**
> How do you turn on the screensaver?

Screensaver probably wasn't a good description. What I meant was the lock screen that appears when you leave the PC unattended for a while.

It can also be manually activated by pressing ctrl-alt-L. Except it doesn't require password to unlock, as I described in my previous post. It's more or less a slide-to-unlock.

I also found that after activating it a few times manually, I ended with a grey screen that I could not get out of.

---

### Post by sgage on 2012-09-08
> **pressureman said:**
> Screensaver probably wasn't a good description. What I meant was the lock screen that appears when you leave the PC unattended for a while.

It can also be manually activated by pressing ctrl-alt-L. Except it doesn't require password to unlock, as I described in my previous post. It's more or less a slide-to-unlock.

I also found that after activating it a few times manually, I ended with a grey screen that I could not get out of.

Aha. Just tried it - pretty slick! Mine DID require a password to unlock, even though I have lock OFF in my settings.

---

### Post by Harry33 on 2012-09-08
> **paul_in_london said:**
> Just tried this out ( don't often log into GS).

Was able to start a GS session from lightdm, but almost nothing worked.

The screen would start to darken almost instantly and then remain dark until I moved the mouse. I could start a terminal by clicking on the icon, but then I couldn't give the terminal window focus. Similarly, I could start system settings, but after the settings window appeared clicking on any of the icons did nothing.

Ok I thought - maybe it's something to do with this apparent dependency on gdm (which is annoying because I prefer to use lightdm). So I changed my default display manager to gdm, but this made no difference - same behaviour when the GS session was launched from gdm. Weird.

[CODE]paul@quantal-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.5.91+git20120907.c866b0db-0ubuntu1~12.10~ricotz0
  Candidate: 3.5.91+git20120907.c866b0db-0ubuntu1~12.10~ricotz0
  Version table:
 *** 3.5.91+git20120907.c866b0db-0ubuntu1~12.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ quantal/main amd64 
...


Right, the log is from Gnome-classic session.
Anyway, you have the newest GS git version from Ricotz Testing PPA installed.
Could you try the QQ version (3.5.91-0ubuntu1) and with the Gdm_3.5.91 (QQ version)?

---

### Post by paul_in_london on 2012-09-08
> **Harry33 said:**
> Right, the log is from Gnome-classic session.
Anyway, you have the newest GS git version from Ricotz Testing PPA installed.
Could you try the QQ version (3.5.91-0ubuntu1) and with the Gdm_3.5.91 (QQ version)?

Hi Harry,

Had some problems downgrading the packages. Anyway, now I have:

```
paul@quantal-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.5.91-0ubuntu1
  Candidate: 3.5.91-0ubuntu1
  Version table:
 *** 3.5.91-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
paul@quantal-64:~$
```

```
paul@quantal-64:~$ apt-cache policy gdm
gdm:
  Installed: 3.5.91-0ubuntu1
  Candidate: 3.5.91-0ubuntu1
  Version table:
 *** 3.5.91-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
        100 /var/lib/dpkg/status
paul@quantal-64:~$
```

Just as bad with the QQ version of GS (with GDM) I'm afraid.

Logged into VT1, deleted **.xsession-errors** and **.xsession-errors.old** to reduce confusion and rebooted back into GS. Then switched back to lightdm and rebooted into gnome classic. I now have stuff in **.xsession-errors** from the current gnome classic session, but the **.xsession-errors.old** (which should have contained stuff from the bad GS session) is empty! :(

Is the QQ version of GS working ok for you?

Part of the problem could be that these commands failed to execute correctly (the first one because I accidentally left synaptic open):

```
sudo ppa-purge ppa:ricotz/testing
sudo ppa-purge ppa:ricotz/unstable
```

so I had to downgrade gnome-shell, gnome-shell-common and gnome-tweak-tool "manually", but perhaps some other packages from those ppas should have been downgraded at the same time.

The ppa-purge commands did have the expected effect of commenting out the deb lines in the /etc/apt/sources.list.d/ricotz*quantal.list files though.

Cheers,

Paul

EDIT2: Re-enabling those two ppas to see what will be upgraded:

```
paul@quantal-64:~$ sudo aptitude full-upgrade                                                                                                                                                                                                 
The following NEW packages will be installed:
  libcogl11{a} 
The following packages will be upgraded:
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gnome-shell gnome-shell-common gnome-tweak-tool libcogl-common libcogl-pango0 
7 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,319 kB of archives. After unpacking 910 kB will be used.
Do you want to continue? [Y/n/?]
```

---

### Post by VinDSL on 2012-09-08
> **sgage said:**
> Sometimes deleting ~/.local/share/gnome-shell gets things working again...Thanks!  But, no joy...

---

### Post by mc4man on 2012-09-08
> **VinDSL said:**
> Thanks!  But, no joy...
first thing i'd try if you didn't is create a new user, log out & into it, see if Gs works there

---

### Post by VinDSL on 2012-09-09
> **mc4man said:**
> first thing i'd try if you didn't is create a new user, log out & into it, see if Gs works thereI took the easy way out.  It's a matter of priorities.

I'm in the middle of adding a new weather component to my Conky script, so I used the "Harry Hack", to save some time.  LoL!  :D

I'll revisit GS 3.5.90-1 in a few days...

> **Harry33 said:**
> Well VinDSL, we have here the same issue.
Gnome-shell_3.5.91 is not working here either: no panels, just the background.

Here is how I did it.

First I had a fully working GS_3.5.4 with LightDM. No issues.
Then I installed Gdm_3.5.91 and chose Gdm as default DM and then purged LightDM.
Still, no problems, everything works fine.
Gdm has a small and nice black login screen in the center of the desktop.

Then I upgraded GS_3.5.4 to 3.5.91.
Now, the Gdm login screen is grey and it fills the entire desktop.
And GS has no panels.

After rebooting I am able to open the Gnome Classic DE and downgrade to GS_3.5.4 and everything is working again.


It may be GS_3.5.91 needs to have a certain package installed (compared to 3.5.4), even it does not depend on it. And I do not have it.
Well, that certainly worked a treat!  ;)


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-8-sep-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-sep-2012-1.png")[/INDENT]


I'm fully updated now, except for gnome-shell/gnome-shell-common 3.5.4-0ubuntu2.  Plus, I purged LightDM.

GS is working great now (and Unity & LXDE).

Thanks, everyone, for the suggestions!

---

### Post by Harry33 on 2012-09-09
> **paul_in_london said:**
> Hi Harry,

Had some problems downgrading the packages. Anyway, now I have:

...

Is the QQ version of GS working ok for you?

Part of the problem could be that these commands failed to execute correctly (the first one because I accidentally left synaptic open):

...
Cheers,

Paul

EDIT2: Re-enabling those two ppas to see what will be upgraded:

...



Well for me GS_3.5.91 does not work at all. I do not get any panels on GS desktop.
I had to downgrade to the version GS_3.5.4 to get it OK.
However, Gdm_3.5.91 is OK and fine here.

---

