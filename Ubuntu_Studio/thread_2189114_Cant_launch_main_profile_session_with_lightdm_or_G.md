---
title: "Cant launch main profile session with lightdm or GDM in 13.10"
date: 2013-11-20
forum: Ubuntu Studio
---

### Post by HugoJJ on 2013-11-20
Since upgrading to 13.10 I can't login on my main user profile. I get the lightdm login screen but when logging in only get the wallpaper, no menus, dock or mouse.
Secondary profiles work however. Is there a lightdm user specific session launch script in /home/user I should edit ?
Tried installing GDM and KDM no luck either.

Am using Ubuntustudio on AMD64.

thanks for any ideas/suggestions.

---

### Post by Toz on 2013-11-20
Hello and welcome to the forums.

Try clearing out your sessions cache before logging in:
[LIST=1]
[*]At the login screen, press Ctrl+Alt+F1 to go to the text console.
[*]Log in here.
[*]Run the following commands:
```
cd .cache
rm -rf sessions
```
[*]Go back to the gui login screen (Ctrl+Alt+F7)
[*]Try logging in.
[*]
[/LIST]

---

### Post by HugoJJ on 2013-11-21
Thanks Toz, unfortunately this didn't resolve the issue. 
Anyone has a suggestion to start a session without lightdm ?

Hugo

---

### Post by Toz on 2013-11-21
If the secondary profiles are logging in successfully, then its probably not lightdm (or GDM/KDM) that is the cause of the problem. Try logging in again and when it gets stuck, move over to the first console (Ctrl+Alt+F1) and log in to the text session again and have a look at the ~/.xsession-errors log file to see if there are any clues there as to what is going wrong.

---

### Post by Spoonman1985 on 2013-11-21
I am having the same problem, looked fine when I first updated then after a restart the desktop is grey and I cant even right click it, thankfuly the menu bar still appears. Unfortunately I dont know enough about ubuntu to really get into trying to solve it myself, nothing similar Ive found on the forums helps either.

---

### Post by Toz on 2013-11-21
> **Spoonman1985 said:**
> I am having the same problem, looked fine when I first updated then after a restart the desktop is grey and I cant even right click it, thankfuly the menu bar still appears. Unfortunately I dont know enough about ubuntu to really get into trying to solve it myself, nothing similar Ive found on the forums helps either.

Hello Spoonman and welcome to the forums.

In your case, click on the menu icon, select "Settings Manager", go to the "Session and Startup" applet then to the "Session" tab. There you will find a "Clear saved sessions" button. Click it, select "Proceed" then log out and back in again to see if it fixes the problem.

---

### Post by Spoonman1985 on 2013-11-21
That worked perfectly Toz, thanks for the help.

---

### Post by HugoJJ on 2013-11-24
Hi, here the output of .xsession-errors.old :

Script for cjkv started at run_im.
Script for default started at run_im.
init: logrotate main process (29222) killed by TERM signal

Any ideas ? 

Best rgds.  Hugo

---

### Post by Toz on 2013-11-24
> **HugoJJ said:**
> Hi, here the output of .xsession-errors.old :

Script for cjkv started at run_im.
Script for default started at run_im.
init: logrotate main process (29222) killed by TERM signal

Any ideas ? 

Best rgds.  Hugo

How about the contents of ~/.xsession-errors (not the old version) while you are stuck on the graphical login? Any different messages there? Also, can you post back:
```
ls -l ~/.cache/sessions
```

---

### Post by HugoJJ on 2013-11-24
When I retry lightdm now get following in .xsession-errors.old:

init: update-notifier-crash (var/crash/_usr_bin_Xorg.o.crash) main process (1728) killed by TERM signal
init: update-notifier-crash (var/crash/_usr_share_apport_apport-gtk.0.crash) main process (1732) killed by TERM signal.

looking in latter file says:
Nonfreekernelmodules: fglrx
Package: apport-gtk 2.15.5-0ubuntu2.1
ProcVersionSignature: Ubuntu 3.8.0-33.25-lowlatency x86_64
Sourcepackage: apport
Tags: saucy
apport-gtk crashed with struct.error in read32(): unpack requires a bytes object of length 4

Regret above is way beyond my linux skillset.

Rgds

Hugo

---

### Post by Toz on 2013-11-24
Can you post back the results of:
```
ls -l ~/.cache/sessions
```
...and
```
ls -l ~/.config/autostart/
```

Lets see what files are sitting there.

---

### Post by HugoJJ on 2013-11-24
Hi Toz,

.cache/sessions turns back : total 0

.xsession-errors just gives flwng 2lines:
Script for cjkv started at run_im.
Script for default started at run_im.

rgds Hugo

---

