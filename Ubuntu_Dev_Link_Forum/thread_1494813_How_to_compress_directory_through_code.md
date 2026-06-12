---
title: "How to compress directory through code"
date: 2010-05-27
forum: Ubuntu Dev Link Forum
---

### Post by usman400 on 2010-05-27
Hi
I am working on a kind of backup/restore system that will facilitate the user
to back up the home folder.
The problem is I dont know, how to do it in C language.
I have downloaded the source codes of TAR and Gzip, but they have
a huge source code.

So please help me in either one of the following:
- How to compress folders using coding in c/c++
- How to use the TAR or Gzip (or any other zip software that works for Ubuntu), in my code

I am using GTK+ with C language

Thanks

---

### Post by allquixotic on 2010-05-28
Assuming you have the relevant experience with GTK and an applications programming language (C, C++, Python, Vala, etc) you could try libarchive for a wide variety of compression techniques: [http://code.google.com/p/libarchive/](http://code.google.com/p/libarchive/)

You can also do the more "GNOMEy" thing and use GIO / Gvfs archive backend to do your file operations. Bindings for GIO are much more widely supported in non-C languages than libarchive, from what I can tell. Check out the API at [http://library.gnome.org/devel/gio/stable/index.html](http://library.gnome.org/devel/gio/stable/index.html) for details (or use Devhelp, a program available on Ubuntu, for a more native format).

This is the wrong forum to ask this question, though. This forum is for developers to share experimental work with the community and to solicit feedback before pushing it up the distribution chain.

---

### Post by usman400 on 2010-05-28
Thanks, I will try on the information you provided

---

