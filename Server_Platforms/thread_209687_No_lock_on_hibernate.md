---
title: "No lock on hibernate?"
date: 2006-07-05
forum: Server Platforms
---

### Post by sigmason on 2006-07-05
I have Ubuntu, Kubuntu, Xubuntu all installed on a Dell Latitude C800 with 512MB of RAM.  They are installed with the same kernel and hence share the
partitions on the disk.

I am currently running kernel: 2.6.15-25-686 (default)
I also have installed: 2.6.15-25-386
I also have installed: 2.6.15-23-386
I also have Windows 2k Pro on dual boot via grub.

I've got my wireless card (Linksys WPC54G v3) working.
My internal network (via the modem/ethernet 3Com MiniPCI) working.

All is well, I also now have the laptop hibernate on lid closing.

However >>>>>

Many times when I close the lid (read not always) I don't get a lock screen on resume.  It literally dumps me back to the desktop (be it X, KDE, or Gnome) without any security lock out at all?

Now I am using this laptop strictly to develop simple code, I own plenty of other computers that I use for everything else.  So I'm not really scared that I may close the lid and someone might start using my laptop when they turn it on...without ever needing to enter a password or identify themselves, but this seems like a REALLY big security issue.

Any suggestions on what might cause the laptop to NOT lock when doing a hibernate as a result of the lidbtn event in ACPI?  I don't see this behavior (ever) if I do hibernate from the Shutdown menus of any of the GUIs (X, KDE, or Gnome.)

Sigmason

---

### Post by 5-HT on 2006-07-09
Not sure if this will help as you mentioned that it's an intermittent issue and you do get screen locking on resume by using the menu option to hibernate, but is screen locking on resume enabled in /etc/default/acpi-support?

---

### Post by sigmason on 2006-07-10
> **5-HT said:**
> Not sure if this will help as you mentioned that it's an intermittent issue and you do get screen locking on resume by using the menu option to hibernate, but is screen locking on resume enabled in /etc/default/acpi-support?

Sadly, yes it is enabled.

It's weird, it happens every so often, it recovers fine, it just doesn't lock...I was thinking maybe the system BIOS was preempting the hibernate with a suspend or something along those lines.  However, I've turned all of those settings in every way I can and it doesn't see to eliminate the problem.

The screen saver works fine too, so my problem is clearly with the hibernate (and maybe suspend.)

---

### Post by jshayden on 2006-09-13
I'm having the same problem..

^bump

---

