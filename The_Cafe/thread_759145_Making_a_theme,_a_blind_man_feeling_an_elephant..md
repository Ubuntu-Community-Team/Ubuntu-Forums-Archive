---
title: "Making a theme, a blind man feeling an elephant."
date: 2008-04-18
forum: The Cafe
---

### Post by Islington on 2008-04-18
So I wanted to make a gnome theme from scratch (read: learning experience with character building) and I started with the tutorials on the gnome site. Unfortunately this means:

1) I type something out/tweak a setting/color/image.
2) I save the file in gedit/gimp
3) I have to rearchive
4) Delete old theme by same name
5) install updated theme.
6) cry with frustration as the tweak is just a little off.
7) repeat 1-6

all this just to test every minor change? Please tell me there is a quick way to see the changes made? Also I put this here because the desktop thread has a lot of desktop perfectionists.Also would appreciate any other resources for theme building.

---

### Post by Mazza558 on 2008-04-18
I've seen many themes show off their widgets using a program called "widget factory" - I don't know what it is, but it might be what you're looking for..?

---

### Post by Islington on 2008-04-18
spot on for the widget factory! dhanyavad. :)

---

### Post by geoken on 2008-04-18
Yeah, you're definately doing it the super long way. When you drag the archived theme onto the gnome theme manager all gnome's doing is taking that archive and extracting it into the ".themes" directory in your home folder.

The quick way to make themes is to directly edit the files in that directory. For example, if you have a theme called myTheme, you'll have the folder /home/username/.themes/myTheme. Just go to that folder and directly edit the theme. When you make a change just save that change, then switch to a different theme and switch back (aka. refresh the theme) and you'll be able to review the new change you made.

---

### Post by LeoSolaris on 2008-04-18
I always just edited what was in the archive, then when I want to put the new file or what ever in, I save it in the same folder as the archive, then use the archive manager to open the archive, and add it to the already existing archive. It has always asked if I want to replace the pre-existing file. I yes that and then close the archive manager. I uninstall then reinstall the theme to make the changes work. That works for me with the login theme I mod.

---

### Post by LeoSolaris on 2008-04-18
> **geoken said:**
> Yeah, you're definately doing it the super long way. When you drag the archived theme onto the gnome theme manager all gnome's doing is taking that archive and extracting it into the ".themes" directory in your home folder.

The quick way to make themes is to directly edit the files in that directory. For example, if you have a theme called myTheme, you'll have the folder /home/username/.themes/myTheme. Just go to that folder and directly edit the theme. When you make a change just save that change, then switch to a different theme and switch back (aka. refresh the theme) and you'll be able to review the new change you made.

Sounds much easier... I'll try that from now on. Shave a few steps off my old way.

Leo

---

### Post by klange on 2008-04-18
Edit, save, switch to a different theme and (before it even loads), switch back to your new theme. Fairly simple. Also, +1 for TWF - you can also hack it for RGBA if you're using Murrine-svn.

---

### Post by Islington on 2008-04-18
> **geoken said:**
> Yeah, you're definately doing it the super long way. When you drag the archived theme onto the gnome theme manager all gnome's doing is taking that archive and extracting it into the ".themes" directory in your home folder.

The quick way to make themes is to directly edit the files in that directory. For example, if you have a theme called myTheme, you'll have the folder /home/username/.themes/myTheme. Just go to that folder and directly edit the theme. When you make a change just save that change, then switch to a different theme and switch back (aka. refresh the theme) and you'll be able to review the new change you made.

Ah, now thats a more logical way..


I havent actually been able to compile murrine svn.

---

### Post by Bubba64 on 2008-04-18
Or try this it is kinda cool for Firefox themes
[http://labs.mozilla.com/2007/12/personas-for-firefox/](http://labs.mozilla.com/2007/12/personas-for-firefox/)

---

### Post by Mr. Picklesworth on 2008-04-18
Rather than working in the .Themes directory, the safer and tidier route would be to create a symlink in .Themes leading to your work. (Create Link in Nautilus). That's how I deal with panel applets, anyway...

---

