---
title: "Xfce 4.4.2 Out"
date: 2007-12-02
forum: The Cafe
---

### Post by Montsegur87 on 2007-12-02
[http://www.xfce.org/download/?PHPSESSID=06281ca135538bdd297538f7e4dfae19](http://www.xfce.org/download/?PHPSESSID=06281ca135538bdd297538f7e4dfae19)

CHANGELOG
```
Utilities Library (libxfce4util):
Fix applications sometimes starting on the wrong screen in multihead setups (Bug #3667).
Fix possible buffer overflow (reported by Vegard Nosum on the ml).
Remove trailing parens on AC_INIT version info to work around bug in intltool 0.35.x and 0.36.x.
Updated translations: Maximilian Schleiss (nl), Dimitri Gogelia (ka), Pablo Vieira and Jose Vitor Lopes e Silva (pt_BR).
New translations: Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Manatsawin (th), Tegegne Tefera (am), RPrieditis (lv).
Widget Library (libxfcegui4):
Fix application windows sometimes opening on the wrong screen in multihead setups (Bug #3667).
Free list returned by gtk_container_get_children().
Remove trailing parens on AC_INIT version info to work around bug in intltool 0.35.x and 0.36.x.
Allocate copy of passed cliend id, program name and working directory in session management, in case the application frees the data.
Properly deal with %-starting 'field codes' in commands from .desktop files.
Updated translations: Maximilian Schleiss (nl), Dimitri Gogelia (ka), Pablo Vieira and Jose Vitor Lopes e Silva (pt_BR).
New translations: Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Tegegne Tefera (am), Manatsawin (th), RPrieditis (lv).
Application extension library (libexo):

Please see the Thunar website for a list of changes. 
Window Manager (xfwm4):
Be more relax with transients, allow transients to be sticky independently of their parent window (Bug #3296).
Fix xfwm4 hanging with gtk+-2.11.x (Bug #3346).
Plug a leak in mouse button grab when changing theme.
Fix dialogs and modals without parents not being automatically centered like before (Bug #3278).
Fix modifier mask not working with all keymaps (Bug #3194).
Fix wrong count of key shortcuts causing switch to last workspace on modifier key press if no window is focused (Bug #3191).
Fix spec file missing from the tar ball causing 'make dist' to fail.
Fix strict bound checking causing wrong window to be focused in focus follow mouse (Bug #2781).
Transients for group shouldn't apply to other transients, or it breaks stacking for some apps, noticeably mozilla "save as" dialog...
Fix typo breaking compilation on systems without XShape 1.1 support.
Desktop Manager (xfdesktop):
Fixed the Italian xfdesktop menu causing a crash.
Fix missing xfce_rc_close() causing memleak and too many open file descriptors (Bug #3065).
Always use button 0 in gtk_menu_popup() as GTK+ 2.11+ expects the same button to be pressed or it doesn't activate the entry (Bug #3359).
Fix menu sometimes not popping up when using the keyboard shortcut, again. Timeout waiting for grab is now 0.25s (Bug #441).
Fix desktop settings only getting applied to the first screen in non-Xinerama dualhead setups (Bug #3467).
Fix spurious drag when double-clicking a volume icon that fails to mount (Bug #3426).
Clean out stale entries in icon position file (Bug #3267).
Some minor memory leak fixes (some still remain, likely).
Fix --disable-menu-editor configure option.
Panel (xfce4-panel):
Fix window manager hints reporting width 1 pixel too wide (Bug #3402).
Improve MCS plugin code.
Fix expansion of items a non-full-width panel.
Make sure tooltips are set for more than 1 clock instance (Bug #3109).
Fix area that is off-limits to other windows (_NET_WM_STRUT hints) for a Xinerama setup with differently sized monitors (Bug #3097).
Fix loading internal plugins if a similar file exists in the start directory (Bug #3279).
Only update the clock once a minute when seconds are disabled. The digital clock is also set in the default layout to minimize the amount of screen updates.
Fix possible buffer overflow in launcher tooltips (Bug #3324).
Use exo-open --launch TerminalEmulator in the default configuration (Bug #3384).
Fix crash when removing a panel in Gtk+ 2.11.x (Bug #3496).
Remove trailing parens on AC_INIT version info to work around bug in intltool 0.35.x and 0.36.x.
Updated translations: Pau Rul-lan Ferragut (ca), Fabio Riga (it), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Vincent Tunru (nl), Dimitri Gogelia (ka), Ivan Masár (sk), Fábio Nogueira (pt_BR).
New translations: Tegegne Tefera (am), RPrieditis (lv).
Settings Manager (xfce-mcs-manager):
Remove the half-second signal-check timeout in favor of a signal-check pipe that's watched by the glib main loop. Helps reduce CPU wakeups that hurt laptop battery performance.
Updated translations: Terje Uriansrud (nb_NO), European Portuguese (pt_PT), Vincent Tunru (nl), Dimitri Gogelia (ka), Ivan Masar (sk), Vladimir Melo (pt_BR), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT).
New translations: Tegegne Tefera (am), RPrieditis (lv).
Settings Manager Plugins (xfce-mcs-plugins):
Make the theme list expand for more natural resize (Bug #3659).
Font DPI is now configurable in the User Interface Settings (Bug #3164).
Fix modifier mask not working with all keymaps (Bug #3194)
Add support for xinput devices when setting left/right handed mouse.
Updated translations: Fabio Riga (it), Nuno Miguel (pt_PT), Tegegne Tefera (am), Vincent Tunru (nl), Dimitri Gogelia (ka), Vladimir Melo (ka), Alexander Nyakhaychyk (be), Jari Rahkonen (fi), Nico Schümann (de), Mike Massonnet (fr), Jeff Bailes (en_GB), Terje Uriansrud (nb_NO), Stavros Giannouris (el), Fabio Riga (it), Luiz Armesto (pt_BR), Stephan Arts (nl).
New translations: Terje Uriansrud (nb_NO), RPrieditis (lv).
Text Editor (mousepad):
Test for support of -Wall, -Werror and -errwarn=%all (Bug #2921).
Remove trailing parens on AC_INIT version info to work around bug in intltool 0.35.x and 0.36.x.
Updated translations: Maximilian Schleiss (fr), Szymon Ka&#322;asz (pl), Pau Rul-lan Ferragut (ca), Stavros Giannouris (el), ByungHyun Choi (ko), Piarres Beobide (eu), Maxim Dziumanenko (uk), Stephan Arts (nl), Nico Schümann (de), Jeff Bailes (en_GB), Daichi Kawahata (ja), Fabio Riga (it), Dimitri Gogelia (ka), Pablo Vieira (pt_BR), Og Maciel (pt_BR).
New translations: Besnik Bleta (sq), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Tegegne Tefera (am), Manatsawin (th), RPrieditis (lv).
Session Manager (xfce4-session):
Updated translations: Pau Rul-lan Ferragut (ca), Fabio Riga (it), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Tegegne Tefera (am), Vincent Tunru (nl), Ivan Masár (sk), Luiz Armesto (pt_BR).
New translations: RPrieditis (lv).
Printing Helper (xfprint):
Updated translations: Stephan Arts (nl), Fabio Riga (it), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Tegegne Tefera (am), Ivan Masár (sk), Fábio Nogueira (pt_BR).
New translations: Denizo Priskorn (eo), RPrieditis (lv).
Development Tools (xfce4-dev-tools):
Add script (xdt-commit) for generating commit messages from ChangeLogs on the fly.
Remove trailing parens on AC_INIT version info to work around bug in intltool 0.35.x and 0.36.x.
Utilities (xfce-utils):
Put back a default DPI value for Xorg (Bug #3164, Bug #3158).
Use gnome-screensaver if xscreensaver is not available (Bug #3131).
Fix typo on XDG_DATA_DIRS path definition (Bug #2967).
Updated credits in the about dialog.
Updated translations: Fabio Riga (it), Nuno Miguel (pt_PT), Dimitri Gogelia (ka), Ivan Masar (sk), Vladimir Melo (pt_BR).
New translations: Terje Uriansrud (nb_NO), Tegegne Tefera (am), RPrieditis (lv).
Volume Control (xfce4-mixer):
Fix parallel build of xfce4-mixer (Bug #2892).
Updated translations: Stephan Arts (nl), Fabio Riga (it), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Dimitri Gogelia (ka), Luiz Armesto (pt_BR).
New translations: Tegegne Tefera (am), RPrieditis (lv).
Calendar and Appointments (xfcalendar):
Recurrence not recurring at the limit date. Missing fix: convert time back to UTC when reading. Caused day to be incremented for -GMT timezones (Bug #2937).
Added missing last update time (Bug #3431).
Orage clock now wakes up only when needed. This fix sacrifies a little of accuracy to save wakeups. If seconds are not visible clock wakes up only once per minute (Bug #3363).
Updated translations: Fabio Riga (it), Pau Rul-lan Ferragut (ca), Daichi Kawahata (ja), Terje Uriansrud (nb_NO), Nuno Miguel (pt_PT), Tegegne Tefera (am), Dimitri Gogelia (ka), Vincent Tunru (nl), Pablo Vieira (pt_PT), Fábio Nogueira (pt_PT).
New translations: RPrieditis (lv).
File manager (Thunar):

Please see the Thunar website for a list of changes. 
GTK theme engine (gtk-xfce-engine-2):
Don't include the iconrc file in gtkrc.
Application Finder (xfce4-appfinder):
Remove trailing parens on AC_INIT version info to work around bug in intltool 0.35.x and 0.36.x.
Updated translations: Nuno Miguel (pt_PT), Dimitri Gogelia (ka), Pablo Vieira (pt_PT), Vladimir Melo (pt_BR).
New translations: Terje Uriansrud (nb_NO), Tegegne Tefera (am), RPrieditis (lv).
```

---

### Post by smartboyathome on 2007-12-02
Awesome! I use XFCE sometimes (right now I am stuck on E17 though ;)), and can't wait for hardy when this will be implimented!

