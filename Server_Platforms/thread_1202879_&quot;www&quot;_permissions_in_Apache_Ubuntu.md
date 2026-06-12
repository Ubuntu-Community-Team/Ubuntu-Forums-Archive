---
title: "&quot;www&quot; permissions in Apache Ubuntu"
date: 2009-07-02
forum: Server Platforms
---

### Post by kirgy on 2009-07-02
Hi, sorry if this is the wrong place to place this, im a newbie here.

Im trying to set up an apache server on my Ubuntu OS to just develop some projects I have. Ive managed to install it, and its running the test page.

In command line ive managed to add a file "test.php" and just leave it empty in the "var/www" directory. This was managed using the root user.

Im wanting to be able to just use the GUI to drag and drop files into the "www" directory. But all I get is I dont have the nessesary permissions to do so, can anyone help? It wont even let me chmod the folder when loged in as root...

Im new to this whole linux thing really!

Thank you, you beautiful people.

---

### Post by masux594 on 2009-07-02
[FONT=monospace]type this command 
[/FONT]```
sudo chown -R YOUR_USER_NAME /var/www
```[FONT=monospace]

Sysc, A
[/FONT]

---

### Post by .Maleficus. on 2009-07-02
You do not want to change ownership of /var/www.  It is owned by root for a reason, please leave it that way.  If you want to use Nautilus to move files and folders there, do this:
```
gksudo nautilus /var/www
```

---

