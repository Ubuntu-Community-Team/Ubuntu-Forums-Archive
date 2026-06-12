---
title: "Seting up first server"
date: 2012-09-02
forum: Server Platforms
---

### Post by pcmichaelbrian on 2012-09-02
I am trying to install a server at work. This is an original server that is not replacing one. I am tring to set up all the basic needs to make things more efficient. I am trying to set 12.04 up to run as a pxe boot server, file server, and a print server. I have having dificulty getting started. Is there anyone who can give me some direction. :p

---

### Post by SeaHawk22 on 2012-09-02
I am doing almost the exact same thing at the moment (home server). I am a complete noob when it comes to servers, so take what I suggest with a grain of salt, but here is the turtorial I am using part 1 of 7 [http://www.youtube.com/watch?v=EMdWoM9b1m4&feature=plcp](http://www.youtube.com/watch?v=EMdWoM9b1m4&feature=plcp)

---

### Post by kennethconn on 2012-09-02
[https://help.ubuntu.com/12.04/serverguide/index.html](https://help.ubuntu.com/12.04/serverguide/index.html)

---

### Post by drdos2006 on 2012-09-02
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/webmin_1.590_all.deb
Install with :
sudo dpkg -i webmin_1.590_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to "https://your_server_IP:10000" to edit files, create shares, startup daemons etc..

regards

---

