---
title: "Gedit does a jiggle and a wiggle, but won't load."
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-19
Gedit will wiggle in Unity launcher but will not load.

 Tried updates.
This a known bug?

---

### Post by Grenage on 2012-01-19
What is displayed when you try and load it from a terminal?

---

### Post by lucazade on 2012-01-19
open gedit from terminal and look for errors.
then, if necessary, open a bug report with:

ubuntu-bug gedit

this way the devs will be aware of the issue and find a fix for it.

---

### Post by ventrical on 2012-01-19
> **Grenage said:**
> What is displayed when you try and load it from a terminal?


Gnome terminal does the same thing as does xterm.

---

### Post by ventrical on 2012-01-19
> **lucazade said:**
> open gedit from terminal and look for errors.
then, if necessary, open a bug report with:

ubuntu-bug gedit

this way the devs will be aware of the issue and find a fix for it.

Thanks ...  bug filed..


[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/918764](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/918764)

---

### Post by drmrgd on 2012-01-19
> **ventrical said:**
> Gnome terminal does the same thing as does xterm.

But, what is the error message you get (if any)?  It's going to be very difficult for anyone to troubleshoot this without seeing what kind of errors you're getting.

---

### Post by jbicha on 2012-01-19
Is there anything else we should know about your computer? Specifically, what PPAs are you using? If other apps aren't working, you should mention those on the bug report too.

Have you tried rebooting or reinstalling ubuntu-desktop?

As lucazade suggested, sometimes running from a terminal provides a little more information about what's going wrong. If gnome-terminal doesn't work, you could always install something like konsole.

---

### Post by ventrical on 2012-01-19
> **jbicha said:**
> Is there anything else we should know about your computer? Specifically, what PPAs are you using? If other apps aren't working, you should mention those on the bug report too.

Have you tried rebooting or reinstalling ubuntu-desktop?

As lucazade suggested, sometimes running from a terminal provides a little more information about what's going wrong. If gnome-terminal doesn't work, you could always install something like konsole.

No PPAs. xterm will work but gedit will not load. As I said above, gnome terminal will not work. No other warnings.

will try a reboot..

 ps... some times it will work ... other times not .. it is intermittent.

---

### Post by ventrical on 2012-01-19
> **jbicha said:**
> Is there anything else we should know about your computer? Specifically, what PPAs are you using? If other apps aren't working, you should mention those on the bug report too.

Have you tried rebooting or reinstalling ubuntu-desktop?



Yep... but didn't work. What did work was that I logged off Unity 3D and logged on to Unity 2D and it worked then.  Looks like a Unity 3D problem then?

---

### Post by effenberg0x0 on 2012-01-19
A tip: If you are unable to launch a terminal via the GUI, you can switch to a VT and launch it:
```
DISPLAY=:0.0 /usr/bin/gnome-terminal
```
See what error messages show right below this command, as they might be important.
If no crash is reported, the terminal will be in your desktop when you switch back to VT7.

Inside the terminal we just launched in your desktop, you could launch compiz. That way, as long as you keep this terminal open, you would be able to see some of the errors/warnings that show when any application is started in the GUI. It has helped me sometimes.
```
compiz --replace &

```

If you close the terminal, you will be in the no DE hell. If that is the case, you can switch back to another VT and launch metacity:
```
metacity --replace &
```

And then, iside the now manageable desktop, relaunch compiz/unity:
```
compiz --replace &
```

---

### Post by mc4man on 2012-01-19
I would suggest for your own troubleshooting - 

create a new user, login to & see what happens

In your user session
Open ~/.xsession-errors in any text editor, then try gedit, see if anything is reported of interest

look in /var/crash for a gedit .crash, if there use r. click > open with > report ..

If this is a pinned gedit launcher, -  remove, log out/in and re-add

---

### Post by ventrical on 2012-01-19
> **mc4man said:**
> I would suggest for your own troubleshooting - 

create a new user, login to & see what happens



Yes ... gedit and gnome-terminal work just fine in new user under Unity 3D.

---

### Post by ventrical on 2012-01-19
> **mc4man said:**
> I would suggest for your own troubleshooting - 

create a new user, login to & see what happens

In your user session
Open ~/.xsession-errors 

 but I do not know what you mean here ... where is (~/.xsession-errors) .. I do not understand the ~/. ??? how do I get there..?

thanks..

---

### Post by ventrical on 2012-01-19
> **effenberg0x0 said:**
> A tip: If you are unable to launch a terminal via the GUI, you can switch to a VT and launch it:
```
DISPLAY=:0.0 /usr/bin/gnome-terminal
```See what error messages show right below this command, as they might be important.
If no crash is reported, the terminal will be in your desktop when you switch back to VT7.

Inside the terminal we just launched in your desktop, you could launch compiz. That way, as long as you keep this terminal open, you would be able to see some of the errors/warnings that show when any application is started in the GUI. It has helped me sometimes.
```
compiz --replace &

```If you close the terminal, you will be in the no DE hell. If that is the case, you can switch back to another VT and launch metacity:
```
metacity --replace &
```And then, iside the now manageable desktop, relaunch compiz/unity:
```
compiz --replace &
```


