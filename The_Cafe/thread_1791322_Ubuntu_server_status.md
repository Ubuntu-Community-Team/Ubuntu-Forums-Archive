---
title: "Ubuntu server status"
date: 2011-06-26
forum: The Cafe
---

### Post by pinus on 2011-06-26
I use Ubuntu on my desktop and was pleased to see the improvements for in the last couple of years. Canonical created great bundles of open source software, easy to use for desktop users. They created forums, wikis which contain documentation which makes the software usable for non geeks. The best software is worthless if you don't know what it does and how to use it.

From my good experience with the desktop, the Ubuntu server was the first choice for my little home server. It should be able to host files for some users. That's so basic that I didn't expect any trouble. The articles on the net made me sceptical but I gave it a try. My assumption was that NFS is the native file share mechanism which should work out of the box. To make it short, it didn't work. And the worst thing is that all the solutions are so far away from the users problem that it really hurts.

The user might want to share storage or files between users. The users should have access to the resources and might be grouped for easier maintenance.

I didn't even find a unified user management, the most basic feature for a server. There are documents describing bits and pieces which you can glue together with some magic to get a usable solution. But that's still far away from a unified solution. You have to add a user to your operating system, to SAMBA...

Each dump router for a couple of $ has a web user interface for maintenance. There isn't such a thing with the Ubuntu Server. 

I think it's time to integrate the services to a working solution combined with a user centric maintenance interface for a server.

---

### Post by Dangertux on 2011-06-26
> **pinus said:**
> I use Ubuntu on my desktop and was pleased to see the improvements for in the last couple of years. Canonical created great bundles of open source software, easy to use for desktop users. They created forums, wikis which contain documentation which makes the software usable for non geeks. The best software is worthless if you don't know what it does and how to use it.

From my good experience with the desktop, the Ubuntu server was the first choice for my little home server. It should be able to host files for some users. That's so basic that I didn't expect any trouble. The articles on the net made me sceptical but I gave it a try. My assumption was that NFS is the native file share mechanism which should work out of the box. To make it short, it didn't work. And the worst thing is that all the solutions are so far away from the users problem that it really hurts.

The user might want to share storage or files between users. The users should have access to the resources and might be grouped for easier maintenance.

I didn't even find a unified user management, the most basic feature for a server. There are documents describing bits and pieces which you can glue together with some magic to get a usable solution. But that's still far away from a unified solution. You have to add a user to your operating system, to SAMBA...

Each dump router for a couple of $ has a web user interface for maintenance. There isn't such a thing with the Ubuntu Server. 

I think it's time to integrate the services to a working solution combined with a user centric maintenance interface for a server.

I think there is one major hole in this logic. Simplicity, in its nature limits functionality.

Take the router you mentioned for example ; yes it has a graphical web front end management system. However, if you look at what the router's capabilities are, you will realize there really isn't all that much it can do. 

When you look at a server application, whether it is a web server, file server, domain controller, or anything else you have to realize that it is going to be created with the most possible functionality in mind. 

Let's look at samba for instance. For your purpose which is relatively simple, sharing files. A graphical user interface might seem intuitive. However, you are limiting the scope of what samba can do to something very basic at that point, user management and basic file sharing. If you dig deeper and research exactly what most server applications are capable of you would find that making a GUI front end for them would present the user a FAR more complicated interface than if they just utilized the command line.  This is not even counting the fact that you want the GUI to ALSO interface with basic operating system features like creating a user account / home directory , etc on the actual system. 

Even still, there are some GUI interfaces for commonly used server applications, I am sure if you google them you will find something for samba. However, you will notice if you delve into the GUI vs what the command line can offer you will find the GUI significantly neuters the functionality of the underlying application. 

I think it is important to realize that functionality and ease of use do not always go hand in hand. For the most part Ubuntu GREATLY simplifies many common tasks. However, once you start delving into the world of networking  in order to maintain the stability, security, and functionality that large networks demand you have to shy away from ease of use to an extent.

In all reality while the learning curve may seem a little steep, the rewards in mastering the command line and actual methodology behind configuring, securing and properly maintaining your own server far outweigh the effort you put into understanding the procedure in the first place.

Example of what I'm talking about  : [http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux](http://ubuntuguide.net/createmodifydelete-samba-shares-with-system-config-sambagui-in-ubuntu-linux)

---

### Post by drdos2006 on 2011-06-26
There is a GUI for Ubuntu server called Webmin which I use every day. I have my Ubuntu desktop with 4 Gig of RAM so I can use Virtualbox and Webmin to develop my web and CMS pages with MySql.

The width and breadth of what Ubuntu server can do is far more than what you are implying. However to be able to access the width and breadth of those services does require some basic knowledge of servers and server security, networking, router configurations etc.

 Perhaps this might help. 
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop and run the server as a virtual machine using Virtualbox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by tgalati4 on 2011-06-26
Ubuntu server works well, but you have to know what you are doing.  There is not the same level of GUI/interface/admin-tools that Ubuntu has worked on for the Desktop.  So the expectation that Ubuntu server has the same level of user-friendliness is sadly mistaken.

If you know the linux command line interface (CLI) and you know about basic server administration tasks using the CLI, then Ubuntu server is a solid distro.

There was an ubuntu homeserver project a few years ago, but it fizzled.  Check out freenas if you want a clean interface:

[http://freenas.org](http://freenas.org)

---

