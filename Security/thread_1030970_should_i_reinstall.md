---
title: "should i reinstall?"
date: 2009-01-04
forum: Security
---

### Post by newbux on 2009-01-04
i am a very new linux user and i added a repository as advised by a forum response on a different website. later i learned i couldve installed it from the command terminal so i thought that i mightve been social engineered to download somehting i dont want. so i reinstalled OS will this take care of any possible problems? thanks

---

### Post by Dave_Connor on 2009-01-04
sudo nano /etc/apt/sources.list and delete with ctrl+k to remove the lines and then enter in terminal "sudo apt-get update". You might have not gotten tricked but the extra lists allow you to install additional software without having to build it yourself.

---

### Post by newbux on 2009-01-04
thanks can you explain in detail what the terminal code does im still catchin on thanks

---

### Post by aesis05401 on 2009-01-04
newbux - you can research the terminal command by opening a terminal and typing: man nano

This will show you the manual page for nano - where it is explained that nano is a text editor knock-off of the pico editor... a text editor. 

The remainder of the command is a path to a file (sources.list) to open in the text editor (where you will delete the entries for the repos you added but do not trust). 

If you are not used to CLI commands then you may find sudo gedit <path to sources.list> more friendly on your eyes.  Gedit is just another text editor that will appear more GUI friendly.

As for the second command: man apt-get displays the manual page - scroll down to the 'update' section and you will find that the command Dave_Connor suggests will synch your machine back up with the repositories listed in sources.list.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)  <-- and check this page out.  Your terminal skills don't need to be elite to be extremely useful, just learn at least enough to feel comfy reading man pages/reading log files and you will be well on your way.

---

### Post by newbux on 2009-01-04
thanks for the help

---

### Post by m_duck on 2009-01-04
Just nitpicking but technically you should use gksudo (or gksu) when using graphical applications and sudo for command line ones. [Useful link.](http://www.psychocats.net/ubuntu/graphicalsudo)

Also, have a look round the rest of the given site, its pretty useful, especially when just getting started.

---

### Post by aesis05401 on 2009-01-04
m_duck, nice link - definitely worth a look.

---

### Post by newbux on 2009-01-04
yes it is nice link thanks

---

### Post by joshmuffin on 2009-01-04
You should never have to re-install ubuntu

That being said: you should have your home on a separate partition just in case.

---

### Post by hyper_ch on 2009-01-05
joshmuffing: I disagree!

you should re-install when you got hacked/rootkitted... because then you can't trust your system anymore.

---

