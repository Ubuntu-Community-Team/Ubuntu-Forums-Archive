---
title: "new to Linux"
date: 2011-03-20
forum: Server Platforms
---

### Post by rareyush on 2011-03-20
hey guys
I am new in linux.
I just got the server of ubuntu and I connect it through putty ssh.
I am using windows xp and connect it via putty ssh.

[IMG]http://i.imgur.com/kshRf.png?4286[/IMG]


I want to upload zip file and install AjaXplorer, php 5.1 + zend optimizer.

I need your help guys
how to do that

---

### Post by rubylaser on 2011-03-20
You'll probably want to install WinSCP so you can have a GUI to transfer files and folders from.
[http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php")

This page has directions to setup AjaXplorer. Although, I hope chmoding the directory to 777 isn't part of the official documentation.
[http://www.thebuzzmedia.com/ajaxplorer-a-web-based-file-manager/]("http://www.thebuzzmedia.com/ajaxplorer-a-web-based-file-manager/")

---

### Post by rareyush on 2011-03-20
> **rubylaser said:**
> You'll probably want to install WinSCP so you can have a GUI to transfer files and folders from.
[http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php")

This page has directions to setup AjaXplorer. Although, I hope chmoding the directory to 777 isn't part of the official documentation.
[http://www.thebuzzmedia.com/ajaxplorer-a-web-based-file-manager/]("http://www.thebuzzmedia.com/ajaxplorer-a-web-based-file-manager/")

hey now I can upload files by  winscp.
now I just want to know how to install  php 5.1 + zendoptimizer + ioncube

---

### Post by volkswagner on 2011-03-20
If you don't want to download files twice (once to your workstation, then upload to server) you can use wget.  You can copy the download link then paste it in putty...

Change to the directory you want the file to be..

cd /var/www/new

or 

cd ~ if you want it in your home directory.

Then:
```
wget http://sourceforge.net/projects/ajaxplorer/files/ajaxplorer/3.2.1/ajaxplorer-core-3.2.1.zip/download
```

---

### Post by rareyush on 2011-03-20
> **volkswagner said:**
> If you don't want to download files twice (once to your workstation, then upload to server) you can use wget.  You can copy the download link then paste it in putty...

Change to the directory you want the file to be..

cd /var/www/new

or 

cd ~ if you want it in your home directory.

Then:
```
wget http://sourceforge.net/projects/ajaxplorer/files/ajaxplorer/3.2.1/ajaxplorer-core-3.2.1.zip/download
```

Thanx dude

but after saving that file 
when I typed the command apt-get install ajaxplorer-core-3.2.1.zip
then error comes
> E: Couldn't find package ajaxplorer-core-3.2.1.zip


---

### Post by volkswagner on 2011-03-20
> **rareyush said:**
> Thanx dude

but after saving that file 
when I typed the command apt-get install ajaxplorer-core-3.2.1.zip
then error comes


Ouch!

Some quick info.  I know you are new, we were all there once.... Your approach may differ.

apt-get install is a command for the included package manager.  When used it does not install local apps.  It will look at /etc/apt/sources.list for available packages, including the CD if enabled.

You should go to Ajaxexplorer site for install instructions.

You may want to to a little reading on apt-get, dpkg, zip, tar etc.

The file you downloaded is a zip file.  Once you unzip it, you can see the contents.  Most likely there will be install instructions and/or a README file.


You may need to install unzip.

```
sudo apt-get update
```

```
sudo apt-get install unzip
```

You will want to familiarize yourself with manuals (aka man pages).  For most any package or even command there are man pages available.

After installing unzip you can read the manual by running.

```
man unzip
``` 

You can page up/down and use q to escape/quit.

To unzip your downloaded file it would be like this:
```
unzip -x ajaxplorer-core-3.2.1.zip
```

---

### Post by rareyush on 2011-03-20
Thanx Guys
now I just want to know how to install php 5.1 + zendoptimizer + ioncube

---

### Post by stmiller on 2011-03-20
```
sudo apt-get install php
```

---

### Post by rareyush on 2011-03-21
hey guys 
how to install php5.3 in ubuntu server

---

