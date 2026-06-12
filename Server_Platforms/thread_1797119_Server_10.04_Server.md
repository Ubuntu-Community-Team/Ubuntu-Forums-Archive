---
title: "Server 10.04 Server"
date: 2011-07-04
forum: Server Platforms
---

### Post by orionmz on 2011-07-04
Good day to all.
Am planning in deploying Ubuntu Server 10.04 LTS Server in my company. I´ld like to know if this version as a Grafical User Interface. My other IT stuff is are not familiar with Terminal and its commands. Thats why i´ld like to have a user graphical interface for a easy management of the server. 
Thanks in advance

---

### Post by arrrghhh on 2011-07-04
> **orionmz said:**
> Good day to all.
Am planning in deploying Ubuntu Server 10.04 LTS Server in my company. I´ld like to know if this version as a Grafical User Interface. My other IT stuff is are not familiar with Terminal and its commands. Thats why i´ld like to have a user graphical interface for a easy management of the server. 
Thanks in advance

No, there is no GUI with Ubuntu Server... that's kinda the point, lean and mean.

If you want a GUI, install Ubuntu Desktop (not the package, the full install).

This way you get a GUI without any fuss.  There are ways to add a GUI to Ubuntu Server, but honestly to me that seems like trying to shove a round peg into a square hole ;).

---

### Post by drdos2006 on 2011-07-04
Yes there is a GUI.

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

