---
title: "EVOLUTION--Please help!"
date: 2007-11-16
forum: Server Platforms
---

### Post by solwyn on 2007-11-16
I am new to linux and so far have enjoyed it. I am having problems with the evolution email client. It worked fine at first. It downloaded my messages from gmail the first time without any problems. Now, however everytime I launch Evolution it starts to freeze up and I have to close it out. Usually as soon as I open the program the screen darkens for a few minutes, then lightens back up. During this time I can not click on ANYTHING. I usually get the message giving me the option to "force to close". I can not read any of the emails it downloaded or do anything else for that matter while Evolution is running (and not working!). Can anyone help me and tell me what to do in laymen's terms?

---

### Post by mdpalow on 2007-11-16
I imagine it could be anything you might have recently done, so maybe let's look at a more simple way to fix it.

Why not open your file browser and go to your .evolution folder. You'll need to press CTRL + H to see it since it's hidden. When you're in that folder, you could copy your MAIL, CONTACTS, CALENDAR, and ADDRESS BOOK to your desktop.

Then open Synaptic from your main menu:

System -> Administration -> Synaptic Package Manager and do a search for Evolution. When it comes up, click on it and Mark it for complete removal. Then reinstall it using Synaptic and then paste your folders back into the .evolution folder.

Copying the .evolution folders is one way of saving the e-mails since you can't get in Evolution to do a backup.

Good luck....

---

