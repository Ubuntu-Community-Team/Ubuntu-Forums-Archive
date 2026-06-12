---
title: "MAC File Server questions"
date: 2007-01-11
forum: Server Platforms
---

### Post by howee on 2007-01-11
I'm trying to make a file server for 10 Macs (all running OSX). My plan was to use Ubuntu Server but my questions are as follows:-
1. Is there a gui that I can use for this, rather than command line. And if so, what services can be taken out as they won't be needed for a server.
2. Is there a package/software etc that I can use to add users, set passwords, set permissions etc.
I need it to be gui orientated as if I ever leave my job the next person will need to be able to carry on looking after this server. It's in a school that has 500 pc's and 6 servers all running XP and server 2003 respectively
Any help would be greatly appreciated. Thanks in advance.

---

### Post by Modernity on 2007-01-11
1st thing - You don't have to install Server edition to make it a server. Install the desktop version and then add packages that you need ie. Apache5, Samba etc. This is a lot simplier and you have a GUI for easier use.

In the same manner, you can add or remove packages you need or don't need. I won't go into telling you the code just yet, for sake as to answering your question. The services you remove will partially depend on what you want and what is needed (some packages have dependacies, so some must stay), other than that, the games and such can be removed. You will have to make that decision after you install.

2nd thing- Adding users for the machine with permissions and passwords, is built in.

---

### Post by howee on 2007-01-12
Thanks for the reply Modernity. I didn't make it clear in my original questions the full scenario, sorry, and that is that I want the Mac users to be able to use the 'Connect To Server' function on whichever Mac they are using and then log on to their own folder on the Ubuntu machine. The Mac users can read and write to their own folder, if possible read a common folder aswell, but not browse anyone elses folders. As administrator I would be able to browse, read and write ALL folders, either locally (logged into the Ubuntu machine) or remotely (from one of the Macs). 
As for installing Apache, is that not a web server application? The Macs, are never connected to the 'net apart from when I update them, the Mac users don't need 'net access.

---

### Post by howee on 2007-01-14
Is there anyone that can help with this or do I have to buy a Mac and OSX Server?

---

### Post by Mike'sHardLinux on 2007-01-14
You do not need to buy a Mac server.

I'm not sure what is the best way, if there is a best way; but you have at least two choices on the server. To have a fileserver for Macs running OSX, you can either use Samba or NFS on your Linux server.

I googled "OSX NFS" and got a TON of hits. You can research it and find several how-tos. It's not hard to set up, but will take some reading, and some time to get the security settings right. Samba and NFS both have their strengths and weaknesses.

At my job, our Linux server serves a mostly windows network, with 1 Mac G4 running OSX. I use Samba, and the Mac is able to connect using the "Connect-to-Server" and it works dandy.

---

### Post by howee on 2007-01-15
Thanks for the reply Mike'sHardLinux, but that's not really the main question I need answering. I'm looking for a package that is gui based, not command line, i.e. something where I can add a user, set permissions, change passwords etc. The reason it needs to be gui lead is that, if I leave my job the person who takes over from me would also have to be linux command line trained, if you see what I mean.

---

### Post by Mike'sHardLinux on 2007-01-15
Ok. Sorry.

Yes, you can install a normal desktop like KDE, Gnome or XFCE and then install GUIs for all the different services.

Firestarter is a good GUI for IPtables.
Samba has SWAT and also Gsambad.
I'm not sure what GUIs exist for NFS.

Also, there is a web-based GUI for servers called Webmin. With that you can control just about every aspect of server operations from a web browser on another computer. Another option is to install a VNC server on the server and then run a VNC client on a workstation and control the server's GUI.

For you, I would have to recommend Webmin. I personally don't use it, but it will allow you to do all that you want from a webbrowser of a workstation (or the server itself). One good thing about Webmin is that you could still run the server without any GUI, but that's not necessary.

---

