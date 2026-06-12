---
title: "Turining off the default gui i installed"
date: 2008-02-12
forum: Server Platforms
---

### Post by James27 on 2008-02-12
I installed ubuntu desktop on top of my server (i know its a waste of cpu) but i dont want it to load by default. i want it to go to the text, and only enter the gui if i enter the startx command. any ideas on how i can accomplish this?
thanks in advance, james

---

### Post by p_quarles on 2008-02-13
There are several ways of doing this, but I learned this trick from another user just recently:
```
sudo mv /etc/init.d/gdm ~/
```
This will remove the script that starts Gnome from the directory that runs on startup, and place it in your home directory. You would then be able to start the GUI back up by going to your home directory and typing:
```
sudo ./gdm start
```

---

