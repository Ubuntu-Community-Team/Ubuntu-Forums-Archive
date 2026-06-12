---
title: "Uninstall LimeWire?"
date: 2005-05-15
forum: Repositories &amp; Backports
---

### Post by picpak on 2005-05-15
Is there a way to uninstall LimeWire using apt-get, or another way? I installed it with the instructions off [Ubuntu Guide](http://ubuntuguide.org/#limewire). I know it's built off Java, so it's been confusing for me to remove.

---

### Post by harryc on 2005-05-15
No way using apt-get. Just delete the following;

/opt/LimeWire/

/usr/bin/runLime.sh

/usr/share/applications/LimeWire.desktop

---

### Post by picpak on 2005-05-15
That's what I thought, but I wasn't sure it would delete everything. It will though?

(I'm too used to Windows programs only uninstalling half of the files and leaving the rest there :razz: )

---

### Post by Xian on 2005-05-15
[QUOTE=picpak]That's what I thought, but I wasn't sure it would delete everything. It will though?[/QUOTE]
Yeah, as you can see by the How-To you followed, the uninstall method illustrated to you simply removes what was created, which was a single directory, desktop and executable file. Once those states are reverted then you are back where you started.

---

### Post by jorgealfonso on 2007-05-05
With the version I installed, it seems to work fine the good old "sudo apt-get remove limewire-basic" (I was starting to panic about not finding the files you listed!!)

---

### Post by hikaricore on 2007-05-07
jorgeal: The post you replied to was from two years ago.  Alot of things have changed since then such as debian/ubuntu packages of software such as limewire being availible.

---

### Post by Kyle12349 on 2007-11-24
Is there any way of uninstalling Limewire without removing any of the files I downloaded on there?

---

### Post by tonys_ub on 2007-12-11
I typed this in the termenal, "sudo apt-get remove limewire-basic". Now my update manager, synaptic manager, and package install will not work until I resolve this problem. Dose anyone have any way to fix this mess?

---

