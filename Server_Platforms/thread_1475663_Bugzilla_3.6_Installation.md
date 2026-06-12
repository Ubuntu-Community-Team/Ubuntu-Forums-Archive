---
title: "Bugzilla 3.6 Installation"
date: 2010-05-07
forum: Server Platforms
---

### Post by satyanash on 2010-05-07
How to install Bugzilla 3.6 on Ubuntu Lucid 10.4 through the Advanced Packaging Tool(apt-get install) ???

---

### Post by just_another_user on 2010-05-07
I think you can't do it through APT. You can download source and compile it manually

---

### Post by motorcyclemarket on 2011-06-11
If you would like to install bugzilla 3.6 or 4.0 on Ubuntu 10.04 or later, have a look at the article I wrote.
 
[http://neil.motorcyclemarket.com/how-to-install-bugzilla-4-0-step-by-step-tutorial-that-works](http://neil.motorcyclemarket.com/how-to-install-bugzilla-4-0-step-by-step-tutorial-that-works)
 
Thank you and feel free to leave me comments.

---

### Post by motorcyclemarket on 2011-06-11
Sorry, there is a cleaner version of my post.
 
[How to install bugzilla 4](http://neil.motorcyclemarket.com/how-to-install-bugzilla-4-0-step-by-step-tutorial-that-works)

---

### Post by satyanash on 2011-06-12
Thanks for digging up this thread and the help. However I was able to set up bugzilla 3.6 apt-get, i don't really remember what caused the problem but I figure it was some dependency issue.
Also since this was a long time  ago I also had to migrate this database to another server, since the current hard disks had gone bad. So all I did was apt-get bugzilla3 to the new server, let it create it's own database(using dbconfig), then after everything had been installed I took a dump of the original bugzilla3 database and just restored it here. directly on top of the existing one(I also backed up).
Much to my surprise it worked, all the users and configuration had been imported from the previous server saving much labour.
I'll also be marking this thread as solved.

---

