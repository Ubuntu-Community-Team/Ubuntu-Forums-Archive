---
title: "[SOLVED] moving files ,vst's for renoise?"
date: 2009-01-06
forum: Ubuntu Studio
---

### Post by rixtr66 on 2009-01-06
i recently bought renoise,and dug up some linux vst's on the net.
i need to put a vst file in /usr/lib,for renoise to recognise it.
but i dont know how to move files.i dont want to use nautilus because i always get permission errors.i just want to move a file from point a to point b!!how do i do that??please help!
Thanks:confused:
Rick

---

### Post by thorgal on 2009-01-06
hehe, unix 101:

open terminal
type 'cd' to enter your home directory (default when opening terminal anyway)

anything under the home directory is owned by you so you can move things around. Anything outside is most of the time owned by the root superuser so you have to have admin rights to move things around (nautilus is probably run by you, not root ;) )

Anyway, in the terminal, if you want to move things into root owned directories, you need to use 'sudo' in front of the 'mv' command, e.g. :

```

sudo mv some_file /usr/lib

```

you can also copy it instead, in which case you will use 'cp' instead of 'mv'. You can make a symbolic link (a bit like a windows shortcut) by using 'ln -s' instead of 'cp' or 'mv'.

I suggest you get a 'Unix in a Shell' book to learn about command line stuff. It is very powerful and often times necessary. I have a couple of linux servers that don't use any windows manager so knowing shell stuff is critical :)

---

### Post by rixtr66 on 2009-01-06
Yes its true i need to brush up on commands!i do however keep notes,i just never wrote this one down(Dohhhh!)anyway Thanks for the info!!!
did what i needed.
Rick

---

