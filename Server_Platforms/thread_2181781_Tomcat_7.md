---
title: "Tomcat 7"
date: 2013-10-19
forum: Server Platforms
---

### Post by suomalainen on 2013-10-19
Ubunteros,

I'm running 12.04 on linux and used this command to install TOmcat 7


sudo apt-get install tomcat7


But I can't find Tomcat anywhere on MATE desktop so I want to remocve it and try again.

What command can I use to remove Tomcat and start over?

Thank you

---

### Post by 3rdalbum on 2013-10-19
Hi,

Tomcat is not an ordinary program that you launch, interact with and then quit. It's more like a system service that runs on startup and quits when you shut down; there's nothing visible on your desktop to show that it's running, it is constantly running in the background.

I'm guessing that you set it up by editing a special text configuration file, or by sending it commands in the terminal. You should really look at the Tomcat documentation.

So no, you don't need to remove Tomcat and reinstall it. As far as I can see it's working just as it should.

---

### Post by suomalainen on 2013-10-19
hi.

1. I setup/install using the terminal command above.
2. Isn't it so that anything you install you can remoce?
3. If Tomcat always runs in background then it's consuming system resources isn't it?

---

### Post by sandyd on 2013-10-19
> **suomalainen said:**
> hi.

1. I setup/install using the terminal command above.
2. Isn't it so that anything you install you can remoce?
3. If Tomcat always runs in background then it's consuming system resources isn't it?

Tomcat is a server - it should always run in background to serve people who access the webserver.
You can disable it to require that you manually start it though

---

### Post by suomalainen on 2013-10-19
I want to remove what I installed. How is this accomplished?

---

