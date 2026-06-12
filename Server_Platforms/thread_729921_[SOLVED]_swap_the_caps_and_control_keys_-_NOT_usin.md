---
title: "[SOLVED] swap the caps and control keys - NOT using desktop env"
date: 2008-03-20
forum: Server Platforms
---

### Post by MountainX on 2008-03-20
I hope this is a good place to ask my question.

How would I swap the caps and control keys at the system level **outside the desktop environment**? I want them to remain swapped when I exit the desktop environment. 

I figured you guys in the server forum might know how to do that. Thanks.

---

### Post by unutbu on 2008-03-20
Do you mean on the virtual console, outside of X?

---

### Post by MountainX on 2008-03-20
Yes, outside of X. It would be ideal if these keys are swapped everywhere I could possibly type. (I suppose it isn't possible to swap them at the bios level -- not that I wouldn't want them swapped there too if I could do it.)

---

### Post by unutbu on 2008-03-20
The command you want is something like

```

loadkeys <keymap>

``` 

See [http://c2.com/cgi/wiki?RemapCapsLock](http://c2.com/cgi/wiki?RemapCapsLock)

The problem is, it refers to emacs2.kmap.gz, which is not on gutsy. I'm googling around to see if I can find emacs2.kmap or an equivalent...

---

### Post by unutbu on 2008-03-20
Ok, no problem: just make a file

```

keymaps 0-63
keycode  58 = Control
keycode  29 = Caps_Lock

```

I'll call it ctrlcapswap.kmap.

From the console, run
```

sudo loadkeys ctrlcapswap.kmap

```

---

### Post by MountainX on 2008-03-20
Thank you! Is there a way to make this loadkeys command run automatically when my system boots?

Can it load even before I log in?

---

### Post by unutbu on 2008-03-20
```

sudo nano /etc/rc.local

```

Add
```

sudo loadkeys ctrlcapswap.kmap

```

*BEFORE* the last line which says 'exit 0'.

Reboot, and I think it should work.

---

### Post by MountainX on 2008-03-20
Thanks. I'll post back if that doesn't work.

---

### Post by MountainX on 2008-03-22
Works perfectly. Thanks!

---

### Post by ubernoob on 2008-03-22
just out of curiousity.... why would someone want to swap these keys? :)

---

### Post by MountainX on 2008-03-22
> **ubernoob said:**
> just out of curiousity.... why would someone want to swap these keys? :)

faster typing
The control key is hard to reach while the little-used caps lock key is easy to reach

---

### Post by unutbu on 2008-03-22
Since you are asking, it means you have a very strong pinky and a very flexible wrist. :)

---

### Post by MountainX on 2008-03-26
I did this on a desktop system with GNOME and it doesn't seem to have an effect in the GUI. 

I could change the keyboard settings inside the GUI using the utility, but that seems to only affect the logged in user.

Is there a way to change the key assignments in one place will affect the entire system?

The best I can do at the moment is use the steps unutbu provided ***plus*** change the keyboard assignment for each user, but then **I still have the old key assignments at the Ubuntu login screen** Plus it is a pain to have to change the setting in multiple places.

SUMMARY:
Make a file called /etc/SwapCapsCtrl.kmap

```

keymaps 0-63
keycode  58 = Control
keycode  29 = Caps_Lock

```

To make permanent, edit:
```

sudo nano /etc/rc.local

```

Add the following code *BEFORE* the last line which says 'exit 0'.
```

sudo loadkeys /etc/SwapCapsCtrl.kmap

```

reboot or from the console, run
```

sudo loadkeys /etc/SwapCapsCtrl.kmap

```

In the GUI, go to System > Preferences > Keyboard | Layouts tab 
click Layout Options
expand Ctrl key positions
select "Swap Ctrl and CapsLock"

---

### Post by MountainX on 2008-04-03
The prior solution was causing me no end of problems with tsclient and in other situations. 

I finally found a solution by reading the man for xmodmap. Here is the info:

I'm using Hardy beta.

Do **NOT** use gnome's keyboard control (Ubuntu System > Preferences > Keyboard > Layout Options). 
**_Instead_** follow the example in man xmodmap as explained below.

NOTE: before doing this, undo any changes in Keyboard layout options. Put the options back to defaults in gnome's keyboard control.

And, if you have done anything advanced to try to work around these issues, remove those modifications too. For example, the following is NOT needed so if you are using it, remove it (may require a restart):
 xmodmap -e "clear lock" -e "add lock = Caps_Lock"

Put the following in a text file.

            !
            ! Swap Caps_Lock and Control_L
            !
            remove Lock = Caps_Lock
            remove Control = Control_L
            keysym Control_L = Caps_Lock
            keysym Caps_Lock = Control_L
            add Lock = Caps_Lock
            add Control = Control_L

save the above as /etc/SwapCapsCtrl.kmap

then, from a terminal, run:
xmodmap /etc/SwapCapsCtrl.kmap


To make the change permanent, do this:
edit /etc/rc.local
add the following before the last line that says 'exit 0'
sudo xmodmap /etc/SwapCapsCtrl.kmap

Everything is now working exactly right for the first time.

---

