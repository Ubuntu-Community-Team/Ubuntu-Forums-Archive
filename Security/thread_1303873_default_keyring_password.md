---
title: "default keyring password"
date: 2009-10-28
forum: Security
---

### Post by abnrangerbill on 2009-10-28
a password to unlock the "default keyring" keeps poping up keeping me from going online with my wifi at home. my regular pw doesn't work. help!

---

### Post by mikewhatever on 2009-10-28
There is no default keyring password. By default, the system asks you to choose one, the first time it's needed. Anyway, you can clear the current password using this guide: [http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/).

---

### Post by mcduck on 2009-10-29
> **mikewhatever said:**
> There is no default keyring password. By default, the system asks you to choose one, the first time it's needed. Anyway, you can clear the current password using this guide: [http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/).

NOt a great way to clear the password, since it also removes all data stored in the keyring.

The correct way is to simply open Applications/Accessories/Passwords adn Encryption keys, seleect the login keyring and then "Change Password" from the right-click menu.

What comes to the original problem, have you at some point changed your login password? In that case the keyring password is same as your old login password was. Use the tool I mentioned above to set the password to same as you current login password is, and the keyring will again unlock automatically when you log in.

---

