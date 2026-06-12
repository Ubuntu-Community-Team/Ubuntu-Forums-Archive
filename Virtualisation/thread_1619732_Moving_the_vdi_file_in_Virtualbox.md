---
title: "Moving the vdi file in Virtualbox"
date: 2010-11-12
forum: Virtualisation
---

### Post by rmcellig on 2010-11-12
I would like to move my WindowsXP.vdi to another machine. Is this possible with Virtualbox? If so, how would I access the file through Virtualbox?

---

### Post by ajgreeny on 2010-11-12
Just put the vdi file into the same folder in the new machine and VB should find it.

However, being windows, I have no idea whether or not the windows authentication palaver will detect that it is a different machine and stop it working.  I am not sure about windows license requirements any more as I have no windows to use.

---

### Post by rmcellig on 2010-11-12
Thanks ajgreeny! Right now I have the vdi file on an external USB drive. I would like to put the vdi file on a laptop, you mention that:

Just put the vdi file into the same folder in the new machine and VB should find it.

What folder would that be?

---

### Post by ajgreeny on 2010-11-12
I can't remember; it's too long since I used VB, but it is in a hidden virtual box folder somewhere in your home folder, if I remember correctly.

---

### Post by rmcellig on 2010-11-12
Thanks. I know what you mean now.

---

### Post by SeijiSensei on 2010-11-12
All your VirtualBox configuration files and virtual machines are in /home/user/.VirtualBox.  If you're moving your installation from one Linux machine to another, I'd recommend moving the entire .VirtualBox directory.

---

