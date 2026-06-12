---
title: "Windows 7 host, virtualbox 9.10 guest.  Additions problems..."
date: 2009-11-07
forum: Virtualisation
---

### Post by Slash621 on 2009-11-07
Hey fellas, how do I get the virtualbox additions to install correctly?  I clock on the vboxlinuxadditions-x86.run and the terminal comes up, but nothing really seems to happen.  It dissapears before I can read whats in the terminal.

Did it or did it not work?  If it didnt? whats the best way to get it to install?

---

### Post by Merk42 on 2009-11-07
Consult page 65 of the [Virtualbox manual](http://download.virtualbox.org/virtualbox/3.0.10/UserManual.pdf):
Open a terminal and go to the CD image then run ```
sudo sh ./VBoxLinuxAdditions-x86.run
```

---

### Post by Slash621 on 2009-11-09
Thanks very much for your help.  I'll give it a try this evening.  Im assuming I'll have to write the full address ahead of the "./" you left in front of the file name.

---

