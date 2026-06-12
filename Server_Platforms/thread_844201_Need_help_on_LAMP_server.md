---
title: "Need help on LAMP server"
date: 2008-06-29
forum: Server Platforms
---

### Post by majikhotline on 2008-06-29
Hello unbuntu community,
i have been working on a Lamp server and had no luck getting it online.  I need some info on this, if i need to i will start from scratch.  I have a simple html page for testing.  i am completely new to this. Please help the newbie!:lolflag:

---

### Post by dominiquec on 2008-06-29
Open a terminal, and type:

sudo apt-get install apache2 php5 php5-mysql mysql-server

The location of the web pages will be at /var/www

---

### Post by mk1w86 on 2008-06-29
There is also an installation option when installing Ubuntu Server to set up a LAMP server automatically.

---

### Post by jamesrfla on 2008-06-29
You might need to change the ownership of /var/www.

---

### Post by Le-Froid on 2008-06-29
for lampp, in the terminal type:
sudo /opt/lampp/lampp start

I also *suggest* typing:
sudo chmod 777 /opt/lampp/htdocs/*
to easily modify files in your web folder

---

### Post by majikhotline on 2008-06-30
thanks guys for helping. the server was auto maticaly installed but its all line command and I'm a little rusty, is there a way that I can man the command to help me copy the html files, is there a web site with some commands,and last how do I test to see if the server is working correctly.  thanks for all the help

---

### Post by mrpeenut24 on 2008-06-30
[http://www.google.com/search?q=linux+basic+commands](http://www.google.com/search?q=linux+basic+commands)  shows a lot of websites that can show some basic linux commands.

To copy a file type:
```

cp *src dest*

```
where src is the file you want to copy and dest is where you want to copy it to.  i.e.

```

cp /home/user/index.html /var/www/index.html

```

If you find a command you know you need to use you can type 
```

man *command*

```
in the console to get a manual for it.


To test if the server is working, go to another computer and type in the ip address of the server.  Or you can go the following at the server itself:
```

sudo apt-get install lynx
...
lynx localhost

```

Lynx is a terminal-based webbrowser.  localhost is the computer you're working on, so lynx localhost will open up a webbrowser to the localhost and test to see if the webpage is working.

---

