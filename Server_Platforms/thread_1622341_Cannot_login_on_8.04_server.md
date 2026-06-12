---
title: "Cannot login on 8.04 server"
date: 2010-11-15
forum: Server Platforms
---

### Post by André_R on 2010-11-15
All of a sudden i cannot login on my server anymore.
Also all THE software running on IT is not responding anymore.

On the console i get the login screen, but after giving in the login IT doesn't come up with the password question but returns to the login question.

Does anyone know how i can solve this? I cannot give the server à reboot command....?
I'm realy stick with this...

---

### Post by arrrghhh on 2010-11-15
Have you tried restting the box..?  If you don't have physical access, certainly someone would if it's a hosted machine.

Does it give you any errors?  It should always try to auth a password, even if the user doesn't exist on the box.  Definitely sounds like something is hung bad.

---

### Post by hawk2010 on 2010-11-16
did you try single user mode

edit grub an do the following

rw init=/bin/bash

---

### Post by linux-hack on 2010-11-16
> **hawk2010 said:**
> did you try single user mode

edit grub an do the following

rw init=/bin/bash

That's not working on ubuntu in my knowledge but ou can try

---

