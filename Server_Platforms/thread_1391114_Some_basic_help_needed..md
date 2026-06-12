---
title: "Some basic help needed."
date: 2010-01-26
forum: Server Platforms
---

### Post by barney13 on 2010-01-26
Hi guys, new to the forums and new to Ubuntu Server.

I have used the desktop versions previously but I have just installed Server 9.10 onto a machine. I'm just wanting to gain some first hand experience with a server and getting to know the OS a little better. So far, no luck. I have installed it and have had a lot of trouble with the command line so I am installing a GUI for it as I type. I figure this will help me seeing as I really am very new to all this. 

It would probably be easier for you and me if you could point me in the right direction of a REALLY newbie guide for setting up a simple server with explanations of what everything does. This command line based stuff is really making me feel way over my head. 

I'm not sure what I want the server to do, but for now a simple file server which can communicate with my other windows machines in the house would be a great starting point. I have found a few guides which instruct me to use Samba. 

From here onwards I really don't know what I am doing. Any help at all would be greatly appreciated.

All the best

James ;)

---

### Post by thefunnyman on 2010-01-26
Here's a good resource to get you started..

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

There is a guide on how to install most of the common services you would need your server to provide.  

As far as learning the command line, try this site out.
[http://linuxcommand.org/](http://linuxcommand.org/)

Hope this helps.

thefunnyman

---

### Post by bodhi.zazen on 2010-01-26
> **barney13 said:**
> Hi guys, new to the forums and new to Ubuntu Server.

I have used the desktop versions previously but I have just installed Server 9.10 onto a machine. I'm just wanting to gain some first hand experience with a server and getting to know the OS a little better. So far, no luck. I have installed it and have had a lot of trouble with the command line so I am installing a GUI for it as I type. I figure this will help me seeing as I really am very new to all this. 

A gui such as gnome or what not does not help much as you are basically working with config files and commands in a terminal.

See the links thefunnyman gave you.

If you are interested in a graphical front end for your server, take a look at something like webmin.

---

### Post by NyteWyyrm on 2010-01-26
I agree, the links above should serve well as guides.

Keep in mind that there is (maybe only in my opinion), very little difference between the Server and Desktop edition.  The Desktop edition runs the GUI and has some extra services that are not typically needed in an enterprise.  The Server version does not run the GUI and extra services so that there are less things to have to secure.  It's also optimized a bit for speed and efficiency; there again, running less unnecessary services.  For a home server, you can likely achieve all you want to do by using the Desktop version.  All of the "server applications" are available to the Desktop edition.  I will always recommend, however, learning the CLI and how the OS operates.  

Most importantly, take your time, ask lots of questions and don't let yourself get frustrated.

---

