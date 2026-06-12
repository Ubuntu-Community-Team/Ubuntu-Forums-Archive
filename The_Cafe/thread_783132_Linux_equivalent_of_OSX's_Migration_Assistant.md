---
title: "Linux equivalent of OSX's Migration Assistant"
date: 2008-05-05
forum: The Cafe
---

### Post by schauerlich on 2008-05-05
Are there any programs for migrating user data like Migration Assistant in OSX? Basically, you backup your partition to an image, install the new OS, hook up your external hard drive with the backup, choose what users you want to migrate, and Migration Assistant will automagically transfer all applications and settings and fix permissions issues. It makes it extremely easy to do a fresh install whenever there's a new OS on the block. I know I can make a backup of /home and pretty much just copy and paste that back in, but that doesn't take care of stuff like a custom xorg.conf, installed programs and other customizations not located in the /home folder.

UPDATE: I submitted the idea of this program to Ubuntu Brainstorm:
[http://brainstorm.ubuntu.com/idea/8124/](http://brainstorm.ubuntu.com/idea/8124/)

---

### Post by spupy on 2008-05-05
It is a good idea for a program. With normal computer usage, there are 3 things you need to backup:
- /home folders, for user configuration
- /etc folder, for system configuration
- List of installed packages. One can easily be generated with the help of apt.

In fact, I think, a script that does that wouldn't be longer than 200 lines and wouldn't be that complex. A simple program with a clean and intuitive interface would be even better. It would backup stuff in a tar.gz, since it can save permission and is usable even without the program.

---

### Post by eragon100 on 2008-05-05
Never, too lazy :lolflag:

---

### Post by schauerlich on 2008-05-05
Maybe we can get LaRoza to write it for us. :)

---

### Post by nerdman978 on 2008-05-05
indeed, that is a great project idea. let me know how it turns out :guitar:

*EDIT* in fact, I would totally help make it if you need any help.

---

