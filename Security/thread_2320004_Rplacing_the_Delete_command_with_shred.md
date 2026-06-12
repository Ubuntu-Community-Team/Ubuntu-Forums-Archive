---
title: "Rplacing the Delete command with shred"
date: 2016-04-09
forum: Security
---

### Post by solouko on 2016-04-09
Hi, I've been getting crazy paranoid with security lately and one thing I've been wondering is, is there a way to replace the delete command(s) in Ubuntu with either the shred command or the secure-delete commands?    What I'm aiming for is to click a file on my computer that shouldn't be there, press the delete button and for Ubuntu to ask me if i want to delete this file, i click yes and then it does a secure delete of some sort.   I'm sick and tired of going through long and lengthy processes when decommissioning hard drives so that nothing can be recovered form them so  if i can set this up on all new installs it will save me a lot of time in the future and give me peace of mind that the things really are gone.  It might be overkill considering I've started encrypting the disks but I've already had an 11 character password hacked which has made me super paranoid.

---

### Post by HermanAB on 2016-04-09
It is OK to be a little paranoid, but then you should use technology that works, not holy water...

Shred doesn't work.  Encrypt your disks with LUKS.  Use loooooooong (minimum 12 characters) and unique passwords for everything and use keypassX to save your passwords so you only need to remember one or two.

My passwords are generally 12 characters and my root passwords are 25 characters.  That seems to be OK.

---

### Post by bashiergui on 2016-04-09
I believe the gui uses "rm" to delete files from the trash, which isn't a secure deletion method. (I'm sure someone will correct me if I'm wrong)

It would be easy to use "dd" instead of "rm" in the terminal. dd allows you to overwrite the data randomly or with 0s or 1s. There are tons of tutorials on how to use dd. Just make sure you understand precisely what the command will do before you use it. It will delete the entire disk if you tell it to.

---

### Post by deadflowr on 2016-04-09
You could install the package [nautilus-wipe]("http://packages.ubuntu.com/trusty/utils/nautilus-wipe")
 then run
```
nautilus -q (or --quit)
```
open Files (nautilus)
right click on a file and a new entry will show for wipe (and also an entry for wipe available space)
click on wipe and it'll ask if you are sure you?
there is also an option dropdown to change the settings (a little)

I think this is something you would want.

It's basically using dd function, as mentioned about above.

And it should go without saying, but I'm saying it anyway, this only works on Ubuntu or a system that uses nautilus as the file manager.

As for adding that to a keyboard shortcut, like for the delete button.
I'm not sure how to do that.

---

