---
title: "Installing apps on the server"
date: 2005-10-12
forum: Server Platforms
---

### Post by bjornxon on 2005-10-12
Hi!
Im going to run a server at home with the Ubuntu 'server-install'. I'm new when it comes to Linux so please excuse my stupid questions.

What is the simplest way to download and install a ftp-, web-server etc when you dont have the graphical environment installed?  Am I supposed to use FTP to connect to a server and download it?  Can I use a webbrowser in the console or something?

Best regards
Bjorn

---

### Post by nocturn on 2005-10-12
[QUOTE=bjornxon]Hi!
Im going to run a server at home with the Ubuntu 'server-install'. I'm new when it comes to Linux so please excuse my stupid questions.

What is the simplest way to download and install a ftp-, web-server etc when you dont have the graphical environment installed?  Am I supposed to use FTP to connect to a server and download it?  Can I use a webbrowser in the console or something?

Best regards
Bjorn[/QUOTE]

Use aptitude (using sudo).

sudo aptitude update - gets the latest package list
sudo aptitude search <package> - finds packages
sudo aptitude install <packages> - downloads and installs packages with dependencies.

---

### Post by bjornxon on 2005-10-12
[QUOTE=nocturn]Use aptitude (using sudo).

sudo aptitude update - gets the latest package list
sudo aptitude search <package> - finds packages
sudo aptitude install <packages> - downloads and installs packages with dependencies.[/QUOTE]
Thank you! That sounds almost to easy to be true!

/Bjorn

---

### Post by nocturn on 2005-10-12
[QUOTE=bjornxon]Thank you! That sounds almost to easy to be true!

/Bjorn[/QUOTE]


LOL, it does.  Just wait until you ever have to install a windows server again, you get used to aptitude very quickly.

---

### Post by nocturn on 2005-10-12
One more cool trick.  Keeping your machine up-to-date/patched:

sudo aptitude update
sudo aptitude upgrade

Done.

---

### Post by wrtrdood on 2005-10-12
dpkg --list | grep <package>    --- to find what's already installed
    apt-cache search <package>   --- to find what's available 
    apt-get install/remove <package>  --- to install or remove the package


I use this all the time.  Also, you might want to check out screen.  It's a handy tool for servers.  You have one login but can switch between multiple "screens", giving you independent shells to work in.  Plus, if you get disconnected for some reason, your session is still there waiting for you.  Especially helpful in remote administration.

---

