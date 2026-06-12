---
title: "How to use grub-reboot in KDE"
date: 2006-06-20
forum: Tutorials
---

### Post by Takis on 2006-06-20
Couldn't find this posted anywhere so I figure I'd better put it up - if only to remind myself next time I rebuild.

The command 'grub-reboot' lets you boot into a specific option listed in the grub boot menu. It's useful, but a little irritating if you have to use sudo powers each time you need to reboot into Windows, for example.

KDE has the option to list what to reboot into in the shutdown menu. If you open System Settings->Login Manager->Shutdown and set your Boot Manager to 'grub' in the dropdown menu, you'll find it'll appear next time you open the shutdown menu. You'll probably need to logout/log in for it to take effect, and you'll need to press and hold the restart button in order for the menu to appear, otherwise it assumes default restart.

---

### Post by rowanparker on 2006-07-16
Is there anyway to do this in Gnome?

---

### Post by Takis on 2006-07-17
I don't know - I'm a bit of a KDE fan myself. Anyone else?

---

### Post by Dsky on 2007-01-30
> **rowanparker said:**
> Is there anyway to do this in Gnome?

up

---

### Post by phormion on 2007-01-30
Wow, that's really useful! There used to be a 'rebootin' script shipped with older versions of Mandrake, but it was using some custom mdk additions as far as I remember (altconfigfile). I tried to run it on Ubuntu but it didn't work, this is all I need. I don't mind running the command with 'sudo', as long as it does the job. 

I guess a quick fix for Gnome would be to create some scripts to run with gksu, each rebooting into one option, and each named something like 'Reboot to Windows', 'Reboot to Ubuntu' etc. Shouldn't be hard to do.

---

### Post by rowanparker on 2007-01-31
> **Dsky said:**
> up
How then?

---

### Post by rlbond86 on 2007-12-02
This always makes KDE freeze for me. How do I fix that?

---

### Post by wensveen on 2013-01-08
> **rowanparker said:**
> Is there anyway to do this in Gnome?

To those stumbling upon this topic and wondering. Yes, there is a way. I've created a tiny shell script that you can use, but you also need to tweak some settings (on Debian at least). You can read [the details on my blog]("http://wensveen.wordpress.com/2012/11/17/reboot-to-windows-from-linux/") (sorry for the shameless plug). This works for Gnome-shell, but probably also Unity.

---

