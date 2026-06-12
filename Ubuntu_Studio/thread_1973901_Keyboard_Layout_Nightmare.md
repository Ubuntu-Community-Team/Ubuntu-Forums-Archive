---
title: "Keyboard Layout Nightmare"
date: 2012-05-05
forum: Ubuntu Studio
---

### Post by Regele IONESCU on 2012-05-05
I wanna setup three keyboard language layouts: English(US), Romanian and Russian(phonetic)
Previously there was a simple fine way of setting keyboard language via settings. Now, it is a nightmare. First of all, layouts and languages are spread around all settings(keyboard layout, language settings, keyboard input method, input method switcher). In some settings(IBus preferences) there is no Romanian layout option even though I have it in other places. Even though IBus is started with default settings(Ctrl Space to activate and Alt Shift_L to change layout) it does not work at all.

Please help me to set up my three languages and switch them with Alt+Left Shift.

Regards,
Christian.

---

### Post by jejeman on 2012-05-05
Which version of ubuntu Studio?

---

### Post by Regele IONESCU on 2012-05-05
12.04

---

### Post by jejeman on 2012-05-05
Working with layouts in Xfce is simply bad. It gave me all kinds of bugs.
So, I find out that the best thing to do is to make a startup script for setxkbmap command. Something like this

```
setxkbmap -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle us,ru -variant ,
```You need to find out the names for layouts and variants you need. Look here /usr/share/X11/xkb/symbols
Open each definition you need to find out the variants
I guess ro is for romania, so

```
setxkbmap -option compose:rwin,lv3:ralt_switch,grp:alt_shift_toggle us,ro,ru -variant ,,
```

---

### Post by jejeman on 2012-05-06
Other way to go is to install xfce4-xkb-plugin. It's really buggy, never does what it should. Broke shortcuts input in Blender.

That's why i recommended script.

---

### Post by Regele IONESCU on 2012-05-25
Thank you for your answers Jejeman. My problem is that I cannot switch the keyboard, the shortcuts do not work at all. I can set any language but I am not able to switch them because the iBus does not respond as expected. Previously I had keboard layouts, I was able to set any shortcut but now all that is gone.

---

### Post by Regele IONESCU on 2012-06-07
Here is the solution I found on a different thread( [http://ubuntuforums.org/search.php?do=finduser&u=790603&starteronly=1]("http://ubuntuforums.org/search.php?do=finduser&u=790603&starteronly=1") ) and it really works for me (quote from user LewisTM):

1) Go to the Settings Manager/Keyboard/Layout tab and ensure that "Use system defaults" is set. Do not modify the rest.
2) Install xfce4-goodies or just xfce4-xkb-plugin
3) This will allow you to add a Keyboard Layouts plugin to your panel. Do so then right-click it and choose Properties.
4) Set everything to your liking: layout, switch keys, etc.

---

### Post by adido on 2012-07-05
hello, dle Ionescu

Can you please detail steps 3 & 4. Where is the new Keyboard Layout that should appear after I installed the plug-in? 

I'm a beginner Ubuntu user and I'm facing the same challenge. I would like to easily switch between Ro/ En/ De/ Fr

I completed steps 1 & 2 from your explanation, and I'm also running the last Ubuntu Studio.

Mersi fain,
Adi

---

### Post by adido on 2012-07-05
Just to give you all the details, after I installed the plug-in, my setting are:

Settings >> Input Method Switcher >> ibus (this was my original setting to switch between Fr/En) - do I live it like this?

Settings >> Settings Manager >> Keyboard >> Application Shortcuts >> xfce4-display-settings --minimal

Thanks again!

---

### Post by architectadrian on 2012-10-24
Dear Ionescu, Sir, a million thank you! (can I also write to you in Romanian? or is against the forum policies? don't know... however) you made my day!

---

### Post by architectadrian on 2012-10-24
adido, in case you didn't find a solution yet, I am detailing here Ionescu's advice that worked perfectly fine for me:

After you install the package (I understand you did this), you go into Settings Manager (right-click on the desktop or menu/Settings/Settings Manager), click on the Keyboard, go on the Layout tab (the third one, on top) and check "use system defaults"; you will need to logout and logon again if you change this. Then you right-click on the upper panel, go to "Panel" command, choose "Add new items", then you select the "Keyboard Layouts" addon from the list. The addon will show on the panel.
You right-click this addon -- initially with a flag on it -- and choose "Properties". In the new open window you can set all the details. Here you can choose how to "Change layout option" (what key to press to do that), you can add new "Keyboard layouts" in a lower section (I added here Romanian and French layouts) etc.
Good luck and thank you again, King Ionescu :)

---

### Post by Tweedle Dee on 2013-01-27
And a big thanks too from me to ionescu & architectadrian - worked great for me too - for gaelic):P

greets

willy

---

### Post by AngelGenchev on 2013-05-02
> **adido said:**
> hello, dle Ionescu
Can you please detail steps 3 & 4. .....Adi
Well go to your panel bar, Right-Click it, choose Panel->Add New Items; then type "key" in the search box and select "Keyboard Layouts". Now an icon will appear near your clock. You need to go to it, rightclick and select "Properties". At "Change Layout Option" select LeftAlt+LeftShift, at Keyboard Layouts add your desired layouts.

---

