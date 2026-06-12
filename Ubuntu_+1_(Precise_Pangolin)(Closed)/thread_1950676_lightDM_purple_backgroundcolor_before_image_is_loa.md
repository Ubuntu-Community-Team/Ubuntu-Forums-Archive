---
title: "lightDM purple backgroundcolor before image is loaded"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sacridex on 2012-04-01
Hello,

as the topic says, lightdm has a purple background before the acutal background image is loaded... [pls subscribe the bug report(click).]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/970024")
This is pretty annoying if you dont like the purple background theme of Ubuntu.

Also, is there a way to disable the lightdm startup sound?

thx

---

### Post by lucazade on 2012-04-01
> **sacridex said:**
> Hello,

as the topic says, lightdm has a purple background before the acutal background image is loaded... [pls subscribe the bug report(click).]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/970024")
This is pretty annoying if you dont like the purple background theme of Ubuntu.

Also, is there a way to disable the lightdm startup sound?

thx

you need to patch lightdm sources because that purple bg is hardcoded.

---

### Post by sacridex on 2012-04-01
> **lucazade said:**
> you need to patch lightdm sources because that purple bg is hardcoded.
Thats what i expected.
But it looks really ugly, if you have changed grub and plymouth backgroundcolor(both black) and lightdm background image to non purple...

I actually tried to lookup the lightdm code by myself, but i'm kinda overstrained by looking up such a huge amount of code. :(

---

### Post by lucazade on 2012-04-01
> **sacridex said:**
> Thats what i expected.
But it looks really ugly, if you have changed grub and plymouth backgroundcolor(both black) and lightdm background image to non purple...

I actually tried to lookup the lightdm code by myself, but i'm kinda overstrained by looking up such a huge amount of code. :(

in fact i've changed grub, plymouth and lightdm background color :)

---

### Post by sacridex on 2012-04-01
> **lucazade said:**
> lightdm background color :)
how?

---

### Post by lucazade on 2012-04-01
```
--- unity-greeter-0.2.6.orig/src/background.vala
+++ unity-greeter-0.2.6/src/background.vala
@@ -223,7 +223,7 @@ public class Background : Gtk.Fixed
         GRID,
     }
 
-    public string default_background {get; set; default = "#2C001E";}
+    public string default_background {get; set; default = "#000000";}
     public string? current_background {get; set; default = null;}
     public bool draw_grid {get; set; default = true;}
     public double alpha {get; private set; default = 1.0;}
--- unity-greeter-0.2.6.orig/src/main-window.c
+++ unity-greeter-0.2.6/src/main-window.c
@@ -921,7 +921,7 @@ static GObject * main_window_constructor
 	_tmp3_ = accel_group;
 	gtk_window_add_accel_group ((GtkWindow*) self, _tmp3_);
 	memset (&bg_color, 0, sizeof (GdkRGBA));
-	gdk_rgba_parse (&bg_color, "#2C001E");
+	gdk_rgba_parse (&bg_color, "#000000");
 	_tmp4_ = bg_color;
 	gtk_widget_override_background_color ((GtkWidget*) self, GTK_STATE_FLAG_NORMAL, &_tmp4_);
 	_tmp5_ = gtk_widget_get_accessible ((GtkWidget*) self);
--- unity-greeter-0.2.6.orig/src/background.c
+++ unity-greeter-0.2.6/src/background.c
@@ -2604,7 +2604,7 @@ static void background_class_init (Backg
 static void background_instance_init (Background * self) {
 	gchar* _tmp0_;
 	self->priv = BACKGROUND_GET_PRIVATE (self);
-	_tmp0_ = g_strdup ("#2C001E");
+	_tmp0_ = g_strdup ("#000000");
 	self->priv->_default_background = _tmp0_;
 	self->priv->_current_background = NULL;
 	self->priv->_draw_grid = TRUE;
--- unity-greeter-0.2.6.orig/src/main-window.vala
+++ unity-greeter-0.2.6/src/main-window.vala
@@ -37,7 +37,7 @@ public class MainWindow : Gtk.Window
         add_accel_group (accel_group);
 
         var bg_color = Gdk.RGBA ();
-        bg_color.parse ("#2C001E");
+        bg_color.parse ("#000000");
         override_background_color (Gtk.StateFlags.NORMAL, bg_color);
         get_accessible ().set_name (_("Login Screen"));
         has_resize_grip = false;
```

