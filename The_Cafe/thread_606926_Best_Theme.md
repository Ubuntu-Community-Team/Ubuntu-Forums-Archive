---
title: "Best Theme"
date: 2007-11-08
forum: The Cafe
---

### Post by RobotoWorks on 2007-11-08
Im having trouble deciding what theme I should install on my Gutsy Gibbon, Im looking for a nice dark theme, got any ideas?

---

### Post by evilregis on 2007-11-08
I suggest you try installing the gnome-art package.

System -> Administration -> Synaptic Package Manager

Search for "gnome-art", click it, mark it for installation then apply.

If you prefer terminal:

```
sudo apt-get install gnome-art
```

---

### Post by scammi on 2007-11-08
TY !

but how i can make it look like a mac pc or like change it compleately?
by thenks

---

### Post by RobotoWorks on 2007-11-08
Okay just did that, only Ive noticed when I apply a theme in "Gnome Art" nothing happens

---

### Post by Jadd on 2007-11-08
If you're looking for themes, don't forget to visit [gnome-look.org](http://www.gnome-look.org). GTK themes affects the icons, Metacity affects the window borders, icon themes obviously change the icons...

---

### Post by RobotoWorks on 2007-11-08
I know, its just for some reason they are getting installed when I use GNOME Art or Emerald

---

### Post by powder on 2007-11-08
[http://www.gnome-look.org/content/show.php/DarkWay?content=64653](http://www.gnome-look.org/content/show.php/DarkWay?content=64653)

---

### Post by philinux on 2007-11-08
Have you tried the macbluebird theme for firefox?

---

### Post by RobotoWorks on 2007-11-08
No, where can I get it?

---

### Post by por100pre1 on 2007-11-08
Check this:

[http://ubuntustudio.org/files/ubuntustudio-feisty-art_0.1_all.deb](http://ubuntustudio.org/files/ubuntustudio-feisty-art_0.1_all.deb)

---

### Post by RobotoWorks on 2007-11-08
Thanx guys, may I ask how can I trick my Compliz out to look like this (5 min. Vid)

[http://www.youtube.com/watch?v=_ImW0-MgR8I](http://www.youtube.com/watch?v=_ImW0-MgR8I)

---

### Post by por100pre1 on 2007-11-08
> **RobotoWorks said:**
> Thanx guys, may I ask how can I trick my Compliz out to look like this (5 min. Vid)

[http://www.youtube.com/watch?v=_ImW0-MgR8I](http://www.youtube.com/watch?v=_ImW0-MgR8I)

The best way is to install **Advanced Desktop Effects Settings**:

```
sudo aptitude install compizconfig-settings-manager
```

You'll find it under **System> Preferences**.

---

### Post by RobotoWorks on 2007-11-08
Oh, I have it already installed, but I really want to know how I can apply those awesome 3d effects

---

### Post by philinux on 2007-11-08
> **RobotoWorks said:**
> No, where can I get it?

macbluebird

[https://addons.mozilla.org/en-US/firefox/addon/3967](https://addons.mozilla.org/en-US/firefox/addon/3967)

---

### Post by TadH on 2007-11-08
> **RobotoWorks said:**
> Oh, I have it already installed, but I really want to know how I can apply those awesome 3d effects

which ones specifically were you looking to use? I have all of that except the animated wallpaper, matrix code I've bene loking for it forever...but all of the other studff I can help you with.

---

### Post by RobotoWorks on 2007-11-08
Thank you this video is a good example of what I want, if theres anything in the vid you cant help with its okay, but Im sure theres some


[http://www.youtube.com/watch?v=_ImW0-MgR8I](http://www.youtube.com/watch?v=_ImW0-MgR8I)

---

### Post by philinux on 2007-11-08
The built in matrix screen saver is excellent.

---

### Post by RobotoWorks on 2007-11-08
TadH, come visit me at [www.robotoworks.prosoftstudio.com](www.robotoworks.prosoftstudio.com) so we can talk

---

### Post by Bruce M. on 2007-11-08
> **evilregis said:**
> I suggest you try installing the gnome-art package.

System -> Administration -> Synaptic Package Manager

Search for "gnome-art", click it, mark it for installation then apply.

If you prefer terminal:

```
sudo apt-get install gnome-art
```

Does this work for 7.04 too?
If so, and I get it, where do I find it after installed?
  1. Menus   2. Terminal program   3. Panel App.

---

### Post by RobotoWorks on 2007-11-08
So can anyone help?

---

### Post by urukrama on 2007-11-08
> **RobotoWorks said:**
> Im having trouble deciding what theme I should install on my Gutsy Gibbon, Im looking for a nice dark theme, got any ideas?

Try MurrinaBrown or GSM (*not* the Murrina GSM theme, the other one). Both are available from Gnome-look.org.

---

### Post by bruce89 on 2007-11-08
Personally, I'd stick to Clearlooks, but change the colours.

---

### Post by silent1643 on 2007-11-08
make your own 
use gnome-look.org
look for inspiration from [studio21]("http://studiotwentyone.wordpress.com/")
:)

---

### Post by BobCFC on 2007-11-08
I agree Clearlooks is the best.  But sometimes working at night a dark theme is easier on the eyes.  

If you install the **gnome-themes-extras** package the is a very nice Darklooks theme, probably the most professional dark theme.

---

### Post by bruce89 on 2007-11-08
> **BobCFC said:**
> I agree Clearlooks is the best.  But sometimes working at night a dark theme is easier on the eyes.

~/.themes/Night Vision/index.theme :
```
[Desktop Entry]
Name=Night vision
Type=X-GNOME-Metatheme
Comment=Used in the night time
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Glossy
MetacityTheme=Glossy
IconTheme=gnome
GtkColorScheme=fg_color:#000000000000,bg_color:#8b8b00000000,text_color:#eeee00000000,base_color:#000000000000,selected_fg_color:#000000000000,selected_bg_color:#eeee00000000,tooltip_fg_color:#000000000000,tooltip_bg_color:#000000000000
CursorTheme=default
CursorSize=24
```

Problem solved.

---

### Post by marco123 on 2007-11-08
> **Bruce M. said:**
> Does this work for 7.04 too?
If so, and I get it, where do I find it after installed?
  1. Menus   2. Terminal program   3. Panel App.

Yes, it works on Feisty too.  You'll find it under System>Preferences>Art Manager in the Gnome-Menu.:)

---

### Post by marco123 on 2007-11-08
My favorite theme has to be Carbonit.  Very professional looking and clean. 

[http://www.gnome-look.org/content/show.php/Carbonit?content=45590](http://www.gnome-look.org/content/show.php/Carbonit?content=45590)

---

