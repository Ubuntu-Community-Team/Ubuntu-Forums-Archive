---
title: "[SOLVED] Theme troubles"
date: 2007-12-09
forum: The Cafe
---

### Post by Techwiz on 2007-12-09
I am *very* new to Ubuntu. And I was wondering how to install themes. I have tried several times before but I have never succeeded. Could you help me? Thanks!

---

### Post by Rabidmonkey1 on 2007-12-09
To install a theme, you download the archive, then under (I believe) Settings>Preferences>Appearance there is a tab named Themes.  Under the Theme tab there is a button that says "Install theme"

Click "Install theme" and this will open a window.  Navigate to where you saved the theme archive and then select it.  The computer will then install the theme, and it will be selectable as an icon in the list of available themes.  

You can then delete the archive, as it is no longer needed.

Get some good themes at gnome-look.org

Sorry if this is rough, I don't have my Ubuntu install open in front of me at the moment...  I will later though, so feel free to ask any other questions!

---

### Post by Techwiz on 2007-12-09
I just tried that but my computer says that the file format is invalid.

---

### Post by smartboyathome on 2007-12-09
You need to extract the theme to /home/your-username/.themes/ , then change it as stated above.

---

### Post by Techwiz on 2007-12-09
I just tried all of that and my computer still says that the file format is invalid.

---

### Post by smartboyathome on 2007-12-09
Did you just select the theme from the list (not install it)?

---

### Post by mcduck on 2007-12-09
> **Techwiz said:**
> I just tried all of that and my computer still says that the file format is invalid.

What theme did you download? Can you give a link?

---

### Post by Tenken on 2007-12-09
What format is the theme you downloaded in? They need to be in the filename*.tar.gz* format for Rabidmonkey's method to work.

---

### Post by crimesaucer on 2007-12-09
The way I would do it, is I would unpack the "new_theme" to my /home/folder


... so it was /home/folder/new_theme



Then, I would use my terminal and in Root, I would move the "new_theme" folder to the proper theme directory:

```
sudo mv new_theme /usr/share/themes
```


... then it should be listed with all of your other themes, and you should be able to select it like all of your default themes.

---

### Post by Techwiz on 2007-12-09
Thank you for all your advice. You have solved my problem. Thanks!

---

### Post by Crashmaxx on 2007-12-09
I've always just dragged and dropped the theme archive right onto the Appearance app. Installs it for you with no trouble. Have to say I really like a lot of the new options for themes too. Very nice to be able to teak the themes and even make your own easily to some extent. Just wish they would fix how you save those changes.

---

### Post by crimesaucer on 2007-12-09
It would also help if you said what type of theme you are trying to install...

Like: gtk-2.0, metacity, emerald, xfwm4....



Some people install there themes into /home/folder/.themes


I prefer to put theme with all of the other theme in the /usr/share/themes directory.


gtk themes, such as clearlooks, go in the /usr/share/themes
icons go in /usr/share/icons
gdm themes go in /usr/share/gdm/themes

---

### Post by crimesaucer on 2007-12-09
> **Crashmaxx said:**
> I've always just dragged and dropped the theme archive right onto the Appearance app. Installs it for you with no trouble. Have to say I really like a lot of the new options for themes too. Very nice to be able to teak the themes and even make your own easily to some extent. Just wish they would fix how you save those changes.

All of that is only for Gnome.

In xfce4.4.2, you still have to use either the ~/.themes folder or /usr/share/themes


And for modifications, you can only do it from modifying the gtkrc.


Gnome is really nice, but I think it is better to know where the themes are actually at, and how to change them yourself if you have to.

---

