---
title: "How to activate DBus-interface in the VLC media-player?"
date: 2013-02-02
forum: Ubuntu Development Version
---

### Post by moma on 2013-02-02
EDIT: This issue was solved by updating VLC from a PPA (package archive).  
Ref: [https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)
Let's hope Ubuntu will update its final version of VLC from this PPA.
------------------

Hello,
How do I activate DBus-interface in the VLC media-player?
I want VLC to show up in the sound-menu. Also audio-recorder needs messages from the DBus. 

Earlier it was easy to set via VLC's menu: 
Tools -> Preferences -> Show all -> Interface -> Control Interface and Enable DBus.

But I cannot find this option anymore.

$ cat /etc/issue
Ubuntu Raring Ringtail (development branch) \n \l

$ vlc --version
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)

Audio-recorder:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)

---

### Post by zika on 2013-02-02
> **moma said:**
> Hello,
How do I activate DBus-interface in the VLC media-player?
I want VLC to show up in the sound-menu. Also audio-recorder needs messages from the DBus. 

Earlier it was easy to set via VLC's menu: 
Tools -> Preferences -> Show all -> Interface -> Control Interface and Enable DBus.

But I cannot find this option anymore.

$ cat /etc/issue
Ubuntu Raring Ringtail (development branch) \n \l

$ vlc --version
VLC media player 2.0.5 Twoflower (revision 2.0.5-0-g1661b7d)

Audio-recorder:
[https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder)
Is it:```
/usr/bin/vlc -I dummy --control dbus
```...?
I've just checked and it is open by default in GS...

---

