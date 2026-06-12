---
title: "Backing up .bashrc and .bash_history"
date: 2013-03-10
forum: Ubuntu One (CLOSED)
---

### Post by k4rizma on 2013-03-10
Is there an easy way to set Ubuntu One to automatically backup my .bashrc and .bash_history?  I could setup a cron job to cat out .bashrc to a plain text file in my documents folder.  That would mean I have to setup the cron job for each new computer I'm using ubuntu on.   I'm always changing machines or bringing up a fresh install for one reason or another.   I would love to simplify this. 

Thanks for any help!

---

### Post by k4rizma on 2013-03-10
I'm also open to using something else than UbuntuOne but would prefer not to. 

Thanks!

---

### Post by Isamu715 on 2013-03-23
Ubuntu One doesn't support syncing files on individual basis. You can move your .bashrc and .bash_history to the Ubuntu one folder and create links in your home directory. Just right click on the files once they've been moved to the U1 folder and select "Make link", copy the links to your home directory and rename them to ".bashrc" and ".bash_history" accordingly.

---

