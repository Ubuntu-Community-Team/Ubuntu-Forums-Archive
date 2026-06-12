---
title: "making a cd.. comand?"
date: 2005-10-14
forum: The Cafe
---

### Post by hcker2000 on 2005-10-14
I need to know how to make a command (cd..) that you guesed it dose the same thing as cd ..

I tryed as sudo and in the /usr/bin/ directory

nano -w cd..
put cd .. in the file (also tryed cd\ ..)
chmod +x cd..

Dosn't work :(

---

### Post by Leif on 2005-10-14
edit ~/.bashrc, put in :

alias cd..="cd .."

save, start a new terminal and see if it works

---

### Post by hcker2000 on 2005-10-14
Thanks that works much better. Saves time I wonder why they don't just set it up that way to begin with.

---

### Post by Pablo_Escobar on 2005-10-14
Because when You cd some directory You type : "cd /home" not "cd/home".
It's the way to unify commands.

---

### Post by GeneralZod on 2005-10-14
[QUOTE=Pablo_Escobar]Because when You cd some directory You type : "cd /home" not "cd/home".
It's the way to unify commands.[/QUOTE]

Yep, there's ambiguity without a space - an unusual situation, to be sure, but what if the user had a directory called "cd" in the current directory, and an executable called "home"?  Far-fetched, but the bash command-line is designed to be as unambiguous as possible, for obvious reasons! :)

---

