---
title: "access to web server files"
date: 2011-07-24
forum: Server Platforms
---

### Post by geauxsaints on 2011-07-24
hello-
i'm new to Linux and have taken over at a company where the linux admin walked out.
he has several older linux based servers running version 8.1
 
i tried running the command sudo apt-get install swat xinetd to setup swat
but i get an error that it can't find the package.
 
in addition, this directory xinetd is no where to be found under the etc directory.
 
i've verified that samba is in fact installed on these servers but for some reason
the xinetd and inetd directories are not on these servers.
 
could it be possible that this older version of linux does not support Swat?
 
i'm considering upgrading very soon to the latest but my main problem right now is
i need to copy all web server html files that he had on the web Server
 
i know there are different ways to copy files from linux systems but need the best way to copy all the files
so none of the website links get broke off this linux server over to my windows server.
 
 
since i don't have access to anything of the directories nor files on the web server,
what is the best way to copy these files and folders off this server?
 
thought SWAT would do the trick but i'm stuck b/c i can't get it initalized even though samba is running.
thanks
 
colin

---

### Post by Gyokuro on 2011-07-24
copy the files via **scp** or **rsync** from the server and swat should you get via **sudo apt-get install swat**. xinetd is not a directory its a daemon (application) and is managing internet connectivity

---

### Post by geauxsaints on 2011-07-24
thanks but i first have to get the directories shared-out via samba so i can see them from my windows pc.
i edited my smb.conf file but i'm having a problem mounting the share.
 
i am using version 8.1 which is old so when i try the mount command on the directory that i want to be visible and accessible;  i'm getting errors.
 
what is the command syntax for 8.1 to mount a share on the root of my linux server-
i've tried :  mount -t smbfs data
 
where data is the directory on the root of the server that i created but it errors -out.
 
thanks

---

### Post by geauxsaints on 2011-07-24
> **geauxsaints said:**
> thanks but i first have to get the directories shared-out via samba so i can see them from my windows pc.
i edited my smb.conf file but i'm having a problem mounting the share.
 
i am using version 8.1 which is old so when i try the mount command on the directory that i want to be visible and accessible;  i'm getting errors.
 
what is the command syntax for 8.1 to mount a share on the root of my linux server-
i've tried :  mount -t smbfs data
 
where data is the directory on the root of the server that i created but it errors -out.
 
thanks
like i said-  this is my first day working on linux
but i finally got the shared directory i created to be accessible from my windows 7 PC.
 
Next question i have is i need to share and / or copy ALL of the Web site files from this linux box
over to my external hard drive connected to my computer.
 
do i need to "share" the folder where the html files are stored and if so- what might that be ?(/etc/apache2/sites-available ??
 
is there a sure-fire way of copying these files so no links get messed-up because i'll be shutting down this Server to decommission in a day and need to move the web site to an off-site Hosting company
like go daddy but want to be sure when i copy them-  i don't get incomplete files and directories.
 
thanks

---

### Post by Gyokuro on 2011-07-25
Hi,

cool - you have to check were the sites got stored and then you copy them to your share. I think as you wrote you have edited smb.conf you have a shell account on the server - to be on the safe site I would copy the whole /etc/apache2/ directory to your share and afterwards check what's in /var/www or whatever directory got mentioned in the apache configuration files and copy that directory also on your share. You should find this information in /etc/apache2/sites-enabled/ and /etc/apache2/sites-available/

---

### Post by geauxsaints on 2011-07-25
GyoKuro,
 
Thanks for the tips.  Being new to an O.S. is challenging but i'll continue to learn and get more comfortable w/ the CLI.
 
Colin:KS

---

### Post by drdos2006 on 2011-07-25
You might find it easier to maintain the server via a Web Interface.

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###  	web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by geauxsaints on 2011-07-25
> **drdos2006 said:**
> You might find it easier to maintain the server via a Web Interface.
 
```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb
###      web site is here: http://sourceforge.net/projects/webadmin/files/webmin/1.550/webmin_1.550_all.deb
Install with :
sudo dpkg -i webmin_1.550_all.deb
 
Add extra libraries with :
sudo apt-get -f install

```
 
regards
 
 
Thanks so much-
i'll give this a shot.  anything to make it easier for me to maintain till
i get up to speed with Linux.
 
Colin

---

