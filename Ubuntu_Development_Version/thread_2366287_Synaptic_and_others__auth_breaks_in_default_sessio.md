---
title: "Synaptic and others?  auth breaks in default session"
date: 2017-07-15
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-07-15
Fresh install of  couple day old iso, updated
The same as seen in the wayland session,  is now happening for the ubuntu session., i.e.

$ synaptic-pkexec
No protocol specified
Unable to init server: Could not connect: Connection refused

(synaptic:2067): Gtk-WARNING **: cannot open display: :0
Could be a bug (- If intended then disappointing,

---

### Post by P-I H on 2017-07-16
I installed the ISO from yesterday 15/7.
It's possible to get Synaptic to work. I made this
- Logged out
- Logged in with Wayland
- Logged out 
- Logged in with Ubuntu

There is also other problems with the ISO
I installed a swedish keybord, but the english keyboard was selected after boot.
When I first opened Files, it only contained  "Desktop" and "Examples". However after update all the expected folders showed up.

---

### Post by rrnbtter on 2017-07-16
Greetings,
It's an incompatibility between x11 apps and Wayland and evidently now gdm3 regarding security protocgols. It will get fixed if Canonical wants to default to Wayland come September. In the beginning I could use LuckyBackup with both Gnome x11 and Wayland but not LuckyBackup Super User. Then with the first gdm3 I could open LuckyBackup in gnome x11 but not in Wayland at all. Now with the newest gdm3 I can't open Lucky Backup with either. So they are working on the problem and I suppose the package maintainers are working on their part also.

Incidentally, I think rsync _root_ if failing also.  That is suppose to work without sudo since it is a server utility. The _xhost +si:localuser:root_  script isn't helping much of this.

sudo -H nautilus works, but pkexec and gksudo doesn't.

---

### Post by corradoventu on 2017-07-17
on my installation after updates BOTH sessions are in wayland, also the 'ubuntu' session. try:
corrado@corrado-HP-aGnome:~$ echo $XDG_SESSION_TYPE
wayland
corrado@corrado-HP-aGnome:~$

---

### Post by dino99 on 2017-07-17
opened report: Bug #1704748

---

### Post by mc4man on 2017-07-18
So what's happening here is even though ubuntu (default) is picked at greeter am being  logged into a ubuntu-wayland session so obviously things that should work don't...

---

