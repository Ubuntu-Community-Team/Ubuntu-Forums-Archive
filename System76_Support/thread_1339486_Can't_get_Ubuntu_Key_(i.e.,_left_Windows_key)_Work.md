---
title: "Can't get Ubuntu Key (i.e., left Windows key) Working"
date: 2009-11-27
forum: System76 Support
---

### Post by NathanZal on 2009-11-27
My system is a Pangolin Performance Version 6, Ubuntu 9.10

Following the instructions here:

[http://knowledge76.com/index.php/Map_Win-Key_To_Main_Menu](http://knowledge76.com/index.php/Map_Win-Key_To_Main_Menu)

I am unable to change the keyboard shortcut bound to "Show the panel's main menu" in "Keyboard Shortcuts" from Alt+F1 to the Ubuntu key. When I press the Ubuntu key (as the instructions direct) nothing happens.

Yes, I did the initial "System -> Keyboard -> Layouts -> Layout Options -> Alt/Win key behavior -> Add the standard behavior to Menu key," but this, of course, has nothing at all to do with the Ubuntu key. And yes, the Menu key produces the context menu as expected.

xev returns this when I press the Ubuntu key:

KeyPress event, serial 36, synthetic NO, window 0x4a00001,
    root 0x13c, subw 0x4a00002, time 19509475, (30,47), root:(1447,764),
    state 0x0, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

... so the key is recognized as Super_L.

BUT when I type something like "Ubuntu-M" (at the same point in System -> Preferences -> Keyboard Shortcuts) it inserts "Mod4-M" as the shortcut; at that point ubuntu-M works in the way that I would like Ubuntu by itself to work. Clearly it's mapping Super_L as a modifier key and not as a simple key; here's my xmodmap output:

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

...so clearly if I want the "Ubuntu key" to produce the Gnome applications menu, I'll need to change this mapping. I don't care about emulating the Windows key behavior; I just want the Ubuntu key to produce the applications menu.

What would be the best way to go about fixing this? I  assume that the key bindings changed with 9.10; presumably the directions in the System76 Knowledge Base will need to be updated eventually. Unless, of course, I've missed something important

By the way, I did have to add a custom shortcut to get the middle quick key (the one with the "W" in it) to open up a browser. It's not mapped to any of the usual suspects, like "XF86WWW" or "XF86Explorer" (which is a good one on Linux...;) but "XF86HomePage." I set it to "firefox" and it comes up now.

Thanks!

Nathan

---

### Post by NathanZal on 2009-11-27
I stumbled on a workaround. If I do this in a console:

>xmodmap -e "remove mod4 = Super_L"

...then when I go back into "Keyboard Shortcuts" and attempt to change the shortcut for the panel menu, pressing the Ubuntu key produces "Super_L," which is what I wanted it to be in the first place.

So the ubuntu key now produces the panel menu.

Better yet, this setting survives rebooting. Even though xmodmap says Super_L is once again a mod4 key, it still works as a panel menu key.

I presume there is a way to fix this that isn't a hack.

---

### Post by betrunkenaffe on 2009-11-29
It's usually used as a modifier key, you just happen to not want it to act like that so I highly doubt it.

You could do a super-X or super-spacebar which will pop up menu with little difficulty.

---

### Post by NathanZal on 2009-11-29
> **betrunkenaffe said:**
> It's usually used as a modifier key, you just happen to not want it to act like that so I highly doubt it.

You could do a super-X or super-spacebar which will pop up menu with little difficulty.
It's supposed to do both on Windows machines, actually. I don't care about the other "Windows key shortcuts" however, as I said before. What I've done here works fine for me, but thanks for the suggestion.

---

### Post by vgrisham on 2009-11-29
Thanks for the workaround, NathanZal.

---

### Post by betrunkenaffe on 2009-11-30
> **NathanZal said:**
> It's supposed to do both on Windows machines, actually. I don't care about the other "Windows key shortcuts" however, as I said before. What I've done here works fine for me, but thanks for the suggestion.

It does but Linux isn't Windows :)

---

### Post by mrebanza on 2009-12-08
no it isn't . . . . it's better . . . . thats why we should work to make it standards complaint and the "Window" or "Ubuntu Super Key" is a standard at this point . . . . I challenge you to find a generic keyboard for sale that does not have one . . . .

---

### Post by Lee_Machine on 2009-12-08
There was this one, but it was discontinued. 

[http://www.amazon.com/Cherry-CyMotion-Master-Linux-Keyboard/dp/B000LXZRXQ](http://www.amazon.com/Cherry-CyMotion-Master-Linux-Keyboard/dp/B000LXZRXQ)

Another thing I had a hard time in doing was finding a good HTPC remote that did not have the Windows Logo on it.

---

### Post by jdb on 2009-12-09
> **Lee_Machine said:**
> There was this one, but it was discontinued. 

[http://www.amazon.com/Cherry-CyMotion-Master-Linux-Keyboard/dp/B000LXZRXQ](http://www.amazon.com/Cherry-CyMotion-Master-Linux-Keyboard/dp/B000LXZRXQ)

Another thing I had a hard time in doing was finding a good HTPC remote that did not have the Windows Logo on it.

The little stickers that Sytem76 sends out work pretty good.

jdb

---

### Post by AZ_RUNE on 2009-12-11
Nathan,

when you execute the command below does that modify it for all users on the system or just for your user account?

Thanks,
AZ_RUNE

> **NathanZal said:**
> I stumbled on a workaround. If I do this in a console:

>xmodmap -e "remove mod4 = Super_L"

...then when I go back into "Keyboard Shortcuts" and attempt to change the shortcut for the panel menu, pressing the Ubuntu key produces "Super_L," which is what I wanted it to be in the first place.

So the ubuntu key now produces the panel menu.

Better yet, this setting survives rebooting. Even though xmodmap says Super_L is once again a mod4 key, it still works as a panel menu key.

I presume there is a way to fix this that isn't a hack.

---

### Post by ligaa9mm on 2009-12-17
[COLOR=Gray]Hey UbuntuForums,

I am, admittedly, an Ubuntu n00b. I have a Starling netbook running 9.10 NR, and I love it. It's taught me a lot about the OS as well, as it complements my desktop running 9.10.

Anyway, to help me make the "transition" into Ubuntu, I was hoping to get the Ubuntu key on my Starling to act like the Windows key. At the very least, I'd like to be able to simply press it and have it take me to the desktop (or Favorites section in Netbook Remix). I was able to go into the Keyboards Shortcut program and set things like Ubuntu+R to open a terminal. I also set the hyper key to work as win-keys, whatever that means...

I tried finding a tutorial or something to help me out, but I think half of my problem is that I don't rightly know what to call this key. It shows up on the system as Mod4, but other than that, I don't know if it's a Meta key, Hyper key, or what.

Can anyone shed some light on this?
Also, when the Keyboards utility mentions Win-keys, what exactly is it refering to?

Thanks for the insight and the help. :)[/COLOR]     


**Edit:** 
Sorry I didn't see this thread originally. But, following NathanZal's workaround, I was able to map the Ubuntu key as SuperL in the Keyboard Shortcuts utility. Now it does whatever I want, but only as a single key, or a single function of that key. Any shortcuts I had set before to be Mod4+____ no longer work, as the function of the SuperL key supersedes them.
Just for everyone's FYI. I'm going to set it back to being a Mod key and manually set Windows-like shortcuts. To be clear, you can do this to set it back if you also disabled Mod4:

>xmodmap -e "add mod4 = Super_L"

Simple enough that even I figured it out. :P

---

### Post by tharpa on 2010-01-31
> **NathanZal said:**
> I stumbled on a workaround. If I do this in a console:

>xmodmap -e "remove mod4 = Super_L"

...then when I go back into "Keyboard Shortcuts" and attempt to change the shortcut for the panel menu, pressing the Ubuntu key produces "Super_L," which is what I wanted it to be in the first place.

So the ubuntu key now produces the panel menu.

Better yet, this setting survives rebooting. Even though xmodmap says Super_L is once again a mod4 key, it still works as a panel menu key.

I presume there is a way to fix this that isn't a hack.

Thanks, Nathan, that works great!

---

### Post by Groucho Marxist on 2010-02-08
> **NathanZal said:**
> I stumbled on a workaround. If I do this in a console:

>xmodmap -e "remove mod4 = Super_L"

...then when I go back into "Keyboard Shortcuts" and attempt to change the shortcut for the panel menu, pressing the Ubuntu key produces "Super_L," which is what I wanted it to be in the first place.

So the ubuntu key now produces the panel menu.

Better yet, this setting survives rebooting. Even though xmodmap says Super_L is once again a mod4 key, it still works as a panel menu key.

I presume there is a way to fix this that isn't a hack.

Thank you very much for posting this! My Ubuntu key is working and my laptop is now 28% more awesome :D

---

### Post by hariks0 on 2010-05-05
Extend the functions with the Super key by following the link at my signature.

---

### Post by NathanZal on 2010-06-01
> **AZ_RUNE said:**
> Nathan,

when you execute the command below does that modify it for all users on the system or just for your user account?

Thanks,
AZ_RUNE
Since the keyboard shortcuts are in the "Preferences" menu, and the xmodmap command is executed as user and not superuser, my guess is that it is user specific, and not machine wide. I don't use multiple accounts, though. Why don't you give it a try and let us know how it works out?

By the way, I had to redo the workaround after upgrading to 10.04. No surprises there.

Cheers!

---

### Post by libssd on 2010-06-11
> **NathanZal said:**
> I stumbled on a workaround. If I do this in a console:

>xmodmap -e "remove mod4 = Super_L"

...then when I go back into "Keyboard Shortcuts" and attempt to change the shortcut for the panel menu, pressing the Ubuntu key produces "Super_L," which is what I wanted it to be in the first place.

So the ubuntu key now produces the panel menu.

Better yet, this setting survives rebooting. Even though xmodmap says Super_L is once again a mod4 key, it still works as a panel menu key.

I presume there is a way to fix this that isn't a hack.
Thanks for posting this. Default behavior for this key changed in 10.04; it worked exactly as you desired in 9.04 and 9.10. I had gotten accustomed to using the "Windows" key (which was labeled as a "Home" key on a Linux Acer AA1) to jump to the desktop. I don't know why Canonical changed the behavior, nor (as far as I can see) why the change isn't documented.

---

### Post by Prium on 2010-08-07
Well, I have used my Super L key to function as the Expo Key ever since I starting using Ubuntu (Hardy), because to me a 'windows key' is far more useful in allowing me to zoom out to show all my desktops :) 

But upgrading to 10.04 broke it. 

Nothing I have read anywhere so far is able to fix this. 

If I clear the Expo key binding from within Compiz and reset it to just the super key, pressing it once makes all my windows disappear and just shows the desktop. Pressing it again brings them back. But the Expo Key is not supposed to do this, obviously. The Expo key zooms out to show the desktops. If I rebind the expo key to 'Ctrl-0' or whatever it does as it should. 

What is going on with the Super L key in 10.04?? 

This didn't change anything for me: 

xmodmap -e "remove mod4 = Super_L


xev gives: 
  ```
  KeyRelease event, serial 35, synthetic NO, window 0x5200001,
    root 0x111, subw 0x0, time 4619735, (-297,517), root:(798,570),
    state 0x40, keycode 133 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```


*Update*

Correction --> after upgrading to 10.04 the key binding settings in my main user account were fully intact (SuperL was and still is bound to Expo Key). But in my wife's account this does not/cannot happen. When I try, the little grey box that shows the key binding immediately changes to 'disabled'. Marvellous. Prehaps if I can somehow apply my account settings to be system wide as the default for all accounts, then this could fix it?

---

### Post by thomasaaron on 2010-08-09
I think in 10.04, the Expo key combination is the Windows Key and Tab simultaneously.

---

### Post by hariks0 on 2010-08-10
> **thomasaaron said:**
> I think in 10.04, the Expo key combination is the Windows Key and Tab simultaneously.

To know/reset the binding to default, one may click on the reset button at the end of the item [with a sweep icon]

:o

---

