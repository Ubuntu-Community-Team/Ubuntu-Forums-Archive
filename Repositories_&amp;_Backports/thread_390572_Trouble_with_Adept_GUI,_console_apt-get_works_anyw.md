---
title: "Trouble with Adept GUI, console apt-get works anyway"
date: 2007-03-22
forum: Repositories &amp; Backports
---

### Post by metalseb on 2007-03-22
Hi ubunteros

I'm facing some weird problem using the adept GUI under Kubuntu 32bits 6.10. I can install/upgrade packages using apt-get thru the console but as soon as I use the Adept GUI, things are going the bad way. I get the messages in the status bar : reading packages list, sorting, building the tree then reading information state and Adept just freezes at this moment. I can do nothing more and I have to kill -9 adept-manager. Same goes with adept-updater. Seems like that some files are locked but .... where ?

Doing some dpkg --configure -a or apt-get clean or even deleting lock file in /var/lib/dpkg does not help more. I even tried to uninstall/reinstall adept thru apt-get and the console but it did not help.

I'm really stuck with this since this morning, if anybody could help ?

Cheers mates !

---

### Post by milton1 on 2007-03-22
Adept seems to like malfunctioning randomly. Try installing synaptic. I have found it to be far more reliable.

---

