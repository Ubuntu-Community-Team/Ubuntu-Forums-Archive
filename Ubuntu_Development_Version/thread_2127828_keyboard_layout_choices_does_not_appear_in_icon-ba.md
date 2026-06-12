---
title: "keyboard layout choices does not appear in icon-bar"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by shantiq on 2013-03-21
i have installed 13.04 with Gnome-fallback and gone to keyboard to System-Settings/keyboard/layout settings and picked French and Russian to add to my English default but the icon does not appear on icon-bar so i cannot switch between layouts


Any ideas to make icon appear [that is the priority here] and/or an easy way to switch from commandline maybe?

---

### Post by dino99 on 2013-03-21
i does not remember exactly the name of the addon you need to "add to panel" when you right click on it; its about the now deprecated systray replaced by appmenu, but not all apps have been updated.

---

### Post by shantiq on 2013-03-21
does that mean wait?   it will be added later?

all i have under k is Keyboard accessibility


[ATTACH=CONFIG]240407[/ATTACH]

---

### Post by dino99 on 2013-03-21
try to "add to panel" : indicator applet appmenu

---

### Post by shantiq on 2013-03-21
hmmmmmmmmm  not only has it nowt to do with keyboard layout but once added cannot be removed the usual way [click ALT right-click remove] but has to be taken down i synaptic and then reload computer to see it gone..

 so if anyone actually knows how to make the keyboard layout icon on gnome appear would still love** that** info ... thanx

---

### Post by dino99 on 2013-03-21
the keyboard icon was monitored by ibus (gnome 3.6) , but now you need to open the System Settings window, then check the keyboard icon inside (gnome 3.8)

---

### Post by shantiq on 2013-03-21
[ATTACH=CONFIG]240409[/ATTACH]

and then pick keyboard layout to set your choices...   that cannot be dragged to the icon-bar   ....    so does anyone know how to do that please

---

### Post by dino99 on 2013-03-21
gnome-fallback is slowly dying, thats it; so stay with the oldish config or use the few ubuntu forks still using the old gnome

---

### Post by shantiq on 2013-03-21
none of these remarks have helped any so far [and once made me waste 15 minutes trying to remove the suggested addition]; 

 please let someone who actually might know about this help here thanx [4 interventions and no help]  >  gnome-fallback is slowly dying is not help; simply sounds to me like judgement; if you know what you are doing all can still work well perfectly with fallback; I am trying to get someone who does regarding this specific issue...

---

### Post by zika on 2013-03-21
> **shantiq said:**
> none of these remarks have helped any so far [and once made me waste 15 minutes trying to remove the suggested addition]; 

 please let someone who actually might know about this help here thanx [4 interventions and no help]   is not help; simply sounds to me like judgement; if you know what you are doing all can still work well perfectly with fallback; I am trying to get someone who does regarding this specific issue...If You want to get it fixed You have to file a bug in LaunchPad... I guess...

---

### Post by shantiq on 2013-03-21
Thanx zika   might do that

I am just wondering whether i forgot to install something or other
but from past installs i cannot remember adding anything; simply adding languages to Keyboard layout was always enough;   no doubt it will all become clear soon one way or the other

i surely cannot be the only guy trying to add layouts with fallback;   wonder how the others are faring?

---

### Post by zika on 2013-03-21
> **shantiq said:**
> Thanx zika   might do that

I am just wondering whether i forgot to install something or other
but from past installs i cannot remember adding anything; simply adding languages to Keyboard layout was always enough;   no doubt it will all become clear soon one way or the other

i surely cannot be the only guy trying to add layouts with fallback;   wonder how the others are faring?There is a thread about that that I've started long ago... If I understand correctly, You are having trouble adding a new language/layout...? If so, You might want to search for that thread of mine... No solution, sadly, yet, that I've found...

---

### Post by dino99 on 2013-03-21
This need some effort of that OP to understand that config change with the packages updating. Its the case about gnome-fallback with is deprecated and replaced by gnome-classic (gnome-shell sub DE). The keyboard icon was pushed by ibus, but again i says "was".
Thats it, i've explained how the system have changed. Its up to that OP to accept it or not.

---

### Post by sudodus on 2013-03-21
Until that bug is fixed, you can use setxkbmap. See this list to find which short description to use (in 12.04 LTS but maybe the same in 13.04)
```
less /usr/share/X11/xkb/rules/base.xml
```

```
setxkbmap gb
```
```
setxkbmap fr
```
```
setxkbmap ru
```

---

### Post by zika on 2013-03-21
> **sudodus said:**
> Until that bug is fixed, you can use setxkbmap. See this list to find which short description to use (in 12.04 LTS but maybe the same in 13.04)
```
less /usr/share/X11/xkb/rules/base.xml
```

```
setxkbmap gb
```
```
setxkbmap fr
```
```
setxkbmap ru
```
Or You could put all hat in one line and choose key to change between them...
I use:
```
/usr/bin/setxkbmap -option lv3:ralt_switch,grp:sclk_toggle,grp_led:scroll,eurosign:5 rs,us,rs -variant latin, altwin:swap_lalt__lwin, caps:super
```

---

### Post by shantiq on 2013-03-22
ok thanx for these great suggestions   [will investigate the commandline/hotkey solutions; they look excellent]




  just found  [another gui route]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914/comments/86") here  

apparently been an issue for a while  [see]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1045914")


[ATTACH=CONFIG]240438[/ATTACH]     The trick or workaround is to install gkrellm-xkb, run gkrellm and turnoff all monitors except xkb [Thanx to Robotron for the idea]

 This is done quite easily; once loaded click on plugins and allow xkb; click on Builtins and untick them all one by one
 Position the applet where wanted and allow 'remember screen location' then to go and add to startup apps


 This is to me a perfectly satisfactory solution .  
Marked as solved  [hhhhhmmm  how to [do this]("http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730") on new Forum?]

---

