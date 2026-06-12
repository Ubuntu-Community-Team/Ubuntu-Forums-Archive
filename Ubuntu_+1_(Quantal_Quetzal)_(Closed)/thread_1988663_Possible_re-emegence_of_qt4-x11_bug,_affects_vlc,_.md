---
title: "Possible re-emegence of qt4-x11 bug, affects vlc, maybe other apps"
date: 2012-05-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mc4man on 2012-05-28
I see it here though unlike when it first occurred in 11.10 dev it's not as widespread.
This time it only affects certain vlc windows, also it's possible that come A1 or so it will go away with some new packages (or maybe it won't

Edit: also, like before,  affects calibre

Like before overlay scrollbars are involved though not the source of the bug.
To see now if affected - 2 ways, the former is recoverable from, the latter isn't. Sometimes the 1st attempt below goes ok, after that not so

Open vlc > Media > Open Disc
or
Open vlc > Tools > Preferences > click on "Show Settings > all" radio button

If affected then workaround for normal usage of vlc until this either goes away or is fixed is to edit the Exec= line in vlc's .desktop
```
sudo gedit /usr/share/applications/vlc.desktop

```

I use this because I also want the menus in vlc
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc %U
```

To just 'fix' this
```
Exec=env LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc %U
```

Orig 11.10 bug
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303)

New bug for 12.10
[https://bugs.launchpad.net/bugs/1005677](https://bugs.launchpad.net/bugs/1005677)

For the curious  - what happens is the window has an impossible size - in the case of 'Open media'

> xwininfo: Window id: 0x1e0004b "Open Media"

  Absolute upper-left X:  -7566
  Absolute upper-left Y:  367
  Relative upper-left X:  3
  Relative upper-left Y:  3
  Width: 16383
  Height: 421
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +-7566+367  --7537+367  --7537-12  +-7566-12
  -geometry 16383x421+-7569-2

---

### Post by mc4man on 2012-05-30
Also see this as being a poor command to run here, (basically what's run when clicking on icon in messages indicator

```
ubuntuone-control-panel-qt
```

While this is ok
```
LIBOVERLAY_SCROLLBAR=0 ubuntuone-control-panel-qt
```

Edit new qt4* packages have fixed for ubuntuone here, vlc & repo calibre remain affected.
(new calibre release that has it's own qt libs runs fine (version 8.5.4

---

### Post by mc4man on 2012-06-13
Also now seen to affect the normal vlc window under some circumstances & Cola Git Gui - same deal, window is too large to open

cola ex.
> xwininfo: Window id: 0x3400012 "ffmpeg [master]"

  Absolute upper-left X:  59
  Absolute upper-left Y:  52
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 16383
  Height: 16383
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: NorthWestGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +59+52  --15162+52  --15162--15635  +59--15635
  -geometry 16383x16383+59+24

---

### Post by balloons on 2012-06-13
Hmm, any other apps that suffer from this -- I wonder what the fix was the first time around? This is going on the radar

---

### Post by mc4man on 2012-06-13
> **guitara said:**
> Hmm, any other apps that suffer from this -- I wonder what the fix was the first time around? This is going on the radarThe orig was fixed mainly in qt4-x11 but never did look at what was done (comment 103 [@ orig. bug]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/805303")

At least this time hopefully because of  the prior occurrence can get this taken care of a bit quicker.
ATM in all the seen occurances here using LIBOVERLAY_SCROLLBAR=0 whether from cli, editing the Exec= in the .desktop or adding an alias for cli use will prevent any possible  poor behavior

Other app previously inc. ReText &  Anki, there may have been others
(the upstream calibre is not affected as it provides it's own built-in  qt4 libs

---

### Post by matt_symes on 2012-06-15
Thanks mc4man. 

Gives me a place to start looking as to why VLC is not starting on my Precise->Quantal upgrade.

```

<snip>
QNativeImage: Unable to attach to shared memory segment. 
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
<snip>
```

Neither 

```
LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc
```

or 

```
QT_X11_NO_NATIVE_MENUBAR=1 LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc
```

provide any fix though.

The main window itself will not open.

---

### Post by mc4man on 2012-06-15
> **matt_symes said:**
> Thanks mc4man. 

Gives me a place to start looking as to why VLC is not starting on my Precise->Quantal upgrade.

```

<snip>
QNativeImage: Unable to attach to shared memory segment. 
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
X Error: BadDrawable (invalid Pixmap or Window parameter) 9
  Major opcode: 62 (X_CopyArea)
  Resource id:  0x0
<snip>
```

Neither 

```
LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc
```

or 

```
QT_X11_NO_NATIVE_MENUBAR=1 LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc
```

provide any fix though.

The main window itself will not open.
Maybe be something else but do this first, (if you haven't)

Open ~/.config/vlc & delete the qt conf file inside, then try vlc again from cli
(any time the 'bad window' tries to open that file must be deleted

---

### Post by matt_symes on 2012-06-15
> **mc4man said:**
> Maybe be something else but do this first, (if you haven't)

Open ~/.config/vlc & delete the qt conf file inside, then try vlc again from cli
(any time the 'bad window' tries to open that file must be deleted

Mc4man. You're a gent and a genius.

That did indeed fix the problem. 

Thanks.

---

### Post by mc4man on 2012-06-15
[QUOTE=matt_symes;12029379
That did indeed fix the problem. 

Thanks.[/QUOTE]

Then I'd adjust your vlc.desktop as in post 1. \(if you inadvertantly run vlc straightup & the problem comes back then again delete that file

The other less than ideal temp workaround is to switch the qt4 gui off of gtk, that's done in qt4-qtconfig ( sudo apt-get install qt4-qtconfig

See screen though I don't really like the non gtk gui's here

The anticipated history of this bug in 12.10 is it will languish until either inadvertently fixed or it becomes a big enough issue to garner some action.

---

### Post by chrissy.millichamp on 2012-08-24
Well, it didnt fix my problem.

---

### Post by chrissy.millichamp on 2012-08-24
This is what I get bascially as an error message in the terminal.
Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 ^AX Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 
X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0 X Error: BadDrawable (invalid Pixmap or Window parameter) 9   Major opcode: 62 (X_CopyArea)   Resource id:  0x0

---

### Post by mc4man on 2012-08-24
> **chrissy.millichamp said:**
> Well, it didnt fix my problem.
Well i'm pretty sure this is your issue, possibly you didn't fix right. see screen 1 where I've removed the fix, tried to open the playlist

So to start from the Top

Open a terminal copy & paste this command, press enter

```
gksudo gedit /usr/share/applications/vlc.desktop
```
scroll down & find the "Exec=vlc %U line"
Edit it to this if you haven't already - see screen 2
```
Exec=env LIBOVERLAY_SCROLLBAR=0 /usr/bin/vlc %U
```
Save & close gedit

**THEN before trying vlc again you need to delete** - Home folder > .config/vlc/vlc-qt-interface.conf  or just run this command in a terminal
```
mv ~/.config/vlc/vlc-qt-interface.conf ~/.local/share/Trash/files/
```
Then try opening vlc from the Dash or Unity launcher, [B]do NOT open vlc from a terminal like before
[/B]
**To open from a terminal** use this instead or do a bash_alias as mentioned in other thread

```
LIBOVERLAY_SCROLLBAR=0 vlc
```

**If you do not delete that file then the same bad behavior will occur**

If you actually can do the above & still no good then post the results of these 2 commands
```
ls ~/.local/share/applications
```
```
ls /usr/local/share/applications
```

---

### Post by mc4man on 2012-09-26
This is all fixed now with new overlay-scrollbar **&** gtk2 packages
(all currently in proposed

---

