---
title: "Apache and vsftpd security question"
date: 2007-01-20
forum: Server Platforms
---

### Post by Bruneauinfo on 2007-01-20
i set up a LAMP server using ubuntu 6.10 alternate install disk, desktop. works awsome and it's easy to manage. i set up a closed forum for my company using Simple Machines Forum software and dropped it right in the /var/www folder since i'm not trying to run a web site on the server. i also set up vsftpd so that i can have an ftp server for a few users and to make things easier for backing up the contents of /www from home and other locations.

now i've added a folder in /www - say it's called /var/www/td

i created a group that owns the folder 'td' and created users and gave them passwords so that they can get to that folder via ftp. they create a single file called index.html and put it in that folder and now all an employee has to do is type the url for the forum and add /td on the end and they can see the index.html file from their browser (which just happens to be the daily schedule for the company.)

problem is that i've give "td" 775 permissions and the www folder and several of the folders in the forum also need 775 permissions so the forum will work. this leaves the forum files and folders suceptible to the owners of "td" since they can SmartFTP into their folder and navigate into the forum folders and add and change them.

so is there a workaround someone can offer to keep the owners of "td" out of the /www folder without building a second server??

thanks

Tim B.

---

### Post by kidders on 2007-01-21
Hi there,

> **Bruneauinfo said:**
> problem is that i've give "td" 775 permissions and the www folder and several of the folders in the forum also need 775 permissions so the forum will work. this leaves the forum files and folders suceptible to the owners of "td" since they can SmartFTP into their folder and navigate into the forum folders and add and change them.I'm not quite clear on why the group that owns the "td" folder needs write permissions on its parent. I *think* that's what you've described, but maybe I've missed something. :confused:

---

### Post by Bruneauinfo on 2007-01-21
it's my understanding that Simple Machines Forum needs write permissions on certain folders in the directory where it resides. in my case i put it in the /var/www folder. this is where apache looks to find the index.html file when a person navigates to the server's IP with a browser. but since i don't have a web page i just dropped the forum into /var/www with all of it's folders and files. 

problem is that now i want to let someone in our company have a web page just for posting the daily schedule. so i created a folder called "td" in the /var/www folder and created a group and gave them ownership of that folder. however, when they log in with SmartFTP it takes them to "td" but also allows them to navigate upwards in the directory tree to www and it lets them create folders there and most likely delete them as well. 

so what i'm asking is probably impossible to avoid without creating a sepaerate web server OR without learning how to configure Apache.

---

### Post by kidders on 2007-01-21
> **Bruneauinfo said:**
> it's my understanding that Simple Machines Forum needs write permissions on certain folders in the directory where it resides.That's fairly common, although the only user that needs write access is the one the forum scripts run as, which I suppose you can find by experimentation, if you don't know it already.

I still feel like I'm missing something though ... As far as I can tell, you want /var/www/td to be writable by a certain group of users, but I don't see why that impacts /var/www. :-(

/var/www directories typically only need world execute permissions to function properly. If you want a script (like your forum) to be able to write there, that normally means you need to grant write access to one additional user. In octal terms, like you used in your o/p, that equates to /var/www = 701, which would prevent anyone but the directory's owner seeing the contents, let alone writing to it. In any case, you should check the specific requirements for the forum app you're using.

> **Bruneauinfo said:**
> so what i'm asking is probably impossible to avoid without creating a sepaerate web server OR without learning how to configure Apache.Well... learning to configure apache is pretty important too!

I hope that's at least *somewhat* helpful ... Sorry if I've misunderstood something.

---

