---
title: "panp5/star1 resume differences[0]: resume on lid open"
date: 2009-12-28
forum: System76 Support
---

### Post by tlroche on 2009-12-28
Dunno how unique this is, but I'm a linux-desktop newbie in a 2xSystem76 household: I've started intensively using a PanP5 (running vanilla jaunty), and my GF just got a Starling (running UNR jaunty), which I've been setting up. I'm noticing some differences in standby/resume behavior between the boxes, which I'd like to harmonize:

If I put the panp5 to sleep, then close its lid, then open its lid, it resumes. This can be problematic: when traveling last week, I pulled the panp5, nearly drained, out of a toasty-warm bag. I had put it in while asleep, but it had awoken, perhaps due to jostling.

If I put the star1 to sleep, then close its lid, then open its lid, nothing happens. If I want to resume it, I must press its power button.

How to make the panp5 behave like the star1, and not autoresume on lid open? FWIW

[LIST=1]
[*]both the panp5 and star1 are running Power Manager 2.24.2.
[*]I set them up to have the same preferences. 
[*]I see preferences for lid-closing behavior, but not lid-opening behavior.
[/LIST]

---

### Post by thomasaaron on 2009-12-28
I'm traveling right now and don't have access to a Starling or a Pangolin for testing.

But the Starling is hard-wired to wake when you press the power button, the Pangolin is not. 

I don't know of a way to harmonize the two. I've looked through gconf-editor, and I don't see anything pertaining to lid-opening activity.

---

### Post by tlroche on 2009-12-28
OK, I'll try my luck on [General Help]("http://ubuntuforums.org/showthread.php?t=1366818").

---

### Post by PatrickVogeli on 2009-12-31
Have you tried, in gnome-power-manager, setting the action when closing the lid to nothing??

That way, it won't suspend when closing the lid, but maybe it doesn't wake up when opening it.

---

### Post by tlroche on 2010-01-02
> **PatrickVogeli said:**
> Have you tried, in gnome-power-manager, setting the action when closing the lid to nothing??

That was already set, in both the AC and battery tabs.

---

### Post by PatrickVogeli on 2010-01-02
there's a file called /etc/acpi/events/lidbtn that has the following:
```
 
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh

```

Maybe commenting the last 2 lines will make the trick. Just put a # in front of both, reboot and try again.

---

### Post by tlroche on 2010-01-02
> **PatrickVogeli said:**
> Maybe commenting the last 2 lines [of /etc/acpi/events/lidbtn] will [do] the trick.

I did

```
tlroche@tlrPanP5:/tmp$ ls -al /etc/acpi/events/lidbtn
-rw-r--r-- 1 root root 118 2009-03-27 05:09 /etc/acpi/events/lidbtn
tlroche@tlrPanP5:/tmp$ date ; cat /etc/acpi/events/lidbtn
Sat Jan  2 20:07:45 EST 2010
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
tlroche@tlrPanP5:/tmp$ sudo cp /etc/acpi/events/lidbtn /etc/acpi/events/lidbtn.0
tlroche@tlrPanP5:/tmp$ sudo emacs -nw /etc/acpi/events/lidbtn
tlroche@tlrPanP5:/tmp$ date ; cat /etc/acpi/events/lidbtn
Sat Jan  2 20:08:36 EST 2010
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

# event=button[ /]lid
# action=/etc/acpi/lid.sh

```

and restarted, then did Fn-F4 to suspend and waited for the box to sleep, then closed the lid and waited 10 sec. But when I opened the lid, the session resumed.

---

### Post by thomasaaron on 2010-01-04
I don't think there is a canned way to assign actions on "lid open" in Ubuntu. However, it *is* possible on *most* systems to read the lid state (i.e. open or closed). For an example of doing this, have a look at this file...

/etc/acpi/lid.sh

It may be possible to detect the lid opening and bypass the "wake from suspend" functionality, but then I'm not really sure *how* you will get the machine to wake from suspend.

I'm sure it can all be done, but it is going to take custom scripting and a good deal of research.

---

### Post by miniyak on 2010-01-12
Its not unheard of for my panp5 to fail to suspend and stay on. This is easy to miss so i can relate with the whole "why is my bag so warm?" ordeal

why this happens i dunno, but mine has never woke up while the lid was closed

---

