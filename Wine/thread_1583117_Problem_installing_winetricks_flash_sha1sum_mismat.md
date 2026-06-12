---
title: "Problem installing winetricks flash: sha1sum mismatch!"
date: 2010-09-27
forum: Wine
---

### Post by bitteralmond on 2010-09-27
I get this error on the terminal:
```
sha1sum mismatch!  Rename /home/bitteralmond/.cache/winetricks/./install_flash_player_ax.exe and try again.
```I remove the file, of course, and use 'ls' to make sure it's gone, but when I run the installation again, the same thing happens. I tried many times.

I need to install flash for IE. How can I do this?

---

### Post by wBinary on 2011-02-12
hi,you can do like this:

> 
cd /home/bitteralmond/.cache/winetricks/
wine install_flash_player_ax.exe


---

### Post by ikeluiz on 2011-03-24
try it

chmod 777 -R ~/.cache/winetricks

=)

---

