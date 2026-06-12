---
title: "Terminator - the cool terminal"
date: 2010-01-30
forum: The Cafe
---

### Post by steveneddy on 2010-01-30
Do lots of terminal work or want a cool terminal that is easy to set up and amaze your friends?

Terminator is your answer.

Not only a tabbed terminal but the cool feature is that is can be split horizontally and vertically, or both, or split with tabs.

Check out the pics and set up config files:

installed from ppa to get the newest version:

[https://launchpad.net/~gnome-terminator/+archive/ppa](https://launchpad.net/~gnome-terminator/+archive/ppa)

Set up the config files in 

~/.config/terminator/config

if you don't have a terminator folder in .config then just add it and then open up the terminator folder and create an empty document and name it config.

Add these lines:

```
background_type = transparent

background_darkness = 0.74

enable_real_transparency = true

scrollbar_position = disabled

```

save the file

now make a launcher with these settings in the Command area of the launcher properties:

```
terminator -b -n --geometry 720x450+300+150
```

This will give you a transparent terminal that launches in the middle of your screen without window borders or a scroll bar.

If you need to move Terminator, since you have no window borders to grab, just Alt+left click grab the terminal and move it wherever you want.

to close, either right click and select "Exit" or simply type **exit** in the terminal itself and hit Enter.

Have fun


:popcorn:

---

### Post by Dr Belka on 2010-01-30
I was introduced to terminator when I started using Crunchbang, and I have loved it ever since.

---

### Post by RiceMonster on 2010-01-30
It's cool; I like the concept. However, every time I tried to use it, it would flicker when I hit backspace. I'll probably try it again and see if it's still doing it.

---

### Post by chessnerd on 2010-01-30
That's nifty, but I actually prefer the maximize option instead of a mini-terminal in the middle of the screen. However, I'd never heard of Terminator before. I'll give it a try over the next few weeks. Terminator's got a pretty sweet concept and I'm sure I'll find a use for it.

---

### Post by Nevon on 2010-01-30
Looks somewhat neat, but I prefer Guake.

---

### Post by mobilediesel on 2010-01-30
> **RiceMonster said:**
> It's cool; I like the concept. However, every time I tried to use it, it would flicker when I hit backspace. I'll probably try it again and see if it's still doing it.

You have to edit ~/.config/terminator/config
and add ```
audible_bell = true
visible_bell = false
```
Then it will beep instead of flash. Or you could set both to false so it wont beep or flash.

The only thing I can't figure out in terminator is how to get the delete key to act like a delete key. When I hit delete, it is interpreted as a backspace.

---

### Post by bluebyt on 2010-01-30
Wow thank you, I like the tab feature!

Can I change the color of the active tab?

---

### Post by Rhapsody on 2010-01-30
> **Nevon said:**
> Looks somewhat neat, but I prefer Guake.
Similar here, but my preference is for Yakuake.

[[IMG]http://img692.imageshack.us/img692/5341/yakuake201001302.th.png[/IMG]](http://img692.imageshack.us/img692/5341/yakuake201001302.png)

Being able to press F12 and see a translucent terminal literally drop down from the top of the screen is about as cool as a terminal can be in my opinion.

---

### Post by Hetor on 2010-01-30
GNU Screen + Xfce4-terminal > all

---

### Post by RiceMonster on 2010-01-30
> **mobilediesel said:**
> You have to edit ~/.config/terminator/config
and add ```
audible_bell = true
visible_bell = false
```
Then it will beep instead of flash. Or you could set both to false so it wont beep or flash.

The only thing I can't figure out in terminator is how to get the delete key to act like a delete key. When I hit delete, it is interpreted as a backspace.

Thanks, that worked.

---

### Post by dragos240 on 2010-01-30
Looks rather bland. I actually like the xfce term the best.

---

### Post by LightB on 2010-01-30
> **Nevon said:**
> Looks somewhat neat, but I prefer Guake.

Same here. It's far more convenient.

---

### Post by steveneddy on 2010-01-30
> **bluebyt said:**
> Wow thank you, I like the tab feature!

Can I change the color of the active tab?

The regular Gnome Terminal has tabs, too, you know.

I don't know how to change the tab colors.

More config options here:

```
man terminator_config
```

---

### Post by dragos240 on 2010-01-30
> **steveneddy said:**
> The regular Gnome Terminal has tabs, too, you know.



As do most terms these days.

---

### Post by Daisuke_Aramaki on 2010-01-30
rxvt-unicode+tmux for me anyday with dvtm occasionally.

---

### Post by x33a on 2010-01-30
This is pretty good for regular wm/de, but if you are using a tiling wm then this is pointless. also, if you are using screen, then also, not much useful.

---

### Post by steveneddy on 2010-05-25
Works well with Lucid, also.

---

### Post by NMFTM on 2010-05-25
Seems like that would be very useful for when you are trying to read a man page and implement the instructions at the same time. Sure, I guess you could have multiple terminal windows open, especially with a widescreen monitor. But....

---

### Post by Rodney9 on 2010-05-26
Guake is terrific, thanks guys, I had never heard of it.

---

### Post by SciFi-Bob on 2010-07-14
> **NMFTM said:**
> Seems like that would be very useful for when you are trying to read a man page and implement the instructions at the same time. Sure, I guess you could have multiple terminal windows open, especially with a widescreen monitor. But....
Well, try tailing several log files, and at the same time have a shell open issuing commands (for example, debugging samba errors..)

it's a MUST!

---

### Post by Xianath on 2010-07-15
> **SciFi-Bob said:**
> Well, try tailing several log files, and at the same time have a shell open issuing commands (for example, debugging samba errors..)

```
tail -n 0 -f <file1> <file2> <file3> ... <fileN> | tee debugsession | less
```

---

### Post by Legendary_Bibo on 2010-07-15
For this Guake terminal, do you just have to hit the tilda key and it comes down and you can use whatever?

---

### Post by slackthumbz on 2010-07-15
Maybe I'm just not getting the point, what does terminator do that I can't do in screen? Also screen gives me a persistent session between logins and uses fewer system resources and it'll run in any terminal you could possibly want to use...

---

### Post by digitalcitizenx on 2010-07-15
> **slackthumbz said:**
> Maybe I'm just not getting the point, what does terminator do that I can't do in screen? Also screen gives me a persistent session between logins and uses fewer system resources and it'll run in any terminal you could possibly want to use...

OK - what WM? - what is the dock on top? - what is the icon style name?

please

;^)

---

### Post by slackthumbz on 2010-07-27
> **digitalcitizenx said:**
> OK - what WM? - what is the dock on top? - what is the icon style name?

please

;^)

