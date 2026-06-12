---
title: "startup login screen security"
date: 2010-08-27
forum: Security
---

### Post by pattais on 2010-08-27
just migrated to Lucid from Jaunty and noticed that the login startup screen looks more like windoze (shows all authorized users).  

One of the endearing security checks with Unix was that if you had access to a console you had to guess both userid AND password - the system wouldn't tell you which was wrong.

I feel that we have lowered security by  making the list of authorized users visible on a console. Is there any way to turn it off and force users to enter both userid and password?

---

### Post by cariboo on 2010-08-27
Probably the easiest way, would be to install Ubuntu-Tweak, the ppa is [here]("https://launchpad.net/~tualatrix/+archive/ppa").You can then change a multitude of settings. 

You can also remove the names using gconf-editor. Press Alt-F2, then go to apps->gdm->simple-greeter->disable_user_list

---

### Post by pattais on 2010-08-27
Thanks - that worked perfectly.

---

### Post by TwoEars on 2010-08-27
If someone has access to the login screen, they have physical access to your computer. In security terms, unless your drive is encrypted, that's it, game over.

---

### Post by FuturePilot on 2010-08-27
IMO if you want to hide the user names from the login screen for security reasons you're only fooling yourself. It's a false sense of security. If you can see the login screen that usually means you have some sort of physical access in which case it doesn't matter if you can see them or not especially if you have a live CD or USB.

---

