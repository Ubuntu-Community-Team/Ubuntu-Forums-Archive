---
title: "I just noticed I cant change themes."
date: 2012-06-20
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-06-20
Appearance doesn't work, gnome-tweak-tool has a bug that stops it starting and myunity has no version for 12.10.

[https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1014633](https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1014633)

---

### Post by JMB74 on 2012-06-20
Comment out line #48 in /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_nautilus.py and I think gnome-tweak-tool will work again?

```
TWEAKS = (
    DesktopIconTweak(group_name=TWEAK_GROUP_DESKTOP),
[COLOR=Blue]#    GSettingsSwitchTweak("org.gnome.nautilus.desktop", "computer-icon-visible",[/COLOR] schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
    GSettingsSwitchTweak("org.gnome.nautilus.desktop", "home-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
```At least work minus the option to show/home the computer icon on the desktop, which I think is now depreciated anyway?

---

### Post by philinux on 2012-06-20
> **JMB74 said:**
> Comment out line #48 in /usr/lib/python2.7/dist-packages/gtweak/tweaks/tweak_nautilus.py and I think gnome-tweak-tool will work again?

```
TWEAKS = (
    DesktopIconTweak(group_name=TWEAK_GROUP_DESKTOP),
[COLOR=Blue]#    GSettingsSwitchTweak("org.gnome.nautilus.desktop", "computer-icon-visible",[/COLOR] schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
    GSettingsSwitchTweak("org.gnome.nautilus.desktop", "home-icon-visible", schema_filename="org.gnome.nautilus.gschema.xml",group_name=TWEAK_GROUP_DESKTOP),
```At least work minus the option to show/home the computer icon on the desktop, which I think is now depreciated anyway?

Righto. That will get over written when anew version comes out I guess.
[edit] And yes it works.

---

### Post by VMC on 2012-06-20
Or even simpler, use cli command:
```
gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'

```or
```
gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'
```

---

### Post by philinux on 2012-06-20
> **VMC said:**
> Or even simpler, use cli command:
```
gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'

```or
```
gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'
```

That's true. However it does not bug test the guis.

---

### Post by balloons on 2012-06-20
> **VMC said:**
> Or even simpler, use cli command:
```
gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'

```or
```
gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'
```

Ahh -- those blasted white-outed menus are fixed now by re-spamming  the gtk ambiance theme using your cli commands :-)

---

### Post by philinux on 2012-06-20
> **guitara said:**
> Ahh -- those blasted white-outed menus are fixed now by re-spamming  the gtk ambiance theme using your cli commands :-)

unity --replace achieves the same.  What package is causing the white out. Is it unity.

---

### Post by mc4man on 2012-06-20
> **philinux said:**
> Appearance doesn't work

If you mean that none of the dropdown choices can be selected I see that as affecting dropdowns in all gtk3 apps where there are dropdown choices
Other examples would be - 
gnome-terminal > profile preferences, pick any option that has a drop down
Rhythmbox > edit > preferences > music, pick any drop down
The list goes on & on

Not affected are gtk2 apps like FF, synaptic or vlc, ect.
Had a bug against light-themes though not sure, added gtk+
[https://bugs.launchpad.net/gtk/+bug/1014481](https://bugs.launchpad.net/gtk/+bug/1014481)

---

### Post by balloons on 2012-06-20
> **philinux said:**
> unity --replace achieves the same.  What package is causing the white out. Is it unity.

Yes, unity --replace is awesome. Except when you don't have the ability to unset sticky edges or have the launcher autohide, etc, because the appearance and display applets are borked. I went thru 3 weeks (just got out of it when someone pushed a fix that got them working on my box long enough to reset things properly) where I was stuck with the default unity desktop. This occurred after trying to fix a basic rendering issue by resetting things. I'll keep the 90% and deal with the 10% :-)

---

### Post by JMB74 on 2012-06-20
> **philinux said:**
> Righto. That will get over written when anew version comes out I guess.
[edit] And yes it works.

Seems to also be a patched version using a different approach to fix in the ricotz testing ppa.

