---
title: "Installed Ubuntu 18.04 in VirtualBox on Dell Inspiron 15 (4K UHD): small font/icons"
date: 2019-11-03
forum: Virtualisation
---

### Post by brucemohler on 2019-11-03
I just upgraded my laptop to a Dell Inspiron 15 which has a 4K UHD screen.  I've always used Ubuntu LTS to do the bulk of my work as a system administrator/DevOps engineer from and when I installed Ubuntu on this laptop, the fonts and icons are so small (and the position of the mouse pointer so far from where it needs to click) that its almost unusable.

Google searches pointed me at unity-tweak-tool and gnome-tweaks and they address just the fonts but not the mouse or icons.

Is there a single solution that makes Ubuntu useful on this laptop screen?

Thank you, in advance.

---

### Post by CatKiller on 2019-11-03
If you're running it in a VM, you tell the VM what resolution you want it to be, and the VM tells the guest OS what the resolution is.

KDE and Cinnamon can both scale the interface up with a couple of clicks, but I don't use Gnome.

---

### Post by SeijiSensei on 2019-11-04
First, if this is running inside a VirtualBox VM, you need to install the Extension Pack which should give you a wider range of resolutions.  You should also be able to select a comfortable display resolution using the Display option in System Settings.  On my desktop I run at 1440x900 rather than the default 1920x1080.

---

### Post by brucemohler on 2019-11-05
CatKiller, I've used VirtualBox for years but never the Scaling Factor option in Settings -> Display.  Worked like a charm and I didn't have to tweak anything inside of Ubuntu.  Worked like a charm.  Thank you.

---

### Post by wildmanne39 on 2019-11-05
*Thread moved to **Virtualisation a more appropriate sub-forum**.*

---

