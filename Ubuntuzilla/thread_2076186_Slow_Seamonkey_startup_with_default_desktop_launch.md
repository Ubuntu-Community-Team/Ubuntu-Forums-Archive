---
title: "Slow Seamonkey startup with default desktop launcher (&quot;Starting..&quot; background window)"
date: 2012-10-25
forum: Ubuntuzilla
---

### Post by chAlx on 2012-10-25
Installed seamonkey-mozilla-build_2.13.1-0ubuntu1_amd64.deb into Debian from the Ubuntuzilla repository. Ran "Mozilla Build of Seamonkey" from Applications menu.

Two new window titles appeared on taskbar: *"Seamonkey"* and *"Starting Mozilla Build of Seamonkey"*
([screenshot]("https://bug804638.bugzilla.mozilla.org/attachment.cgi?id=674256")). First is an empty navigator window, second is not switchable and has no a window frame.
Desktop became busy (watches in mouse cursor while over desktop/taskbar).
After ~15 seconds annoying not-a-window title disappeared from the taskbar and mouse cursor got normal.

Some details:

* Reproduced: always when i start Seamonkey from the Applications menu.
* I have some Seamonkey windows opened (in other desktops).
* I have the "Restore session on startup" feature turned on, and a home page for new windows. But launcher opens blank navigator.
* Launcher menu item dragged to the Gnome panel have the same behavior.
* Copied panel icon became normal after dummy command edition (added+deleted space). The command is "seamonkey %u".
* Just copied desktop icon has no panel2.d config file.
* Edited desktop icon has config file ~/.gnome2/panel2.d/default/launchers/seamonkey.desktop:

#!/usr/bin/env xdg-open

[Desktop Entry]
Encoding=UTF-8
Name=Mozilla Build of Seamonkey
GenericName=Internet Suite
Comment=Web Browser, Email/News Client, HTML Editor, IRC Client
Exec=seamonkey %u
Icon=seamonkey-mozilla-build
Terminal=false
X-MultipleArgs=false
StartupWMClass=SeaMonkey
Type=Application
Categories=Network;WebBrowser;Email;WebDevelopment;IRCClient;
Icon[en_US]=seamonkey-mozilla-build
Name[en_US]=Mozilla Build of Seamonkey
Comment[en_US]=Web Browser, Email/News Client, HTML Editor, IRC Client

* Original menu item file /usr/share/applications/seamonkey-mozilla-build.desktop:

[Desktop Entry]
Encoding=UTF-8
Name=Mozilla Build of Seamonkey
GenericName=Internet Suite
Comment=Web Browser, Email/News Client, HTML Editor, IRC Client
Exec=seamonkey %u
Icon=seamonkey-mozilla-build
Terminal=false
X-MultipleArgs=false
StartupNotify=true
StartupWMClass=SeaMonkey
Type=Application
Categories=Network;WebBrowser;Email;WebDevelopment;IRCClient;

---

### Post by nanotube on 2012-10-25
Hi,

Thank you for your detailed report.

Unfortunately, I am not able to reproduce this behavior here (running xubuntu 64bit), and I really don't know what is causing the startup delay you're describing. Maybe try terminating your already-running session, and see if the behavior persists?

Also, not sure why you mention editing the launcher file - does that fix your problem?

---

### Post by chAlx on 2012-10-26
> **nanotube said:**
> 
Thanks for reply.

The problem is rather old (several months); there were some reboots and updates after it was discovered.

Could you please compare your version of *seamonkey-mozilla-build.desktop* (or *firefox-*) with mine? May be I have an unstable mix of previous installations, upgrades and migrations.

> **nanotube said:**
> Also, not sure why you mention editing the launcher file - does that fix your problem?
Yes, that's the strange thing: then i force *.desktop* file to be created on the panel (with the same params as the menu one) the problem disappears.

---

