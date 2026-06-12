---
title: "Gnome shell panel font size"
date: 2015-04-08
forum: Ubuntu Development Version
---

### Post by William_Shand on 2015-04-08
Hey guys,

Just recently started using Ubuntu Gnome again, but my top panel seems a little small, and the font is barely readable, is there anyway to increase the font size, as i tried gnome tweak tool and that didn't help :(

Thanks

---

### Post by dino99 on 2015-04-08
dconf (dconf-editor need to be installed) let you set your prefs

the theme can be changed/modified as into that blog: [http://rlog.rgtti.com/2012/01/29/how-to-modify-a-gnome-shell-theme/](http://rlog.rgtti.com/2012/01/29/how-to-modify-a-gnome-shell-theme/)

the easiest way is to use gnome-tweak-tool, but i does not like changing font size that way, due to known possible troubles

---

### Post by Elfy on 2015-04-08
Re-opened, closed an unanswered one.

---

### Post by kansasnoob on 2015-04-08
I always change the default Ubuntu GNOME fonts to the Ubuntu defaults:

[ATTACH=CONFIG]261175[/ATTACH]

[ATTACH=CONFIG]261176[/ATTACH]

And on my media-center I go certifiably insane:

[ATTACH=CONFIG]261177[/ATTACH]

I never use anything but gnome-tweak-tool to change fonts, but don't use it in Unity as it seems to have the potential to really mess up the Unity DE!

---

### Post by deadflowr on 2015-04-08
> **9d9 said:**
> dconf (dconf-editor need to be installed) let you set your prefs
Curiously, I have to ask if you know where/how in dconf this can be done?

---

### Post by kerry_s on 2015-04-08
> **deadflowr said:**
> Curiously, I have to ask if you know where/how in dconf this can be done?

i have dconf-editor & don't see any settings for that, i think he's just wrong.
the only thing i see that works is tweak tool-> fonts-> scaling factor, but that changes everything to be larger.

---

### Post by ventrical on 2015-04-09
> **kerry_s said:**
> i have dconf-editor & don't see any settings for that, i think he's just wrong.
the only thing i see that works is tweak tool-> fonts-> scaling factor, but that changes everything to be larger.

But it does the job if you just want a tweak :)

---

### Post by zika on 2015-04-09
> **kerry_s said:**
> i have dconf-editor & don't see any settings for that, i think he's just wrong.I do not know if he was wrong but what he wrote is true and there are plenty of settings in dconf-editor that are superset of gnome-tweak... All of those settings are available/accessible through command-line, without GUI which comes handy if someone messes things too much... ;)
Also take a look into gconf-editor and its CLI companions...

---

### Post by kerry_s on 2015-04-09
what i meant was i went through every setting in dconf-editor, opened every sub directory, there is no setting just for the panel fonts, so i'm saying he's wrong that there is that setting.

---

### Post by deadflowr on 2015-04-09
So, it took me a minute to figure it out...

The easiest way to adjust the panel font sizes is to muck around with the gnome-shell.css file.
This is a system file, so mucking about can be a pain.
gnome's workaround though, is add the [user themes extension from gnome extensions]("https://extensions.gnome.org/extension/19/user-themes/")
Which will allow the user to make the changes without needing to edit as root.

After adding the user theme extension create a new text file,
add this to it
```
@import url("/usr/share/gnome-shell/theme/gnome-shell.css");


#panel {
    background-color: black;
    background-color: rgba(0,0,0,0.01);  
    font-weight: bold;
    font-size: 1.20em;  
    height: 1.50em;
}
```
save the file in ~/.themes/some-theme-name/gnome-shell/gnome-shell.css  -- you can probably name the theme something like, MyTheme. 
(You will probably need to create a .themes folder, a theme-name folder,  and a gnome-shell folder.)
(The .themes folder has a dot so that means it will normally be hidden in the file manager, to view the folder in Files press ctrl + H)

Now open gnome tweak and go to shell theme and you should have a new entry with the new theme you just created.
Toggle to that theme and see what happens.


Addings: Any thing you enter into this file will override the setting in the system gnome-shell.css file.
So you can add other panel settings in here as well.
You can peruse the system file in /usr/share/gnome-shell/theme/gnome-shell.css for any other panel or shell theme settings you may want to try changing.
If you so desire.

(This theme setting is my own personalized setting, so the line for background-color: rgba(0,0,0,0.01); makes the panel transparent.
the line for font-size makes the panel font size rather large, as written, so you may want to adjust that. The normal size should be something like 1.0em, me thinks
The height setting relates to how much bigger the panel is in relation to the font-size. Hard to explain, but playing around with these two settings you will figure out what I mean, hopefully)

Hope this makes sense.

This methodology is based on tips from here [http://rlog.rgtti.com/2012/01/29/how-to-modify-a-gnome-shell-theme/](http://rlog.rgtti.com/2012/01/29/how-to-modify-a-gnome-shell-theme/) (thanks 9d9)
My bad, i forgot to add this attribution.

---

### Post by kerry_s on 2015-04-09
> **deadflowr said:**
> So, it took me a minute to figure it out...

The easiest way to adjust the panel font sizes is to muck around with the gnome-shell.css file.
This is a system file, so mucking about can be a pain.
gnome's workaround though, is add the [user themes extension from gnome extensions]("https://extensions.gnome.org/extension/19/user-themes/")
Which will allow the user to make the changes without needing to edit as root.

After adding the user theme extension create a new text file,
add this to it
```
@import url("/usr/share/gnome-shell/theme/gnome-shell.css");


#panel {
    background-color: black;
    background-color: rgba(0,0,0,0.01);  
    font-weight: bold;
    font-size: 1.20em;  
    height: 1.50em;
}
```
save the file in ~/.themes/some-theme-name/gnome-shell/gnome-shell.css  -- you can probably name the theme something like, MyTheme. 
(You will probably need to create a .themes folder, a theme-name folder,  and a gnome-shell folder.)
(The .themes folder has a dot so that means it will normally be hidden in the file manager, to view the folder in Files press ctrl + H)

Now open gnome tweak and go to shell theme and you should have a new entry with the new theme you just created.
Toggle to that theme and see what happens.

Addings: Any thing you enter into this file will override the setting in the system gnome-shell.css file.
So you can add other panel settings in here as well.
You can peruse the system file in /usr/share/gnome-shell/theme/gnome-shell.css for any other panel or shell theme settings you may want to try changing.
If you so desire.

(This theme setting is my own personalized setting, so the line for background-color: rgba(0,0,0,0.01); makes the panel transparent.
the line for font-size makes the panel font size rather large, as written, so you may want to adjust that. The normal size should be something like 1.0em, me thinks
The height setting relates to how much bigger the panel is in relation to the font-size. Hard to explain, but playing around with these two settings you will figure out what I mean, hopefully)

Hope this makes sense.


your a genius!

---

### Post by dino99 on 2015-04-09
> **kerry_s said:**
> your a genius!

that genius idea, as you said, was already proposed by the link provided into #2  :lolflag:

---

### Post by deadflowr on 2015-04-10
> **9d9 said:**
> that genius idea, as you said, was already proposed by the link provided into #2  :lolflag:

I actually never read your edited post. I don't look at old posts unless a later post says something about an edit.
I think we were still awaiting word on how to use dconf...

However, I did run across that link(great minds search alike), so edited my post to attribute to it.
Thanks. I totally forgot i should have added a link originally, I was playing with themes while writing it, so...

---

