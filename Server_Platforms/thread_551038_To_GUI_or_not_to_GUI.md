---
title: "To GUI or not to GUI"
date: 2007-09-14
forum: Server Platforms
---

### Post by baronne on 2007-09-14
Hi folks,
I'm a Windows Server Admin/Consultant having a little dabble with Ubuntu server. I have had a little experience with Ubuntu desktop. 
My question is: Does the server come with a GUI, is it worth putting it on? Or would it be best to install Ubuntu Desktop and install the server features?

---

### Post by zero-9376 on 2007-09-14
ubuntu server doesnt come with a gui, according to numerous posts this is because you want to preserve resources on a server, additionally there are no gui config tools so there isnt much point. if your more comfortable using gui text editors then i guess that would be an advantage but you could simply install X and have it not start automatically but rather use it over ssh

---

### Post by southernman on 2007-09-14
> **baronne said:**
> Hi folks,
I'm a Windows Server Admin/Consultant having a little dabble with Ubuntu server. I have had a little experience with Ubuntu desktop. 
My question is: Does the server come with a GUI, is it worth putting it on? Or would it be best to install Ubuntu Desktop and install the server features?
1- No, it doesn't come with a DE... it's as barebones to make it serve the purpose you need it to do.

2- Depends on your intended use for it. Will it be internet facing?

3- See #2

---

### Post by baronne on 2007-09-16
I have managed to get webmin installed, and plan to have it internet facing, but will probably want to have something like dansguardian on or something to that effect.

---

### Post by steve.horsley on 2007-09-16
I'm going to disagree with the others. I think it's worth installing the GUI, just to make life easier when you need it. You can install the GUI onto the server with the command:
**sudo apt-get install ubuntu-desktop**
but then I would prevent it launching at startup by renaming /etc/rc2.d/S13gdm - changing it ti start witha lower-case 's' will do the trick. hen you can start the GUI just when you want it with the command **startx**.

A graphical file explorer is much easier than using **ls** a lot. And I tend to prefer a graphical editor, too.

---

### Post by southernman on 2007-09-16
To the contrary, clearly the server box isn't your only computer. Assuming you have the server and your desktop (full blown GUI installation) going through the same router you can setup a network connection between your desktop and server, which will let you browse, edit, and install apps from the desktop.

Anytime you put a server (or desktop for that matter) there is no guarantee your safe from the crackers (evil doers). Therefore, I am still of the opinion to limit these risk to the least minimum possible. This isn't to imply that Steve is.

As your aware security isn't a set it and forget it but an ongoing process.

---

### Post by ssam on 2007-09-16
if you have ssh access to the server set up then you can use nautilus to browse the disk (Places -> connect to server, will add the server to the nautilus side bar), and double clicking a text file will open it in your loacal text editor.

---