### Post by chAlx on 2012-10-26
Here it is: when i add the original (from menu *.desktop* file) param **StartupNotify=true** to the panel file, Seamonkey starts poorly. When i remove it (e.g. by rewriting panel *.desktop* file in GUI) start success immediately.

I have a lot of other menu and panel items with Startup Notification as well as most menu items: gedit, gcalctool, meld etc. They start a way faster but with flicking "Starting gedit" window too (for less than a second). I've checked the gentoo with GNOME2: it starts applications with StartupNotify=true with the same lag.

So the problem is somewhere between Seamonkey and GNOME2. I think the XFCE desktop of Xubuntu can't reproduce a GNOME2-specific bug. Maybe MATE can.

---

### Post by nanotube on 2012-10-26
Hi
Ah, well it could be that the official mozilla 64bit build is configured without the --enable-startup-notification option... in which case maybe that's why when you set StartupNotify=true, it doesn't play nice.

StartupNotify appears essentially pretty useless. Literally the only function it appears to have is to "turn on the busy cursor and show the 'starting $thing' non-window", ([http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html)). I just tried both =true and =false here on my system, and did not see any difference, so there's probably no harm in removing the StartupNotify=true line from the default .desktop file. 

That said, i'll ask on mozilla irc and see if i can come up with any useful "expert opinion" :)

---

### Post by nanotube on 2012-10-26
I checked in about:buildconfig, as recommended on irc, and indeed the mozilla seamonkey build doesn't include the '--enable-startup-notification' option. So... we should just remove that line from the .desktop file. Never saw it cause trouble before, and it's been like this for a while. Either something in gnome changed, or something in seamonkey...

---

### Post by nanotube on 2012-10-27
By the way - would you be able to test if you see the same behavior using the mozilla builds of firefox and thunderbird as well?

---

### Post by chAlx on 2012-10-29
Wow, thanks a lot!

Now i know what it is about and able to find some historical quotes.

Launchpad [(c)]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/11462"):
> With startup notification enabled as it is now, you get a busy cursor for the first launch and everything works fine. For the second launch though, the startup notification completion message is never broadcast, so you get a stuck busy cursor (until it times out).

Bugzilla [(c)]("https://bugzilla.mozilla.org/show_bug.cgi?id=223492"):
> This patch also makes the startup-notification part disabled by default; you have to --enable-startup-notification to get it, because the resulting build will not run unless libstartup-notification is present.

There are several newer bugs ([416053]("https://bugzilla.mozilla.org/show_bug.cgi?id=416053"), [607900]("https://bugzilla.mozilla.org/show_bug.cgi?id=607900") etc) for the same issue.

I've tested other Ubuntazilla amd64 builds:

**Thunderbird**/16.0.1 has *StartupNotify=true* in .desktop files. No *--enable-startup-notification* option in buildconfig. Starts with the lag too but it seems to actually wait for control to get back (while Thunderbird reads mail archives, connects to several servers etc). Lag is not so noticeable (about 5 seconds, not 15 as of Seamonkey). But the **second run** (as described in Launchpad quote) brings the same ~15s lag!

**Firefox**/16.0.2 has *StartupNotify=true* in .desktop file. No *--enable-startup-notification* option in buildconfig. Starts without lag first and second time.

Seems that *StartupNotify* param in .desktop files should be depended on *--enable-startup-notification* build option.

---

### Post by nanotube on 2012-10-31
Hi,
Well, I've made a change in the packaging and turned off the StartupNotify option. So the latest releases of everything that I just pushed have that turned off.
Should be all working now.

Let know if that is indeed the case. :)

---

### Post by chAlx on 2012-11-29
Checked with new package *(SeaMonkey/2.14 build 20121118122904)*: no  StartupNotify in the menu file and no lag. It still starts as a  background window sometimes but AFAIK it's another problem.

Thanks!

---

### Post by nanotube on 2012-11-29
Glad it's working.
Thank you for reporting this and also for figuring out the cause! :)

---

