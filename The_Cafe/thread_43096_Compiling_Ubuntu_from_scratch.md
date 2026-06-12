---
title: "Compiling Ubuntu from scratch?"
date: 2005-06-20
forum: The Cafe
---

### Post by dmb on 2005-06-20
Hey, any of you geek enough to compile ubuntu from scratch, to a fully functional version? I was wondering, because i think i'm going to try to do it. Any of yo make a tutorial or scripts to do it automatically?

---

### Post by AgenT on 2005-06-20
[QUOTE=dmb]Hey, any of you geek enough to compile ubuntu from scratch, to a fully functional version? I was wondering, because i think i'm going to try to do it. Any of yo make a tutorial or scripts to do it automatically?[/QUOTE]

You should look into [Gentoo]("http://www.gentoo.org"). Doing it for Ubuntu seems a little, well, pointless. :roll: Or try [LFS]("http://www.linuxfromscratch.org/") (Linux From Scratch), but Gentoo is much more recommended.

---

### Post by poofyhairguy on 2005-06-20
[QUOTE=dmb]Hey, any of you geek enough to compile ubuntu from scratch, to a fully functional version? I was wondering, because i think i'm going to try to do it. Any of yo make a tutorial or scripts to do it automatically?[/QUOTE]

This should be the closest you will find:

[http://people.debian.org/~jgoerzen/dfs/html/dfs.html](http://people.debian.org/~jgoerzen/dfs/html/dfs.html)

---

### Post by somuchfortheafter on 2005-06-20
well you could install the base ubuntu system and well then use apt-get source to upgrade the system....

---

### Post by escuchamezz on 2005-06-20
just type make in the command line  :) 

 ;-)

---

### Post by dmb on 2005-06-21
Yeh, I am a primary gentoo user, and also i have tried LFS, but it seems like it would be possible becuase of all the source packages for ubuntu.  I guess i could just get a main system, and use dpkg to compile the core packages, and move on.

---

### Post by somuchfortheafter on 2005-06-21
yeap you do that then go back to making cool songs like the space between.. its what your good at.

---

### Post by AgenT on 2005-06-21
[QUOTE=dmb]Yeh, I am a primary gentoo user, and also i have tried LFS, but it seems like it would be possible becuase of all the source packages for ubuntu. I guess i could just get a main system, and use dpkg to compile the core packages, and move on.[/QUOTE]

If you really want to do this, then you should really look into [checkinstall]("http://asic-linux.com.mx/%7Eizto/checkinstall/"). It is very useful for source compiling. It is available on one of the Ubuntu repositories. Also, if you need more information, just search for checkinstall on this forum.

---

### Post by supenguin on 2005-06-21
I recently switched from Gentoo to Ubuntu with a brief stop in between to try Linux From Scratch. It was definitely a good learning experience to see how all the bits and pieces of Linux fit together. My idea was to do the LFS thing, and then install additional packages as encap packages (see [www.encap.org](www.encap.org) for more info). I quickly ran into software that didn't play nice with --prefix.

Correct me if I'm mistaken, but don't the Debian packaging utilities have a feature that allows you to compile a package from source? It seems to me that, in theory, you could just write a script that would go through all the installed packages and compile them from source.

---

### Post by somuchfortheafter on 2005-06-21
*cough* above *cough*

---

### Post by jdong on 2005-06-21
May I be another curious soul who asks **WHY**?

You get a binary-identical system to the currently shipped one. All of the optimizations/CFlags deemed to be safe are already applied within the source packages.

---

