---
title: "Missing keys in gsettings"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bhb192 on 2012-03-16
Problem: gnome-settings-daemon is crashing because the key 'screenshot' cannot be found in the gsettings schema 'org.gnome.settings-daemon.plugins.media-keys'

Indeed, if I go to a terminal and type in 'gsettings list-keys org.gnome.settings-daemon.plugins.media-keys', screenshot isn't one of them.

However, the screenshot key is defined in the XML schema file and it shows up in dconf-editor also. 

How do I get gsettings to recognize this key?

---

### Post by mc4man on 2012-03-16
certainly doesn't sound normal.

I would 1st try creating a new user, logging in to it & see if all is normal. If so then it's a local issue, maybe your ~/.config/dconf/user file is 'bad'.

If the new user  shows the key then back in your user session try opening dconf-editor, select the screenshot key (there are several actually
unset or edit the key, then reselect & set back to default. See if that gets the key written to your gsettings

---

### Post by bhb192 on 2012-03-16
I created a new user account and it had the same issue. Clearing the keys and then resetting to default in dconf-editor didn't change the situation either. 

Do you know where gsettings imports its data from and where dconf-editor imports its data from?

---

### Post by bhb192 on 2012-03-16
Finally figured this out!

At some point in the past, gnome-settings-daemon must have installed its gsettings schemas into the folder /usr/**local**/share/glib-2.0/schemas rather than the default /usr/share/glib-2.0/schemas. Therefore, gsettings was reading those schemas instead.

---

