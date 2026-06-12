---
title: "[SOLVED] Create a business desktop by script?"
date: 2006-08-21
forum: The Cafe
---

### Post by rattlerviper on 2006-08-21
Does anyone out there have the ability to write a script like Automatix, Bumps, or Easy Ubuntu (alphabetical order no preference given) that would be able to uninstall Ubuntu-desktop, Ekiga, and all the gnome games and install JRE and Flash?
Or would it be easier to create a business desktop package.  For the medical Ubuntu project we need a quick and easy way to get the desktop wiped clean and ready to use.  Some people may be unable to follow ```
sudo apt-get remove ubuntu-desktop
``` as well as a convience issue when setting up a large number of computers using Ubuntu in a medical setting.
Any ideas on how to better accomplish this goal please let me know.
thanks

---

### Post by mips on 2006-08-21
Would it not be better to do a server install and then use a script to install everything you need ?

---

### Post by saracen on 2006-08-21
What is exactly in the server by default?  Is it the desktop install minus the 'ubuntu-desktop' metapackage?

---

### Post by Brunellus on 2006-08-21
> **saracen said:**
> What is exactly in the server by default?  Is it the desktop install minus the 'ubuntu-desktop' metapackage?
the server install is the ubuntu-minimal isntallation.  No GUI, just shell.

---

### Post by IYY on 2006-08-21
Remove Ekiga? Isn't it the most business oriented program in Ubuntu?

---

### Post by rattlerviper on 2006-08-21
> **IYY said:**
> Remove Ekiga? Isn't it the most business oriented program in Ubuntu?

I don't really think that it is.  Most medical offices are not going to be using the computer as a phone.  probably ought to cut gaim out too.  

Great idea about making the server install and adding on from there!

---

