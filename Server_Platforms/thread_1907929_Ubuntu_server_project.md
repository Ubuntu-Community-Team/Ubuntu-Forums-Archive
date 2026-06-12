---
title: "Ubuntu server project"
date: 2012-01-12
forum: Server Platforms
---

### Post by HackOmikron on 2012-01-12
Hi everyone, I'm currently trying to configure my first server installation to do a few things but I'm not sure how exactly to accomplish it.  Please have a look and let me know if you can suggest anything.
 
Most of my issues stem from not knowing all the commands, but I'm working on that.
 
Here is my to-do list:
 
1.  I need to change the listen port for SSH connections to 5837
2.  I've installed apache, but now I need it to display an index.html file when my server is accessed via a web browser.
3.  I've installed ebox, but I have no clue how to configure it to allow administration through it.
4.  I've installed Samba, but again, have no clue how to configure it.
 
If anyone could offer some help, that would be awesome.  Thank you all!

---

### Post by teward on 2012-01-12
I can help you with the SSH thing.

If you installed `openssh-server`, then find the file `/etc/ssh/sshd_config` and edit it as superuser: `sudo nano /etc/ssh/sshd_config`

Modify the sshd_config file's Port lines so that they only say:

Port 5837

Then do: `sudo service ssh restart`.

That will fix your SSH port up.
(NOTE: DO NOT type the ` characters, i'm using those to denote commands, file paths, etc. in this post only)


As for the other parts of your question, i'll let someone more knowledgeable in those areas help you.

---

### Post by KdotJ on 2012-01-12
> **HackOmikron said:**
> 
2.  I've installed apache, but now I need it to display an index.html file when my server is accessed via a web browser.


I'm pretty sure this is done by default when you first setup the server. Start the apache server with the command:

```
sudo service apache2 restart
```

Then open a web browser, in the URL bar type "127.0.0.1" without the quotes. It should display a page that says something like "**It Works!**". This file will in the in apache2 root folder for webpages (which by default is **/var/www**) and you can edit it to your heart's desire, this is where you place your website stuff.

> **HackOmikron said:**
> 
4.  I've installed Samba, but again, have no clue how to configure it.

To set it up, you need to edit the samba config file, which is located at **/etc/samba/smb.conf**. The Samba page on the [Ubuntu wiki]("https://help.ubuntu.com/community/Samba/SambaServerGuide") explains how to set up directories and share them over samba.

---

### Post by HackOmikron on 2012-01-12
Kdot, your signature is amazing lol

---

### Post by KdotJ on 2012-01-12
> **HackOmikron said:**
> Kdot, your signature is amazing lol

Lol thanks, it's from a small comic strip I saw a while back.
Did you have any more luck with your server?

---

### Post by HackOmikron on 2012-01-12
Yes, everything you guys advised is working great.  Just ebox left and I think I'll be set!

---

### Post by HackOmikron on 2012-01-13
Hey guys, sorry for the bump.  Just wondering if anyone had some insight into the ebox configuration?
 
Thanks

---

### Post by nothingspecial on 2012-01-13
Moved to Server Platforms.

---

### Post by drdos2006 on 2012-01-13
Have you installed Zentyal ? It uses a web interface to set up shares and configuration files etc. 

ebox is renamed Zentyal and is based on Ubuntu 10.4 Long Term Support last time I checked.

regards

---

### Post by SeijiSensei on 2012-01-13
You might also consider installing [Webmin]("http://www.upubuntu.com/2011/09/how-to-install-webmin-on-ubuntu.html").  It lets you manage the server via a web browser.  If the server is exposed directly to the Internet, you need to ensure that Webmin can't be seen by arbitrary remote browsers.  If you're logged directly into a server behind a firewall in a trusted network, Webmin is an excellent tool.

---

### Post by HackOmikron on 2012-01-18
I haven't been able to find anything on Zentyal.. but my issue with ebox is that I don't understand how to configure it.  All I've been able to do is install it.  Is there a config file I need to find and edit?

---

### Post by rubylaser on 2012-01-18
> **HackOmikron said:**
> I haven't been able to find anything on Zentyal.. but my issue with ebox is that I don't understand how to configure it.  All I've been able to do is install it.  Is there a config file I need to find and edit?

Have you looked at the [documentation]("http://doc.zentyal.org/en/"), that provides step-by-step instructions for almost everything from install to configuring all of it's services.  The configuration is all done with a web browser.

---

### Post by drdos2006 on 2012-01-18
Then you should look here. 
This is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings. Based on Debian with very minor changes for Ubuntu and ebox.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage: [http://woodel.com](http://woodel.com)

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

Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons, control PostgreSQL etc..

regards

---

### Post by HackOmikron on 2012-01-24
Hi everyone, just wanted to update and let you know that everything is working great.  I now have everything installed and working.  Thank you all for your help and for bearing with my noobishness :)

---

