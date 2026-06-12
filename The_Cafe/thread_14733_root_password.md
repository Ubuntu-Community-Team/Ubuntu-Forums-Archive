---
title: "root password"
date: 2005-02-09
forum: The Cafe
---

### Post by dejavu on 2005-02-09
hello to all .. 
i dont think im maillng to the right forum but i couldnt find one suitable for my problem ..

ive downloaded Ubuntu linux and got it installed but the main problem is that it never asked me for a ROOT PASSWORD !

neither during installation nor  after installation .. i need to update things in it but cant cause i DONT have a root passwd !

What to do ?

---

### Post by TobyCat on 2005-02-09
You can always bring up a shell 

#> sudo passwd

it'll then prompt you to change the root password. That's how I changed mine :)

---

### Post by Titeuf on 2005-02-09
You don't need a root password:
do as your normal user: "sudo <WhatYouWantToDo>" and then type the password of the user, NOT the one of root.

---

### Post by basse1989 on 2005-02-09
You don't need a root password. When it promts you for a password, for example when you try "sudo apt-get" you should type your own password.

---

### Post by basse1989 on 2005-02-09
[QUOTE=Titeuf]You don't need a root password:
do as your normal user: "sudo <WhatYouWantToDo>" and then type the password of the user, NOT the one of root.[/QUOTE]

That's what I meant. :)

---

### Post by hungry1 on 2005-02-09
I messed up my chances of sudo,  I tried to edit the sudoers file and now it has a parse erre\or.  I would simply change the file back to the original, but... it's read only and now I can't sudo to change it? any ideas?
Thanks,
curt :o

---

### Post by jdong on 2005-02-09
At bootup, Press ESC to bring up the kernels list. Press "e" twice, add **init=/bin/bash rw** to the end of the line.

This will boot up a mini-Linux with a passwordless Root console. From there, you can either

1. Use passwd to reset your ROOT password
2. edit /etc/sudoers to reverse your changes


**TO REBOOT**
Don't use CTRL+ALT+DEL, "exit", CTRL+D, or anything similar to reboot! It would be an improper shutdown. The only safe way to shut down from this mini-console is:

1. **sync;mount -o ro /;sync**
2. Hit your reset button!

---

### Post by Jad on 2005-02-09
cant we set alias or a shortcut to perform "sync;mount -o ro /;sync" when you press CTRL + ALT + DEL?
my machine shut down with CTRL + ALT + backspace

---

### Post by jdong on 2005-02-09
No, I was specifically referring to shutting down from the init=/bin/bash shell prompt.

This is no ordinary bootup -- all that exist are the kernel and a BASH shell. Exitting the bash shell in any way, shape, or form would instantly cause a KERNEL PANIC: Attempted to kill init!, potentially causing filesystem corruption.

---

