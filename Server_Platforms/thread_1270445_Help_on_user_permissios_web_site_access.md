---
title: "Help on user permissios web site access"
date: 2009-09-19
forum: Server Platforms
---

### Post by TheRealRilo on 2009-09-19
I have read so many things, but still have found no answer to the following:

I have set up an Ubuntu Jaunty virtual server (VirtualBox) on my Ubuntu desktop, to use it as a web development environment. The problem is: I constantly get errors concerning access rights (access denied...). I changed owner to my account to all the folders use. I used /var/www, used the userdir module and even the websited transferred (via vsftpd) to that folder don't work. 

It seems like only the folders i create directly in the virtual server are accessable, but anythuing else isn't.

Furthermore, I even tried to use xampp, but installing it in /opt still gives me errors. I've read something about giving the apache user access, but the same article warned about security issues also.

Well, to make things short: I need a virtual apache/php/ftp serever for development and learning. And I need access to it. How do I set it up? (I've set it up, but how do I make it work?

Any hepl would be very much appreciated. I am not new to php, I know a little bit about linux, but I am still learning on Ubuntu and Apache.

Thanks in advance!

---

### Post by utnubuuser on 2009-09-19
Is there a particular reason why you're using "virtual"?  Installing LAMP in Ubuntu works ok.
> [http://www.lullabot.com/node/289]("http://www.lullabot.com/node/289")

---

### Post by TheRealRilo on 2009-09-21
Well, as I stated in my post, I tried using xampp. But the problems concerning access to the folders and subfolders remain. 
 
But besides that, I just want to use the virtual server, also for paractice.
 
Now,
 
I created the public_html forlder in the user's home dir (using the server's terminal) as the user (that way the user is owner right? I know that you can also set that using chow, but this also works)
 
Used vsftpd to copy the 'joomla15' folder to the public_ html folder (logged in as the user).
 
But navigating to ```
http://<ip-address_of_virtual_server>/~<username>/joomla15/
``` results in "permission denied"
 
So I presume that Apache does not have access to that joomla15 folder, but why do I not get that error when navigating to ```
http://<ip-address_of_virtual_server>/~<username>/
``` ??? It just gives me a direcory listing (empty).
 
Edit:
Changed permissions of all files and folders to 777 and, of course,  this works. Not exactly the most intelligent solution, but it will do for now. If anyone knows a good beginner-tutorial on the subject, please let me know!

---

