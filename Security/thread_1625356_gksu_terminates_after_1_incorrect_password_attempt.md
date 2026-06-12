---
title: "gksu terminates after 1 incorrect password attempt"
date: 2010-11-19
forum: Security
---

### Post by theyain on 2010-11-19
Just like the title says, if I were to try to run anything through gksu and accidentally put in an incorrect password, instead of the gksu window coming up again, it would just terminate.

```

theyain@theyain-laptop:~$ gksu update-manager
GNOME_SUDO_PASSGNOME_SUDO_PASSSorry, try again.
sudo: 3 incorrect password attempts

```

Whats interesting is that it gives me the sudo error after only one incorrect password attempt.

Is there any way for me to fix this?

---

### Post by amauk on 2010-11-19
Just FYI, you don't actually need to run update-manager as root

---

### Post by theyain on 2010-11-19
Well, you do need to, but I don't specifically need to be root before I run it.  This was just an example.

---

### Post by cariboo on 2010-11-19
You don't need to use gksu from the terminal, in some cases it won't work. From the command line use sudo instead. You should only need gksu when you for example press Alt-F2 to bring up the run dialogue box.

---

### Post by theyain on 2010-11-19
I was using gksu from the terminal just so that there was a log present.  I know I can use sudo.  This was all just an example.  It doesn't matter if I do it in gnome-panel's alt-F2 window or in a terminal or if a shortcut/link calls gksu before it opens the application (such as Truecrypt for example).

No matter where I use it, gksu still terminates on 1 incorrect password instead of three.

Sheesh

---

### Post by cariboo on 2010-11-19
If you want an answer to your question, you can't use generalities. If you'd given us the exact use case to start with, you wouldn't gotten all these speculative answers.

---

### Post by sisco311 on 2010-11-19
Known bug: [lpbug]298217[/lpbug].

---

### Post by theyain on 2010-11-19
> **cariboo907 said:**
> If you want an answer to your question, you can't use generalities. If you'd given us the exact use case to start with, you wouldn't gotten all these speculative answers.

But using specifics makes it seem to be a bug with one program and not any program I choose to run through gksu.   I also specifically mentioned that this bug would happen with any program I choose to run through gksu.  Because of that I was sure people would just view the fairly short log as just extra information and not try and get hooked on one thing that really has nothing to do with the problem at hand.

---

### Post by cariboo on 2010-11-20
It actually is a bug in one program, the program is gksu. Check the bug that sisco311 linked to.

---

