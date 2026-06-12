---
title: "GUI temporary sudo - possible?"
date: 2008-11-20
forum: Security
---

### Post by Thalarse on 2008-11-20
Hey folks. I hope this is in the right forum. I've done a bit of searching and couldn't find anything on the subject. I've been meaning to post this for a while, but every time I feel like a stupid noob and change my mind. 

As a newbie fresh from windows, one of the things that bugs me is having to use the shell and perform tasks with the CLI. Mostly I've had this problem with copying or unzipping files into directories for games (the original game files for OTTD, as well as addons for other games, that sort of thing).

Of course the destination folders aren't owned by me, so I need root access to do this - which the unzip program (file roller?) doesn't have. I don't want to give the program permanent root access obviously, and to do it temporarily would probably mean a command string in CLI so there's no point doing that. 


So what I'm wondering is it possible to have a popup dialogue asking for the root password when a program is told to do something it doesn't have permissions for. The same kind of popup you get when opening synaptic package manager and other things. Once the operation is complete the program would lose it's root privileges of course. 


I don't have anything against the CLI, it seems to be better for alot of things, but for general use - especially for a windows convert - something like this could help dumbarse noobs like me. :p 

So is there a way to do this already, or is it a case of having to learn code-fu and doing it myself... by which time (believe me, it'd take years) I would not need it! haha. 

Anyway, thanks. :)

---

### Post by lakersforce on 2008-11-20
My advice: press Alt + F2, and write "gksudo nautilus". I know that's not quite what you are asking for, but it's the procedure I'm using.

---

### Post by Thalarse on 2008-11-20
Thanks! It works at least. It'd be nice if the root password thingy came up by itself as required, but oh well. heh. 

(I know, I know. Lazy windows user) :p

---

### Post by The Cog on 2008-11-20
You can always create a desktop launcher icon with the command **gksudo nautilus** in it. Or add it to you menus somewhere.

---

### Post by daleus on 2008-11-20
In terms of security, why not create a directory specifically somewhere for installing things and give your account access to this folder? that way you don't have to escalate in the future, Just a suggestion.

---

### Post by Thalarse on 2008-11-20
Uh. I didn't know this was possible. Everything seems to install where it wants, which was annoying until I realised that you don't really need to know where a program is to launch it. Simply typing "openttd" (for example) will do the job, rather than cd'ing to the directory first like in DOS.

---

### Post by lakersforce on 2008-11-21
That's because in this example openttd is in your path variable. Dos supports paths too (and so does Windows).

---

