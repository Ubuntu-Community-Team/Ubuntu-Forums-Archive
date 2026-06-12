---
title: "Xampp for Linux and Lamp Server"
date: 2009-09-25
forum: Server Platforms
---

### Post by CFBauer on 2009-09-25
Hello all,

I've installed Xampp for linux to do some web design work locally.

I tried installing some other software through Synaptic, which required a LAMP server using the "mark packages by task" option and selecting Lamp Server. Now when I go to [http://localhost](http://localhost), it takes me to the "It Works!" page, which corresponds with the Lamp install.

What I want is for it to show my Xampp for linux setup at localhost, located at /opt/lampp. Is there a way to change this?

Thanks!

-Chris

---

### Post by Michael.Godawski on 2009-09-25
Moved to Server P. ;)

---

### Post by CFBauer on 2009-09-26
Thanks for moving the thread. Also, bamp.

---

### Post by cariboo on 2009-09-26
Lamp and Xampp accomplish the same thing, I would suggest uninstalling Xampp, as they conflict with each other as far as ports are concerned. Apache uses port 80, no matter where you install it, and mysql uses 3386. The only way you are going to use both at the same time, is to configure either LAMP to use different ports or Xampp to use alternate ports. I would suggest using only one, as it will make things a lot easier for you.

---

### Post by CFBauer on 2009-09-26
> **cariboo907 said:**
> Lamp and Xampp accomplish the same thing, I would suggest uninstalling Xampp, as they conflict with each other as far as ports are concerned. Apache uses port 80, no matter where you install it, and mysql uses 3386. The only way you are going to use both at the same time, is to configure either LAMP to use different ports or Xampp to use alternate ports. I would suggest using only one, as it will make things a lot easier for you.
Right, I was trying to use only Xampp, but I don't know how to uninstall Lamp or switch to Xampp.

Anyway, I recently just decided to use Lamp instead. Thanks for the help.

---

