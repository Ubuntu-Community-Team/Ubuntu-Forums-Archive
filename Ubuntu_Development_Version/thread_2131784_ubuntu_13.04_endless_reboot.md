---
title: "ubuntu 13.04 endless reboot"
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by Redalien0304 on 2013-04-02
Dell optiplex gx520 that i have the live DVD boots normally,black blank screen blinking cursor, then Reboots endlessly or just hangs finally. 
I know Dvd is good tried it another system which Raring installed just fine. also burned at slower speed. Linux Mint 13 is installed just fine on this system.

Dell Optiplex gx520 2gb Ram Nividia 6200 512mb PCI graphics card

---

### Post by ManamiVixen on 2013-04-02
The Nvidia is to blame. There are issues with some cards on the 3.8 kernel where the nouveau driver fails to load.

---

### Post by Redalien0304 on 2013-04-02
ok is there a solution workaround? for nvidia Cards?

---

### Post by ManamiVixen on 2013-04-02
Usually, it solely falls on the card. Most of the older cards mess up alot, while the newer cards like the GT210 and newer tend to work well enough to install the proprietary driver. I'm on an Nvidia Quadro 600 (GT430 based) and it runs the nouveau driver just fine. You can try the nomodeset option on live boot. Just look up the tutorial to do so, it' rather easy.

---

### Post by deadflowr on 2013-04-02
> **alien0304 said:**
> Dell optiplex gx520 that i have the live DVD boots normally,black blank screen blinking cursor, then Reboots endlessly or just hangs finally. 
I know Dvd is good tried it another system which Raring installed just fine. also burned at slower speed. Linux Mint 13 is installed just fine on this system.

Dell Optiplex gx520 2gb Ram Nividia 6200 512mb PCI graphics card

From what I gather, you're trying to boot a live session and it hangs or boots into a blank screen?
Is that right?
Have you tried setting the nomodeset option? Sometimes that helps.
When you get to the boot screen with the 'try ubuntu,install ubuntu, etc,etc, look at the bottom and you should see F-key listing, I think you can press the F6 key (I think) to open the options and then up/down arrow to the nomodeset option, press spacebar to set and then esc key to exit the option panel, then try booting into the live session.

---

### Post by Redalien0304 on 2013-04-02
decided not to Install Ubuntu 13.04 on this desktop for now. Already Installed 13.04 on my other desktop.

---