### Post by mc4man on 2013-02-02
it should be auto-enabled. If not then do so in in dconf (dconf-editor > 
com.canonical.indicator.sound interested-media-players

(sometimes in lieu of above just opening vlc > tools > preferences, changing anything & saving that change will add vlc to sound menu next time opened

edit: for reference - [http://forum.videolan.org/viewtopic.php?f=13&t=107797](http://forum.videolan.org/viewtopic.php?f=13&t=107797)

---

### Post by moma on 2013-02-02
Ok, thank you.

This works fine:
$ [COLOR="DarkGreen"]vlc --control dbus[/COLOR]
Sound-menu now shows all controls for VLC. Good.
Audio-recorder also receives correct messages form VLC.

But when I close VLC, the sound-menu still (correctly) displays "VLC media player". If I start VLC from it, the player obviously fires without "--control dbus" option and looses its Dbus-capability (and the controls won't work). 

VLC should absolutely have a permanent option for the sound-menu (for the DBus). **This is not going to work**. Something has gone wrong.

Many applications except to see MPRIS2-messages (like org.mpris.MediaPlayer2.vlc) on the DBus.

@mc4man: Thanks for the link. That explains a lot.
"vlc" is already in the interested-media-players list. I even tried "vlc --control dbus".

---

### Post by mc4man on 2013-02-02
You could test some of the simple (supported??) with either types - 
Ex.'s, add a few tracks to vlc

```
qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Play
qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Pause
```
ect.

or the variant - 
```
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Previous
```
ect.

---

### Post by moma on 2013-02-02
Hello,
The commands of course fail when VLC is started without DBus-interface. 
$ [COLOR="DarkGreen"]vlc[/COLOR]

$ qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Stop

Service 'org.mpris.MediaPlayer2.vlc' does not exist.
etc. many similar error messages.
------------

The commands works well if VLC is started with --control dbus.
$ [COLOR="DarkGreen"]vlc --control dbus[/COLOR]

$ qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Play

All these work: Play,Stop,Pause,Next,Previous

Also this:
$ qdbus org.mpris.MediaPlayer2.vlc /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Quit
-------------

So the question is: Will Ubuntu 13.04 come with VLC whose DBus-interface is auto-enabled? This is a very important issue. **VLC cannot integrate with Unity (and its sound-menu or audio-recorder of all!) without DBus.**

---

### Post by mc4man on 2013-02-02
> **moma said:**
> 
So VLC should absolutely have a permanent option for the sound-menu (for the DBus). **This is not going to work**. Something has gone wrong.

Many applications except to see MPRIS2-messages (like org.mpris.MediaPlayer2.vlc) on the DBus.

@mc4man: Thanks for the link. That explains a lot.
"vlc" is already in the interested-media-players list. I even tried "vlc --control dbus".

Vlc is permanent here, only seen as 'vlc', in dconf (screen

have you tried a log out after adding to dconf?

---

### Post by moma on 2013-02-02
Re-hi,
Yes, I just did re-login. The login-screen has started to speak ;-)

No change. The "vlc" command itself fails to activate DBus. So does the sound-menu.

[[img]http://bildr.no/thumb/1382765.jpeg[/img]](http://bildr.no/view/1382765)

I have installed various media-players to test the audio-recorder for Raring. Looks good.
EOL.

---

### Post by mc4man on 2013-02-02
Try a little experiment - 
(you could use a hatchet job on your current user, ie. move ~/.config/dconf/user to a .bak, & remove ~/.config/vlc/vlcrc, log out/in, ect. but try instead - 

Set up a new user (apologizes for gnome dev's thinking a 9 char password is needed..
Log in to new user, open vlc > tools > pref's, enable something like 'one instance', save, close vlc.
log out/in, is vlc in the sound menu?

---

### Post by zika on 2013-02-03
> **moma said:**
> So the question is: Will Ubuntu 13.04 come with VLC whose DBus-interface is auto-enabled? This is a very important issue. **VLC cannot integrate with Unity (and its sound-menu or audio-recorder of all!) without DBus.**
It does on this machine... As I said already...

---

### Post by moma on 2013-02-03
Olá,
Zika and mc4man: I will keep eye on this issue. I'll come back if I find what's going on with this VLC and Raring installation. Especially porque the DBus was not activated by default.

Just for info and later review. The installed VLC-packages are: 
$ [COLOR="DarkGreen"]dpkg -l | grep -i vlc[/COLOR]
```
ii  libvlc5  2.0.5-1 i386 multimedia player and streamer library

ii  libvlccore5   2.0.5-1  i386 base library for VLC and its modules

ii  vlc  2.0.5-1  i386 multimedia player and streamer

ii  vlc-data  2.0.5-1  all Common data for VLC

ii  vlc-nox  2.0.5-1  i386  multimedia player and streamer (without X support)

ii  vlc-plugin-notify  2.0.5-1  i386 LibNotify plugin for VLC

ii  vlc-plugin-pulse  2.0.5-1  i386  PulseAudio plugin for VLC
```

---

### Post by zika on 2013-02-03
> **moma said:**
> Olá,
Zika and mc4man: I will keep eye on this issue. I'll come back if I find what's going on with this VLC and Raring installation. Especially porque the DBus was not activated by default.

Just for info and later review. The installed VLC-packages are: 
$ [COLOR="DarkGreen"]dpkg -l | grep -i vlc[/COLOR]
```
ii  libvlc5  2.0.5-1 i386 multimedia player and streamer library

ii  libvlccore5   2.0.5-1  i386 base library for VLC and its modules

ii  vlc  2.0.5-1  i386 multimedia player and streamer

ii  vlc-data  2.0.5-1  all Common data for VLC

ii  vlc-nox  2.0.5-1  i386  multimedia player and streamer (without X support)

ii  vlc-plugin-notify  2.0.5-1  i386 LibNotify plugin for VLC

ii  vlc-plugin-pulse  2.0.5-1  i386  PulseAudio plugin for VLC
```You just reminded me, I have ppa:videolan/master-daily turned on...

---

### Post by mc4man on 2013-02-03
> **moma said:**
> Olá,
 I'll come back if I find what's going on with this VLC and Raring installation. Especially porque the DBus was not activated by default.

If you do (come back), it would be of some interest here to know how does AR start a player when it's set as the source ? (either from autostart or from AR window
Seems to run the binary?? vs. the .desktop which the sound menu uses in some manner 

(only of interest here because I prefer media players to retain their menus which is done thru an env in their .desktops

Edit: semi confirmed here that AR uses the binary, I have audacious in /opt/bin & AR would always 'lose' it on a restart. If I symlink audacious in /usr/bin then AR keeps aud in it's avail. players list.
No way to have AR use gtk-launch <player> instead??

---

### Post by moma on 2013-02-06
Hello and desculpe for the late reply.

I updated VLC from the PPA and it now behaves correctly within the sound-menu and a.r.
Ref: [https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

Now the version number is 2.1.0.
$ [COLOR="DarkGreen"]dpkg -l | grep -i vlc[/COLOR]
```
ii  libvlc5 2.1.0~~git20130206+r2423-0~r92~raring1
ii  libvlccore5 2.1.0~~git20130206+r2423-0~r92~raring1
ii  vlc  2.1.0~~git20130206+r2423-0~r92~raring1
...
ii  vlc-plugin-pulse
```

Obrigado, the updated version of VLC fixed this bug.
---

>>If you do (come back), it would be of some interest here 
>>to know how does AR start a player when it's set as the 
>>source ? 

The very recent version of a.r (in the Launchpad.net) uses the xxx.desktop file to load both the player's name and exec command with possible arguments. So the xxx.desktop file determines everything. This applies to the very latest code that you find in the [https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder).

[[You may currently use an older a.r that simply guesses the name of executable from player's service-name.]]

Audio-recorder uses the MPRIS2-standard (DBus-command: "DesktopEntry") to ask the name of player's .desktop file. I am sure the sound-menu does exactly the same thing.

Look for "DesktopEntry" in this file:
[http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/dbus-mpris2.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/dbus-mpris2.c)

Please see also function mpris2_start_app(gpointer player_rec) in the same source. It starts the player when needed. It will finally call the exec_command_async() function. That is defined in the src/utility.c file.

We should improve the function so it also brings the window to the front. Seems like the MediaPlayer2 (MPRIS2 base object) actually defines a Raise() method.
See: [http://specifications.freedesktop.org/mpris-spec/latest/Media_Player.html](http://specifications.freedesktop.org/mpris-spec/latest/Media_Player.html)
We could simply call it. Hopefully media-players implement this method too.

>No way to have AR use gtk-launch <player> instead??
An interesting suggestion. 
This would need an option in the settings of a.r. Would you support that?

And thanks so far. Very good result.

---

### Post by mc4man on 2013-02-06
Was likely using r294, latest (r303) definitely does use the .desktop.
(however it won't be able to use an Exec= that passes an env, no big deal though, don't think too many users care about such.
In any event solved here by making the Exec= point to a script that exports QT_X11_NO_NATIVE_MENUBAR=1 & starts vlc which AR is fine with in the .desktop.

Ot - The sound-indicator opens listed apps in a different fashion so having an env in the .desktop isn't an issue & it's properly passed.
(maybe in mpris2-interfaces.vala

---

