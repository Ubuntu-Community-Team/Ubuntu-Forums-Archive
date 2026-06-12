---
title: "&quot;semi-tiling&quot; window manager-- is there such a thing?"
date: 2008-10-19
forum: The Cafe
---

### Post by MaxIBoy on 2008-10-19
What I'm looking for is a window manager that normally acts like a standard overlapping window manager, but can be told not to allow one specific window to overlap with another specific window, or not to allow one window to overlap with any other windows but the other windows can overlap each other, and various other things like that. Is there something along those lines?

---

### Post by jimi_hendrix on 2008-10-19
awesome...i had a hard time finding tutorials though

---

### Post by LaRoza on 2008-10-19
wmii and xmonad can do that.

---

### Post by MaxIBoy on 2008-10-19
Awesome! I'm gonna try that!

Can you really make ad-hoc one-off rules for specific windows? (Example: gedit can overlap with Xterm but not the calculator, xterm can overlap with the calculator or gedit, thunar can't overlap with anything, and Audacious is always on top.)


EDIT: I can already see that wmii won't do that, just by looking at the manpage. However, it's a decent approximation of what I need. I'll use it for a while, see if it's good enough.

But seriously, 500-odd kilobytes total for an entire window manager and some dependencies? I'm impressed.

---

### Post by Dr Small on 2008-10-19
Wmii can make windows 'float'.

---

### Post by Grant A. on 2008-10-19
Personally I can't use a window manager that has no theme-ability or no already made themes ATLEAST similar to Windows 2k's theme.

I am a noob on these tiling window managers... is it possible to make wmii or xmonad to run over kde's window manager?

---

### Post by MaxIBoy on 2008-10-19
No, but I see no reason why you couldn't use it in KDE. The window borders will look different, though. (Haven't actually tried wmii yet, only installed it. This is based on technical knowledge and experience running *box under GNOME.)

---

### Post by LaRoza on 2008-10-19
> **Grant A. said:**
> Personally I can't use a window manager that has no theme-ability or no already made themes ATLEAST similar to Windows 2k's theme.

You are missing the point ;) There is no "theme ability" because you shouldn't be looking at nothing. 

You can do a bit of colouring though. If you plan at looking at the window title bars or desktop, then you shouldn't use a tiling window manager. If you plan on doing work with applications, then tiling is for you.

---

### Post by -grubby on 2008-10-19
> **Grant A. said:**
> 
I am a noob on these tiling window managers... is it possible to make wmii or xmonad to run over kde's window manager?

I'm not sure what you mean there.. but I doubt it since kwin and wmii are both window managers. I tried running wmii and kdesktop together, it didn't work well

---

### Post by MaxIBoy on 2008-10-19
So anyway, is there a way to set up these kind of elaborate rules (described in my earlier post) on-the-fly? Multiple tiling and floating layers which can be added and removed at random would do the job.

---

### Post by Istonian on 2008-10-19
There is a compiz plugin that allows you to tile. Its called tile...

---

### Post by kk0sse54 on 2008-10-19
I use AwesomeWM and it's a fantastic hybrid

---

### Post by evilkastel on 2008-10-19
well, eitherway is not very likely to achieve what you want, that's selective overlapping, but really selective. And in the matter of coloring and themes... i don't know. personally i don't like to use even emerald in GNOME, (but i have a nice looking dark theme)

---

### Post by MaxIBoy on 2008-10-19
> **Istonian said:**
> There is a compiz plugin that allows you to tile. Its called tile...
Doesn't actually ENFORCE the tiling, though. If you want to stay tiled, you have to hit the key combo over and over again.


AwesomeWM doesn't seem to be what I'm looking for, but thanks anyway.

---

### Post by Lux Perpetua on 2008-10-19
> **Grant A. said:**
> Personally I can't use a window manager that has no theme-ability or no already made themes ATLEAST similar to Windows 2k's theme.If you care deeply about window title bars, then tiling managers are probably not for you. However, if it's GTK theming you want, then it's just a matter of running gnome-settings-daemon. The window manager is irrelevant.