[https://launchpad.net/~ricotz/+archive/testing/+build/3592169](https://launchpad.net/~ricotz/+archive/testing/+build/3592169)

i.e the [COLOR=Blue]00_catch_keyerror.patch[/COLOR], to work around the key error.

Can't see anything changed in upstream git yet though.

---

### Post by philinux on 2012-06-21
> **mc4man said:**
> If you mean that none of the dropdown choices can be selected I see that as affecting dropdowns in all gtk3 apps where there are dropdown choices
Other examples would be - 
gnome-terminal > profile preferences, pick any option that has a drop down
Rhythmbox > edit > preferences > music, pick any drop down
The list goes on & on

Not affected are gtk2 apps like FF, synaptic or vlc, ect.
Had a bug against light-themes though not sure, added gtk+
[https://bugs.launchpad.net/gtk/+bug/1014481](https://bugs.launchpad.net/gtk/+bug/1014481)

Indeed yes the drop downs dont work from appearance themes. But the gnome terminal prof prefs works fine here.

---

### Post by mc4man on 2012-06-21
> **philinux said:**
> Indeed yes the drop downs dont work from appearance themes. But the gnome terminal prof prefs works fine here.
Looks like it's time for a fresh install here to double ck. what's 'valid'  vs. possibly locally induced.

---

### Post by jerrylamos on 2012-06-21
> **philinux said:**
> Indeed yes the drop downs dont work from appearance themes. But the gnome terminal prof prefs works fine here.Philinux, drop downs are not working on a lot of different actins in my case from install to wireless to whatever.  Who in development knows anything about what has changed in drop downs?  gtk?

thanks, Jerry

---

### Post by mc4man on 2012-06-21
> **jerrylamos said:**
> Philinux, drop downs are not working on a lot of different actins in my case from install to wireless to whatever.  Who in development knows anything about what has changed in drop downs?  gtk?

thanks, Jerry
Switching to the Adwaita theme allows all to work here so I think it's light-themes with the new gtk+ from the other day 

Another easy test is, as mentioned, > rhythmbox > Edit > preferences > music
or
In dconf-editor many keys have dropdown choices, none can be selected here, Ex.
com.canonical.desktop.interface > scrollbar-mode

---

### Post by philinux on 2012-06-21
> **jerrylamos said:**
> Philinux, drop downs are not working on a lot of different actins in my case from install to wireless to whatever.  Who in development knows anything about what has changed in drop downs?  gtk?

thanks, Jerry
Bugged already. [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014481](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/1014481)

This is a different issue than thread topic though.

Try this. First do:-

gsettings set org.gnome.desktop.interface gtk-theme 'Radiance'
then
gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'

As per post #6

---

### Post by philinux on 2012-06-21
> **mc4man said:**
> Looks like it's time for a fresh install here to double ck. what's 'valid'  vs. possibly locally induced.

Reinstalled and yes not worky. So you do not need to.

I added my me too to your bug report.

---

### Post by balloons on 2012-06-21
> **philinux said:**
> Reinstalled and yes not worky. So you do not need to.

I added my me too to your bug report.

Duplicate of this?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497)

---

### Post by mc4man on 2012-06-21
> **guitara said:**
> Duplicate of this?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1015497)

looks likely  so duped mine, thanks for link

---

### Post by JMB74 on 2012-06-22
Allegedly a fix for dropdown selection problem.

[https://launchpad.net/ubuntu/quantal/+source/light-themes/0.1.11-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/light-themes/0.1.11-0ubuntu1)

---

### Post by mc4man on 2012-06-22
> **JMB74 said:**
> Allegedly a fix for dropdown selection problem.

[https://launchpad.net/ubuntu/quantal/+source/light-themes/0.1.11-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/light-themes/0.1.11-0ubuntu1)
works here

---

### Post by jppr on 2012-06-22
> **mc4man said:**
> works here

This update works too [https://launchpad.net/ubuntu/quantal/+source/light-themes/0.1.11-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/light-themes/0.1.11-0ubuntu1)

---