---

### Post by bmbaker on 2012-04-01
how did you change the color in plymouth and lightdm?
cheers :-)

---

### Post by sacridex on 2012-04-01
/lib/plymouth/themes/default.grub for the grub background
```
if background_color 0,0,0; then
[...]
```you have to run update-grub afterwards

/lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script for plymouth
```
[...]
Window.SetBackgroundTopColor (0.00, 0.00, 0.00);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.00, 0.00, 0.00);  # an equally nice colour on the bottom
[...]
```


edit:
@lucazade: thanks, im trying to replace it. ;)

---

### Post by cottfcfan on 2012-04-04
Sacridex..
If you manage to solve the Lightdm background issue, please post back.
This issue bugged me in 11.10 & is still not fixed.

---

### Post by sacridex on 2012-04-04
I just changed the color in the code(like lucazade described).
Get the code, change the two colors (from #2C001E to #000000) in the background.vala and main-window.vala file, then configure, make, make install it. (the .c files do not need to be changed, they are newly created by the vala compiler).

EDIT: I cut the flaming. ;)
Figured out how to solve the problem. ^^

---

### Post by cottfcfan on 2012-04-04
Ive changed the grub background by editing the /etc/default/grub file & changed the plymouth theme.
But what file needs changing to change the login screen background?

---

### Post by sacridex on 2012-04-04
> **cottfcfan said:**
> But what file needs changing to change the login screen background?
Ah sry, now i know what you mean.
It's in "/etc/lightdm/unity-greeter.conf", just edit the specific line for the background(Only in 11.10 not in 12.04).

I now have kinda fixed the background color thing, but with the new unity-greeter version, the standard background image will be loaded afterwards and THEN it will fade to your own background image sigh...
Anyways, i uploaded a patch file to the bugreport.
I would appreciate you testing it. It is my first patch ever. ;)

---

### Post by cottfcfan on 2012-04-04
Hi Sacridex
I already changed the Background= in that file to one of my choice, but it doesn't stop the purple background coming up 1st, and spoiling my blue plymouth theme & login screen.
Is there a workaround for that?

---

### Post by sacridex on 2012-04-04
Hello again,

i think i fixed both bugs now(purple background color and the pink image issue).
[Here]("https://bugs.launchpad.net/unity-greeter/+bug/970024") is the bug report again, pls test my fix. ;)

Thanks

---

### Post by cottfcfan on 2012-04-05
Sacridex..
I checked out your bug report, and saved your fix as a file, in /etc/lightdm. Calling the file greeter-bottom-color.conf, which is where I assume it should be.
After reboot, the purple colour is still there.
Have I saved the file to the right directory? and does anything need editing within the file?
Sorry for the questions, but I never generally mess with code or files like this.

---

### Post by sacridex on 2012-04-05
> **cottfcfan said:**
> Sacridex..
I checked out your bug report, and saved your fix as a file, in /etc/lightdm. Calling the file greeter-bottom-color.conf, which is where I assume it should be.
After reboot, the purple colour is still there.
Have I saved the file to the right directory? and does anything need editing within the file?
Sorry for the questions, but I never generally mess with code or files like this.
You have to apply the patch to unity-greeter, too.
And i dont know if it works with the old Ubuntu 11.10 version, i doubt it.
I'm gonna try today.

---

### Post by sacridex on 2012-04-05
So... i installed Ubuntu 11.10 and i had the bug, too.
You have to get the sources via "apt-get source unity-greeter", then change all the #2C001E to your desired color(in src/unity-greeter.vala and src/user-list.vala). [Afterwards build the code and install it]("http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html").
I didnt test it, but it should work.

---

### Post by MacUntu on 2012-04-05
I wouldn't do it like linked.

Rather bump the version string in 'debian/changelog' and do: ```
debuild -us -uc
``` That will give you package files in the parent directory that you can install. Makes removal/downgrades much easier.

