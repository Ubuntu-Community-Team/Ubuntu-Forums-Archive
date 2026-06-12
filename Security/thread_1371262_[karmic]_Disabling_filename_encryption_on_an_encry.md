---
title: "[karmic] Disabling filename encryption on an encrypted home directory..."
date: 2010-01-03
forum: Security
---

### Post by Keyper7 on 2010-01-03
...does anyone know how to do that?

Not using filename encryption when you create a new encrypted folder is easy, but how to disable it in the home encryption that is automatically set up by the Karmic installation CD?

---

### Post by BkkBonanza on 2010-01-03
I had a look into this. The mount options are determined at runtime by the PAM module reading in the Private.sig file. This means they are encoded at install time by the ecryptfs-setup-private script. 

This means it would be difficult or impossible to change this option on the fly or after install. The only way that I can see would be to copy all data out as backup and then run,

ecryptfs-setup-private --undo

which will give you the instructions for removing the current encrypted home. 

And then follow the tutorial for creating a new encrypted home but choosing the option for non-encrypted filenames. This means follow the article below but add the "--no-fnek" option to the ecryptfs-setup-private command (which is not discussed in the tutorial because it's not the default).

[http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

This looks to me like the way to do this but **I have not tried this**. Make sure you backup everything in case it goes wrong.

---

