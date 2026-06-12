---
title: "php script has wrong icon on desktop"
date: 2012-09-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by pqwoerituytrueiwoq on 2012-09-30
click for full size
[[IMG]http://i.imgur.com/RVXfbl.png[/IMG]](http://i.imgur.com/RVXfb.png)

---

### Post by effenberg0x0 on 2012-09-30
I just wanted to point out that it definitely still works when the file has an extension. Here's a .php file:

[ATTACH]224901[/ATTACH]

I'm not sure what mechanism is used to recognize the file type or mime-type of a file with no extension, but maybe it got simplified or exterminated along with other nautilus features. 

Regards,
Effenberg

---

### Post by mc4man on 2012-09-30
> **effenberg0x0 said:**
> 
but maybe it got simplified or exterminated along with other nautilus features. 

In Ubuntu I believe that's simply a theme deal, so it would be probably a dozen mimetypes, (xml, html, php, ect.), using  the same icon - text-html.svg.  As seen in 
/usr/share/icons/Humanity/mimes/*

As far as xubuntu/thunar would know unless tried

*Ot - As far as how ext.less file's mime are determined could be from 'shared-mime-info'

---

### Post by mc4man on 2012-09-30
As far as xubuntu - 
initially it seems to use the correct icon on the Desktop for php in the elementary theme
As soon as the Desktop is right clicked on, (in this case to check backgrounds), it switches to the icon for .swf

Would then appear to be a theme (elementary) issue

---

### Post by pqwoerituytrueiwoq on 2012-09-30
> **mc4man said:**
> As far as xubuntu - 
initially it seems to use the correct icon on the Desktop for php in the elementary theme
As soon as the Desktop is right clicked on, (in this case to check backgrounds), it switches to the icon for .swf

Would then appear to be a theme (elementary) issue
Where do i go to report this one?

to others it does not matter if it has .php on it or not, same icon regardless

i have had this problem in 12.04 but i was running xfce 4.10

---

### Post by mc4man on 2012-10-01
> **pqwoerituytrueiwoq said:**
> Where do i go to report this one?

to others it does not matter if it has .php on it or not, same icon regardless

i have had this problem in 12.04 but i was running xfce 4.10

Not exactly sure yet, I guess if I did an install may be more apparent.

Anyway - on a live session tracked down to what's in (or the mere existence) of 1 file. This file doesn't exist until r. click on Desktop > appearance. Then the file is created & the icon changes from php to swf
Edit: note that only the elementary icon theme is affected by this file

If I rename the file, log out/in then the icon returns to php on the Desktop
Maybe you can figure out if it's what in that file that is affecting, or just having it there at all - the file is -

~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml

As seen upon first creation & causes the icon change
```
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-desktop" version="1.0">
  <property name="desktop-icons" type="empty">
    <property name="style" type="empty"/>
    <property name="file-icons" type="empty">
      <property name="show-home" type="empty"/>
      <property name="show-filesystem" type="empty"/>
      <property name="show-removable" type="empty"/>
      <property name="show-trash" type="empty"/>
    </property>
    <property name="icon-size" type="uint" value="32"/>
  </property>
  <property name="backdrop" type="empty">
    <property name="screen0" type="empty">
      <property name="monitor0" type="empty">
        <property name="image-path" type="empty"/>
        <property name="image-show" type="empty"/>
        <property name="last-image" type="string" value="/usr/share/xfce4/backdrops/xubuntu-quantal.png"/>
        <property name="last-single-image" type="string" value="/usr/share/xfce4/backdrops/xubuntu-quantal.png"/>
      </property>
      <property name="monitor1" type="empty">
        <property name="image-path" type="empty"/>
        <property name="image-show" type="empty"/>
      </property>
    </property>
  </property>
</channel>
```

---

### Post by pqwoerituytrueiwoq on 2012-10-01
thanks i found the line that makes this problem appear
[IMG]http://i.imgur.com/ZBfxS.png[/IMG]

This effects the 32px size icon for php
if you zoom out in thunar this issue is visible
GUI workaround:
[IMG]http://i.imgur.com/A1WLw.png[/IMG]
edit:
any # over 32 works, i think i like 34

---

### Post by mc4man on 2012-10-01
That sounds like a good solution for you (quick & easy
If you wanted to file a bug it would be on xubuntu-icon-theme

Not using Xubuntu but out of curiosity - another possible would be to replace the main php symlink in the 32 folder with an actual 32x32 php icon, then replace the other symlink with one pointing to the new real icon

So viewing that folder on an ubuntu install there are 2 php links in the 32 folder - screen one
Then after replace, re-link would be like as in screen 2
Attached a 32x32 icon
Not sure if worth the hassle (& I think the 32x32 is correctly done but being a T&E person...

---

### Post by morgengenuss on 2012-10-02
Thanks for discovering this issue with our icon-theme.

However, the correct place to report this is launchpad, specifically here: [https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/](https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/)

So I'd ask you to report it there, I'm afraid it's probably too late to get the fix for this into 12.10 since we're past all the freeze-dates, but to keep it in mind for R (or provide a better workaround for ppl who want to fix it for themselves) it'd be good to have things documented there.

---

### Post by pqwoerituytrueiwoq on 2012-10-02
just made it
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/+bug/1060226](https://bugs.launchpad.net/ubuntu/+source/xubuntu-artwork/+bug/1060226)

here is a command to patch it
```
cd /usr/share/icons/elementary-xfce/mimes/32;sudo ln -s -f text-html.svg application-x-php.svg
```

---