---

### Post by sacridex on 2012-04-05
nvm what i wrote, it was my own failure.
It works with a .deb installation, too.

---

### Post by NHclimber on 2012-04-05
> **sacridex said:**
> If i build a package and install from it, nothing is changing.
I have to build and install by hand, dunno why.

Any ideas?

What's the output when you try to install a *.deb file that you've built? Eg.
```
sudo dpkg -i blahblah-3.2.0-1ubuntu2.deb
<what's here?>
```

---

### Post by MacUntu on 2012-04-05
In my case it's:
```
$ sudo dpkg -i unity-greeter_0.2.7-0ubuntu2~depurpled_amd64.deb 
(Reading database ... 370771 files and directories currently installed.)
Preparing to replace unity-greeter 0.2.7-0ubuntu1 (using unity-greeter_0.2.7-0ubuntu2~depurpled_amd64.deb) ...
Unpacking replacement unity-greeter ...
Setting up unity-greeter (0.2.7-0ubuntu2~depurpled) ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...

```

---

### Post by mc4man on 2012-04-06
> **sacridex said:**
> Hello again,

i think i fixed both bugs now(purple background color and the pink image issue).
[Here]("https://bugs.launchpad.net/unity-greeter/+bug/970024") is the bug report again, pls test my fix. ;)

