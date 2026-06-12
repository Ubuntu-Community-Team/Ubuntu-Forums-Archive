---
title: "Fresh Server"
date: 2011-07-19
forum: Server Platforms
---

### Post by serverMe on 2011-07-19
Hello,

I just install a new server and I would like to now what are the basics that I should install. It currently has LAMP stuff. Any one know how are the VPS server configured at hostgator.com and similar web hosting platforms. 

Please let me know.

---

### Post by Lars Noodén on 2011-07-20
What do you want to use the server for?  Tell us more about the planned activities and that will determine what applications you can choose.

---

### Post by rubylaser on 2011-07-20
Hostgator uses [CPanel]("http://www.cpanel.net/") AFAIK.  You're not going to want to pay for a license for that, so if you want a web interface to manage your server, I'd suggest [Webmin]("http://woodel.com/").

---

### Post by serverMe on 2011-07-20
Hey guys thanks for the respond.

I am using it for hosting Kaltura - open source video platform. [http://corp.kaltura.com/](http://corp.kaltura.com/)
Please suggest if there are better platform I could use.

There will also be a wordpress installation and probably wiki.

---

### Post by serverMe on 2011-07-21
> **rubylaser said:**
> Hostgator uses [CPanel]("http://www.cpanel.net/") AFAIK.  You're not going to want to pay for a license for that, so if you want a web interface to manage your server, I'd suggest [Webmin]("http://woodel.com/").

Hello There,

Would you have any suggestions? Please let me know.

---

### Post by schnelle02 on 2011-07-21
If you already have your LAMP and SSH installed then run ```
sudo update
``` then ```
sudo upgrade
```  See how you have to type your password everytime....that gets annoying so type ```
sudo passwd root
``` and set a password for your root user.  Now you can log in as root.  Type ```
exit 
```then log in as root.

Now, your LAMP is completely updated and ready to go.  So follow this [tutorial]("http://www.ubuntugeek.com/webmin-installation-and-configuration-in-ubuntu-linux.html") to get Webmin installed.  Now you can access your computer via FTP client, Putty, or Webmin.

To get to webmin go to [https://12.34.56.78:10000](https://12.34.56.78:10000) or [https://localhost:10000](https://localhost:10000).
Now you can set your apache default to where you want, access and create new databases and all that fun stuff without using the command line!

---

### Post by drdos2006 on 2011-07-21
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

