---
title: "Possible to scroll Raring left and right?"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by ping-wu on 2013-04-11
Since moving away from Precise, I lost the ability to scroll the screen left and right.  I miss it.  Is there any way to put it back to Raring?

This problem was solved.  Please see a separate thread:

[http://ubuntuforums.org/showthread.php?t=2134894&p=12600259#post12600259](http://ubuntuforums.org/showthread.php?t=2134894&p=12600259#post12600259)

---

### Post by grahammechanical on 2013-04-12
I am not sure what you mean by "scroll the screen left and right." Do you mean switch workspaces? This can be done in Raring by Ctrl+Alt+arrow key but it is disabled by default. Go to System Settings>Appearance>behaviour and tick the box for workspaces.

Regards.

---

### Post by dino99 on 2013-04-12
@graham

i've seen comments on webupd8 about what you also have posted above "System Settings -> Appearance"; i remember havint that Appearance icon some months ago, but now its gone on that RR i386 system. So i wonder about which package (setting) has been removed/changed on my system ?

---

### Post by mc4man on 2013-04-12
> **dino99 said:**
> @graham

i've seen comments on webupd8 about what you also have posted above "System Settings -> Appearance"; i remember havint that Appearance icon some months ago, but now its gone on that RR i386 system. So i wonder about which package (setting) has been removed/changed on my system ?
Does this work for you - 
```
gnome-control-center unity-appearance
```
If not then make sure that 
gnome-control-center-unity  is installed
(Obviously only useful for a ubuntu session

---

### Post by dino99 on 2013-04-12
> **mc4man said:**
> Does this work for you - 
```
gnome-control-center unity-appearance
```
If not then make sure that 
gnome-control-center-unity  is installed
(Obviously only useful for a ubuntu session

Thanks for the command line  .
Yes gcc-unity was installed; i've purged then reinstalled it, but still miss that icon. Something is borked as i get:

** (gnome-control-center:8963): WARNING **: Ignoring broken panel credentials (missing desktop file)

So that missing .desktop needs to be rebuilt (or copy/paste from yours)

---

### Post by mc4man on 2013-04-12
would be here- (though can't see why you wouldn't have??
/usr/share/applications/gnome-control-center-unity-appearance.desktop
```
[Desktop Entry]
Name=Appearance
Comment=Change the background and the theme
Exec=gnome-control-center unity-appearance
Icon=preferences-desktop-wallpaper
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Settings;DesktopSettings;X-GNOME-Settings-Panel;X-GNOME-PersonalSettings
OnlyShowIn=Unity;
X-GNOME-Settings-Panel=unity-appearance
# Translators: those are keywords for the appearance control-center panel
Keywords=Wallpaper;Background;Screen;Desktop;Theme;Appearance;Launcher;Unity;Menus;
X-Ubuntu-Gettext-Domain=gnome-control-center-unity
```

If you were to browse there should be seen at the top of folder. (Appearance),  & clickable from there

---

### Post by dino99 on 2013-04-12
Strangely that "Appearance" file was already there (owned by root), and has been opened by gedit, but "Settings" and X-Gnome-"Settings"-panel are red highlighted on the line 9 (Categories). I cant see typo (erased then rewritten, but still that issue).

note: that is shown when the "gedit view" is set to display ".desktop" (from Others mode). If the display mode is set as "plain texte" then nothing complaint.

---

### Post by ping-wu on 2013-04-12
Sorry I didn't make it clear.  What I meant is that in Raring, I lost the ability to move the screen horizontally with two fingers.  Instead, I have to resort to using the left and right curvor keys to shift the screen horizontally.

But thanks for a new trick that I never realized exists.   Learn something new everyday!

---

### Post by mc4man on 2013-04-12
> **dino99 said:**
> Strangely that "Appearance" file was already there (owned by root), and has been opened by gedit, but "Settings" and X-Gnome-"Settings"-panel are red highlighted on the line 9 (Categories). I cant see typo (erased then rewritten, but still that issue).

note: that is shown when the "gedit view" is set to display ".desktop" (from Others mode). If the display mode is set as "plain texte" then nothing complaint.
Don't think the highlighting matter, at a loss for your issue.
Does this open the panel (will report something about adwaita that is unimportant,

```
gtk-launch gnome-control-center-unity-appearance

```
(terminal usually needs exit afterwards

---

### Post by dino99 on 2013-04-12
the panel open, but no Appearance icon, and still get:
** (gnome-control-center:10062): WARNING **: Ignoring broken panel credentials (missing desktop file)
** (gnome-control-center:10062): WARNING **: Could not find settings panel "unity-appearance"

Thats strange, "Appearance" .desktop is created in the right place. I'm using Radiance as the theme.

note: Thanks for your help; as its not a show stopper anyway, and that partition will be formated later to get RR final when released, i'll continue as it is for now.

And have a good WE  :)

---

### Post by serdotlinecho on 2013-04-14
> **ping-wu said:**
> Sorry I didn't make it clear.  What I meant is that in Raring, I lost the ability to move the screen horizontally with two fingers.  Instead, I have to resort to using the left and right curvor keys to shift the screen horizontally.

But thanks for a new trick that I never realized exists.   Learn something new everyday!

Hello, ping-wu. 

I hope this will help you. Install unity-tweak-tool:

[IMG]http://i.imgur.com/1ocJyTtl.png[/IMG]

---

### Post by ping-wu on 2013-04-15
Thanks.  I "had been" so scared of Unity Tweak, I guess it's about time to give it a fresh "Raringly" look.

---