Thanks
It builds up ok though does introduce some new warnings (significant, don't know

At the end of the day, unless I'm missing something, it just allows changing the color of a moment that shouldn't be occuring in the first place.

At least here, once the custom screen greeter landed some time ago, it worked perfectly for all of the 1st. 2 weeks, if that. Since then it's been one thing or another ..

---

### Post by sacridex on 2012-04-10
> **mc4man said:**
> At the end of the day, unless I'm missing something, it just allows changing the color of a moment that shouldn't be occuring in the first place.
Yeah. But its still better then the way it behaves at the moment.

Well, anyone knows if the bug will get fixed until the final release?
In my opinion a purple background and afterwards the standard wallpaper fading to the user selected one is not pixel perfect at all. :(

---

### Post by mc4man on 2012-04-10
> **sacridex said:**
> Yeah. But its still better then the way it behaves at the moment.

Well, anyone knows if the bug will get fixed until the final release?
In my opinion a purple background and afterwards the standard wallpaper fading to the user selected one is not pixel perfect at all. :(

I haven't searched to see if there is a bug on - would think there is because it's completely obvious & apparently widespread

The other thing that happens here occasionally is after entering the password the fade out/in to Desktop sometimes goes black - that seems somehow connected to having multiple 12.04 installs (maybe 11.10 also  - don't know, don't have one

(- i did file on that when it started here but think I'll mark invalid
When it first started happening using enter key always was good, clicking > always went black.
With a couple of fresh installs I now see that doesn't hold true

---

### Post by NHclimber on 2012-04-13
> **sacridex said:**
> In my opinion a purple background and afterwards the standard wallpaper fading to the user selected one is not pixel perfect at all. :(

You're seeing the default wallpaper in between the solid background and the user-configured one? Can you post the contents of /var/log/lightdm/x-0-greeter.log? (only the user name is revealed and you could redact that if req'd)

If the default wallpaper *is* showing, you can set it to what you want with the following commands
```
sudo su
xhost +SI:localuser:lightdm
sudo su lightdm -s /bin/bash
gsettings set com.canonical.unity-greeter background '/usr/share/backgrounds/awesome_.png'
exit
exit
```*Edit: FWIW, for anyone that does askubuntu, there's a bounty being offered for this answer *[http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm](http://askubuntu.com/questions/64001/how-do-i-change-the-wallpaper-in-lightdm)[I](you also need to indicate that lightdm doesn't have backgrounds -- only the greeters do)
[/I]
Note: the single quotes are required for strings. Obviously, permissions to the file must be appropriate for the lightdm user; this means don't set the background to a file in your home directory.

While logged as the lightdm user, these commands will shed some light on other configurable items in the greeter:
```
gsettings list-keys com.canonical.unity-greeter
gsettings get com.canonical.unity-greeter draw-grid
gsettings get com.canonical.unity-greeter font-name
<etc.>
```

---

### Post by sacridex on 2012-04-15
Here is my /var/log/lightdm/x-0-greeter.log:
```

** (process:1293): WARNING **: unity-greeter.vala:806: Error starting the at-spi registry: Kindprozess »/usr/lib/at-spi2-core/at-spi-bus-launcher« konnte nicht ausgeführt werden (Datei oder Verzeichnis nicht gefunden)
[+0,00s] DEBUG: unity-greeter.vala:814: Starting unity-greeter 0.2.7 UID=104 LANG=de_DE.UTF-8
[+0,00s] DEBUG: unity-greeter.vala:817: Setting cursor
[+0,00s] DEBUG: unity-greeter.vala:821: Creating background surface
[+0,00s] DEBUG: unity-greeter.vala:824: Loading command line options
[+0,00s] DEBUG: unity-greeter.vala:852: Setting GTK+ settings
[+0,09s] DEBUG: unity-greeter.vala:875: Creating Unity Greeter
[+0,09s] DEBUG: Connecting to display manager...
[+0,09s] DEBUG: Wrote 17 bytes to daemon
[+0,09s] DEBUG: Read 8 bytes from daemon
[+0,09s] DEBUG: Read 120 bytes from daemon
[+0,09s] DEBUG: Connected version=1.2.0 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0,16s] WARNING: unity-greeter.vala:130: Failed to load state from /var/lib/lightdm/.cache/unity-greeter/state: Die Schlüsselwertedatei enthält die Zeile »&#65533;&#65533;&#65533;«, welche kein zulässiges Schlüssel-Wert-Paar, keine Gruppe und kein Kommentar ist.

[+0,22s] DEBUG: menubar.vala:318: LANG=de_DE.UTF-8 LANGUAGE=(null)
[+0,35s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0,35s] DEBUG: get entries
[+0,36s] DEBUG: menubar.vala:511: Adding indicator object 0x841a1dc at position 0
[+0,36s] DEBUG: Evaluating bitmask for '%H:%M'
[+0,36s] DEBUG: Checking against 1 possible times
[+0,50s] DEBUG: Guessing max time width: 36
[+0,50s] DEBUG: get entries
[+0,50s] DEBUG: menubar.vala:511: Adding indicator object 0x847901c at position 1
[+0,51s] WARNING: IndicatorObject class does not have an accessible description.
[+0,52s] WARNING: IndicatorObject class does not have an accessible description.
[+0,52s] DEBUG: get entries
[+0,52s] DEBUG: get entries
[+0,52s] DEBUG: menubar.vala:511: Adding indicator object 0x836b52c at position 2
[+0,52s] DEBUG: menubar.vala:335: LANG=de_DE.UTF-8 LANGUAGE=(null)
[+0,53s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, Diese Sitzung meldet Sie bei Ubuntu an)
[+0,53s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0,53s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0,55s] DEBUG: Ignoring session /usr/share/xsessions/gnome-shell.desktop
[+0,55s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0,55s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0,79s] DEBUG: Setting keyboard layout to 'de'
[+0,84s] DEBUG: main-window.vala:98: Screen is 1024x768 pixels
[+0,84s] DEBUG: main-window.vala:104: Monitor 0 is 1024x768 pixels at 0,0
[+0,85s] DEBUG: Loading users from org.freedesktop.Accounts
[+0,85s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0,89s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0,89s] DEBUG: unity-greeter.vala:325: Adding/updating user bob (bob)
[+0,89s] DEBUG: unity-greeter.vala:184: Adding guest account entry
[+1,16s] DEBUG: unity-greeter.vala:494: Failed to write state: Fehler beim Schreiben in Datei: Ungültige Adresse
[+1,16s] DEBUG: Starting authentication for user bob...
[+1,16s] DEBUG: Wrote 19 bytes to daemon
[+1,17s] DEBUG: unity-greeter.vala:878: Showing greeter
[+1,17s] DEBUG: unity-greeter.vala:350: Showing main window
[+1,17s] DEBUG: New style for time label
[+1,18s] DEBUG: Evaluating bitmask for '%H:%M'
[+1,18s] DEBUG: Checking against 1 possible times
[+1,18s] DEBUG: Guessing max time width: 36
[+1,20s] DEBUG: background.vala:315: Regenerating backgrounds
[+1,20s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1024x768
[+1,20s] DEBUG: New style for time label
[+1,20s] DEBUG: Evaluating bitmask for '%H:%M'
[+1,20s] DEBUG: Checking against 1 possible times
[+1,20s] DEBUG: Guessing max time width: 36
[+1,21s] DEBUG: unity-greeter.vala:891: Starting main loop
[+1,21s] DEBUG: Read 8 bytes from daemon
[+1,21s] DEBUG: Read 33 bytes from daemon
[+1,21s] DEBUG: Prompt user with 1 message(s)
[+1,21s] DEBUG: settings-daemon.vala:97: Could not start gnome-settings-daemon over DBus: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Keine derartige Schnittstelle »org.gnome.SettingsDaemon« des Objekts im Pfad /org/gnome/SettingsDaemon
[+1,52s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/Precise_Pangolin_by_Vlad_Gerasimov.jpg at 1024x768
[+1,55s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Keine derartige Schnittstelle »com.canonical.dbusmenu« des Objekts im Pfad /com/canonical/indicator/users/menu
[+1,59s] DEBUG: Setting keyboard layout to 'de'
[+1,94s] MESSAGE: Couldn't get devices: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Keine derartige Schnittstelle »org.gnome.SettingsDaemon.Power« des Objekts im Pfad /org/gnome/SettingsDaemon/Power

[+1,94s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+1,94s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+1,94s] DEBUG: should_be_visible: no
[+1,94s] DEBUG: menubar.vala:519: Removing indicator object 0x836b4d4
[+1,94s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1,94s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1,94s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1,94s] WARNING: menubar.vala:531: Indicator object 0x836b4d4 not in menubar
[+1,97s] DEBUG: notify visible signal received
[+1,97s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1,98s] DEBUG: New calendar item
[+2,08s] DEBUG: unity-greeter.vala:310: starting system-ready sound
[+2,37s] DEBUG: indicator-sound: new_volume_slider_widget
[+2,38s] DEBUG: indicator-sound: new_voip_slider_widget
[+2,46s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+2,48s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/Precise_Pangolin_by_Vlad_Gerasimov.jpg complete
[+4,37s] DEBUG: Providing response to display manager
[+4,37s] DEBUG: Wrote 19 bytes to daemon
[+4,48s] DEBUG: Read 8 bytes from daemon
[+4,48s] DEBUG: Read 15 bytes from daemon
[+4,48s] DEBUG: Authentication complete for user bob with return code 0
[+4,49s] DEBUG: Starting session ubuntu
[+4,49s] DEBUG: Wrote 18 bytes to daemon
```

I know that i can change the background that way(logging in as lightdm user), but i think it would ask too much from an unexperienced user. So it would be better, if the "standard background" isn't shown at all.

My [provided patch]("https://bugs.launchpad.net/unity-greeter/+bug/970024") would avoid the standard background situation and make the solid backgroundcolor editable via config file. Which is a bit easier for new users to handle(just edit a color value in a config file).

---

### Post by georgelappies on 2012-04-17
How can one revert back to the standard way it was? Is there a way to reinstall packages and tell them to delete all current config files etc. and replace them with the defaults?

EDIT

Managed to do it by:

```

$sudo mv /lib/plymouth//themes/default.grub /lib/plymouth//themes/default.grub.backup
$sudo mv /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script.backup
$sudo apt-get -o Dpkg::Options::="--force-confmiss" install --reinstall plymouth-theme-ubuntu-logo
$sudo update-grub

```

and then reboot

---

### Post by sacridex on 2012-04-23
I did some more changes, and proposed my [branch]("https://code.launchpad.net/%7Esacridex/ubuntu/precise/unity-greeter/purple-background-on-startup-fix") for merging.
Pls review it.

---

