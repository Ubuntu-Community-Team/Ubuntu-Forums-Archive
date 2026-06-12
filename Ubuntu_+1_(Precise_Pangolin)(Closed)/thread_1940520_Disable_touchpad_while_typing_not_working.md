---
title: "Disable touchpad while typing not working?"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by x-shaney-x on 2012-03-13
I have the option enabled in system settings but it doesn't appear to be working at all.
As an example, I had to go back and correct this short posting 3 times because accidental touching of the pad moved the cursor back to the top line.

Synaptics touchpad.

---

### Post by mc4man on 2012-03-13
Works fine here, the only recent change was to disable in lightdm which should have no effect in a in use install

Check & see if the mouse plugin is enabled in g-s-d, look in dconf-editor as screen or to check
```
gsettings get org.gnome.settings-daemon.plugins.mouse active
```
If set to false then enable

```
gsettings set org.gnome.settings-daemon.plugins.mouse active true
```

(- The occurrences of cursor freeze due to g-s-d starting a 2nd instance of syndaemon have dropped dramatically, a permanent fix is in the works

---

### Post by mcellius on 2012-03-13
I have had the same problem.  I downloaded and installed touchpad-indicator and set it to run on startup and disable the touchpad, and it works perfectly.  It's the only way I've found to reliably deal with the problem.

sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator

Then open it in the Dash and set its settings from the icon in the panel.

---

### Post by x-shaney-x on 2012-03-14
@ mc4man

Tells me the plugin is set to true already. 
I have an 11.10 install and was using that late last night and didn't suffer the problems there.


@ mcellius

I tend to switch between touchpad and mouse but generally use touchpad more lately so disabling it isn't really an option to me.

---

### Post by mc4man on 2012-03-14
There is a new gnome-settings-daemon upgrade today, install it, log out/in & see if it improves

If not try this to test,
Open system settings & disable the option
Open a terminal, run this, leave the terminal open (command will exit when terminal is closed), & see if it then works while command is running

```
syndaemon -i 0.5 -K -R
```

---

### Post by x-shaney-x on 2012-03-14
The update didn't solve anything :(

However, I have done some tests:

Disabled the option started typing in a document with one hand and started nudging and moving the touchpad with the other.
The pointer moved around throughout.

I then enabled the option and did the same.
For a split second there was no pointer movement then I was able to move the pointer freely despite still typing.

I then tried disabling again and used the synclient command:
A longer pause before I was able to move the pointer then the movement would come and go, which is pretty much what I would expect it to do and what happens in 11.10 with the option enabled.

So the option clearly is doing something but I wouldn't say it's working properly.

---

### Post by mc4man on 2012-03-14
Kinda wierd that it's not *really* working for you, may be some hardware specific glitch

I guess you could try some 3rd party app or maybe it'll just start working at some point (fresh install

You could try creating a new user & see if it works there or boot to a live session & check

Worst case you could disable in System Settings & run syndaemon thru a Startup

To do locally something like
```
mkdir -p ~/.config/autostart && gedit ~/.config/autostart/syndaemon.desktop
```

```
[Desktop Entry]
Type=Application
Exec=syndaemon -d -K -R -i [COLOR="Blue"]0.5[/COLOR]s
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=touchpad1
X-GNOME-Autostart-Delay=5
```

If you wanted more or less of a delay till mouse movement is returned then adjust blue, 1/2 sec is pretty much seamless, some people prefer a longer delay
Before logging out open up 'power cog' > Startup Applications & make sure "touchpad1" is enabled, (or whatever you use for Name= in the .desktop), usually it is already

---

### Post by x-shaney-x on 2012-03-14
Thing is I can live with it for now and will assume it's something I have done at some point.
I do tend to use these dev releases for experimenting with apps and stuff before trying them in my "proper" install so I may have messed something up somewhere.

---

### Post by x-shaney-x on 2012-03-14
Hmm, I just discovered that it actually works properly after disabling 2-finger scrolling.

I normally always use 2 finger scrolling and have never actually tried edge scrolling (which is the unity default).

I'll give this a go for a while and see if I take to it and if not, maybe the disable while typing problem will have gone away :)

---

### Post by x-shaney-x on 2012-03-16
The problem has now gone away.
I am not sure exactly what fixed it but I have noticed evdev and libtouch updates in the past couple of days so may be connected to one of those.

---

