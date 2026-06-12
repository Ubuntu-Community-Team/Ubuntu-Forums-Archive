---
title: "Beryl without gnome or other Desktop?"
date: 2007-02-20
forum: The Cafe
---

### Post by m.e.danko on 2007-02-20
I wonder if anyone can help me, I really like beryl and think that it is a wonderful window manager but I would like to know if anyone can point me to a solution, I would like a really minimal desktop environment but not gnome or xfce4 -- I'm looking for something like FVWM but with beryl running, I understand that FVWM is just a window manager that's why I am asking. Thank in advance, Martin.

---

### Post by erkki70 on 2007-02-20
Hi,
Looks like there's not much point in running Beryl alone...
Read this post:
[http://ubuntuforums.org/showthread.php?t=365724](http://ubuntuforums.org/showthread.php?t=365724)
Cheers,

---

### Post by Kindred on 2007-02-20
I usually run Beryl alone when i'm playing with it, I usually just have a key bind to a run dialog app of some kind (gmrun works great) and it's fine.  I think there's a seperate root desktop menu app around too but I haven't tried that yet.

---

### Post by reacocard on 2007-02-20
Shouldn't be hard, just make a session script that launches the things you need. Something like

```
#!/bin/sh

<autostarted apps go here> &

emerald &
exec beryl
```

Would be enough. Then use that for .Xsession or make a .desktop file using it for GDM. Voila, pure beryl goodness.

As for apps to go with it, that's up to you. You'll probably want a simple panel (pypanel?), a desktop, and possibly a run dialog.

---

### Post by RAV TUX on 2007-02-20
I would love to run Beryl in Fluxbox or E16.

---

### Post by bonzodog on 2007-02-20
Rav, see the other thread referenced above - you can't run Beryl in Flux or E17, because they are both the same thing-  Window Managers. Besides, E17 has it's own set of composite effects, much like xfwm.

---

### Post by reacocard on 2007-02-20
> **bonzodog said:**
> Rav, see the other thread referenced above - you can't run Beryl in Flux or E17, because they are both the same thing-  Window Managers. Besides, E17 has it's own set of composite effects, much like xfwm.

Exactly. However, the tools that come with the WM (panels, docks, etc.) *can* be used with beryl. You just have to figure out how to launch them w/o the WM.

---

### Post by m.e.danko on 2007-02-21
Hello, thanks for everyones replies, with the help of the links posted and other searching around the internet I kind of found out the answer to my question, so thanks alot. 

To run beryl on it own (Just in case anyone is interested) basically what you do is load beryl then load separate desktop bits.

Associate A keyboard shortcut command in beryl to run an application. I choose **<Alt>r** to run **xfrun4** - The xfce4 run dialog box.

Log into a TTY
Stop X running
run **xinit beryl**
Press **<Alt>r**
type **emerald** to get window borders.
Press **<Alt>r** to load say [B]xfce4-panel
[/B]

if you have gnome installed **<Alt>r** nautilus - if you want desktop icons.

I do have another question though, does fluxbox or blackbox or any small window manager have separate little applications like xfce4 does to say load the desktop menu? If so what ones? 

Thanks in advance, Martin.

---

### Post by pulver on 2007-02-21
> **RAV TUX said:**
> I would love to run Beryl in Fluxbox or E16.

you what!? I'd like to run e16 in beryl :) then I'd have a cube with 2048 desktops
now take that for a spin! muahahaha :guitar:

---

### Post by Kindred on 2007-02-21
> **m.e.danko said:**
> Hello, thanks for everyones replies, with the help of the links posted and other searching around the internet I kind of found out the answer to my question, so thanks alot. 

To run beryl on it own (Just in case anyone is interested) basically what you do is load beryl then load separate desktop bits.

Associate A keyboard shortcut command in beryl to run an application. I choose **<Alt>r** to run **xfrun4** - The xfce4 run dialog box.

Log into a TTY
Stop X running
run **xinit beryl**
Press **<Alt>r**
type **emerald** to get window borders.
Press **<Alt>r** to load say [B]xfce4-panel
[/B]

if you have gnome installed **<Alt>r** nautilus - if you want desktop icons.

I do have another question though, does fluxbox or blackbox or any small window manager have separate little applications like xfce4 does to say load the desktop menu? If so what ones? 

Thanks in advance, Martin.

Sorry if I misunderstand.. but you know, you can start all these apps in ~/.xinitrc so they all launch when X does instead of doing this manually. 

e.g for when I use openbox:

eval `cat $HOME/.fehbg` &
exec xfce4-panel &
exec dbus-launch --exit-with-session openbox
exec openbox

Just a matter of playing around with it really. 

Also, since you didnt want xfce, you might consider using gmrun instead of the xfce run, it's actually better I think (tab completion for one..).

---

### Post by m.e.danko on 2007-02-21
> **Kindred said:**
> Sorry if I misunderstand.. but you know, you can start all these apps in ~/.xinitrc so they all launch when X does instead of doing this manually. 

e.g for when I use openbox:

eval `cat $HOME/.fehbg` &
exec xfce4-panel &
exec dbus-launch --exit-with-session openbox
exec openbox

Just a matter of playing around with it really. 

Also, since you didnt want xfce, you might consider using gmrun instead of the xfce run, it's actually better I think (tab completion for one..).

Thanks for that information Kindred, I'll try that out, I only really wanted to play around with beryl on its own with hardly anything running, just a couple of apps etc, I  wont give up on having a desktop and beryl running. How can I? I could go without Gnome! Thanks anyways, Martin. :)

---