---

### Post by kadath on 2007-12-02
4.4.2 will be in Hardy. Looking forward to it!

---

### Post by crimesaucer on 2007-12-08
Using it on Archlinux, and it's so fast. I turned off Compiz Fusion, and turned on xfwm4 composting, and everything is running so smooth and fast.

---

### Post by clubsoda on 2007-12-10
Debian has this in their unstable section but I don't find any downloadable DEBs.  

Will this appear in Gutsy backports, by any chance?

---

### Post by clubsoda on 2007-12-10
[quote="crimesaucer"]..turned on xfwm4 composting...[/quote]Some other users reported that xfwm4 composting turned their system into sh...
Oh hang on, is that a typo? :lol::-):lol:

---

### Post by maarten80 on 2007-12-12
I'm currently using Xubuntu feisty. Could I upgrade/update the Xfce environment to 4.4.2 or is that impossible without upgrading my entire ubuntu distro?

---

### Post by Markor on 2007-12-12
I installed Xfce 4.4.2 from source (there is installer to download, that compiles everything and installs it)

But now, I don`t have keyboard Layouts in "Keyboard settings" 
panel. :(
i can`t use environment that does not allow me to change
keyboard layout settings.
How do I go back to Xfce included with Xubuntu now,
or, How do I enable keyboard layouts?? :confused:

