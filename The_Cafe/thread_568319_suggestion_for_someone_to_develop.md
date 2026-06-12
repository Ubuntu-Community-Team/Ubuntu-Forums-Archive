---
title: "suggestion for someone to develop"
date: 2007-10-05
forum: The Cafe
---

### Post by noyhcat on 2007-10-05
I have a suggestion for future thought and maybe implication. Making a user able to login and do root user actions without having to do root. but dont throw this out yet. my idea is making it so it has a timer so after 1 minute or what u specify it shuts back off so u only have basic access again.     i came up with it after attempting to move a bunch of unrelated files around which unfortunately turned out to be under folders with root user permissions.   
if i felt like doing all the command lines for all these random folders everywhere all over i could have but how much easier is it to drag and drop? i could login as root but as it seems thats not a smart thing to stay logged in as and i dont wanna relogin every 2 minutes.

being able to be temporarily root quickly could be very useful and being bale to drag and drop like normal might help some people with the windows to linux transition.

perhaps there is something like this? im halfway new to linux but as of yet i havnt heard of anything like this

---

### Post by fwojciec on 2007-10-05
From what I understand you're describing the functionalities of sudo...  Am I missing something here?

---

### Post by happysmileman on 2007-10-05
> **fwojciec said:**
> From what I understand you're describing the functionalities of sudo...  Am I missing something here?

It appears to be that to me as well...

You run "sudo *command*" and it'll ask you for a password and perform action as root, however if you use sudo more than once in a row (within a space of a few minutes) it won't ask you for the password each time. That way you can run commands as root without being logged in as root.

To launch a graphical program as root you use "gksu *program*" in GNOME or "kdesu *program*" in KDE, so running Nautilus as root (gksu nautilus) would allow you to run the file manager as the root users, moving files, accessing files, etc. But you'll only be root in that program, or any program you start from nautilus, so none of your other programs running are affected. And when that program closes the root session is over, sorry if I explained it bad

---

