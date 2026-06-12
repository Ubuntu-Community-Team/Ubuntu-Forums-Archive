---
title: "I want to help"
date: 2005-08-31
forum: Ubuntu Backports
---

### Post by kyaneos on 2005-08-31
Hello. This is my first post in English. I am from Castille, in the Spanish Kingdom, and then my fist language is Castillian (commonly Spanish). I need some packages for my (K)ubuntu which i do not find in the official tree (main, universe, multiverse and restricted). And this is all, i need information about the process of creating .deb packages to contribute to the community. I have a PC-style 32 bits processor. I use KDE and then i need some packages for KDE. I need information early if it is possible. Thank you very much. (Sorry for my English)

---

### Post by macgyver2 on 2005-08-31
[QUOTE=kyaneos]Hello. This is my first post in English. I am from Castille, in the Spanish Kingdom, and then my fist language is Castillian (commonly Spanish). I need some packages for my (K)ubuntu which i do not find in the official tree (main, universe, multiverse and restricted). And this is all, i need information about the process of creating .deb packages to contribute to the community. I have a PC-style 32 bits processor. I use KDE and then i need some packages for KDE. I need information early if it is possible. Thank you very much. (Sorry for my English)[/QUOTE]
No need to apologize...your English is very good!

Here's some reading material for you:
[https://wiki.ubuntu.com/KubuntuPackagingGuide](https://wiki.ubuntu.com/KubuntuPackagingGuide)

---

### Post by kyaneos on 2005-08-31
Thank you very much for your help. I think i write this post too early, before I googled well x). But i have another question. When i package a program, what have i do with that? Where do i leave it? Thank you very much.

---

### Post by duffman25 on 2005-08-31
[QUOTE=kyaneos]Thank you very much for your help. I think i write this post too early, before I googled well x). But i have another question. When i package a program, what have i do with that? Where do i leave it? Thank you very much.[/QUOTE]

It depends on the type of package. If the package is not in breezy, I think you need to contact a MOTU (master of the universe) which are the people who package apps for ubuntu's universe/multiverse repositories. Check:
[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

If it's a backport, you should contact the backport team. (Here in the forums, or the backports mailinglist), check:
[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

---

### Post by macgyver2 on 2005-08-31
[QUOTE=kyaneos]Thank you very much for your help. I think i write this post too early, before I googled well x). But i have another question. When i package a program, what have i do with that? Where do i leave it? Thank you very much.[/QUOTE]
Once you package something you can use it yourself with dpkg.  Basically just
```
dpkg -i <packagename>.deb
```installs it.

If you want to start contributing your packages to the official repos there's a process to go through. I don't know all of the details, especially for kubuntu, so I'd suggest jumping on IRC (try #kubuntu-devel).

Edit: I got interrupted while replying so I didn't realize duffman25 had already posted that good info. :)

---

### Post by duffman25 on 2005-08-31
> Edit: I got interrupted while replying so I didn't realize duffman25 had already posted that good info. :)

Sometimes posting here is a matter of speed ;)

---

