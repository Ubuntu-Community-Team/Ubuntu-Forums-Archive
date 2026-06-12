---
title: "Logout and Hibernate"
date: 2015-11-06
forum: Ubuntu Development Version
---

### Post by metinkale38 on 2015-11-06
Hey,

thinking about Windows Fastboot i came to the idea to try the same for Ubuntu.
My Idea was to Hibernate after Login Out the User.

How to to that? Can i somewhere put a script, which is called after Log-Out, from where i can prevent shutdown and hibernate instead?

I tried to write a script with gnome-session-logout ... && pm-hibernate, but it will hibernate before logging out, because gnome-se.. works asynchron, and i dont know, whether the script could continue when logged out.


Any idea about that? How to do it?

---

### Post by cariboo on 2015-11-06
I use suspend, my system is up and running before the monitors (which I turn off) are usable.

---

### Post by Cavsfan on 2015-11-08
I also use suspend only. I have a 1MB swap file so hibernate is the same as power off here.

And I have to be careful moving the mouse after selecting suspend as it goes to sleep in like a second.

---

### Post by metinkale38 on 2015-11-08
I know, that I can use suspend :) 
I want it for my laptop, I don't want it to drain battery when not using it...

---

### Post by sammiev on 2015-11-08
I can use hibernate with 1MB swap set to activate when the lid of the laptop is closed.

If you try this with many windows open or large project, it will not work.

---

