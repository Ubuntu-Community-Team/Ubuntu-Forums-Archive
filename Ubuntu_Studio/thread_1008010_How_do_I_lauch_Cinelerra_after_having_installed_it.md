---
title: "How do I lauch Cinelerra after having installed it?"
date: 2008-12-11
forum: Ubuntu Studio
---

### Post by timchesonis on 2008-12-11
After having spent an hour reading teh forums, websites, etc., and having installed Cinelerra, I can't figure out how to launch it!  The icon to launch the app does not display in Applications > Sound & Video, and I don't know what the command line is to launch the application.  I followed the instructions found at [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu).

Can someone offer some assistance or direction?  Thanks!

---

### Post by barisurum on 2008-12-11
Open synaptic and find the application's main package ie: cinelerra, right click on it and select properties. Move to the installed files tab and try to find the executable inside /usr/bin/ or /usr/local/bin/. Enter that in a terminal to run the program.
If you want a quick launch right click on the desktop and create a launcher.

---

### Post by timchesonis on 2008-12-11
I can't find cinelerra in Synaptec Package Manager, or in either one of those locations you mentioned.

---

### Post by barisurum on 2008-12-11
[http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html](http://cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html)

If you installed it without errors by compiling from source you should run it by: > ALT-F2 / cinelerra

---

### Post by ncs on 2009-05-25
If you did the same as me when following instructions at  [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)  you may have only installed the repository - you now need to install the application 

Open Synaptic package manager 
Select Reload. 
Close Synaptic and re-open it.
Search for cinelerra - it should list a choice of cinelerra options - select cinelerracv or one of the other versions depending on your PC. 
Mark it for installation and apply. 

It appeared under Sound & Videos launcher in 9.04 for me. If not follow previous instructions for creating launcher.

I am not sure why the package was not available and I had to close Synaptic and re-open a few times before it was available for installation.

---