Ok.. will try this  .. but as I said .. I have gnome- terminal in Unity 2D working just fine along with  gedit.

---

### Post by effenberg0x0 on 2012-01-19
> **ventrical said:**
> but I do not know what you mean here ... where is (~/.xsession-errors) .. I do not understand the ~/. ??? how do I get there..?

thanks..

Hey Ventrical,

~ = /home/you = $HOME
Like:
cd <enter> is the same as cd ~<enter> and cd $HOME <enter>

so ~/.somedotfile is the same as /home/you/.somedotfile or $HOME/.somedotfile

[B]EDIT:
[/B]To make it clearer: See that the effect of the following commands is the same:
Your HOME dotfiles are: cd && find . -maxdepth 1 -name ".*"
ls -la ~/.*
ls -la /home/you/.*
ls -la $HOME/.*

---

### Post by effenberg0x0 on 2012-01-19
> **ventrical said:**
> Ok.. will try this  .. but as I said .. I have gnome- terminal in Unity 2D working just fine along with  gedit.

Yea, I was just wondering what errors in the Compiz/Unity session were preventing you from launching gedit/gnome-terminal on it. I was guessing on some lib crashing but mc4man nailed it (as usual) when he advised you to try a new user.

---

### Post by ventrical on 2012-01-19
> **effenberg0x0 said:**
> Yea, I was just wondering what errors in the Compiz/Unity session were preventing you from launching gedit/gnome-terminal on it. I was guessing on some lib crashing but mc4man nailed it (as usual) when he advised you to try a new user.

Yes.. but the problem still remains with that one user. So, I logged on to Unity 2D, ran gnome-terminal, entered the command you suggested and a phenomenon occured.  The Unity 3D  sidepanel overlayed on top of the Unity 2D sidepanel.

  Gnome terminal reported a bunch of errors and then will not proceed to close .. so I am assuming to log-off now or reboot??

[http://www.youtube.com/watch?v=JOFR2J6LEqE](http://www.youtube.com/watch?v=JOFR2J6LEqE)

---

### Post by ventrical on 2012-01-19
> **effenberg0x0 said:**
> Hey Ventrical,

~ = /home/you = $HOME
Like:
cd <enter> is the same as cd ~<enter> and cd $HOME <enter>

so ~/.somedotfile is the same as /home/you/.somedotfile or $HOME/.somedotfile

[B]EDIT:
[/B]To make it clearer: See that the effect of the following commands is the same:
Your HOME dotfiles are: cd && find . -maxdepth 1 -name ".*"
ls -la ~/.*
ls -la /home/you/.*
ls -la $HOME/.*

ok.. thanks .. gee .. I feel like such an idiot...

---

### Post by ventrical on 2012-01-19
Ok.. I think it may have to do with my KVM ... or a conflict there..

```

Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/ventrical/.profile
Loading resource: /etc/X11/Xresources/x11-common
Loading X session script /etc/X11/Xsession.d/20x11-common_process-args
Loading X session script /etc/X11/Xsession.d/30x11-common_xresources
Loading X session script /etc/X11/Xsession.d/40x11-common_xsessionrc
Loading X session script /etc/X11/Xsession.d/50_check_unity_support
Loading X session script /etc/X11/Xsession.d/50x11-common_determine-startup
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk3-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/52libcanberra-gtk-module_add-to-gtk-modules
Loading X session script /etc/X11/Xsession.d/55gnome-session_gnomerc
Loading X session script /etc/X11/Xsession.d/60x11-common_localhost
Loading X session script /etc/X11/Xsession.d/60x11-common_xdg_path
Loading X session script /etc/X11/Xsession.d/60xdg-user-dirs-update
Loading X session script /etc/X11/Xsession.d/65compiz_profile-on-session
Loading X session script /etc/X11/Xsession.d/70gconfd_path-on-session
Loading X session script /etc/X11/Xsession.d/75dbus_dbus-launch
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-eHFSM7
GNOME_KEYRING_CONTROL=/tmp/keyring-eHFSM7
GPG_AGENT_INFO=/tmp/keyring-eHFSM7/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-eHFSM7
GNOME_KEYRING_CONTROL=/tmp/keyring-eHFSM7
GPG_AGENT_INFO=/tmp/keyring-eHFSM7/gpg:0:1
SSH_AUTH_SOCK=/tmp/keyring-eHFSM7/ssh

color-plugin-WARNING **: failed to get edid: unable to get EDID for output
unity-2d-launcher: [WARNING] X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x0
unity-2d-panel: [DEBUG] Scanning panel plugin directory "/usr/lib/unity-2d/plugins/panel" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appindicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-appname.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-homebutton.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-indicator.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-legacytray.so" 
unity-2d-panel: [DEBUG] Loading panel plugin: "/usr/lib/unity-2d/plugins/panel/libpanelplugin-separator.so" 
unity-2d-panel: [DEBUG] Configured plugins list is: ("appname", "!legacytray", "indicator") 
Initializing nautilus-gdu extension
unity-2d-launcher: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-launcher: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+S" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-launcher: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
unity-panel-service: no process found
unity-2d-panel: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "F10" 
unity-2d-launcher: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+T" 
** Message: moving back from GtkStatusIcon to indicator
unity-2d-launcher: [WARNING] void LauncherApplicationsList::onRemoteEntryUpdated(QString, QMap<QString, QVariant>): Application sent an update but we don't seem to have it in the launcher: "application://nautilus.desktop" 
unity-2d-launcher: [WARNING] void LauncherApplicationsList::onRemoteEntryUpdated(QString, QMap<QString, QVariant>): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 
unity-2d-launcher: [WARNING] void LauncherApplicationsList::onRemoteEntryUpdated(QString, QMap<QString, QVariant>): Application sent an update but we don't seem to have it in the launcher: "application://empathy.desktop" 

** WARNING **: recent-manager-provider.vala:125: Desktop file for soffice was not found

** WARNING **: Trying to register gtype 'GMountMountFlags' as enum when in fact it is of type 'GFlags'

** WARNING **: Trying to register gtype 'GDriveStartFlags' as enum when in fact it is of type 'GFlags'

```

---

### Post by ventrical on 2012-01-19
I went into another user of same install and  got a nautalis error while trying to open gedit and filed another bug.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/918852](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/918852)

