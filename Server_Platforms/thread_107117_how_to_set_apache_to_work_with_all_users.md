---
title: "how to set apache to work with all users?"
date: 2005-12-22
forum: Server Platforms
---

### Post by pedrotuga on 2005-12-22
Hey all!

This is a very basic question.

how do i set apache to serv the files in every user's public_html do

[http://myserver.com/~user/](http://myserver.com/~user/)

?

---

### Post by LordHunter317 on 2005-12-22
Assuming apache2, enable mod_userdir:```
sudo a2enmod userdir
```But it should already be.  Users will need world access ('x') bits on the their /home directory and world read and access ('rx') on their public_html directory.

---

### Post by pedrotuga on 2005-12-22
mmm...
lets see...

i should use chmod right?
should i like:

```
chmod 666 public_html
```
?

or.. something else than 666?
i allways mix up wich pirmitions should i give

---

### Post by pedrotuga on 2005-12-22
BTW, tank you hunter i think it should be on.. lets try change the pirmisions

---

### Post by LordHunter317 on 2005-12-22
No.  **Never give 666 or 777 permissions.**

On the home directory, you want at *least* 701.   On public_html and directories below you want *at least* 705.  On the files inside public_html you want [i]at leas[t/i] 604.

---

### Post by pedrotuga on 2006-02-23
What da heck...

```

Forbidden

You don't have permission to access /~pedro/index.htm on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
```

The module is already on. I chmoded the dir 755. And still this is not working. Apache is runing well for the main directory. but this users this is not :(

what can it be?

---

### Post by Eternal Blade on 2006-02-23
The error you got came from the lack of permission for the user to access your index.html.  When you granted permissions to the directory did you also go in and grant permissions for the files in the directory?

---

### Post by pedrotuga on 2006-02-23
yes i did.... i think i a m missing something somewhere.

---

