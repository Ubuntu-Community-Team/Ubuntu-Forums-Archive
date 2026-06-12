---
title: "How to transfer files to Apache root folder"
date: 2010-08-25
forum: System76 Support
---

### Post by ShowMeGrrl on 2010-08-25
The saga continues on my switch from Windows to Linux. 

I had an absolutely delightful experience installing the entire LAMP stack (Apache Web server, MySQL database, PHP, and MyPHPAdmin) in about 5 minutes all at once, thanks to a great Ubuntu project I learned about on the Internet. Wow, what a fantastic project that is! Directions at: [http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)

Now, however, I have a question. In order to have various Web pages available locally in my Web browser at localhost, I need to transfer a number of folders into Apache's var/www folder.

Here is my question: Because the var/www folder is in root space rather than my user space (I don't know if I am phrasing this correctly), I would have to move the files and folders in there as root. But then if I want to work on those files using, say, Bluefish or Netbeans, I would be working as user and presumably would be denied access. 

What is the best solution to this issue? When I did this on my Starling netbook, I had a big problem with permissions, though I can't remember the details. I would like to do it properly this time. (I am using a desktop Wild Dog this time.)

---

### Post by jml on 2010-08-25
This is not an officially approved way to do things, but you can enable the root account.  Log in as root and then do what you need to do, then change back to being a regular user.  I used this trick to do some things on my system that were easier to accomplish as root.  Here is the link:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The steps to both enable and disable the root account is found near the end of the document.  Hope that this helps.

Joe

---

### Post by zaphod777 on 2010-08-27
Probably the easiest thing to do is create a sym link in the www folder that goes to where you are storing the files on you server that you have access to. Or you could create a group called "web" and then put yourself and root in the group. Then give that group access and give it read / write access.

Then > sudo chgrp -R web /var/www
sudo chmod -R g+wr /var/www


---

### Post by zaphod777 on 2010-08-27
> **zaphod777 said:**
> Probably the easiest thing to do is create a sym link in the www folder that goes to where you are storing the files on you server that you have access to. Or you could create a group called "web" and then put yourself and root in the group. Then give that group access and give it read / write access.

Then

Actually scratch the las commands it didn't work with my testing. But this will you need to give your group access to the whole path. But in Apache you can also create a new site and just point the document root to somewhere in your home directory also.
```

chgrp web /var
chgrp web /var/www
chmod g+rwx /var/www
chmod g+rwx /var/www

```

---

### Post by Derath on 2010-08-27
Here are some other options, depending on how you want to do it. The symlink is not a bad option. If you wanted to copy and/or move the files to the ServerRoot, you can do this:
```
sudo cp <directory of files>/* /var/www/

-OR-

sudo mv <directory of files>/* /var/www/
```

First is copy, second is move

Another options is if you look in the /etc/apache2/httpd.config, /etc/apache2/apache2.conf or /etc/apache2/sites-available/examplesite.com <or whatever name it may be in here> (also depends upon set up, I don't have a current apache2 setup at the moment.

Somewhere in one of these config files will be a line that says 
```
DocumentRoot "/var/www/"
```

You can change the "/var/www" to whereever you have those files at (maybe "/home/<user>/web/files"...)

While it will be serving files out of your home directory (and some people are not fond of this), it would allow easy access for you to edit, save, delete, etc files without needing to use root or sudo.

If you

---

### Post by ShowMeGrrl on 2010-08-27
Thanks for these suggestions. I have been doing research on the Internet the past few days. I have written up a description of the approach that I ended up taking on this:


How to develop Web pages on your LAMP set-up on Ubuntu Lucid Lynx (10.04)


}}}}}}}INSTALL LAMP STACK -- in one fell swoop!{{{{{{{{

1. Install Apache2, PHP, MySQL, PHP, and MyPHPAdmin in about five minutes with a minimum of muss and fuss. This is a fantastic Ubuntu project that will save you mucho time and headaches installing your LAMP stack. Follow the clearly written directions at:

[http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/)



}}}}}}}CREATE YOUR OWN USER FOLDER TO HOLD YOUR WEB PAGES AND SCRIPTS{{{{{{{{

This solves the problem that Web pages in Apache2's var/www folder are owned by root, which makes it difficult for you as a mere user to edit those pages. There are various solutions to this problem, but here is the one that most appealed to me: Set up your own user directory that you own, yet that Apache2 can use to display Web pages and run scripts just as it does in its own default directory (var/www).

1. Open a terminal and type: "a2enmod userdir" (without the quotes) (This will enable Apache2's userdir module.)

2. Create a folder within your home directory called "public_html." You can do that in the terminal by typing: "mkdir ~/public_html" (without the quotes) and then hit enter.

3. Place within the "public_html" folder an index.html file with "Hello world" or other content. 

4. Create another folder within the public_html folder called, say, "Testing."  Place within it a .php file, called, say, "test.php," with php content such as 
<?php phpinfo(); ?>

5. In the terminal, change permissions for your userdir.
First, type: "chmod +x $HOME" (without the quotes) and hit enter
Then type: "chmod 755 $HOME/public_html" (without the quotes) and hit enter


}}}}}}}}ENABLE PHP SCRIPTING WITHIN YOUR public_html{{{{{{{{{

You must do the following steps to allow php scripts to run within your userdir. Otherwise, when you browse to a .php file, your browser will download it to your hard drive instead of executing it.

1. Open the terminal and type: "sudo gedit /etc/apache2/mods-enabled/php5.conf" (without the quotes) and hit enter.

 When the file opens in gedit, find these five lines:


<IfModule mod_userdir.c>

    <Directory /home/*/public_html>

        php_admin_value engine Off

    </Directory>

</IfModule>

and disable these five lines, either by deleting the lines, or, better, by placing a # sign before each line.

Save the file and quit gedit.



}}}}}}}}RESTART APACHE2{{{{{{{{{{

The following step will eliminate the "Could not reliably determine the server’s fully qualified domain name, using 127.0.1.1 for ServerName" error when you try to restart Apache2 on Ubuntu.

1. Go to the terminal and type:

 "sudo gedit /etc/apache2/httpd.conf" (without the quotes) and hit enter.

The httpd.conf file will be blank. Type this line into the file: "ServerName localhost" (without the quotes).

Save the file, close it and exit from gedit.

 
2. Restart Apache2 server in order to load all of the changes you have made to Apache2 files.

Open a terminal and type: "sudo /etc/init.d/apache2 restart" (without the quotes). Hit enter.



}}}}}}}}}TESTING YOUR SETUP{{{{{{{{{{{{{


Everything should work now. To test whether it is working, do the following:

1. Open your browser and type into the address bar: "http://localhost/~username/" (without the quotes) and hit enter. You should see the contents of the "index.html" file that you placed in your "public_html" folder.

2. Next, type into your browser's address bar: "http://localhost/~username/Testing/test.php" (without the quotes) and hit enter. Your browser should display the content created by your php script in the Testing folder within public_html.

You should substitute your Ubuntu user name for "username" in the above Web address. For example, [http://localhost/~johndoe/Testing/test.php](http://localhost/~johndoe/Testing/test.php)   You do not include the "public_html" in the address. Apache2's userdir module is by default configured to navigate automatically to that folder to look for Web content. 


I can now create and edit Web pages and php scripts in this user directory (public_html) and, thus, will not have the thorny permissions issues that I would face if I were trying to do my development in root's var/www folders. One of the downsides is you have a longer Web address to type than you normally would, because you have to add the ~username to the address. There may be other downsides that I will discover as I start developing pages, but in my preliminary tests, things have worked fine: I can edit pages in my Bluefish editor and view the results in my browser and I haven't had to do anything ugly or sinful like logging in as root while developing or changing permissions on root folders. These above instructions are for developing pages on your own personal machine and not for serving the pages to the public. To do the latter no doubt would require more consideration of security, scalability and other issues.


I looked at many Web pages while trying to figure out how to get my userdir setup working. There were two in particular that solved the problems I was running into, and their authors are to be thanked and credited for most of the content here.

[http://devplant.net/2010/05/04/linux-php-not-working-in-userdir-public_html/](http://devplant.net/2010/05/04/linux-php-not-working-in-userdir-public_html/)

[http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/](http://mohamedaslam.com/how-to-fix-apache-could-not-reliably-determine-the-servers-fully-qualified-domain-name-using-127011-for-servername-error-on-ubuntu/)

---

### Post by Krissi on 2012-11-28
Dude, yes there are always other sources but you're the one that did the work to find them and explained it perfectly to basic users like me. I'm learning as I go along, developing a web page and getting to more and more complicated elements but big gaps in my knowledge really stop me when I'm reading a lot of these "solutions" as, with full respect as they are giving their time for free, a lot of these programmers leave out a lot of small details assuming they are so basic you should know them. But if you really look at what is being asked it is best to over explain and run the risk of someone feeling "of course I know that, I'm not an idiot!!" than to simply jump over minor but important details. Until you know and understand this stuff it might as well be chinese so a big thank you for your layout of this issue, solved a problem I've been trying to figure out for over 2 weeks.

---

