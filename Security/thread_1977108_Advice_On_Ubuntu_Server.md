---
title: "Advice On Ubuntu Server"
date: 2012-05-09
forum: Security
---

### Post by f07sa on 2012-05-09
Hi Guys,  I am a huge Ubuntu enthusiast but I'm only a novice... At work we only have Windows OS's Windows Server, XP et and we use Kaspersky for our network security/Network monitoring, I want to if possible install Ubuntu or a distro of Ubuntu on a spare server and find tools that can monitor/protect our network, the same tasks as Kaspersky. I would love to find a way to do so to impress the boss and to improve my knowledge in the IT world... I have noticed the amount of talent found within this forum so I thought this would the best place to come, if anyone could offer any advice I would be extatic.


All the best and thank you!


Chris.

---

### Post by drdos2006 on 2012-05-09
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

