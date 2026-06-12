---
title: "Installing Updates gives Unknown Media Type for shared-mime-info (1.2-0ubuntu1)"
date: 2014-02-28
forum: Ubuntu Development Version
---

### Post by su:bhatta on 2014-02-28
Hi,
I just updated my 14.04 and this are some codes which I want deciphered :

```
Unpacking pulseaudio-module-bluetooth (1:4.0-0ubuntu10) over (1:4.0-0ubuntu7) ...
Processing triggers for man-db (2.6.6-1) ...
Processing triggers for libglib2.0-0:i386 (2.39.90-0ubuntu1) ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for libglib2.0-0:amd64 (2.39.90-0ubuntu1) ...
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for gnome-menus (3.10.1-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for fontconfig (2.11.0-0ubuntu4) ...
Processing triggers for gconf2 (3.2.6-0ubuntu1) ...
Processing triggers for xine-ui (0.99.7-1) ...
Updated the MIME types in xine's menu file.
```

For the last 3 updates I did, everytime this 'Unknown Media type was given but restart showed no system problem. But what does this relate to? Any need to do something or get worried.
Just did a dist-upgrade and last few lines are also given :

```
Setting up python3-crypto (2.6.1-4) ...
Exception ignored in: <bound method Popen.__del__ of <subprocess.Popen object at 0x7f51037db438>>
Traceback (most recent call last):
  File "/usr/lib/python3.4/subprocess.py", line 897, in __del__
TypeError: 'NoneType' object is not callable
Exception ignored in: <bound method Popen.__del__ of <subprocess.Popen object at 0x7f51037db4a8>>
Traceback (most recent call last):
  File "/usr/lib/python3.4/subprocess.py", line 897, in __del__
TypeError: 'NoneType' object is not callable
Setting up ubuntu-settings (14.04.4) ...
Setting up vinagre (3.10.2-0ubuntu1) ...
Setting up xfce4-settings (4.11.2-1ubuntu1) ...
Installing new version of config file /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml ...
Installing new version of config file /etc/xdg/autostart/xfsettingsd.desktop ...
Setting up kubuntu-docs (14.04ubuntu5) ...
Setting up libkpeople3 (0.2.1-0ubuntu1) ...
Setting up p11-kit (0.20.2-1ubuntu2) ...
Setting up pulseaudio-module-bluetooth (1:4.0-0ubuntu10) ...
Processing triggers for libc-bin (2.19-0ubuntu2) ..
```

The system wants restart and I will do so after posting. 

Any enlightment regarding these would be helpful.
Fingers crossed, going for restart.

Edit : System restart gave no errors and everything seems to be running fine. :) So I will play a little -200 to 200 in Cafe !

---

### Post by su:bhatta on 2014-03-01
* bump *

---

### Post by su:bhatta on 2014-03-03
Really, nothing ?? 

Meanwhile, my Amarok sometimes fails to play wma files saying ' Windows Media audio 8 decoder' plugin is required. 

Have got Restricted-extras installed and last night it played the same track no problem !

---

### Post by mc4man on 2014-03-04
> **bhattabhishek said:**
> Really, nothing ?? 

Well you are running 14.04  studio with kde stuff...
Maybe take a look here, I'd see if there  was a kde.xml file about & remove it.

[https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/289592](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/289592)

As far as Amarok, haven't used since 1.x though wouldn't surprise me if it was inconsistent, even in Kubuntu

---

### Post by wgarcia on 2014-03-04
This is, as far as I know, innocuous. I've seen it in different updates in different Ubuntu versions. It seems it can be removed by:

```
sudo rm /usr/share/mime/packages/kde.xml 
sudo update-mime-database /usr/share/mime
```

---

### Post by Elfy on 2014-03-04
> **bhattabhishek said:**
> Really, nothing ?? 

Meanwhile, my Amarok sometimes fails to play wma files saying ' Windows Media audio 8 decoder' plugin is required. 

Have got Restricted-extras installed and last night it played the same track no problem !

Clementine refuses to play a wma here 

Parole plays it fine.

Make of that what you will.

---

### Post by su:bhatta on 2014-03-04
mc4man, wgarcia & Elfy  Thanks so much for the responses. I can have a little peace of mind. 

All I needed was something to show that I am not facing these problems singularly. 
As mentioned in the first post, there is as such no problems with my system.

And, yes mc4man, I have Kubuntu desktop installed in UStudio, which I run with Xfce when using auido applications and when am using my laptop for normal work, like now, I enter KDE DE. What player are you using currently, I want one which supports covers and have tried Clementine and Audacious before.

Elfy, another thing that is happening to me is that video playbacks are not working. Everytime I play any video, in any player, the system logs off, a report was generated and Bug reported, forgot to keep track of that one.

As, of now, video playback works only with VLC by turning off 'Accelarated Video output-overlay' from video settings. 

Marking the thread as Solved.
Thanks for your inputs.

---