---

### Post by Tundro Walker on 2007-12-13
If you go into Synaptic, I think there's a way to click on the package and have it roll back to a previous version.  Look at the menu options...I remember seeing something about rolling back.

I'm half-tempted to try this out myself.  I use default Ubuntu Gnome, but I keep it bare-minimum.  A couple quick-start icons on the panel and the weather applet (which I can live without if need be).  I'll just need to keep some Gnome apps I use, like Gnomad 2.  Might be interesting...

---

### Post by Polygon on 2007-12-13
i compiled it and tried it out

its HIGHLY HIGHLY HIGHLY HIGHLY (did i mention highly?) annoying that you cant move panel items where you want them to go. Its so freaking annoying im not going to even consider using xfce until they fix it.

If you set the panel to full width, everything bunches up on the left, and you cant move it to the right by clicking move, it only moves it to the left or right of existing panel objects that are also bunched up on the left. The only way i have figured out how to make stuff like the clock go on the very right of the panel is to have a separator and then specify "expand' in its options. Come on xfce, is it THAT HARD to make it so you can move panel objects wherever you want on the panel instead of having it just to the left/right of another object? gah!

the menu editor still sucks, sure it lets you edit it, but it doesnt let you edit the stuff like under 'internet' 'games' ' graphics', etc. 

sure it might be fast, but its even less configurable then gnome, and since gnome is supposed to be about simplicity, thats really bad.

---

### Post by Markor on 2007-12-18
I installed Xfce 4.4.2 from source because there is no x86-64 binary .deb package(s) available. 
How to deinstall 4.4.2 when i installed it with Xfce installer
and Not .deb package manager(apt,synaptic)?

I now have 2 Xfce items listed in gdm menu,as environments to choose. Whatever I choose, I get 4.4.2 Now.
Also beside that, I cant change keyboard layouts 
(option for layout is missing from settings)
I am also unable to use hibernate/suspend/switch user options.
Also Thunar plugins previously installed does Not work 
anymore! (Like archiver plugin to make archives..)

Also, the bug with blocking Thunar in an endless loop, remains again in 0.9 Version, making Thunar as file manager
quite useless, unless you consider great practice to use
only One open window of default environment file manager.
:confused:

Right now, I would be quite happy to make my keyboard layouts work in present xfce 4.4.2 
and to find solutions for missing suspend/resume/user 
switch , thunar crashing and archiver plugin problems 
for a later time.

---

