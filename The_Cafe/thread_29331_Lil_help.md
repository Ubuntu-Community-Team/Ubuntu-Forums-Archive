---
title: "Lil help?"
date: 2005-04-23
forum: The Cafe
---

### Post by Digitallysick on 2005-04-23
i have modified my xorg.conf file and i want to put it in the /etc/X11 directory, but it states i dont have permisson?? what do i need to do?? (trying to get my forward and back buttons on my mouse to work with firefox)

---

### Post by sas on 2005-04-23
[QUOTE=Digitallysick]i have modified my xorg.conf file and i want to put it in the /etc/X11 directory, but it states i dont have permisson?? what do i need to do?? (trying to get my forward and back buttons on my mouse to work with firefox)[/QUOTE]
 you need to use "sudo" to give you the privileges to write to /etc/, you can do this by typing 

```
sudo cp xorg.conf /etc/X11/xorg.conf
```

---

### Post by Digitallysick on 2005-04-23
it still says that it is read only and wont let me edit it in the text editor? i just need to be able to edit and save it

---

### Post by somuchfortheafter on 2005-04-23
sudo gedit xorg.conf?

---

### Post by sas on 2005-04-23
[QUOTE=Digitallysick]it still says that it is read only and wont let me edit it in the text editor? i just need to be able to edit and save it[/QUOTE]
 save the file in your home directory (file > save as) and then ```
sudo cp xorg.conf /etc/X11/xorg.conf
```

OR copy the text and then run the command ```
sudo gedit /etc/X11/xorg.conf
``` then paste in your text and then save

---

### Post by XDevHald on 2005-04-23
Or possibly 

[b]sudo chmod 777 /etc/X11

[/b]Then open your /etc/X11 directory and also open the directory where your .conf file is at but open the directory in a seperate window, and just right click on the file, **Copy File** and then just goto the X11 folder and right click, then **Paste File **and you're all set :)

**Note: **It'll recognize the .conf once you place it in the X11 dir :)

---

### Post by TravisNewman on 2005-04-23
ooohhh chmod 777 on /etc/X11 may not be the greatest of ideas.

The simplest way is to 
sudo nano /etc/X11/xorg.conf
and edit it there, or
sudo gedit /etc/X11/xorg.conf

Nano is CLI based, gedit is graphical based.

---

