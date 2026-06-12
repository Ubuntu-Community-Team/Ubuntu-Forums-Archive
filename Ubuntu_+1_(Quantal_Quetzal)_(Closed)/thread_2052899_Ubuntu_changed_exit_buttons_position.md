---
title: "Ubuntu changed exit buttons position"
date: 2012-09-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cavetrolldigger on 2012-09-04
Hi, today I turned my laptop with ubuntu 12.10 (with gnome 2D without effects) on, and I noticed that buttons position moved from left to right side, and program title font has changed. My question is, how is it even possible? I turned off all updates, and I didn't do any on my own. Is there a way to trace what has happened?
Pictures: [before]("http://imageshack.us/photo/my-images/222/beforer.png/") ; [after]("http://imageshack.us/photo/my-images/411/afterc.png/")
EDIT: I have also noticed that some (but not all) shortcuts are not working like Alt+tab (default), super+m (my custom).

---

### Post by coffeecat on 2012-09-04
*Thread moved to **Ubuntu +1 (Quantal Quetzal)**.*

---

### Post by kyleabaker on 2012-09-04
I'm not sure how they would have changed without applying any updates, so I can't help you there. However, if you're wanting to change them back then you can use a tool such as the one mentioned here:

[http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for-lucid-and-karmic-users](http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for-lucid-and-karmic-users)

---

### Post by effenberg0x0 on 2012-09-04
To make it look like "before":
```
gconftool-2 --set --type string /apps/metacity/general/button_layout "close,minimize,maximize"

```
To make it look like "after":
```
gconftool-2 --set --type string /apps/metacity/general/button_layout ":minimize,maximize,close"
```

Regards,
Effenberg

---

### Post by jbicha on 2012-09-04
effenberg, you need to update your tip. Quantal is using gsettings for that now.

org.gnome.desktop.wm.preferences button-layout

---

### Post by effenberg0x0 on 2012-09-04
> **jbicha said:**
> effenberg, you need to update your tip. Quantal is using gsettings for that now.

org.gnome.desktop.wm.preferences button-layout

True, thanks. I completely forgot, too much time doing things the same way. I tested, it still works though.

Regards,
Effenberg

---

### Post by mc4man on 2012-09-04
(with the OP not updating anything can happen..

There was a period not to long ago where one of the Classic sessions would rewrite that metacity setting & cause the buttons to move. 
(may have been Classic with compiz & an offshoot of the Default profile not having any plugins enabled.

As it stands now the gconf metacity setting shouldn't affect Classic *no effects at all But will actually change the position in a unity session for some reason..

---

### Post by cavetrolldigger on 2012-09-04
Sorry, it's is fairly easy to change it, and I've already done it. But, as I asked, I need to know how it could happened, I don't like when something magically changes. 
I managed to track apt-get history to check if I haven't install sth by accident in /var/log/apt/history.log.1.gz but it looks clean and now have no clue where should I even start looking. Any ideas?
EDIT: I read your msg [mc4man]("http://ubuntuforums.org/member.php?u=320715") after posting, 
> There was a period not to long ago where one of the Classic sessions  would rewrite that metacity setting & cause the buttons to move.It seems strange and I hardly believe that, I didn't change anything in appeariance for many weeks, so it would be **extremely** strange to me if some program would all of the sudden invoke changing appearance function
I'm not sure but I thought that gnome classic is not unity (or any overlay) so even if it would change unity appearance (which I never use) it shouldn't change gnome classic.

---

### Post by kyleabaker on 2012-09-04
> **cavetrolldigger said:**
> Sorry, it's is fairly easy to change it, and I've already done it. But, as I asked, I need to know how it could happened, I don't like when something magically changes. 
I managed to track apt-get history to check if I haven't install sth by accident in /var/log/apt/history.log.1.gz but it looks clean and now have no clue where should I start even looking. Any ideas?

mc4man provided the most likely cause of the problem.

---

### Post by effenberg0x0 on 2012-09-04
> **cavetrolldigger said:**
> Sorry, it's is fairly easy to change it, and I've already done it. But, as I asked, I need to know how it could happened, I don't like when something magically changes. 
I managed to track apt-get history to check if I haven't install sth by accident in /var/log/apt/history.log.1.gz but it looks clean and now have no clue where should I start even looking. Any ideas?

I have no idea, sorry. I couldn't keep up with the migration from gconf to dconf and only test unity. mc4man is the guy for these things :)

Regards,
Effenberg

---

### Post by Bowmore on 2012-09-04
Well, sort of a mess right now.

Unity and Gnome Classic (effects):
Gconf: /apps/metacity/general/button_layout

Gnome Classic (no effects):
Dconf: org.gnome.desktop.wm.preferences button-layout

Gnome Shell:
Dconf: org.gnome.shell.overrides button-layout

This might answer your question, i.e probably a first step migration from gconf to dconf for Classic no effects. Final step now is to move Unity and Classic with effects to dconf as well.

---

### Post by effenberg0x0 on 2012-09-04
Geez... maybe we need another layer of abstraction on top of everything.

ubuntu-very-own-settings set window-buttons-show "fo shizl"
ubuntu-very-own-settings set window-buttons "'x','_','&#9632;'"

Then ubuntu-very-own-settings daemon can dispatch to gconf, dconf, zconf, etc.

Regards,
Effenberg

---

### Post by jbicha on 2012-09-24
Those of you with buttons on the right side suddenly and similar issues...

Make sure ubuntu-desktop is installed (which should install ubuntu-settings). If you prefer the GNOME Remix, you can install ubuntu-gnome-desktop (which installs ubuntu-gnome-default-settings).

What happened is that we moved the Ubuntu gsettings overrides to a separate package so that it's easier for someone to ship a purer GNOME without needing to match a dozen packages.

---

