---
title: "HowTo: Volume and Music Player Control during a Screensaver or a Fullscreen Game"
date: 2010-09-30
forum: Tutorials
---

### Post by undecim on 2010-09-30
I originally posted this on my Ubuntu blog at [http://blog.undecim.org/2010/09/volume-and-music-control-during-a-screensaver-or-fullscreen-game/](http://blog.undecim.org/2010/09/volume-and-music-control-during-a-screensaver-or-fullscreen-game/), but have reproduced the entire howto below:



How many times has this happened to you? You're playing music through your laptop speakers while working on something away from the computer. The phone rings, so you press the pause button on your keyboard and the screensaver password dialog comes up without stopping your music.

Or maybe you've started a fullscreen game like Stepmania or Globulation and decided that your volume is too high, but were unable to turn it down with the volume button on your keyboard? If you're Linux savvy, maybe you switched to a virtual console and used alsamixer to turn the volume down, only to find a static cursor sitting in the middle of your guxame window, forcing you to quit the game to get rid of it.

This is an annoyance that has been bugging me for some time, and for which I've recently found a fix. The reason that you cannot change your volume or control your music while a screensaver or a fullscreen SDL application is running is because both of those applications "capture" the keyboard, meaning that no other application on your desktop can listen to your keyboard, including your desktop environment which handles all the keyboard shortcuts in Ubuntu.

The solution is to make volume and media control something that is not dependent upon your graphical interface. There is a program called Gizmo Daemon or GizmoD in the Ubuntu repositories that is perfect for that. In nutshell, GizmoD lets you write python scripts that will check every input event (keystroke, mouse movement, etc) and run any code you wish. In this article, I will show you how to use Gizmod to control your volume and music player when your desktop environment would fail to do so.

First thing to do of course is install GizmoD from the Ubuntu repositories. Open a terminal and run

```
sudo aptitude install gizmod
```

While that's installing, let's go ahead and disable our desktop environment's keyboard shortcuts for volume and music control. In Gnome (i.e. the default Ubuntu desktop) go to System -&gt; Preferences -&gt; Keyboard shortcuts, and disable each volume control and music control shortcut so that your "Sound" section looks roughly like this:

[IMG]http://blog.undecim.org/wp-content/uploads/2010/09/KeyboardShortcuts.png[/IMG]

By now, GizmoD should be installed and ready to setup. However, as of writing this article there is a bug in the GizmoD package. It's configuration is stored in /etc/gizmod, but it looks for it in /usr/etc/gizmod. There is of course, a simple way to fix that: Add the /usr/etc directory and add a symbolic link to /etc/gizmod by running these two commands in a terminal:

```
sudo mkdir /usr/etc
sudo ln -s /etc/gizmod /usr/etc/
```

GizmoD comes with a lot modules, most of which you probably won't use. Since we will be running GizmoD as root, it's best to err on the side of caution and delete most of the scripts. The following command will remove every script from /etc/gizmod/modules, except for the debug script:

```
sudo rm /etc/gizmod/modules/{001..999}*
```

You will get a lot of "No such file or Directory" errors, but you can ignore those. If you typed the above command properly, you should only have one file and two directories in /etc/gizmod/modules.

Now we need to put some scripts into place. You will need to download [these PulseAudio control scripts]("http://undecim.org/downloads/view.download/6/30"), [this wrapper script]("http://undecim.org/downloads/view.download/6/32") and [this GizmoD module]("http://undecim.org/downloads/view.download/6/31"). Download these files to your home directory, extract the PulseAudio scripts to your home directory and run these commands:

```
sudo cp {pa{mute,vdown,vup},forallxdisp}.sh /usr/local/bin/
sudo chmod a+x /usr/local/bin/{pa{mute,vdown,vup},forallxdisp}.sh
sudo cp 198-KeyboardVolumeAndMusic.py /etc/gizmod/modules/
```

GizmoD should now be ready for a test run:

```
sudo -i gizmod &
```

Now try your volume control keys. You won't get a big OSD icon showing your current volume, but you will notice the change in the volume control applet on the toolbar. Play some music, lock your screen and try changing your volume.

Once you're satisfied with your new controls, you need to make sure GizmoD starts every time you start your computer. Press alt+f2 and type:

```
gksu gedit /etc/rc.local
```

Then put "gizmod &" on a new line before "exit 0", save the file, and exit.

UPDATE 1: Currently, there seems to be a bug in my GizmoD module that is not immediately noticeable. Sometimes, the music control keys will completely stop functioning until GizmoD is restarted by running "sudo -i killall gizmod; sudo -i gizmod &". The volume control keys still work consistently, however. I'm currently looking into this, but it seems impossible to reproduce predictably.

UPDATE 2: Okay, turns out it the only reason volume control was working in the first place was because of how I was testing. I've got [a small wrapper script]("http://undecim.org/downloads/view.download/6/32") that fixes this now, and have updated [the GizmoD script]("http://undecim.org/downloads/view.download/6/32")

---

### Post by undecim on 2010-10-19
Finally fixed the media control. It should all work now.

---

### Post by Apff on 2011-07-19
What about brightness control buttons ?

---

### Post by HunterZ on 2011-09-29
For Xfce it looks like you can disable the mute, volume down and volume up keys by using this for ~/.Xmodmap :

```
keycode 121 =
keycode 122 =
keycode 123 =
```I'm not sure if it's universal, but it works for both my laptop's built-in buttons and my Logitech G15 keyboard.

I haven't tried setting up gizmod yet (that's my next step) so I don't know if this will cause problems or not.


Update:

Got the gizmod part working too, although I haven't set it to automatically load on startup yet. There is also more useful info in the comments on the original blog post, although the post seems to have moved to [http://blog.undecim.org/volume-and-music-control-during-a-screensaver-or-fullscreen-game/](http://blog.undecim.org/volume-and-music-control-during-a-screensaver-or-fullscreen-game/)

---

