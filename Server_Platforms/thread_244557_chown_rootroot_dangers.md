---
title: "chown root:root dangers?"
date: 2006-08-26
forum: Server Platforms
---

### Post by redchair on 2006-08-26
Usually, if I download important files, I immediately use the command:

sudo chown root:root *

in the directory of the downloaded files to prevent changing by other programs. Things where this seems necessary is in the ~/.mozilla/plugins folder where I change the owner from a normal user account to root on the flash plugins after using the installer from Adobe.

Does this present a danger to the system, do executables that are owned by root automatically run with root privileges?

---

### Post by LKRaider on 2006-08-26
Why change ownership to root? 
There is no need to do that :\
What are you trying to accomplish with this?

---

### Post by Klaidas on 2006-08-26
as long as "others" can't execute it, you're fine.

More info [http://www.linux.org/lessons/beginner/l14/lesson14a.html](http://www.linux.org/lessons/beginner/l14/lesson14a.html)

---

### Post by Randomskk on 2006-08-26
Ownership is only changed to root if the SetUID bit is set.
By default, it's not, so any executable owned by root but without SetUID won't run as root.

"man chmod" for more info on SetUID and such.

---

### Post by redchair on 2006-09-02
Thanks for your helpful replies, especially about SetUID. I will have to read that built-in man page carefully. (I am changing ownership to root so that a normal person who sits down to my computer will not be able to change these files.)

---

### Post by LKRaider on 2006-09-02
The best way IMO would be to lock your screen when you leave, and if you want to share the pc with more people, create another user for them (even a general "guest" user would do fine - just don't add security-critical privileges to it then).

---

### Post by aysiu on 2006-09-02
If a file or directory is owned by root but has 777 privileges, it can be modified by anyone.

Ownership here isn't the issue--it's privileges.

I agree with LKRaider--set up a guest account for other users if you're that worried. There are various kiosk tools you can use, too, to restrict what the guest user can do. For KDE there's *kiosktool*. I believe there's something for Gnome as well that starts with an *s*--forget the actual name.

---

