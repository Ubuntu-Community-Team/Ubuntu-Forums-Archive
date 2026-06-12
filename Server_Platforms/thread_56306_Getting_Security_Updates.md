---
title: "Getting Security Updates"
date: 2005-08-12
forum: Server Platforms
---

### Post by orion27 on 2005-08-12
This is probably a stupid question, but I'll ask anyway.  I've seen quite a few ubuntu notices and updates on security sites recently.  What do I need to do to be sure my Ubuntu box is up to date with the latest security patches?  Is running the Synaptics manager and applying updates too all packages that need them enough?  Should I be doing anything else?  Also, what is the best way to stay updated through a shell.  I really don't want to use a GUI if I can help it.

Thanks for your help.
-M

---

### Post by abandoned_hussam on 2005-08-12
In terminal, you can type:
sudo apt-get update && sudo apt-get upgrade
That's all you have to do.

---

### Post by garnertr on 2005-08-12
[QUOTE=hussam]In terminal, you can type:
sudo apt-get update && sudo apt-get upgrade
That's all you have to do.[/QUOTE]

Thanks for the answer, I was searching for something else and I thought the && was unusal (I'm a newbie), anyway, I use aptitude and was always wondering how to use multiple commands, this helps out quite a bit!  thank you!!

---