---

### Post by kk0sse54 on 2008-10-19
> **MaxIBoy said:**
> 
AwesomeWM doesn't seem to be what I'm looking for, but thanks anyway.

Mind if I ask why? I know my biggest problem with it was that it was utterly confusing at first and I didn't even know how to launch any programs. Other than the obvious tiling wm's like wmii, dwm etc etc have you tried Echinus?

---

### Post by MaxIBoy on 2008-10-19
What I need is to be able to set up elaborite sets of window management rules on the fly. If you don't mind, I'll just copy and paste from an earlier post of mine:
> (Example: gedit can overlap with Xterm but not the calculator, xterm can overlap with the calculator or gedit, thunar can't overlap with anything, and Audacious is always on top.) And then I can totally change that set of rules with a few holding-down-a-combo-and-clicking-a-few-windows actions. For example, hold down alt-shift, select gedit, then select thunar, and from then onwards, gedit cannot overlap with that specific thunar window (although there are no rules for if I pull up a seperate thunar window.) 

I could accomplish something approximating this if there was a WM that allowed multiple layers of floating and tiling windows to be added and removed at random. Is there anything like this out there?

---

### Post by elmer_42 on 2008-10-19
Sadly, I don't know anything that sounds like what you are mentioning. The only thing I really miss from switching from Compiz+GNOME to Openbox is the Maximumize plugin [SIZE="1"](if anybody knows how to do something similar to it, I will give you a cookie)[/SIZE]. Perhaps that would help?

---

### Post by chucky chuckaluck on 2008-10-19
to the OP, if i understand what you're asking for, it sounds like it would be a lot easier to just do all that with your mouse. openbox has an option to open new windows under the mouse (instead of the heap in the middle) and it generally opens windows in the same geometry they were closed in. maybe that would be close.

xmonad has instructions on their site for using it as a window manager for both gnome and kde (and i think xfce). i know i've seen screenshots of it, but i don't know how good a setup it produces.

---

### Post by cardinals_fan on 2008-10-19
> **elmer_42 said:**
> Sadly, I don't know anything that sounds like what you are mentioning. The only thing I really miss from switching from Compiz+GNOME to Openbox is the Maximumize plugin [SIZE="1"](if anybody knows how to do something similar to it, I will give you a cookie)[/SIZE]. Perhaps that would help?
Devilspie can provide window-specific rules.  It works with Openbox.

---

### Post by MaxIBoy on 2008-10-19
Ooh, I already have openbox! *investigates*

---

### Post by kk0sse54 on 2008-10-19
> **MaxIBoy said:**
> What I need is to be able to set up elaborite sets of window management rules on the fly. If you don't mind, I'll just copy and paste from an earlier post of mine:
 And then I can totally change that set of rules with a few holding-down-a-combo-and-clicking-a-few-windows actions. For example, hold down alt-shift, select gedit, then select thunar, and from then onwards, gedit cannot overlap with that specific thunar window (although there are no rules for if I pull up a seperate thunar window.) 

I could accomplish something approximating this if there was a WM that allowed multiple layers of floating and tiling windows to be added and removed at random. Is there anything like this out there?

ahh quite a predictament there my friend :) as for which I have no recommendation for. The closest thing I could think of would be to edit an awesomerc so that certain programs open tiled on one virtual desktop while opening others on another virtual desktop set to float. Problem there would be you would have to switch between virtual desktops. I'd instead try looking into the Compiz window's rule plugin and setting specific programs to open without a window title similiar to how one would use compiz to embed a terminal into the desktop.

---

### Post by MaxIBoy on 2008-10-19
Mmm... well, if I were to let the cat out of the bag, I was basically thinking of making something along these lines myself, and I was wondering if such a thing existed.

No guarantees, though, I certainly don't have time to make it now.


Thanks for all the help everyone, you guys are great!

---

