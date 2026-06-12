---
title: "gnome shell crashes while pressing m in overview mode"
date: 2012-02-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jiyinyiyong on 2012-02-24
Ubuntu 12.04 , GNOME Shell 3.2.2.1
In overview mode, press 'm' and the desktop reloads (like alt+f2  and press 'r' to reload..), but if repeat this for a second time, the desktop will not respose, no panel, no title bar, no respose to keyboard, no click, only the ability to move the mouse.
Here's my .xsession-errors file:
```
Running X session wrapper
Loading profile from /etc/profile
Loading profile from /home/chen/.profile
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
Loading X session script /etc/X11/Xsession.d/80im-switch
Setting IM through im-switch for locale=en_US.
Start IM through /home/chen/.xinput.d/en_US linked to /etc/X11/xinit/xinput.d/ibus.
Loading X session script /etc/X11/Xsession.d/90consolekit
Loading X session script /etc/X11/Xsession.d/90qt-a11y
Loading X session script /etc/X11/Xsession.d/90x11-common_ssh-agent
current session already has an ibus-daemon.
Loading X session script /etc/X11/Xsession.d/99x11-common_start
GNOME_KEYRING_CONTROL=/tmp/keyring-rGTkF6
SSH_AUTH_SOCK=/tmp/keyring-rGTkF6/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-rGTkF6
SSH_AUTH_SOCK=/tmp/keyring-rGTkF6/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-rGTkF6
SSH_AUTH_SOCK=/tmp/keyring-rGTkF6/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-rGTkF6
SSH_AUTH_SOCK=/tmp/keyring-rGTkF6/ssh
GPG_AGENT_INFO=/tmp/keyring-rGTkF6/gpg:0:1

color-plugin-WARNING **: failed to get edid: unable to get EDID for output
** Message: applet now removed from the notification area
[21032:21042:21375970992:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21042:21375971109:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21042:21375973183:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21042:21375973234:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21040:21376083392:ERROR:print_backend_cups.cc(66)] Cannot load libgnutls.so
** Message: using fallback from indicator to GtkStatusIcon
[21032:21048:21376219411:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21048:21376219487:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21048:21376220870:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21048:21376220913:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21042:21376252743:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
[21032:21042:21376254107:ERROR:nss_ocsp.cc(581)] No URLRequestContext for OCSP handler.
Window  manager warning: Log level 128: Read-only property 'read-only-view' on  class 'GeeAbstractSet' has type 'GeeCollection' which is not equal to or  more restrictive than the type 'GeeSet' of the property on the  interface 'GeeSet'

      JS LOG: GNOME Shell started at Sat Feb 25 2012 10:07:11 GMT+0800 (CST)

folks-WARNING **: Failed to find primary PersonaStore with type ID 'eds' and ID 'system'.
Individuals will not be linked properly and creating new links between Personas will not work.
The configured primary PersonaStore's backend may not be installed. If you are unsure, check with your distribution.
** Message: applet now embedded in the notification area

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/.xsession-errors" was not found, exec: sublime_text,  mime_type: application/octet-stream

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/js/github-flavored-markdown/scripts/showdown.js"  was not found, exec: sublime_text, mime_type: application/javascript

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/.config/sublime-text-2/Packages/User/Default%20(Linux).sublime-keymap"  was not found, exec: subl, mime_type: application/octet-stream

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/js/seed/zetcode/argv.coffee" was not found,  exec: sublime_text, mime_type: application/octet-stream

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/coffee/browserid/source/login.jade" was not  found, exec: subl, mime_type: application/octet-stream

** WARNING  **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/mongodb/skin.coffee" was not found, exec: subl,  mime_type: application/octet-stream

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/qingtan" was not found, exec: subl,  mime_type: inode/directory

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/titleleaf/diary/111031%E6%84%9F%E5%86%92%E5%88%9A%E5%A5%BD"  was not found, exec: sublime_text, mime_type: application/octet-stream

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/Videos/out.mpg" was not found, exec: nightly,  mime_type: video/mpeg

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/titleleaf/diary/120209%E6%B3%A1%E5%BD%B1%E7%9A%84%E6%97%B6%E5%85%89"  was not found, exec:  file:///home/chen/code/git/titleleaf/diary/120209%E6%B3%A1%E5%BD%B1%E7%9A%84%E6%97%B6%E5%85%89,  mime_type: text/plain

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/.xmonad/xmonad.hs" was not found, exec:  file:///home/chen/.xmonad/xmonad.hs, mime_type: text/x-haskell

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/zhongli/source/server.coffee" was not found,  exec: file:///home/chen/code/git/zhongli/source/server.coffee,  mime_type: text/plain

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/zhongli/source/client.coffee" was not found,  exec: file:///home/chen/code/git/zhongli/source/client.coffee,  mime_type: text/plain

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/titleleaf/diary/120211%E7%BB%A7%E7%BB%AD%E5%AF%BB%E6%89%BE%E6%96%B9%E5%90%91"  was not found, exec:  file:///home/chen/code/git/titleleaf/diary/120211%E7%BB%A7%E7%BB%AD%E5%AF%BB%E6%89%BE%E6%96%B9%E5%90%91,  mime_type: text/plain

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/titleleaf/diary/120210%E9%99%8C%E7%94%9F%E4%B8%8D%E8%BF%9B%E7%8A%B6%E6%80%81"  was not found, exec:  file:///home/chen/code/git/titleleaf/diary/120210%E9%99%8C%E7%94%9F%E4%B8%8D%E8%BF%9B%E7%8A%B6%E6%80%81,  mime_type: text/plain

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/Pictures/canvas.png" was not found, exec: gimp-2.7,  mime_type: image/png

** WARNING **:  recent-manager-provider.vala:133: Desktop file for "file:///home" was  not found, exec: chromium-browser, mime_type: inode/directory

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen" was not found, exec: chromium-browser, mime_type:  inode/directory

** WARNING **: recent-manager-provider.vala:133:  Desktop file for  "file:///home/chen/code/git/jiyinyiyong.github.com/projects/trinary/calculator"  was not found, exec: sublimetext2, mime_type: inode/directory

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/jiyinyiyong.github.com/projects/trinary/calculator/trinary.coffee"  was not found, exec: sublimetext2, mime_type: application/octet-stream

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/code/git/jiyinyiyong.github.com/projects/web_tools/web_editor/editor.coffee"  was not found, exec: sublimetext2, mime_type: application/octet-stream

**  WARNING **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/Music/%E5%A4%A9%E4%BD%BF%E4%B8%AD%E7%9A%84%E9%AD%94%E9%AC%BC.mp3"  was not found, exec: deadbeef, mime_type: audio/mpeg

** WARNING  **: recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/Music/%E8%BF%BD%E6%A2%A6%E4%BA%BA.mp3" was not found,  exec: deadbeef, mime_type: audio/mpeg

** WARNING **:  recent-manager-provider.vala:133: Desktop file for  "file:///home/chen/Music/%E9%81%87%E8%A7%81%E6%88%91.mp3" was not found,  exec: deadbeef, mime_type: audio/mpeg

** WARNING **: Trying to register gtype 'GMountMountFlags' as enum when in fact it is of type 'GFlags'

** WARNING **: Trying to register gtype 'GDriveStartFlags' as enum when in fact it is of type 'GFlags'
AUP timeline: Entered aup.init()                          (first event)
AUP timeline: * calling prefs.init()                      (0)
AUP timeline: * calling filterListener.init()             (2)
AUP timeline: * calling proxy.init()                      (0)
AUP timeline: * calling filterStorage.init()              (0)
AUP timeline: * Entered filterStorage.loadFromDisk()      (0)
AUP timeline: * * done locating patterns.ini file         (0)
AUP timeline: * * done parsing file                       (92)
AUP timeline: * * load complete, calling observers        (0)
AUP timeline: * filterStorage.loadFromDisk() done         (33)
AUP timeline: * calling policy.init()                     (1)
AUP timeline: * calling synchronizer.init()               (0)
AUP timeline: aup.init() done                             (0)
Running global cleanup code from study base classes.
Window manager warning: Log level 16: invalid (NULL) pointer instance
Window manager warning: Log level 8: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Window manager warning: Log level 8: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** Message: applet now removed from the notification area
gnome-shell-calendar-server[21052]: Got HUP on stdin - exiting
gnome-session[20915]: WARNING: Application 'gnome-shell.desktop' killed by signal
Window  manager warning: Log level 128: Read-only property 'read-only-view' on  class 'GeeAbstractSet' has type 'GeeCollection' which is not equal to or  more restrictive than the type 'GeeSet' of the property on the  interface 'GeeSet'

      JS LOG: GNOME Shell started at Sat Feb 25 2012 10:08:46 GMT+0800 (CST)
** Message: applet now embedded in the notification area

folks-WARNING **: Failed to find primary PersonaStore with type ID 'eds' and ID 'system'.
Individuals will not be linked properly and creating new links between Personas will not work.
The configured primary PersonaStore's backend may not be installed. If you are unsure, check with your distribution.
** Message: applet now removed from the notification area
gnome-session[20915]: WARNING: App 'gnome-shell.desktop' respawning too quickly
gnome-shell-calendar-server[21348]: Got HUP on stdin - exiting
gnome-session[20915]: CRITICAL: We failed, but the fail whale is dead. Sorry....
gnome-session[20915]: WARNING: Application 'gnome-shell.desktop' killed by signal
```

