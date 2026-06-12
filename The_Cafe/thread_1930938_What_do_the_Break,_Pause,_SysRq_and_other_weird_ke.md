---
title: "What do the Break, Pause, SysRq and other weird keys do?"
date: 2012-02-24
forum: The Cafe
---

### Post by AgenT on 2012-02-24
What do the following keyboard keys do? Do people still use them, and for what? And what is their function in a modern GNU/Linux or Ubuntu desktop or server?

The weird keys in question:

[LIST=1]
[*]SysRq
[*]Scroll Lock (ScrLk)
[*]Pause
[*]Break
[*]Insert
[/LIST]

If you have any other keyboard keys that you have no idea what they do, list them!

---

### Post by roelforg on 2012-02-24
> **AgenT said:**
> What do the following keyboard keys do? Do people still use them, and for what? And what is their function in a modern GNU/Linux or Ubuntu desktop or server?

The weird keys in question:

[LIST=1]
[*]SysRq
[*]Scroll Lock (ScrLk)
[*]Pause
[*]Break
[*]Insert
[/LIST]

If you have any other keyboard keys that you have no idea what they do, list them!

1. Launch the screenshot prog.
2. I don't have a clue
3. As the KB design comes from old systems and game consoles; i could see how you could use this to pause execution.
4. See 3. (Same key)
5. To switch between insert and replace (overwrite) modes for text-editors.

---

### Post by sudodus on 2012-02-24
SysRq:

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted.

See for example [[COLOR="Red"]_http://kember.net/articles/reisub-the-gentle-linux-restart/_[/COLOR]]("http://kember.net/articles/reisub-the-gentle-linux-restart/")

---

### Post by JRV on 2012-02-24
Holding down Alt and SysRq (which is the Print Screen key) and typing K will log you out and restart the X server.  This replaces <CTRL><ALT><Backspace> which is no longer supported in Ubuntu

---

### Post by mcduck on 2012-02-24
> **sudodus said:**
> SysRq:

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted.

See for example [[COLOR="Red"]_http://kember.net/articles/reisub-the-gentle-linux-restart/_[/COLOR]]("http://kember.net/articles/reisub-the-gentle-linux-restart/")

Actually holding down SysRq alone does that.

...but if your SysRq key is combined with the PrintScr key (like it usually is), you need the Alt to access the SysRq key in the first place. So the shortcut is either Alt+PrtScr+magic key, or SysRq+magic key. ;)

(...and yes, I'm using a machine with separate keys for PrtScr and SysRq, so no Alt for me when doing magic key shortcuts...:D)

Scroll Lock is rarely used for anything these days, but originally it altered between using arrow keys to move the cursor or to scroll the screen.

Pause will (or at least it used to) pause the current program until another key is (was) pressed. And Break has had many different uses, usually related to interrupting or stopping a program, or even rebooting the system. I'm not sure if Break really does anything on modern operating systems any more. (yes, my Pause and Break are also separate keys... What a great keyboard!)

...and like roelforg said, Insert key switches between insert and replace modes while typing text.

---

### Post by roelforg on 2012-02-24
> **mcduck said:**
> Actually holding down SysRq alone does that.

...but if your SysRq key is combined with the PrintScr key (like it usually is), you need the Alt to access the SysRq key in the first place. So the shortcut is either Alt+PrtScr+magic key, or SysRq+magic key. ;)

(...and yes, I'm using a machine with separate keys for PrtScr and SysRq, so no Alt for me when doing magic key shortcuts...:D)

Scroll Lock is rarely used for anything these days, but originally it altered between using arrow keys to move the cursor or to scroll the screen.

Pause will (or at least it used to) pause the current program until another key is (was) pressed. And Break has had many different uses, usually related to interrupting or stopping a program, or even rebooting the system. I'm not sure if Break really does anything on modern operating systems any more.

...and like roelforg said, Insert key switches between insert and replace modes while typing text.

On avg. i get 3 Support requests every month from family where the problem is accidentally pushing the insert key (usually the requester is in panic b/c text "disappears" when they type)... Man you start hating that key after a few month.

---

### Post by mcduck on 2012-02-24
> **roelforg said:**
> On avg. i get 3 Support requests every month from family where the problem is accidentally pushing the insert key (usually the requester is in panic b/c text "disappears" when they type)... Man you start hating that key after a few month.

:o

That is probably one of my most used keys in the keyboard. Something I'd have considered as basic key as Space or Return. It's amazing, and quite sad really, that people don't know how to use it any more.

...on the other hand I've had to help people with even more common keys, like Tab or Del. And of course misuse of the Return key is quite common when people are using word processors. Which only proves my belief that everybody should do a 2-week crash course on CLI only system before they are allowed to use a modern graphical UI. How much better people would understand what they are doing (and how much less problems they'd have in future) had they at least for a while actually done things without the UI hiding everything from them... ;)

