---
title: "GUI for Ubuntu server"
date: 2009-11-30
forum: Server Platforms
---

### Post by ishfady on 2009-11-30
Hi

I am new to Ubuntu server. I come from microsoft server and I am used to GUI for admin work, such creating user, email setup etc.

Is there any good GUI tool I can use with Ubuntu server 9.10 for admin work.

many thanks

---

### Post by tomdagreek on 2009-11-30
sudo apt-get install ubuntu-desktop

---

### Post by shred_eng on 2009-11-30
there is always webmin which includes a module called usermin, this is certainly worth checking out, and saves going to the extreme of installing a desktop :)

---

### Post by snowpine on 2009-11-30
> **ishfady said:**
> Hi

I am new to Ubuntu server. I come from microsoft server and I am used to GUI for admin work, such creating user, email setup etc.

Is there any good GUI tool I can use with Ubuntu server 9.10 for admin work.

many thanks

Hi ishfady, you can create user accounts, setup emails, etc. using only the command line. I encourage you to learn the terminal to administer your server.

If you want a GUI, you have a wide range of choices, from "sudo apt-get install ubuntu-desktop" (for a full Ubuntu Gnome desktop, just as if you'd installed desktop Ubuntu) to "sudo apt-get install xorg xterm icewm" for a simple, lightweight icewm interface.

---

### Post by R.Bucky on 2009-11-30
You are going to open yourself up to hacks if you install a GUI. Try a virtual machine or another box if you want GUI. A server should be command line. 

With that said, phpmyadmin, webmin, and/or splunk are great if your hardware can handle it.

---

### Post by HermanAB on 2009-11-30
If your 'server' has a screen and a keyboard, then simply use ordinary Ubuntu.  The warnings about running a server with X enabled are somewhat exaggerated and it easy to start/stop X when needed.

The Ubuntu server edition is aimed at headless machines sitting in dank data centres, administered remotely over SSH.  If your machine has a head, then by all means, use it.

---

### Post by Iowan on 2009-12-01
[https://help.ubuntu.com/community/ServerGUI]("https://help.ubuntu.com/community/ServerGUI")

---

### Post by yaddi on 2009-12-01
I've been installing ubuntu-desktop on my server. but i don't want it run automatically.
I want the X environment run if I runs **startx**

What should I do?

---

### Post by munky99999 on 2009-12-01
> **yaddi said:**
> I've been installing ubuntu-desktop on my server. but i don't want it run automatically.
I want the X environment run if I runs **startx**

What should I do?

[http://ubuntuforums.org/showthread.php?t=254540](http://ubuntuforums.org/showthread.php?t=254540)

Basically the lack of a gui is a good thing. Just looking at a few of the recent exploit codes put out recently. Notepad has one. stack buffer overflow. Sure you need local access. Which can come many ways. Obviously this is for windows. However I'm just making a point. Would you ever think of notepad being exploitable? Well microsoft didnt. Notepad is available in server core. Your physically insecure rodc server core boxes can now be taken out.

That said. When you install that gui to go with your OS. It comes with lots more code which can be exploited potentially.

Highly suggested you dont use gui for internet exposed boxes.

---

### Post by solar george on 2009-12-02
btw [The Official Ubuntu Server Book]("http://www.amazon.com/Official-Ubuntu-Server-Book/dp/0137021186/ref=sr_1_1?ie=UTF8&s=books&qid=1259730061&sr=8-1") is a good read and would probably be helpfull in your case.

---

