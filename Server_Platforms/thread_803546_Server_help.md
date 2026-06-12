---
title: "Server help"
date: 2008-05-22
forum: Server Platforms
---

### Post by CodeCruncher on 2008-05-22
I have installed ubuntu server and then installed the gui for the desktop.

Can i not add files to the server from there and controll the server. Hell I cant even find the htcos folder to add my site to.

Yes I'm very new to Linux!

---

### Post by cdtech on 2008-05-22
Sure you can.

> Hell I cant even find the htcos folder to add my site to
Hell, it aint windows:
In a terminal, type /var/www, thats your site directory.

Learn the command line, thats what GNU/Linux Server edition is all about.

If you need practice, why don't you just use the desktop version to learn on?

---

### Post by CodeCruncher on 2008-05-22
> **cdtech said:**
> Sure you can.


Hell, it aint windows:
In a terminal, type /var/www, thats your site directory.

Learn the command line, thats what GNU/Linux Server edition is all about.

If you need practice, why don't you just use the desktop version to learn on?

Yes I know this isn't windows thats why I asked here and not a windows form. A simple ---> hey man the web servers home dir in Linux is /var/www---> would have been great!

I'm trying to learn this that's why I'm asking to questions. If we all already new everything there would be no reason for this forum.

I installed the server edition because i need a server and I want to learn Linux.


So now back to my issue if anyone else could help. There is no /www under the /var directory.

When i look in the System monitor and processes I don't see Apache running. In firfox I type localhost I get site not found. When I installed the GUI from the server command line I rebooted to the desktop. When doing that will the server start on it's own? Will the server even run while in the desktop????

Thanks for any help----> Yes I'm very green to Linux:lolflag:

---

### Post by NateMan on 2008-05-22
The server should keep running while your running a desktop. I do believe that you may have taken a wrong turn on your design of your server. If you want to learn how to really setup a linux/ubuntu server, why don't you take a look at this guide: [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) . I use it to setup all of my servers and it works fantastic. However there are a few things I like to install that it doesn't mention, in particular webmin. Its a web-based GUI for a linux server. It runs really well and allows you to graphically edit all of the (at least to new users) confusing config files. Webmin can be install very easily by downloading it and running dpkg --install whateverthewebminnameis . Here's the webpage for webmin: [http://www.webmin.com/](http://www.webmin.com/) . Download the .deb file for easy ubuntu installation. If you have any questions with any of that I'd be glad to help. Servers with desktops aren't worth it. Webmin and ssh can do everything I can do with a GUI desktop, and it runs sooo much lighter < 100MB of ram usage. Hope that helps!

---

### Post by CodeCruncher on 2008-05-22
Hey NateMan thanks for the help! I'm going to reformat ad start a new install and follow your directions.:guitar::guitar::guitar:

---

### Post by NateMan on 2008-05-22
No problem. You'll hear people on here complain about how the perfect server guide enables root, but its not really a big deal. Every major enterprise linux server setup I've seen uses root, so just don't leave any huge security holes and its not a problem. Plus if you use a strong password there isn't really any danger. Always a random series of letters, numbers and symbols. It would take take a VERY long time to try to brute force it.

---

