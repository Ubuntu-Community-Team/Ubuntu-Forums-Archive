---
title: "How to setup Apache"
date: 2009-11-11
forum: Server Platforms
---

### Post by Stolea on 2009-11-11
My apologies in advance if this is not the correct forum.
I run a PHP based website for my business that is hosted on a server in the US.
The commercial template software is written in PHP and Dreamweaver.
We are in the process of rewriting some interface parts of the website and need to test the modifications before uploading them to the live website.
My setup here is 3 Computers on a network, 2 Ubuntu 9.04, 1 WinXP Pro. The plan is to setup the test server on a Ubuntu machine and do the Dreamweaver stuff on the XP machine. I have considered using Vbox on the same machine as the server, but am not really confident that this could work.
Basically I need to duplicate what happens the live website on my computer and make sure that everything is works before uploading the changes.
If I sound confused it is because I am way out of my depth here trying to do something that I don't really understand.

Question:
Where can I do some reading up on how to do this and maybe some good links.
Thanks in advance. I love Linux but there lots of things to learn.
Cheers

---

### Post by X-Rated on 2009-11-11
Install apache with php, install database if required.
Copy the whole directory structure of the website onto apache testing server.
Copy database structure if required onto testing server.

fire it up and see that it works, try access it via browser. you will probably need to change some stuff like database passwords and apache config files.

sorry if i'm a bit vague, but so is your question lol

---

### Post by Stolea on 2009-11-11
Thanks,
but I know that I have to copy my files and database off my server.
What I haven't got a clue about what I need to do to set things up on my computer. What I am looking for is a "How  To" for newbies, like Stormbringers how to for setting up Samba.

---

### Post by badger_fruit on 2009-11-11
I presume the existing website is on a remote server; in which can, use FTP to get onto it and make a local copy of the files.  I'll also presume you're installing Apache on your Ubuntu machine ...

Install Apache (I've only ever done this via Suse) and PHP onto the PC you want to be the test server.  Apache installs an INDEX.HTML in the wwwroot folder* which will advise if apache works or not.

*I think it's usually /srv/www/htdocs but reading /etc/apache2/httpd.conf will confirm.

If you're building the PHP pages on XP then you'll need to create remote access (FTP/Samba) to the wwwroot folder so you can upload the pages when done.  Although, Dreamweaver for PHP? Pah, Notepad for the win!!!

Useful links:-

[http://httpd.apache.org/](http://httpd.apache.org/)
[http://dev.mysql.com/](http://dev.mysql.com/)
[http://php.net/](http://php.net/)
[http://www.google.com/](http://www.google.com/)

Anyway, as for if the remote webserver is DB driven then consult the user-guide for that particular DB server, if it's mysql then you can get a nice PHP based interface to it which you can export the DBs and content into a single .SQL file which can be run and will create the schemas and content on another machine (also an ideal backup!)

Good luck!

---

### Post by Stolea on 2009-11-11
Yes my site is being hosted on a remote server which I acces via ftp. for file modifications. The products are in a MySql database which I backup on a regular basis.

I will have a read through the material on the links. Thanks.

P.S.
My friend who is doing the rewrite of the webpage design would agree with you about Dreamweaver and hard codes in something like notepad. She recons Dreamweaver creates a lot of useless code and is for pussies :)

---

### Post by gordintoronto on 2009-11-11
The default location for an apache web site is /var/www.

If you point a browser on another machine at the IP address of the machine running Apache, it should show you something useful, as soon as you install Apache.

---

### Post by mmlinx on 2009-11-11
install whole lamp server (Apache, Mysql, php) like this. 

**sudo apt-get install lamp-server^**

last character is magical, don't forget it. 

**Then browse to [http://localhost](http://localhost)**

to restart apache server use: 

**sudo /etc/init.d/apache2 [COLOR=Red]restart [/COLOR]  [COLOR=Red]  (or start or stop or reload)[/COLOR]**

same for mysql database:

**sudo /etc/init.d/mysql [COLOR=Red]restart [/COLOR]     [COLOR=Red] (or stop or start)[/COLOR]**

i would install phpmyadmin too for your mysql database config with web interface.

**sudo apt-get install phpmyadmin**

after restarting apache you will find phpmyadmin here : 
**[http://localhost/phpmyadmin](http://localhost/phpmyadmin)**

if not then make a symbolic link from /usr/share/phpmyadmin to /var/www.
 [B]
sudo ln -s /usr/share/phpmyadmin /var/www[/B]

 2. Edit **/etc/apache2/apache2.conf** like this.

**sudo gedit /etc/apache2/apache2.conf**

and add the following lines to the end of the file

**Include /etc/phpmyadmin/apache.conf**

 then restart apache and try [http://localhost/phpmyadmin](http://localhost/phpmyadmin) again

**sudo /etc/init.d/apache2 restart**  


if done this on both virtual machines and on 'Normal' machines.
ubuntu 9.04 and 9.10. works on both.

Now you have a ubuntu server with apache2, mysql database, php, phpmyadmin for testing everything you want. 

TIP : Instead of working with dreamweaver look into joomla and drupal cms (opensource).
you can install these free content management systems on your newly configured server ;) 

Have fun with Linux :D

Just giving back to the community what i have learned :KS

---

### Post by Stolea on 2009-11-11
Thank you all for your generous help. 
The spirit of this forum's community never ceases to amaze me. It helps keep a balanced side to the jaded view of life one gets when dealing with the public.
3 Cheers Guys!!!

---

### Post by Stolea on 2009-11-11
I somehow managed to screw up the username and password to get into phpmyadmin:(

Any ideas how to reset this?](*,)

---

### Post by Stolea on 2009-11-12
Just worked out what the username and password are. The default username is root, which is one of those bits of information that comes up but easily passes by unnoticed if you don't read every word on the screen.

---

