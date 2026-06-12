---
title: "Server that has 16mb video ram."
date: 2010-08-15
forum: Server Platforms
---

### Post by hockey97 on 2010-08-15
Hi, I am currently building a server top notch. Since the server is very expensive. I was thinking to not add a pci-express graphics card. Since it has a onboard gpu.

I guess that I can't install an OS like ubuntu that will run it's gui OS.

What I want to do is without any upgraded gpu cards. I want to find some way that I can still use a computer that has a gui that will be able to access all files at the root of ubutnu  over a internet connection meaning internal.

I want to use a GUI type interface rather then a command line. I need to spend less time doing stuff and focus more on programming stuff.

I do got webmin which is a internet infeface that can access most things but no tall files.

Just saying that just in case if the server files got currpted I could still use a graphical system tools.

I also would like to know how I can transfer programs without installing them.

Right now I got apache2 and others already setup. I  got webmin also setup. I was woundering if there is some way where I can grab those files put it on a external hard drive and transfer them to the server or transfer them threw the home network and those files would without installation be running on that server. In otherwords whats the less painful way to move apps from one computer to another that has their own configs etc.

The reason I ask this is that I know if I have to re-install everything I would make small errors that will cost alot of time to fix and figure out why the software or program won't install or work.

I am saying more of a plug and play type of thing where you grab all of the softwares flies and plop it to the server and then it would work for example webmin. If I copied what I got now I will transfer all of the files to the server where it then will start running the webmin server software on the server.

---

### Post by CharlesA on 2010-08-15
Kind of hard to understand what exactly you want to do, but you should be able to forward X over SSH and run graphical programs like gedit/kate/etc that are running on the server from your local machine.

Honestly, I haven't really used any GUI editors when working on my server, outside of comparing old/new conf files. Most of the time I just use vim or nano.

---

