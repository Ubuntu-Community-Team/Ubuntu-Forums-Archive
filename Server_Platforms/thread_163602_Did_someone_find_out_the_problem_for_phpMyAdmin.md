---
title: "Did someone find out the problem for phpMyAdmin?"
date: 2006-04-21
forum: Server Platforms
---

### Post by rensu on 2006-04-21
phpMyAdmin 2.6.4-pl1-Debian-1ubuntu1
PHP5, Apache2, MySQL5
I can log from console into mysql but I can't login from web with phpMyAdmin.](*,) 
Tried to login with root, username and password are right!
Getting this error:
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
Did anyone find out a solution for this problem?
Tried to change in config.inc.php:
$cfg['Servers'][$i]['host']          = 'localhost';
to
$cfg['Servers'][$i]['host']          = '127.0.0.1';
That didn't help:(
Putted a socket into this line:
$cfg['Servers'][$i]['socket']        = '/tmp/mysql.sock';
Nothing didn't work!
For last changed the connection_type to:
$cfg['Servers'][$i]['connect_type']  = 'tcp';
And that too didn't work](*,) 
Can someone help me?:confused:

---

### Post by rensu on 2006-04-22
Any information about that problem ?:confused:

---

### Post by adamkane on 2006-04-22
How did you install apache/php/mysql/phpmyadmin?

phpmyadmin works with apache2/php4/mysql4. If you want to use phpmyadmin with php5/mysql5, then you have to install phpmyadmin from source.

Give more details.

---

### Post by rensu on 2006-04-22
Uh installed php5,apache2, phpmyadmin with apt-get and mysql5 manually :( should I install phpmyadmin manually ?:confused:

---

### Post by adamkane on 2006-04-22
apache/php/mysql/phpmyadmin is very difficult to install and maintain. I still use apache2/php4/mysql4/phpmyadmin, so the only help I can offer is to suggest you find a useful howto or guide, and follow it to the letter. 

Don't deviate, until you've gathered experience with apache/php/mysql/phpmyadmin.

I don't know if this helps:
[https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

If you need more help, just keep bumping your thread once a day. There are knowledgable people who can help, but this situation comes too frequently to respond every time it comes up.

Also, once you install a particular version of apache/php/mysql/phpmyadmin, it is extremely difficult to uninstall and install a different version. Be prepared to completely re-install Ubuntu, if you make the wrong choice.

---

### Post by rensu on 2006-04-24
Nevermind, I just removed everything and installed XAMPP and some other stuff. Didn't find a solution for that problem. It's pretty hard to find one if you have installed with apt-get and some programs manually. I give a advice to install everything with apt-get or everything manually.

---

### Post by adamkane on 2006-04-24
Troubleshooting is even more difficult with XAMPP.

Install apache2/php4/mysql4/phpmyadmin if you want ease of installation/maintenance:
[https://wiki.ubuntu.com/ApacheMySQLPHP]("https://wiki.ubuntu.com/ApacheMySQLPHP")

Just a suggestion.

---

### Post by TreetopClimber on 2006-04-24
Thanks for the link ;) , But I am new to ubuntu and linux period. How do I get to comand prompt like in windows, or the terminal to install these programs? I have tried to use my root name and password at login but it wont take it only the user name and password for the desk top?

.... Instead of making a double post I will just use this. A good friend in the UK told me I should use ubuntu for my website instead of windows server which I already have. I have replaced it with ubuntu 5.10 and I have no idea what to do. He told me when installing it to just click the enter then use multiseat, so I did. It is fully loaded as far as I know, but I dont know how to get the apache2, php4, mysql4, & phpmyadmin installed, these are the basic things I need installed for my site to work, he mentioned apt-get but again I have no clue. Please if anyone can help I would be very thankful, greets TT

---

### Post by rensu on 2006-04-25
There are many ways but the easiest way is to install them with apt-get. Apt-get will install and configure most of stuff for you. You will need only change some stuff if it's needful. I would recommend you to use apt-get. Try man apt-get. Search arround in this forum and will find some webs where are some instructions for installing them. In the link he gave you should install everything.

---

### Post by TreetopClimber on 2006-04-25
Thank you for your quick reply. Out of pure luck last night I figured out how to install these things, I found that by going through applications/ system tools/ terminal on the ubuntu desk top I was able to use that links dirrections on how to install apache2, php4, mysql4, & phpmyadmin. Now my only problem is on how to copy my files to the proper folder for use on my site, with windows it was easy just put them on a disk and copy them over to the server via the cdrom, I have tried that with this and it tells me I dont have permission to write in these folders (I dont own them) bull, I do I just dont know how to fix this. Another thing is my ubuntu pc and my windows pc are on the same IP so I dont believe I can ftp them to my server shell... or can I? Or how do I fix this ownership issue?

---

### Post by rensu on 2006-04-27
Try to do command with sudo, so you can copy everything. And actually for changing permissions is command <chmod> if need some help for this command, use man chmod. For example chmod 777 folder, this will set permissions that will allow people to do everything with the file. Better read or find out what do mean the numbers before changing chmods. Ownership of the file you can change with chown, for help look man <chown>. For example sudo chown user.user foldername_you_want_to_change. Hope this helps you. Sorry for delay.

---

### Post by TreetopClimber on 2006-04-29
rensu I started a new thread on this subject here > [http://ubuntuforums.org/showthread.php?t=166176](http://ubuntuforums.org/showthread.php?t=166176)
Maybe you could post there and help me, there are a couple of others trying as well. I started it there cuz I figured I wouldnt get any other replies from this board. Thanks for your help too.
instead of a double post
> Better read or find out what do mean the numbers before changing chmods.
I do know what these are and how they are used.
The web site stuff isnt new to me just linux is or using it like this. I have had my site hosted for me in the past under a different name. Now I want to host it and my friend said ubuntu was easy to use and learn from so that is why I am using it or trying to use it. 2 things in question tho are > for help look man <chown> So in terminal what do I type? And > sudo chown user.user foldername_you_want_to_change
what is meant by user.user? Would that be like root.root or admin.admin?

---

