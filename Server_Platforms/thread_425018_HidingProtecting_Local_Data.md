---
title: "Hiding/Protecting Local Data"
date: 2007-04-27
forum: Server Platforms
---

### Post by CybaCowboy on 2007-04-27
Hi,


I have certain files on my computer that I do not want to be visible or accessible to other users, and I was wondering what you guys could suggest?

Basically, I want to be able to mark individual files as "private", hide them and make them inaccessible by anyone else...

I'm guessing that somewhere out there, there will be some software that can perform such a task, whether it be through a password-protected folder or in some other form.


What can everyone suggest?

---

### Post by murlosad on 2007-04-27
Anything in your home folder is only writeable to the owner of the home folder.  You can change permissions to individual files and/or folders by right-clicking and selecting Properties. This would allow you to make the selected file neither readable or writeable or even executable to anyone but the owner (yourself).

If you just want to hide stuff, add a "." before the filename, e.g. ```
document1.txt
``` becomes ```
.document1.txt
``` This works about the same way as marking a file as 'hidden' in Windows. It is still viewable if the user selects 'Show hidden files', or uses 'ln -a' from a terminal.

hope this helps.

---

### Post by CybaCowboy on 2007-04-28
What I wouldn't mind is something I can password-protect and/or encrypt... Like an electronic safe or something.

---

### Post by murlosad on 2007-04-28
I'm sure there is something like that out there, and probably someone around here even knows about it, but I've never had a use for anything like that.  Try searching google, and the rest of the board, something like 'password protect files' here or throw in a 'linux' for google.

---

