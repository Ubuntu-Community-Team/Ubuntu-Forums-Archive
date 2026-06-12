---
title: "mysql recovery?"
date: 2009-05-10
forum: Server Platforms
---

### Post by venalicio on 2009-05-10
I recently updated kernel on my server.  Everything was fine until I rebooted the server.  The machine hangs at the ubuntu splash (with the little bar filling across the bottom).  I dont keep anything valuable on the box so if I have to wipe it, no biggy.  I would however like to recover the mysql db I use for the website that I host on the box.  Is this possible from a live environment? 

Any help would be greatly appreciated.

Thanks in advance

---

### Post by ikonia on 2009-05-10
first thing is remove the ubuntu splash screen to you get more info on where it's hanging on the boot.

second comment, try hitting the capslock key on your keyboard see if the keyboard light comes on off, normally gives you an idea (just an idea not fact) if the whole machine is hung

third comment, boot from the live cd - mount your disk, go to /var/lib/mysql (or the mysql data dir you setup) and copy of off all the files, they can be used on a clean machine to re-import your old databases.

---

### Post by ejschaefer on 2009-05-10
Hi, 

Did you happen to leave the old/working Kernel's entries in your boot loaders configuration? If so, are you able to properly boot your old kernel? Assuming you're using Grub, just hit ESC when the "GRUB loading, please wait..." prompt appears. You should have several listings of previous kernel versions.

Hopefully this works out for you.

---

