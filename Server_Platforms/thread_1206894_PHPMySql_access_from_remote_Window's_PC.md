---
title: "PHP/MySql access from remote Window's PC"
date: 2009-07-07
forum: Server Platforms
---

### Post by WASHAD on 2009-07-07
Hello all;

I'm proud to say I have completed my first Server install, and sucessfully get the "It Works" message from index.html. 

I'm quitely trying to set-up a Server for the company I work for, to save machine run data and such. My question is this; 

1. Given that I only have a Windows(TM) PCs to work with, can I do my PHP and MySql programming remotely? I'm afraid that I still need the GUI crutch for development. What would be the best way to do this?

2. If the above option is too difficult, would bringing my personal laptop (Ubuntu installed) make it more feasable? The question would still remain as to the best way.


I'm sure that there are tutorials for doing this, I just don't know the right keywords to search for. If someone could give me just a high level overview of how do do this, you would have my thanks. 

SteveJ

---

### Post by Kolipoki on 2009-07-08
Hihi. Well I'm not totally sure of what would be your PHP/MySQL editing needs. Nonetheless, I (for now) connect to my Ubuntu Server through a Win machine, using WinSCP. It will work just as an FTP client (SFTP rather, more secure), letting you edit files remotely.

For this option you will need to install the SSH server:```
sudo apt-get install ssh openssh-server
``` Then install WinSCP in your Win machine and use the port# 22 (you can change this later, if you want to.) 

Also, for editing MySQL, you can use PHPMyAdmin:```
sudo apt-get install phpmyadmin
``` You can then browse to [http://yoursite.com/phpmyadmin](http://yoursite.com/phpmyadmin) and log into the application (https would be better if you can set it up).

Hope this helps...

---

### Post by wojox on 2009-07-08
WinSCP

+1

---

### Post by WASHAD on 2009-07-09
> You can then browse to [http://yoursite.com/phpmyadmin](http://yoursite.com/phpmyadmin) and log into the application (https would be better if you can set it up).


OK, thanks - I installed phpmyadmin. When I connect via http, though, it tells me that I cannot connect to the database. . 

> #1045 - Access denied for user 'localhost'@'localhost' (using password: YES)

I login to mysql on the server with the command: "sudo mysql -p". I notice that when I try to login with "sudo mysql -h username -p", the login fails. I wonder if that has anything to do with it? Should the user be the same username that I use to log into the Server?

Thanks, 

SteveJ

---

### Post by WASHAD on 2009-07-09
Ok, I got it. I follow the steps at this link..

[http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html]("http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html")

---

### Post by Stephen_at on 2009-07-10
There is a version of TOAD which works with MySQL and its free to download.

If you want to work on PHP files then I'd use something like WINScp to copy the files back and forward and edit them on your PC.

Or if you install a GUI on your server (and then turn it off in the run level editor so it doesn't run all the time) then you can install NXServer on your server and the NXClient on your PC and when you login through that it gives you a full KDE/Gnome/whatever desktop running from your server, but when you terminate the connection it closes down the X server on the server.

---

### Post by WASHAD on 2009-07-12
Thanks all, I working with phpandmin now and WinSCP looks like it will do the trick. I really appreciate the help. 

> Or if you install a GUI on your server (and then turn it off in the run level editor so it doesn't run all the time) then you can install NXServer on your server and the NXClient on your PC and when you login through that it gives you a full KDE/Gnome/whatever desktop running from your server, but when you terminate the connection it closes down the X server on the server.

I'm interested in exploring this, but I'm going to start it in another post as not to complicate this one any further. For the purpose of my original question, I think that the post is solved. 

I thought that there was a way to mark a post as solved, but I don't see how to do that. Am I just blind?

Thanks again for all of the help.

---

### Post by WASHAD on 2009-07-14
Thanks so much, Kolipoki, for your help on this. To recap, for others reading this post, here are the steps I finally used. 

For remote control of MySql

1. First I had to grant access to the database at the Server (command line). See link in one of my other eclosed posts. 
2. Then I installed phpmyadmin [see Kolipoki's reply]
3. Then, on my Window's(TM) browser I typed in the Server Ip/phpmyadmin and my login window appeared.
4. I typed in the user name and password from step 1, and it worked. 


To be able to FTP my PHP files to the server

1. Installed SSH [see Kolipoki's reply]
2. Installed WinSCP on my Window's(TM) machine. 
3. Setup WinSCP, using my server username and password. 
4. Am able to navigate my server folders like any other ftp site. 


Thanks again all, 

SteveJ

---