### Post by Ptero-4 on 2007-12-19
The thing with the panel not allowing you to move applets freely have been there since xfce 4.3b1 (or the alphas even IIRC).

---

### Post by new2*buntu on 2007-12-19
> **clubsoda said:**
> Some other users reported that xfwm4 composting turned their system into sh...
Oh hang on, is that a typo? :lol::-):lol:

Did that to me, especially when dragging windows with transparency. So I turned it off and went to good ol' Compiz Fusion, which has caused no troubles.

---

### Post by tw1ggy.ramir3z on 2007-12-22
Ok guys! This is my xmas present for Ubuntu's community. I've build XFCE 4.4.2 deb packages for (X)Ubuntu Gusty Gibbon 7.10. Lemme know if it works. If you want other packages just ask me! ;)

Now I'm lookin' for someone put it on a repo. Lemme know! MERRY XMAS!:)

_This is the link to download:_ [http://rapidshare.com/files/78432733/xfce4_4.4.2_gutsy.tar.bz2.html](http://rapidshare.com/files/78432733/xfce4_4.4.2_gutsy.tar.bz2.html)

---

### Post by Hero of Time on 2007-12-31
> **tw1ggy.ramir3z said:**
> Ok guys! This is my xmas present for Ubuntu's community. I've build XFCE 4.4.2 deb packages for (X)Ubuntu Gusty Gibbon 7.10. Lemme know if it works. If you want other packages just ask me! ;)

Now I'm lookin' for someone put it on a repo. Lemme know! MERRY XMAS!:)

_This is the link to download:_ [http://rapidshare.com/files/78432733/xfce4_4.4.2_gutsy.tar.bz2.html](http://rapidshare.com/files/78432733/xfce4_4.4.2_gutsy.tar.bz2.html)
Thanks for the package. I just installed it. Could you, for the other users, make a list on what package you have to install first before you install the other? I had some trial and error before I got the right order (missing dependencies, broken cache). Now I'm off to reboot and see if it changed much. I also updated my video driver, so I'm even more curious as to what will happen.

---

### Post by Methuselah on 2007-12-31
Xfce is excellent.
Fast, good looking, understandable and easy to configure.
It's the most full featured DE that can run on an old PII with 192MB of RAM that I have lying around.

---

### Post by jej2003 on 2008-01-06
I haven't tried tihs yet, but does this have all the latest supporting apps as well? (Thunar, mousepad) also anyone know how to use apt-build with this to compile for my system?

---

### Post by mrgnash on 2008-01-06
There is no need to put the changelog in <code>. All that does it make it hard to read.

---

### Post by mlg81 on 2008-01-08
Just installed it.
After reboot, synaptic showed up broken packages:
libexo-0.3-dev
libthunar-vfs-1-dev
libxfce4mcs-dev
libxfce4util-dev
libxfcegui4-dev
python-exo-dbg
xfce4-mcs-manager-dev
xfce4-panel-dev

synaptic just removed them.
They are -dev packages so i hope i wont need them :-S
And if you do not know what package install first:
- uncompress all the debs in a single folder
- open Terminal
- enter the folder using 'cd' command
- install everything: sudo dpkg -i *.deb

Or maybe i got broken packages for using -i *.deb??

---

### Post by mikewhatever on 2008-01-12
In my case, it got compiled after several tries, but would not run. After choosing XFCE at login, the screen would turn black showing a message 'This session lasted less then 10 seconds' and then some missing directories or files. Much as I like XFCE, I had no desire to troubleshoot yet again, and so uninstalled the whole thing.

---

### Post by crimesaucer on 2008-01-12
> **clubsoda said:**
> Some other users reported that xfwm4 composting turned their system into sh...
Oh hang on, is that a typo? :lol::-):lol:

No problems for me, xfwm4 works fine... much faster than Compiz Fusion and less resources. Maybe it's something with the Ubuntu version?

---

### Post by Ron O on 2008-02-26
> **maarten80 said:**
> I'm currently using Xubuntu feisty. Could I upgrade/update the Xfce environment to 4.4.2 or is that impossible without upgrading my entire ubuntu distro?
Here is a pretty official link that gives you the instructions. 

[http://j1m.net/2008/01/07/get-xfce-442-on-xubuntu-gutsy-gibbon-or-feisty-fawn-2/](http://j1m.net/2008/01/07/get-xfce-442-on-xubuntu-gutsy-gibbon-or-feisty-fawn-2/)

But since I did the update, I cannot mount my NTFS Windows partitions. I cannot blame the update for sure, but it certainly looks like a likely suspect. Have 2 help requests in (Xubuntu and XFCE) and been working on this all day- nothing yet.

---

