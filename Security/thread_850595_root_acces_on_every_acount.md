---
title: "root acces on every acount?"
date: 2008-07-05
forum: Security
---

### Post by djnapster on 2008-07-05
Hi,

how can i get root rights on every acount of my ubuntu installation? when i try to copy fonts to my fonts map, it says that i have not the necesery rights to copy any file to there.

can i permanently fix this?

im the only user on my computer, and i am a home user so i don't think the safety of my computer is getting in danger by setting root rights to every acount.

I don't want to use the terminal for just copying one stupid single file to my filesystem.

I hope i get a quick response,
Thx

& sory for my bad english:)

---

### Post by sisco311 on 2008-07-05
quick response:
Alt+F2:
```
gksu nautilus
```to open the file browser as root.

---

### Post by djnapster on 2008-07-05
> **sisco311 said:**
> quick response:
Alt+F2:
```
gksu nautilus
```to open the file browser as root.

thx, but is it possible to set it up just like windows.
windows xp: every user with 'admin' rights could edit everything

i want it just the same on my linux system, so i don't get disturbed by annoying autorizations. And that i can edit every text file of my filesystem and i can copy, edit or cut every file i want from the filesystem.

thx for the fast reply =)

bye

---

### Post by war59312 on 2008-07-06
Just login as root then?

---

### Post by The Cog on 2008-07-06
I don't think it is possible to give all rights to all users. I think if you tried, not only would your system be horribly insecure, it would probably stop working and you would have to reinstall to fix it.

You could of course enable root login and just have everyone log in as root, but even this is discouraged.

I advise that you live with the security arrangemens as they are. You ony need to give the password when uou are doing system admin work, not when working as a user on your own files in your home folder. And the amount of admin work gets less and less as you get the system bedded down how you like it.

---

### Post by bobbob1016 on 2008-07-06
gksu nautilus gives you an admin nautilus window, allowing you to do whatever you want.  I think this is the best way.  If you give yourself admin rights, you lose the advantages of Linux's security.  You can right click a panel, and add a custom application, and add "gksu nautilus" without the quotes.  This way, you just click it, and have an admin nautilus window.

---

### Post by aysiu on 2008-07-06
What you're asking for, you won't get on these forums.

Read more [here](http://ubuntuforums.org/showthread.php?t=765414).

---

