---
title: "Shift, control key and other keys problem with VmWare running"
date: 2008-06-28
forum: Virtualisation
---

### Post by Barmaleychik on 2008-06-28
If I start VmWare usually but not always immediately I am getting problems with shift and control keys - they simply don't work. In addition if I work with mouse Firefox works fine, but if I press any key it crashes. Turning off VmWare does not help, but after rebooting everything is working again.

I got this message in another forums:

> **Zardus said:**
> ... the thing with VMWare killing control and shift and such is a known issue. Running:

```
# setxkbmap
```

fixes it temporarily (I think at least until you restart vmware). It's still a pain in the ***, though.

In my case it does not work unless I used the command wrong: at the prompt I copied and pasted:   # setxkbmap    and pressed enter.

Any ideas?

---

### Post by fjgaude on 2008-06-28
A few folks seemed to have an issue like you describe, most don't though. What kind of computer are you using... just trying to tie the problem to some hardware or BIOS.

---

### Post by Barmaleychik on 2008-06-28
I built my system around ASUS A8N VN CSM motherboard with 2 GIG of RAM, which has built in video and sound. I use seagate SATA 500gig harddrive and which I do not think affect my VmWare :)

---

### Post by fjgaude on 2008-06-28
Well, it's the "built-in" that's likely something the Ubuntu, Linux developers haven't fully taken into account... there is likely a workaround but I don't know what it might be.

Good luck with finding a solution.

---

### Post by jonofan on 2008-07-15
did you have any luck finding a solution barmaley?

i'm having the exact same issue. my graphics are however not inbuilt. running an hp dv2000 notebook with an nvidia go7200.

---

### Post by robgolding63 on 2008-07-15
I have the same issue. I'm running Ubuntu 8.04 on a Dell Dimension, with a PCI-E nVidia graphics card. The only way I can resolve it is to logout of gnome (cannot use Ctrl+Alt+Backspace for obvious reasons), then restart X with the aforementioned key combination.

Strange, and annoying really.

Rob

---

### Post by biggreen03 on 2008-07-16
Hey all, 
  In most posts where people type a command they will use the # sign as an indication of a command prompt.  Not sure if I'm stating the obvious, but I think its worth pointing out that # is not part of the command.  When Barmaleychik said: "at the prompt I copied and pasted: # setxkbmap and pressed enter."  It made me think s/he included the #.  Use the command setxkbmap but don't paste the #.  I solved the same issue using this command.

---

### Post by dvaey on 2008-07-29
I found this solution on another forum.  Simply create a script called "/fix" with the following content.  When your control keys stop working (often after switching out of vmware), you can either run /fix from an xterm or from the run dialog.  Dont forget to run [FONT="Fixedsys"]chmod u+x /fix[/FONT] to allow you to use the script.

This isnt a fix for the problem, but it is a bandaid solution to allow you to continue using your X session after vmware mucks up your keys.

As a side note, Ive found the 'alt' key is untouched, but if you want to switch to a text terminal, you must first click in the vmware window to give vmware full keyboard control, then use Ctl-Alt-FN to jump to text terminal, as the Ctl key wont be recognized unless vmware has keyboard focus.

--- /fix script below ---
[FONT="Fixedsys"]
#!/bin/sh
/usr/bin/xmodmap - << XXX
clear shift
add shift = Shift_L Shift_R
clear lock
add lock = Caps_Lock
clear control
add control = Control_L Control_R
clear mod1
add mod1 = Alt_L Alt_R
clear mod2
add mod2 = Num_Lock
clear mod3
clear mod4
add mod4 = Super_L Super_R
clear mod5
add mod5 = Scroll_Lock
XXX
[/FONT]
--- end of /fix script ---

---

### Post by insulae on 2008-09-19
> **dvaey said:**
> I found this solution on another forum.  Simply create a script called "/fix" with the following content.  When your control keys stop working (often after switching out of vmware), you can either run /fix from an xterm or from the run dialog.  Dont forget to run [FONT="Fixedsys"]chmod u+x /fix[/FONT] to allow you to use the script.

This isnt a fix for the problem, but it is a bandaid solution to allow you to continue using your X session after vmware mucks up your keys.