---

### Post by mc4man on 2012-01-19
> **ventrical said:**
> I went into another user of same install and  got a nautalis error while trying to open gedit and filed another bug.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/918852](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/918852)

That crash,(bug), will be duped to another bug which will be tied to a fairly longstanding X11 bug.
In other words, if you want to resolve on that hardware & that install in the near term, you'll need to resolve yourself and or hope it just goes away.

I remember reading the X11 bug in the past so I guess I've seen that crash before, as I remember it was probably one of those crashs where nothing appeared to be affected.

I'd suspect most current PP users have no current issue opening gedit.

---

### Post by fjgaude on 2012-01-19
> **mc4man said:**
> That crash,(bug), will be duped to another bug which will be tied to a fairly longstanding X11 bug.
In other words, if you want to resolve on that hardware & that install in the near term, you'll need to resolve yourself and or hope it just goes away.

I remember reading the X11 bug in the past so I guess I've seen that crash before, as I remember it was probably one of those crashs where nothing appeared to be affected.

I'd suspect most current PP users have no current issue opening gedit.

As least with me, no issues, period. The few error messages received have been reported, but usually many folks have already reported them. It's gonna be a solid win for **Unity** in 12.04 LTS.

---

### Post by ventrical on 2012-01-19
> **mc4man said:**
> That crash,(bug), will be duped to another bug which will be tied to a fairly longstanding X11 bug.
In other words, if you want to resolve on that hardware & that install in the near term, you'll need to resolve yourself and or hope it just goes away.

I remember reading the X11 bug in the past so I guess I've seen that crash before, as I remember it was probably one of those crashs where nothing appeared to be affected.

I'd suspect most current PP users have no current issue opening gedit.

 I guess that is the way it goes ... thanks for the help. 

 All my other installs (10) don't act up like this one. Time to move on . I got an idea.

---

### Post by ventrical on 2012-01-19
> **fjgaude said:**
> As least with me, no issues, period. The few error messages received have been reported, but usually many folks have already reported them. It's gonna be a solid win for **Unity** in 12.04 LTS.


 I still have 10 good installs :)   I just like working on hopeless cases.. :)

thanks a lot  all..

---

### Post by effenberg0x0 on 2012-01-19
> **ventrical said:**
> Yes.. but the problem still remains with that one user. So, I logged on to Unity 2D, ran gnome-terminal, entered the command you suggested and a phenomenon occured.  The Unity 3D  sidepanel overlayed on top of the Unity 2D sidepanel.

  Gnome terminal reported a bunch of errors and then will not proceed to close .. so I am assuming to log-off now or reboot??

[http://www.youtube.com/watch?v=JOFR2J6LEqE](http://www.youtube.com/watch?v=JOFR2J6LEqE)

The command I posted was (unity --replace & or compiz --replace &) is meant to load Compiz/Unity, so it's not weird that, if you are in the 2d session and launch it, you'll see an overlay of launcher, things can go bad, etc. The command should be issued on a Unity session. But no need to reboot, just restart lightdm and things will be ok. sudo service lightdm restart.

---

### Post by ventrical on 2012-01-19
> **effenberg0x0 said:**
> The command I posted was (unity --replace & or compiz --replace &) is meant to load Compiz/Unity, so it's not weird that, if you are in the 2d session and launch it, you'll see an overlay of launcher, things can go bad, etc. The command should be issued on a Unity session. But no need to reboot, just restart lightdm and things will be ok. sudo service lightdm restart.


 I just chose <save> and ripped the original user of that alpha Oneiric /Precise Transition install that you had worked with me on several months back.  I removed  something suggested by one of the users and lost the apps lens in Unity so that <user> has been acting up since then.   It's like System Restore .. a lot faster . :) Manage Users app  allows you to save all of the <users> files for import later so there is no loss of bandwidth . Spawning  new users seems to have a purifying effect on possibly corrupt .conf files.

Thanks for all your help and support.

regards,

ventrical..

---

