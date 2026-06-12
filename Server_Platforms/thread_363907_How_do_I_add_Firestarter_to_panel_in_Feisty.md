---
title: "How do I add Firestarter to panel in Feisty?"
date: 2007-02-17
forum: Server Platforms
---

### Post by floke on 2007-02-17
have just grabbed firestarter from the repos for feisty and it doesn't appear, like edgy, in the menu lists from where I can right click and select 'add to panel'. Instead, it appears in the control centre, from where right clicking just brings up the option to start it or add it to startup progs. Incidentally, when you start it, you get the firestarter window up (which I don't want), and when you close the window it seems that firestarter shuts down since the 'firewall on' icon disappears from my panel.

Any ideas anyone?

---

### Post by buuntuu! on 2007-02-17
as far as i know, what you refer to is only the gui for changing stuff, so don't be afraid if the icon disappears when you close it, the firewall won't be stopped by closing the window. only the "stop firewall" button will do that if i am not mistaken.

from the firestarter [manual]("http://www.fs-security.com/docs/tutorial.php")
"Quitting the program
A frequently asked is question is, what happens when you quit the program. The answer is that the firewall will keep functioning. If you are running Firestarter as a system service, which is automatically set up for you when installing Firestarter from a binary package, the firewall is in many cases even running before you start the program. "

have you tried adding firestarter to your menu with applications > accessories > alacarte?

---

### Post by floke on 2007-02-17
Of course! Fantastic. All sorted.
Thanx very much!

---

### Post by buuntuu! on 2007-02-17
happy to help! actually you are my first "solved case" :)

---

### Post by floke on 2007-02-17
Thanks - although actually there is still a problem!!

I added firestarter to the menus, then from there a right click and add to panel - but then it tells me I need to be root to launch it - even changing the launch to 'sudo firestarter' doesn't do it!

---

### Post by buuntuu! on 2007-02-17
change it to "gksu firestarter"
that should work!

---

### Post by floke on 2007-02-17
Marvellous! Now it IS all done!
Thanx v. much once more.

---

### Post by buuntuu! on 2007-02-17
can someone please create a "feet on the table and complacently smiling" emoticon?

---

### Post by floke on 2007-02-17
For me it's

:guitar: 

A la - Ubuntu rocks!

---