---

### Post by forrestcupp on 2012-02-24
> **JRV said:**
> Holding down Alt and SysRq (which is the Print Screen key) and typing K will log you out and restart the X server.  This replaces <CTRL><ALT><Backspace> which is no longer supported in Ubuntu

Awesome. Thanks.

---

### Post by kurt18947 on 2012-02-24
I've come up with a use for the pause/break key in Firefox.  I installed an extension "customizable shortcuts" that enables me to assign browser functions to keys.  I made the pause/break key a 'page back' key.  It's located on my keyboard such that it works pretty well with a 2 button trackball.

---

### Post by grahammechanical on 2012-02-24
I thought so. SyRq = System Request.

[http://en.wikipedia.org/wiki/System_request]("http://en.wikipedia.org/wiki/System_request")

---

### Post by alphacrucis2 on 2012-02-24
Ctrl-Break is used with programmes like putty that can operate a serial console connection to a Cisco router. Ctrl-Break interrupts the normal boot process to get into the Cisco rommon

---

### Post by AgenT on 2012-02-27
Thanks everyone for the information. 

I had no idea people still used serial cables. So pause & break don't really do anything on modern machines/software, does it? I tried to use it in bash to "pause" or "break" execution, but it did nothing. I also tried in ssh, nothing. 

Double checked xev to make sure both buttons register correctly, and they do. Weird that they still make these two buttons on keyboards. And out of the two, only break is useful to probably no more than 0.001% of the computer population which still uses serial cables :)

I still don't get the point of Scroll Lock and why it's on any modern keyboard.

SysRq (system request) is insane! From what I understand, it does nothing by itself, but is used in combinations to send siganls straight to the kernel. In fact, there are like 50 key combinations! The [Magic SysRq key is crazy powerful]("http://en.wikipedia.org/wiki/Magic_SysRq_key").

So if I bind pause, break and scroll lock to some desktop / window shortcuts, similar to what kurt18947 suggested, I won't see any adverse effects, will I?

---

### Post by sudodus on 2012-02-27
> **AgenT said:**
> ...
So if I bind pause, break and scroll lock to some desktop / window shortcuts, similar to what kurt18947 suggested, I won't see any adverse effects, will I?
I don't use break at all. I have KVM switches in order to use one desktop set of hardware (monitor, keyboard, mouse, speakers) for several computers, and one of those KVMs actually uses 'doubleclick scroll lock' as a hotkey, but otherwise I have never used it.

So go ahead and bind those keys :-)

---

### Post by mcduck on 2012-02-27
> **AgenT said:**
> Thanks everyone for the information. 

I had no idea people still used serial cables. So pause & break don't really do anything on modern machines/software, does it? I tried to use it in bash to "pause" or "break" execution, but it did nothing. I also tried in ssh, nothing. 

Double checked xev to make sure both buttons register correctly, and they do. Weird that they still make these two buttons on keyboards. And out of the two, only break is useful to probably no more than 0.001% of the computer population which still uses serial cables :)

I still don't get the point of Scroll Lock and why it's on any modern keyboard.

SysRq (system request) is insane! From what I understand, it does nothing by itself, but is used in combinations to send siganls straight to the kernel. In fact, there are like 50 key combinations! The [Magic SysRq key is crazy powerful]("http://en.wikipedia.org/wiki/Magic_SysRq_key").

So if I bind pause, break and scroll lock to some desktop / window shortcuts, similar to what kurt18947 suggested, I won't see any adverse effects, will I?
All these keys are still used by various programs, even though they might not have any universal purpose any more.

And also keep in mind that in many industry (and other) fields, it's not uncommon to still run over 15 years old applications, in which case all keys and functions like this are still needed. Computers are not only for desktop and office applications... ;)

edit: you can actually use scroll lock to pause command output in Linux terminal, at least if you use it in a TTY instead of a terminal emulator running on your desktop. If you want to try it, hit Ctrl_Alt-F1 to get into TTY1, log in, run something like "ls -Rl" that results in loads of putput, and hit Scroll Lock...

---

### Post by nikonian on 2012-02-27
I have a special keyboard, that none of you have. It has an "[any]" key, useful for when software asks you to "Press any key to continue".

If you want it, it's a collector's item, and £45,000

---

