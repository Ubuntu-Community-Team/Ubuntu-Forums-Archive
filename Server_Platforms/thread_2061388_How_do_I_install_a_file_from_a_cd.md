---
title: "How do I install a file from a cd?"
date: 2012-09-22
forum: Server Platforms
---

### Post by Extol11 on 2012-09-22
I currently don't have internet at home. So I took my PC to my friend's house and installed everything I needed to make it a server... Everything except the php5 apache module. I installed PHP5 but the CLI. I did manage to download the Ubuntu 12.04.1 image while I was there anyways. So I was thinking there has got to be a way for me to install that module from the cd instead of the repositories. Could anyone help me out with that? I'll check back tomorrow. Thanks in advanced for any help.

---

### Post by drdos2006 on 2012-09-22
The files are located in /pool/main/p/php5

From your server you would run :

sudo dpkg -i /<cd-name>/pool/main/p/php5/<required-package>.deb

The -i is for install.

Have you installed Webmin on your server ?

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
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to your server to edit files, create shares, startup daemons etc..

regards

---

### Post by matt_symes on 2012-09-22
Hi

You could add the Ubuntu CDRom to your sources file if it is not already there. Take a look at 

```
man apt-cdrom
```This will automate adding an entry for you.

Something along the lines of

```
sudo apt-cdrom add
```

You should then be able to install software using apt.

Kind regards

---

### Post by Extol11 on 2012-09-24
I'll try this later today. Thanks for helping me out, I'll let you know how it worked.
Edit: And yes, Drdos2006. I know how to install webmin. It rocks.

---

