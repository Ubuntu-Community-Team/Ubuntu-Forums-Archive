---
title: "How to free dialog windows"
date: 2017-10-14
forum: Ubuntu Development Version
---

### Post by ubname on 2017-10-14
I notice that dialog windows are stuck to main window, how to free
the dialog from the main window?

thanks.

---

### Post by dino99 on 2017-10-14
Have you an example of what you named "dialog windows" ?
Usually a 'dialog' window is an app output that is informative or requesting an answer from the user. Why should you want to clear it ?

---

### Post by ubname on 2017-10-14
> **dino99 said:**
> Have you an example of what you named "dialog windows" ?
Usually a 'dialog' window is an app output that is informative or requesting an answer from the user. Why should you want to clear it ?

Open File, in File open Preferences, try to move the Preferences window, also File moves with the window they are "stuck together"

---

### Post by corradoventu on 2017-10-14
gsettings set org.gnome.mutter attach-modal-dialogs false

---

### Post by kurros on 2017-10-14
It is also an option in Gnome Tweak Tool under Windows (Attach Modal Dialogs)

---

### Post by ubname on 2017-10-15
Thanks Corrado and Kurros,
is it safe to use tweak tools?

is "gsettings" a standard ubuntu tool for such activity

wonder how it can not be possible to change that behaviour that make
impossible to use some application in ubuntu 17.10

is this supposed to be a feature?

Should i report this as a bug or is there a plan to add
this feature with updates?

thanks

---

### Post by corradoventu on 2017-10-15
gsettings is a standard terminal command, enter the command from terminal for a small help or man gsettings for a complete manual or look at: [https://developer.gnome.org/GSettings/](https://developer.gnome.org/GSettings/)
gsettings allows to configure every aspect of your gnome system.
you may find tweak tool (gnome tweaks) in Ubuntu software. Tweak tool is mostly a graphical interface for gsettings,
Some time ago I opened a bug because in tweak tool attach modal dialogs OFF had no effect and the bug is now closed: [https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1717530](https://bugs.launchpad.net/ubuntu/+source/gnome-tweak-tool/+bug/1717530)
if You read the bug You will understand the relationship between tweak tool and gsettings.
Please open a bug, I will subscribe immediately.
I think the option to separate windows should be added in Ubuntu settings = gnome control center.

---

### Post by mc4man on 2017-10-15
> **ubname said:**
> 

wonder how it can not be possible to change that behaviour that make
impossible to use some application in ubuntu 17.10

is this supposed to be a feature?


It's a feature in wayland session to eliminate a minuscule risk (for most users) so no, it won't be changed. Some current non working apps may be adjusted to work, some will never be.
You can either log into an xorg session or run this command in a wayland session (it's a per session command
```
xhost +si:localuser:root 
```
That would allow *some* non working apps to now work

---

### Post by ubname on 2017-10-15
thanks mc4man,

do you mean this will never change for future ubuntu releases?
I use specific applications with many data tables and not being able
to move them is not feasible, i will have to look for other solutions

what about the proposed solution from Corrado gsettings set org.gnome.mutter attach-modal-dialogs false
will this put the pc at risk?

if you can point me where i can find more about this problem please

thanks.

---

### Post by corradoventu on 2017-10-15
command: xhost +si:localuser:root --- allows running some applications needing authorizations like gparted and synaptic
command: gsettings set org.gnome.mutter attach-modal-dialogs false --- separates the 'child' window from the main window

---

### Post by ubname on 2017-10-16
> **corradoventu said:**
> command: xhost +si:localuser:root --- allows running some applications needing authorizations like gparted and synaptic
command: gsettings set org.gnome.mutter attach-modal-dialogs false --- separates the 'child' window from the main window

Ok thanks now it's clear, i was not talking about synaptic or gparted indeed

---

