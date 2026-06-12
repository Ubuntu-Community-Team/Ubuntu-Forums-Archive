---
title: "How to change orange colour in Unity's theme"
date: 2012-02-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-17
After spending a lot of time trying to change this awful orange colour , I decided to ask a question here. With Gnome 2.0 it was quite easy. Actually, all the customizations were easy with Gnome, opposed to Unity now. How do I change this colour? How do I get and install new themes? How do I get, install and change icon sets?

---

### Post by winh8r on 2012-02-17
I found this which might be of interest to you:


[http://www.noobslab.com/2011/11/transparent-swar-red-unity-theme-for.html]("http://www.noobslab.com/2011/11/transparent-swar-red-unity-theme-for.html")


also while you are there, check out this:

[http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html]("http://www.noobslab.com/2011/11/themes-collection-for-ubuntu-1110-unity.html")


OR you could revert back to the gnome-type environment by installing something like this:

[http://mate-desktop.org/]("http://mate-desktop.org/")
hope this is of some use to you.

---

### Post by shuttleworthwannabe on 2012-02-17
kewl...this may just come in handy for Gnome Shell!

---

### Post by kansasnoob on 2012-02-17
> **&#1058 said:**
> After spending a lot of time trying to change this awful orange colour , I decided to ask a question here. With Gnome 2.0 it was quite easy. Actually, all the customizations were easy with Gnome, opposed to Unity now. How do I change this colour? How do I get and install new themes? How do I get, install and change icon sets?

Theming is a bit messy ATM. This should improve by Beta 1 :D

---

### Post by the_blue_box on 2012-02-17
You should use Ubuntu tweak [http://www.omgubuntu.co.uk/2012/02/ubuntu-tweak-adds-ubuntu-12-04-support/](http://www.omgubuntu.co.uk/2012/02/ubuntu-tweak-adds-ubuntu-12-04-support/)

---

### Post by Bowmore on 2012-02-17
Try this,
```
gsettings set org.gnome.desktop.interface gtk-color-scheme 'selected_bg_color:#FF20FF;'
```which replaces orange with kind of purple.

You can then change the color #FF20FF to your preference.

This works for light-themes except for icons such as the close button that you have to recolor yourself.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-02-18
Neat, thanks everyone. I sure hope handling the Appearance will improve in the final 12.04.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-12
> **Bowmore said:**
> Try this,
```
gsettings set org.gnome.desktop.interface gtk-color-scheme 'selected_bg_color:#FF20FF;'
```which replaces orange with kind of purple.

You can then change the color #FF20FF to your preference.

This works for light-themes except for icons such as the close button that you have to recolor yourself.

Okay, I've tried your advice and it worked. Thanks a lot. But now I tried using [these colour themes](http://www.webupd8.org/2012/01/download-ambiance-and-radiance-themes.html), and they all have problems (white text on white background, black text on black background). Is there a way for me to undo this change that you recommended?

---

### Post by treesurf on 2012-04-12
I think those themes need to be updated to work properly with gtk3.4

---

### Post by zombifier25 on 2012-04-12
EDIT: NINJA'D!
Actually, it's not the gsettings changes that messed it up. It's the themes. Those themes are not updated to work properly with GNOME 3.4, so they'll experience issues. You should remove the themes and wait for them to be updated.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-12
Ah, okay. It makes sense now :) For a moment I thought I was going crazy. I have the same themes installed on another computer, and over there they're working properly. I thought it's because I messed up something with my tweak, but apparently they're working on the other machine because the OS there is 11.10. Thanks again.

---

### Post by treesurf on 2012-04-12
This one should work for you:
[http://www.webupd8.org/2012/04/bluebird-theme-ported-to-gtk3-works.html#more](http://www.webupd8.org/2012/04/bluebird-theme-ported-to-gtk3-works.html#more)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-12
> **treesurf said:**
> This one should work for you:
[http://www.webupd8.org/2012/04/bluebird-theme-ported-to-gtk3-works.html#more](http://www.webupd8.org/2012/04/bluebird-theme-ported-to-gtk3-works.html#more)

Thanks, but I kinda really like Ubuntu's default themes. If only it wasn't for this awful awful eye-popping orange...

---

### Post by treesurf on 2012-04-12
I know what you mean.  I'm really hoping that Ambiance Blue theme, or Elements-Unity gets updated soon.  The eye-popping orange and these light colored right-click menus hurt my eyes.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-04-12
Exactly my thoughts.

---

