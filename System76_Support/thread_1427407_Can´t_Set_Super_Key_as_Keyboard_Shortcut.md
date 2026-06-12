---
title: "Can´t Set Super Key as Keyboard Shortcut"
date: 2010-03-11
forum: System76 Support
---

### Post by jpoRS on 2010-03-11
Hey,

Panp4i, fresh install of Karmic 64, haven´t tried anything yet because I don´t know where to start.

Setting up a new user account on my computer, and trying to set the super key to summon a terminal.  No real reason, I have just always done it that way so I want to do it that way again.

Anyway, when I go into keyboard shortcuts, I can´t set the super key to do anything, let alone open a terminal.  When I set up the window to grab a shortcut, I press the Super key and nothing happens.  Even when I try something like Ctrl+Super, it won´t work.  On my other (original) account I can still summon a terminal using Super, but I am afraid to try and change it to something else for fear it will be irreversible.

Thanks for your help,
jim

---

### Post by jpv on 2010-03-11
Search these forums.  Specifically:
[http://ubuntuforums.org/showthread.php?t=1339486&highlight=Super-L](http://ubuntuforums.org/showthread.php?t=1339486&highlight=Super-L)

---

### Post by thomasaaron on 2010-03-12
Since the super key does work from your admin (first) account, but not the second, I'd log in to the admin acct and go to System > Admin > Users and Groups. Click the unlock button and enter your password. Then click the username of the second account, then click "Properties" and "Privs" and make sure "Administer the system" is checked. Then log back into the second account and see if anything has changed.

If that *works*, then it is an issue because you might not want the second user to have admin privs! 

Nevertheless, it will be interesting to see if that does the trick.

---

### Post by jpoRS on 2010-03-16
Thanks jpv, solution worked.

And TA- it was already set to admin.  So we won´t know if that works.

Thanks!
jim

---