the WM is compiz-fusion in gnome, I've just removed the gnome-panel altogether (requires a little gconf-editor jiggery pokery), the dock is Avant Window Navigator and the icon theme is 'Any Color You Like' from gnome-look.org

---

### Post by Zorgoth on 2010-07-28
+1 for screen

I just use guake, gnome-terminal, and screen mostly.

Guake is great for running a command line process transparent over your whole screen so you can watch its progress while at the same time being bored and also looking at your sudoku or whatever.

Terminator does look moderately cool, and I will look into it though as a possible replacement/addition to gnome-terminal :)

The main advantages over screen would be that
a) you can click to change frames, which is moderately useful, although I normally use the keyboard to do that anyway
b) you don't clutter up your screen sessions with tasks that don't need screen
c) you can scroll with the scroll wheel/touchpad

---

### Post by Lucradia on 2010-07-28
> **steveneddy said:**
> Works well with Lucid, also.

Lol, almost 6 month bump.

---

### Post by Zorgoth on 2010-07-28
OK, ten minutes of experimentation and I am definitely using terminator.  It does look like it is a little bit heavier than gnome-terminal, but it seems plenty fast so far.

---

### Post by doorknob60 on 2010-07-28
There's two terminals called terminator, here's the other: [http://software.jessies.org/terminator/](http://software.jessies.org/terminator/)

I thought they were the same for a while...then I realized one was python and one was Java :P Not sure which one is better...

---

### Post by aikikode on 2010-12-17
I agree - Terminator is a very handy tool in Gnome, it's a must-have when it comes to screen splitting (also I must admit KDE konsole also has such feature).

To me it has only one drawback: the style of tabs is not customizable and tab height is too much. But as it is said on its development forum they use GTK theme and not going to override it.

---