---

### Post by keithpeter on 2012-02-25
> **jiyinyiyong said:**
> Ubuntu 12.04 , GNOME Shell 3.2.2.1
In overview mode, press 'm' and the desktop reloads (like alt+f2  and press 'r' to reload..), but if repeat this for a second time, the desktop will not respose, no panel, no title bar, no respose to keyboard, no click, only the ability to move the mouse.


Hello jiyinyiyong

What graphics card/driver are you using? I can't tell from your log extract (but others might be able to)

I'm having similar issues with attempting to search on Gnome shell leading to crashes. I use the nvidia restricted drivers. This is a known issue apparently

---

### Post by jiyinyiyong on 2012-02-26
> **keithpeter said:**
> Hello jiyinyiyong

What graphics card/driver are you using? I can't tell from your log extract (but others might be able to)

I'm having similar issues with attempting to search on Gnome shell leading to crashes. I use the nvidia restricted drivers. This is a known issue apparently
NVIDIA Corporation GT218 [GeForce 310M]
And I installed the recomended driver.

---

### Post by alleskapot on 2012-03-03
Hi jiyinyiyong , 

I used to have the same problem. Gnome shell crashing after typing  'virt' ( to find virtualbox real quick ) in the menu. It reinitialises itself one time, but stayed away the second time. 

I also used the nvidia closed source drivers and had the lastest 'recommended' version for my card. 

Fix for me was downgrade to one version before latest.  

295.20 <- this was the latest for my card
275.43 <- this is the one I downloaded and installed

Hope that helps

---

### Post by jiyinyiyong on 2012-03-06
It's a bit hard for me to install a driver by myself yet, so I tried to update gnome-shell to the latest version instead.
It doesn't crash now, but.. all keyboard shortcuts was reseted, even can not change in the setting.

---

### Post by jbicha on 2012-03-06
The Nvidia crash is [bug 936132]("http://pad.lv/936132").

Currently, gnome-control-center in Precise only sets gconf keyboard shortcuts (Unity, GNOME Shell 3.2) and not gsettings shortcuts (GNOME Shell 3.3 and higher). You could use dconf-editor as a workaround. That is discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=1933323").

---

