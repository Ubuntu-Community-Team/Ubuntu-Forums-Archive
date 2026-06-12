---
title: "Starting A Web Server from scratch"
date: 2010-05-13
forum: Server Platforms
---

### Post by gggccc on 2010-05-13
In need help setting up a web server from a old dell computer running kubuntu 10.04 32bit. The computer stats are: 1ghz processor, 256mb ram, 40gig HD with only kubuntu installed. I know how to port forward and all that stuff, but i just need help with the setting up the core web server data. I already have the databases made with xampp from a previous site I made and want to use those and I have a htdocs folder filled with the site to go with the databases. Could anyone help?

---

### Post by arrrghhh on 2010-05-13
It sounds like you've already got all the hard work done... just install apache and drop the site into /var/www...

---

### Post by gggccc on 2010-05-13
How do I run the mySQL server though? It's based on wordpress and I just installed the new OS. I don't have anything installed at all. Do you know if Webmin would work?

---

### Post by arrrghhh on 2010-05-13
You may want to do a clean ubuntu-server install and setup LAMP from the get-go.

Note - you don't HAVE to do this.  You can install mysql on top of what you have, without any problems.  You just mentioned it's running KDE, and with those stats you may want to ditch the GUI entirely for performance reasons...

---

### Post by Leppie on 2010-05-13
i find phpmyadmin very useful for handling mysql databases, just install it from the repos:
```
sudo apt-get install mysql-client mysql-server
```

---

### Post by gggccc on 2010-05-13
> **arrrghhh said:**
> You may want to do a clean ubuntu-server install and setup LAMP from the get-go.

Note - you don't HAVE to do this.  You can install mysql on top of what you have, without any problems.  You just mentioned it's running KDE, and with those stats you may want to ditch the GUI entirely for performance reasons...
The computer runs fine, it hosts my site better than a mac computer with 2x its power. Also I need to use it for other things, not just hosting a site, so I still need the GUI

---

### Post by gggccc on 2010-05-13
> **Leppie said:**
> i find phpmyadmin very useful for handling mysql databases, just install it from the repos:
```
sudo apt-get install mysql-client mysql-server
```
Thanks

---

### Post by gggccc on 2010-05-13
Would Xubuntu work better? I just read that it has less system requirements that Ubuntu or Kubuntu.

---

### Post by arrrghhh on 2010-05-13
> **gggccc said:**
> Would Xubuntu work better? I just read that it has less system requirements that Ubuntu or Kubuntu.

I think it's gotten pretty bloated lately.  Lubuntu may be a better bet for you.  However, if you're happy with the performance from Kubuntu, then keep it! :D

---

### Post by gggccc on 2010-05-13
I can't install the server edition (of anything) because I still need to do other stuff on it, not just host a site.

---

### Post by gggccc on 2010-05-13
> **arrrghhh said:**
> I think it's gotten pretty bloated lately.  Lubuntu may be a better bet for you.  However, if you're happy with the performance from Kubuntu, then keep it! :D
I want what evers faster! Is it really that much faster?

---

### Post by BobVila on 2010-05-13
Geeeeewwwww to running a mysql-backed web server with 256mb of ram!

With mysql and KDE running at the same time, I'm astonished that your machine isn't running at a glacial pace. I'd have to second the calls to move to a more lightweight WM, or none at all if you can figure out how to do the rest of what you need without the GUI.

---

### Post by gggccc on 2010-05-13
I'm now downloading Lubuntu. Can you do the same web site hosting with it?

---

### Post by BobVila on 2010-05-13
> **gggccc said:**
> I'm now downloading Lubuntu. Can you do the same web site hosting with it?

Sure you can - the additional packages you'll need to install don't have any bearing on the GUI, so you'll be fine once the LAMP stuff gets installed.

---

### Post by gggccc on 2010-05-13
> **BobVila said:**
> Geeeeewwwww to running a mysql-backed web server with 256mb of ram!

With mysql and KDE running at the same time, I'm astonished that your machine isn't running at a glacial pace. I'd have to second the calls to move to a more lightweight WM, or none at all if you can figure out how to do the rest of what you need without the GUI.
The computer was running XP Home when I made the website at first and now it has kubuntu and might be switching to lubuntu. It was always sort of slow, but got no slower when I installed xampp and started the mySQL and Apache servers.

---

### Post by gggccc on 2010-05-13
> **BobVila said:**
> Sure you can - the additional packages you'll need to install don't have any bearing on the GUI, so you'll be fine once the LAMP stuff gets installed.
Just so you know, LAMP was turned into XAMPP for Linux.

---

### Post by arrrghhh on 2010-05-13
LAMP, XAMPP, they're the same thing really.  Replace "Linux" with "Cross-platform" and there's no difference.

---

### Post by gggccc on 2010-05-13
What are the commands to install the required packages to host the site?

---

### Post by gggccc on 2010-05-13
> **arrrghhh said:**
> LAMP, XAMPP, they're the same thing really.  Replace "Linux" with "Cross-platform" and there's no difference.
Yeah, I know.

---

### Post by BobVila on 2010-05-13
> **gggccc said:**
> Just so you know, LAMP was turned into XAMPP for Linux.

They can change the acronym all they want, but I'll probably always call it LAMP  ;)

---

### Post by gggccc on 2010-05-13
I'm now installing lubuntu

---

### Post by arrrghhh on 2010-05-13
> **gggccc said:**
> What are the commands to install the required packages to host the site?

If you install LAMP (or XAMPP) from the get-go, all the packages are included... what are you missing?

---

### Post by BobVila on 2010-05-13
> **arrrghhh said:**
> If you install LAMP (or XAMPP) from the get-go, all the packages are included... what are you missing?

He's installing lubuntu - think he wants the commands for installing apache and mysql.

gggccc, here's a walkthrough:

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by gggccc on 2010-05-13
> **BobVila said:**
> He's installing lubuntu - think he wants the commands for installing apache and mysql.

gggccc, here's a walkthrough:

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

Thank you. That is just what I wanted. Lubuntu is almost installed!

---

### Post by gggccc on 2010-05-13
How do I carry over my previous mySQL databases and htdocs folder?

---

### Post by arrrghhh on 2010-05-13
You can simply copy the htdocs folder over.  The MySQL stuff is a little more difficult, you'll have to take a backup to the old DB and restore it onto the new one.

---

### Post by gggccc on 2010-05-13
What directory is mySQL installed by default?

---

### Post by arrrghhh on 2010-05-13
You have to backup MySQL using MySQL... I'm leaving work now, if someone doesn't answer the question I'll find it for you.  In the meantime, google backup mysql or backup/restore mysql, something like that.  Not sure off the top of my head, the command isn't simple unfortunately.

---

### Post by gggccc on 2010-05-13
> **arrrghhh said:**
> You have to backup MySQL using MySQL... I'm leaving work now, if someone doesn't answer the question I'll find it for you.  In the meantime, google backup mysql or backup/restore mysql, something like that.  Not sure off the top of my head, the command isn't simple unfortunately.

There's one problem with that for me. I only have the database files and the htdocs folder. All the other data is gone.

---

### Post by sirko on 2010-05-13
That's everything you need to install for ur server

sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-server
sudo apt-get install php5-mysql
sudo apt-get install phpmyadmin

---