### Post by Toz on 2013-11-24
There are also 2 log files in var/log/lightdm that might be useful. However, you need root privileges to read them. They are:
- /var/log/lightdm/lightdm.log
- /var/log/lightdm/x-0-greeter.log

If you could post back the contents, it would be helpful.

---

### Post by HugoJJ on 2013-11-24
Hi Toz, you are incredibly fast !!!, faster than I can type responses ! Regardless whether we can resolve this in the end, thanks sooo much for your help !!!

output of ls -l .config/autostart/ 
total 12
-rw-rw-r-- 1 hugo hugo 235 Aug 11 21:21 dropbox.desktop
-rw-rw-r-- 1 hugo hugo 2434 Aug 18 19:13 xfce4-notes-autostart.desktop
-rw-rw-r-- 1 hugo hugo 29 nov 18 2012 xfce4-settings-helper-autostart.desktop

Rgds Hugo

---

### Post by HugoJJ on 2013-11-24
Hi Toz,

X-0-greeter.log gives:
(lightdm-gtk-greeter:2236): GLib-CRITICAL **: g_shell_parse_argv: assertion 'command_line != NULL' failed
Error opening directory /usr/share/lightdm/sessions' no such file or directory 
Error opening directory /usr/share/lightdm/remote-sessions' no such file or directory 
Error opening directory /home/hugo/.face: no such file or directory 

lightdm.log is very big too much to copy. But top line seems normal, don't see armor mags or warnings
'Starting Light Display Manager 1.8.4 UID=0 PID=1111'

Rgds Hugo

---

### Post by Toz on 2013-11-24
> (lightdm-gtk-greeter:2236): GLib-CRITICAL **: g_shell_parse_argv: assertion 'command_line != NULL' failed

This looks interesting. Lets try clearing the lightdm cache (with root privileges):
```
rm /var/cache/lightdm/dmrc/<your_user_id>.dmrc
```
...where <your_user_id> is the user id of the problem account.

Then try again.

---

### Post by HugoJJ on 2013-11-25
Hi Toz,

Some progress. Can see top menu bar and dock at the bottom however no mouse cursor visible although I can highlight areas on menubar and dock. On top right where usually I see alert for updates a red circle with inside horizontal white bar like a no entry sign.  Can't access menu so regret can't show screenshot. 

Rgds

Hugo

---

### Post by Toz on 2013-11-25
Anything new in ~/.xsession-errors or /var/log/lightdm/X-0-greeter.log?

Try pressing Alt+F2 and running:
```
xfce4-popup-applicationsmenu
```
...to access the applications menu.

---

### Post by HugoJJ on 2013-11-25
Hi Toz,

.xsession-errors gives:
init: upstart-dbus-session-bridge main process (1798) terminated with status 1

in x-0-greeter.log exactly same error msgs as before.

xfce4-popup-applicationsmenu gives:
xfce4-panel: cannot open display
Failed to parse arguments: cannot open display:

Rgds Hugo

---

### Post by HugoJJ on 2013-11-25
Sorry discovered I made a mistake on xfce4-popup-applicationsmenu which I tried to launch from terminal.
I now tried to launch this from the xwindow and can type in the command however nothing happens.

Rgds

---

### Post by Toz on 2013-11-25
> **HugoJJ said:**
> Hi Toz,

.xsession-errors gives:
init: upstart-dbus-session-bridge main process (1798) terminated with status 1

in x-0-greeter.log exactly same error msgs as before.

xfce4-popup-applicationsmenu gives:
xfce4-panel: cannot open display
Failed to parse arguments: cannot open display:

Rgds Hugo

> **HugoJJ said:**
> Sorry discovered I made a mistake on xfce4-popup-applicationsmenu which I tried to launch from terminal.
I now tried to launch this from the xwindow and can type in the command however nothing happens.

Rgds
Something is definitely wrong with your profile and I can't seem to be able to fix it. Since the secondary profiles work, you're probably better off resetting your Xfce profile back to defaults and starting over. To do so, you'll want to log in to the text console and move certain folders (no data will be lost - in case you need to access information from within them at a later date) so that new ones will be created with default settings when you login in graphically again. _Please note_ that this will remove all of your customizations and you'll need to redo them. The folders to move (backup) are:
- ~/.config
- ~/.cache
You can use the following commands (while logged into a text console):
```
mv ~/.config ~/.config.BAK
mv ~/.cache ~/.cache.BAK
```
...then go back to the gui login screen and try logging in again.

---

### Post by HugoJJ on 2013-11-26
It worked, I have my desktop back ! Thanks a lot Toz for your patience and reactivity. It's great to be part of a community being so supportive and helpful !

Kind rgds

Hugo

---

### Post by Toz on 2013-11-26
Glad to hear that it worked. If you don't mind, can you mark this thread as SOLVED using the "Thread Tools" link above? Thanks.

---

