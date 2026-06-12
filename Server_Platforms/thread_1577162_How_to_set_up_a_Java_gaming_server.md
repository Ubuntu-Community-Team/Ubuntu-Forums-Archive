---
title: "How to set up a Java gaming server?"
date: 2010-09-18
forum: Server Platforms
---

### Post by Neilos1985 on 2010-09-18
Hi,

I intend to develop a game using Java. I will need a dedicated server for running the server side code for clients to connect to.

For ease of development I was hoping to use an old PC sat next to my desktop to run as a server.

I have downloaded the 32 bit server platform (all the CPU will allow on this machine) and put it on a USB stick and can run it and it all works ok. When I get midway through the installation I get to a screen that asks me to 'Choose software to install', I was just wondering if there were some choices that I should make here. For instance I will be using MySQL, Java etc...

I am persisting on with an installation for the moment but I will be able to reinstall everything again if necessary.

Thanks

---

### Post by Neilos1985 on 2010-09-18
Well this is as far as I have got.

I installed the 'Basic Ubuntu Server'.

I completed the installation and was able to boot into the server and can see various information and a command prompt.

I'm leading myself blindly through this process as it is much like a voyage of discovery. And now I am stuck.

What should I do next? The idea I had in my head was that I would be able to access this computer via my desktop machine. Performing all uploads etc from there and have it just work! At the moment my router is dead and I'll connect it to my new one when it arrives but imagine for now that I have both computers connected to the internet through my router.

What do I do?!?! lol

Thanks

(ps feel free to tell me if I am going in completely the wrong direction with this)

---

### Post by nicolasdiogo on 2010-09-19
i assume your game will run on some application server as tomcat

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/)

alternatively you can try glassfish

or explain what is needed to support your application.


Nicolas

---

### Post by Neilos1985 on 2010-09-20
At the moment I need to run a Java application that will access a MySQL database. The server will handle communication between clients and keep the database up to date, sending the information to the clients when necessary.

At the moment that is all that will need to happen on the server but things may well change/be added.

Isn't Tomcat a web server? Or is a web server synonymous with a game server?

---

### Post by Neilos1985 on 2010-09-21
bump

---

### Post by arrrghhh on 2010-09-21
> **Neilos1985 said:**
> bump

I don't know what you're bumping dude... we can help you setup certain things, but if  you're developing something... you're kinda on your own there.

I mean we can try to help, but again since you're developing the game - how can we support that...?

---

### Post by BobVila on 2010-09-21
We really need some more detail here. Have you installed/configured openssh-server on the server machine? If you want to connect to it from your desktop to administer and upload, you'll need to be able to ssh into it.

As far as the components to support your development, apt-get install is your friend. Installing mysql and java are straightforward enough. Do you know how to configure the supporting services? If not, you'll have a lot to learn before you start coding a game to leverage them.

---

### Post by kulshoks2121 on 2010-09-21
Tomcat Server is the answer.

just define your java application folder on the tomcat server.

---

