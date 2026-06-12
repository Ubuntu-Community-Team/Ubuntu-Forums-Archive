---
title: "Ubuntu 9.10 Secure Web Server Help Needed"
date: 2010-05-03
forum: Server Platforms
---

### Post by gtrguy63 on 2010-05-03
Hello all,
 
I am new to Ubuntu and am trying to setup a simple, but secure, webserver that will be used to host a public vBulletin forum. My network consists of the Ubuntu machine and a Windows 7 PC.
 
My current Ubuntu test machine has the following installed:
32 bit Ubuntu Server 9.10
Xubuntu GUI (for now)
LAMP Server
Open SSH
Samba
PHPmyAdmin
 
I am trying to learn how to setup and operate everything without a GUI, but am using the GUI to get to know the operating system. 
 
I have figured out how to modify all the config files but have not found an easy (and secure) way to manage the website files in /var/www without the GUI. I would like to eventually remove the keyboard, monitor, and mouse, and operate the server from my Windows 7 PC.
 
Questions:
1. Is there a secure way to share the /var/www folder using Samba?
2. Can I copy files from the windows machine to /var/www using SSH? If so how?
3. Can I plug a USB stick in the server and copy the files from it using SSH?
4. Is there an easier way to manage the directory?
 
Thanks in advance.

---

### Post by dudumomo on 2010-05-03
Hello gtrguy63,

1) Yes you can do it with samba. Or if you prefer, you can share folder with SFTP.
2) Yes you can copy folder or file with SSH with the command: scp
Example: 
scp -P 2222 /Where/It_is/ontheclient [email]user@192.168.my.IP[/email]:/Where/I/Want/ontheserver
(-P 2222 to use the port 2222)
In my case:
scp -P 2222 /home/morgan/Desktop/Server_status.html myuser@192.168.1.199:/var/www/freelydifferent/

and to download a file from your server to your computer:
scp -P 2222 [email]user@192.168.my.IP[/email]:/Where/It_is/on_the_server /Where/I/want/on_my_computer

3)Yes you can, you will have to mount the pendrive:
By example, create a folder pendrive in mnt (sudo mkdir /mnt/pendrive)
then mount your pendrive
sudo mount /dev/sda2 /mnt/pendrive
if you pendrive is located in /dev/sda2

4) I don't really know what you are looking for...
What are you needs ?

If you want to check some tutorials, here are mine:
[http://www.freelydifferent.com/self-hosting/self-hosting-for-dummies/](http://www.freelydifferent.com/self-hosting/self-hosting-for-dummies/)

---

### Post by gtrguy63 on 2010-05-03
Thanks for the quick reply dudumomo.
 
Awesome tutorials on your website.
 
Samba would be the easiest way for me to work with the files, how would I set the sharing rights on the /var/www folder without causing a security risk? I have left the folder locked down with the default rights and have been running the graphical file manager as root via sudo to copy files into the folder. I am fine with having to enter a user ID and password when accessing the folder.

---

### Post by dudumomo on 2010-05-03
I haven't used samba for a while, so I don't really know how it works in detail... I might not be able to help you.
(But I should try and post a new article on my blog :D)

---

### Post by Jive Turkey on 2010-05-03
> **gtrguy63 said:**
> Hello all,
 Questions:
1. Is there a secure way to share the /var/www folder using Samba?
2. Can I copy files from the windows machine to /var/www using SSH? If so how?
3. Can I plug a USB stick in the server and copy the files from it using SSH?
4. Is there an easier way to manage the directory?
 
Thanks in advance.

1. Yes, make sure that only trusted hosts can connect to the samba share, and only over your LAN, not from outside.  The directive might look something like this (in /etc/samba/smb.conf)
```
[webroot]
   comment = document root on webserver
   path = /var/www
   valid users = yourusername
   read only = No
```
You should then firewall it or restrict it in hosts.allow/deny as well.  The smb.conf also accepts global directives to restrict access, like:```
hosts allow = 127.0.0.1, 10.0.0.0/24
```

The ssh/sftp protocol is better if you want to edit this stuff from outside your LAN.

2. Yes, some people swear by winscp, I havent used it myself.  I prefer filezilla using sftp (ssh).

3. Yes just like you would on a local machine.  You should get familiar with the commands "cd" "mount" "ls" "rm" "cp" and "mv" eventually you will start using "cat" "grep" "tail" and countless others, google for examples.

4.  I have found it crucial to be mindful of the ownership and permissions of the files, its helpful to know that apache acts as the user "www-data", I usually set ownership to www-data user and my username's group.  There are some nice guides around the web for linux file permissions you should look into if you haven't yet.

---

### Post by gtrguy63 on 2010-05-04
Thanks for the great information, it has been very helpful.
 
I think I am going to go with SSH since I now know that I can use Filezilla to manage files. I am now trying to figure out the correct permissions for the /var/www folder in order to copy, edit, and set permissions in this directory with Filezilla.
 
I found this document, which seems to work well:
 
[http://joomla-and-more.com/2009/10/28/how-to-set-rights-for-varwww-when-using-apache-under-ubuntu/](http://joomla-and-more.com/2009/10/28/how-to-set-rights-for-varwww-when-using-apache-under-ubuntu/)
 
Would someone please review this and let me know if this process is secure for a public web server, I am concerned with giving 775 permissions to this folder, 774 seems to work but I am not sure if even that is safe?
 
Also, what is the purpose of "sudo chmod g+s" and is it needed?
 
Thanks again.

---

### Post by Toretto on 2010-05-05
> **gtrguy63 said:**
> Thanks for the great information, it has been very helpful.
 
I think I am going to go with SSH since I now know that I can use Filezilla to manage files. I am now trying to figure out the correct permissions for the /var/www folder in order to copy, edit, and set permissions in this directory with Filezilla.
 
I found this document, which seems to work well:
 
[http://joomla-and-more.com/2009/10/28/how-to-set-rights-for-varwww-when-using-apache-under-ubuntu/](http://joomla-and-more.com/2009/10/28/how-to-set-rights-for-varwww-when-using-apache-under-ubuntu/)
 
Would someone please review this and let me know if this process is secure for a public web server, I am concerned with giving 775 permissions to this folder, 774 seems to work but I am not sure if even that is safe?
 
Also, what is the purpose of "sudo chmod g+s" and is it needed?
 
Thanks again.

Hey, glad to see you found my blog post - somewhat - useful.  I'm not an Ubuntu specialist; but I've done some experimenting since that particular post; and I don't think that the sudo chmod g+s command is neccessary.

Your permission concern is valid; but again: I'm no Ubuntu specialist and just proposed permissions "that work".  I'm sure the specialists here will be able to tell you what permissions are better to use.

---

