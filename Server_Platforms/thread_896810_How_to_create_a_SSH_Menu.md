---
title: "How to create a SSH Menu"
date: 2008-08-21
forum: Server Platforms
---

### Post by vorgusa on 2008-08-21
I was curious how companies create an SSH interface on their appliances.  I have tried googling but I only find website about creating a gnome menu to make it easier to ssh into a computer.  Does anyone know a site for creating an interface for when someone SSHs into your computer?

---

### Post by windependence on 2008-08-21
Ummm I think they call it PuTTY?

Seriously, I don't have a concept of what you mean by interface. You just open a terminal and type ssh user@computer and hit return. Can you give us an example on the web?

-Tim

---

### Post by vorgusa on 2008-08-21
exactly what makes it difficult too google... I do not want a GUI for SSH.. I want to SSH into a server and have the server give me a menu of things to do... like what you get when you serial into most appliances

1.  Network settings
2.  Backup Server
3.  Input Software Key
4.  Restart Device

Input option:#

---

### Post by Dr Small on 2008-08-21
They run a shell script at login, perhaps?

---

### Post by windependence on 2008-08-21
OHHHHHH, OK, for that you need to learn some scripting. I would recommend perl for the menu type of thing but you could do it in just about any scripting lamguage.

-Tim

---

### Post by vorgusa on 2008-08-21
hmm ok.. I will look into it.  Thanks

---