As a side note, Ive found the 'alt' key is untouched, but if you want to switch to a text terminal, you must first click in the vmware window to give vmware full keyboard control, then use Ctl-Alt-FN to jump to text terminal, as the Ctl key wont be recognized unless vmware has keyboard focus.

--- /fix script below ---
[FONT="Fixedsys"]
#!/bin/sh
/usr/bin/xmodmap - << XXX
clear shift
add shift = Shift_L Shift_R
clear lock
add lock = Caps_Lock
clear control
add control = Control_L Control_R
clear mod1
add mod1 = Alt_L Alt_R
clear mod2
add mod2 = Num_Lock
clear mod3
clear mod4
add mod4 = Super_L Super_R
clear mod5
add mod5 = Scroll_Lock
XXX
[/FONT]
--- end of /fix script ---

great script!! you save my life :D :D, i hate this vmware problem.

---

### Post by trmentry on 2008-09-19
there is a bug filed on this.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982)

---

### Post by adibadi on 2008-09-20
I don't know if this is the same problem, but if my vmware window is not active, and do any ctrl-drag actions in that window (for example, making a box around some icons on the desktop), the ctrl, alt, shift keys stop working outside of vmware.

Another side-effect is that if I open any gnome-terminal windows after that, pressing ANY key in it will close the terminal.  I can only type in existing terminals.

An easy fix was to add a new application launcher in my top bar, running /usr/bin/setxkbmap

Creating the application launcher didn't work while the problem was active.  It also closed the window, just like the terminal.  I had to copy/paste setxkbmap from this web page into a new terminal with the middle mouse button, then paste a new-line from somewhere to execute it :)

nice to be able to reproduce the problem and fix it with a single click of this button now!

---

### Post by sites on 2008-10-03
FINALLY!  I have this problem, & the "setxkbmap" command fixes it.

Thanks =)

---

### Post by toineurlings on 2009-12-28
> **dvaey said:**
> I found this solution on another forum.  Simply create a script called "/fix" with the following content.  When your control keys stop working (often after switching out of vmware), you can either run /fix from an xterm or from the run dialog.  Dont forget to run [FONT="Fixedsys"]chmod u+x /fix[/FONT] to allow you to use the script.

This isnt a fix for the problem, but it is a bandaid solution to allow you to continue using your X session after vmware mucks up your keys.

As a side note, Ive found the 'alt' key is untouched, but if you want to switch to a text terminal, you must first click in the vmware window to give vmware full keyboard control, then use Ctl-Alt-FN to jump to text terminal, as the Ctl key wont be recognized unless vmware has keyboard focus.

--- /fix script below ---
[FONT="Fixedsys"]
#!/bin/sh
/usr/bin/xmodmap - << XXX
clear shift
add shift = Shift_L Shift_R
clear lock
add lock = Caps_Lock
clear control
add control = Control_L Control_R
clear mod1
add mod1 = Alt_L Alt_R
clear mod2
add mod2 = Num_Lock
clear mod3
clear mod4
add mod4 = Super_L Super_R
clear mod5
add mod5 = Scroll_Lock
XXX
[/FONT]
--- end of /fix script ---

Used it, but it's not fixed and the "setxkbmap" also fails

---

### Post by toineurlings on 2009-12-28
SOLVED IT! It added a new keyboard with the same options and set it as default for the whole system, it worked.

So it has to do something with the option for the keyboard which is used ad installed. It didn't just worked with plugging in another keyboard at the same time. But.....
SHITTTTTTTTTTT start VWware and it showed up again, tried it again without VMware and it just works for a very short term (my arrow keys work again)

HUH... sometimes it works for 10 seconds and then it fails again

edit: It's getting stranger and stranger... I can zoom using ctrl+scroll

---

### Post by toineurlings on 2009-12-28
Deleted VMware and want to keep it away, but not solved yet

---

### Post by toineurlings on 2009-12-29
here they talk about the problem but i -sorry, shift doesn't work- don't see a solution in this story
[http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html](http://www.vmware.com/support/ws55/doc/ws_devices_keymap_linux_longer.html)

---

### Post by radiobuzzer on 2011-03-30
Problem appeared again in 10.04. I am following the bug ticket, to see if there is going to be a solution

---

