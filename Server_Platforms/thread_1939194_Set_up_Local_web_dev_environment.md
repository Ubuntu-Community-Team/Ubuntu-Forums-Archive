---
title: "Set up Local web dev environment"
date: 2012-03-11
forum: Server Platforms
---

### Post by Jacob72 on 2012-03-11
Hello,

I hope this is in the correct category?

I want to set-up a local web dev environment for building and testing basic dynamic websites/maybe a cms like wp. I do not want to host websites. I have read up on how to install LAMP on Ubuntu.

Please can I get some guidance on what security steps I need to take and if I am using LAMP appropriately?

Thank you

---

### Post by acc61287 on 2012-03-11
> **Jacob72 said:**
> Hello,

I hope this is in the correct category?

I want to set-up a local web dev environment for building and testing basic dynamic websites/maybe a cms like wp. I do not want to host websites. I have read up on how to install LAMP on Ubuntu.

Please can I get some guidance on what security steps I need to take and if I am using LAMP appropriately?

Thank you

Try this link I made this tutorial:
[https://www.facebook.com/note.php?note_id=304348809620386](https://www.facebook.com/note.php?note_id=304348809620386)

In CMS I use joomla:
[https://www.facebook.com/note.php?note_id=201097319945536](https://www.facebook.com/note.php?note_id=201097319945536)

For monitoring/security I use webmin:
[https://www.facebook.com/note.php?note_id=276203469101587](https://www.facebook.com/note.php?note_id=276203469101587)

---

### Post by Jacob72 on 2012-03-11
Thanks!

Bluefish editor - when trying to connect to remote directory:

Open file
Type file name
[ftp://user@host/](ftp://user@host/)

The editor does not respond?

---

### Post by acc61287 on 2012-03-11
> **Jacob72 said:**
> Thanks!

Bluefish editor - when trying to connect to remote directory:

Open file
Type file name
[ftp://user@host/](ftp://user@host/)

The editor does not respond?

Welcome:D

---

### Post by Jacob72 on 2012-03-12
I should start by saying I am a Windows user trying to switch to Ubuntu.

Great, I installed LAMP and have everything running.

I have followed [Virtual Host in LAMP]("http://www.youtube.com/watch?v=2vA2Yzv-NoI&feature=plcp&context=C42216c1VDvjVQa1PpcFOvX9wGRsOHAQptymBMqVObRozo6a-nG98%3D")  YT tutorial and so far created folders and a file via Nautilus in  /var/www/ which works. I was slitly uncertain what Virtual Host referred  to? To make sure, I only want to set up a _local_ web dev managment environment and am hoping I have done the right thing?

As a Windows user I am not used to 'Permissions', I was hoping I could  copy and paste existing websites into /var/www/. Do I have to re create  all the folders/files via Nautilus?

Now that I have set up mysite.co.uk locally I can not use the browser to  view the live version remotely - when I type in the full url I get the  the local version? 

I am trying Quanta Plus in hope I can set it up like DW's manager sites?
I have created a project with ftp connection, and want to know how to  create the local directory settings for the same project? Also there  does not seem to be a download option for this project?

---

### Post by CharlesA on 2012-03-12
I use virtualhosts when testing on my web dev box. I used the documention here:

[http://www.debianhelp.co.uk/virtualhosts.htm](http://www.debianhelp.co.uk/virtualhosts.htm)

---

### Post by acc61287 on 2012-03-12
> **Jacob72 said:**
> I should start by saying I am a Windows user trying to switch to Ubuntu.

Great, I installed LAMP and have everything running.

I have followed [Virtual Host in LAMP]("http://www.youtube.com/watch?v=2vA2Yzv-NoI&feature=plcp&context=C42216c1VDvjVQa1PpcFOvX9wGRsOHAQptymBMqVObRozo6a-nG98%3D")  YT tutorial and so far created folders and a file via Nautilus in  /var/www/ which works. I was slitly uncertain what Virtual Host referred  to? To make sure, I only want to set up a _local_ web dev managment environment and am hoping I have done the right thing?

As a Windows user I am not used to 'Permissions', I was hoping I could  copy and paste existing websites into /var/www/. Do I have to re create  all the folders/files via Nautilus?

Now that I have set up mysite.co.uk locally I can not use the browser to  view the live version remotely - when I type in the full url I get the  the local version? 

I am trying Quanta Plus in hope I can set it up like DW's manager sites?
I have created a project with ftp connection, and want to know how to  create the local directory settings for the same project? Also there  does not seem to be a download option for this project?

Yup! you can copy and paste your work. You can use nautilus or via terminal.
For example:
1. sudo nautilus
2. Browse your file the copy and paste to /var/www
But after that, If your trying to edit your work only root have access on that file. What will you do is change the change the ownership and permission of that file.
If you prefer to edit it using user:
3. sudo chown -R $USER:root /var/www/(folder or filename)
or sudo chown -R $USER:USER /var/www/(folder or filename)
The command above chown (change ownership) to $USER and group root. They have the authority on that file. It's depend on you :)
4. And use chmod, basically 644 for file and 755 for folder. It represent octal number. try using ls -l command you will see at the left side of the terminal:

-421421421
-rwxr--r-- = it represent a number 644
drwxr-xr-x = it represent a number 755

r - read
w - write
x - execute

the first 421 is for user
the second 421 is for group
the last 421:confused: (I for got :D)

If your confused about this try to read about file permission, groups and ownership

I hope you got this:)

---

### Post by CharlesA on 2012-03-12
Using gksu instead of sudo for graphical apps prevents permission problems.

---

### Post by Jacob72 on 2012-03-13
Thanks for the replies!

Continuing from a previous question:

>  Now that I have set up mysite.co.uk locally I can not use the browser to   view the live version remotely - when I type in the full url I get the   the local version? 

Not sure I have made myself clear? I am working on a site which is set up for local testing; 'test', the site is also hosted remotely; 'live'. When I try to brows the 'live', I get directed to 'test'? I would like to test both simultaneously, what can I do?

---

### Post by Jacob72 on 2012-03-13
> Thanks for the replies!

Continuing from a previous question:

 	Quote:
 	 	 		 			 				 Now that I have set up mysite.co.uk locally I can not use the  browser to   view the live version remotely - when I type in the full  url I get the   the local version? 			 		 	 	 
Not sure I have made myself clear? I am working on a site which is  set up for local testing; 'test', the site is also hosted remotely;  'live'. When I try to brows the 'live', I get directed to 'test'? I  would like to test both simultaneously, what can I do? 	

I renamed the /var/www/ folder to dev. :razz:

---

### Post by CharlesA on 2012-03-13
Did you change the configuration file to point to /var/dev instead of /var/www ?

I have my test box set up to only access the test version via the hosts file - if I type in the URL, I have it pointing to the IP of the test box. If I want to test the live version, I'll upload the files and go from a different machine.

---

### Post by Jacob72 on 2012-03-13
> Did you change the configuration file to point to /var/dev instead of /var/www ?
No :(

I will rename the folders to test1/2/3 and so on if dev will cause a problem?

> I have my test box set up to only access the test version via the hosts  file - if I type in the URL, I have it pointing to the IP of the test  box. If I want to test the live version, I'll upload the files and go  from a different machine. 	

Is that not a bit of a hassle?

I did the permission change to one of the folders to work on it, that went OK. Then when I decided to rename the sites I deleted all the folders/files and re done the configuration files. I am now getting:

> syntax error on line 230 of /etc/apache2/apache2.conf could not open configuration file

I tried to remove apache2 with:

> apt-get remove apche2


and got:

> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


?

---

### Post by MG&amp;TL on 2012-03-13
Read up on permissions: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

For your command, you want:

```
sudo apt-get remove apache2
```

Use *sudo* for CLI apps, and *gksu* for graphical apps.

---

### Post by Jacob72 on 2012-03-13
My typo - I did:

```
sudo apt-get remove apache2 
```On ubuntu restart I am now getting:

> Could not update ICE authority file /home/jacob. ICE authority

---

### Post by Jacob72 on 2012-03-13
After:
```
sudo /etc/init.d/apache2 restart
```
I get:
```
Syntax error on line 230 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/testsite.co.uk: No such file or directory
Action 'configtest' failed.

```
?

---

### Post by Jacob72 on 2012-03-13
As I am starting out with Ubuntu and on a fresh install I ran the Ubuntu install again and started from scratch. Starting over taking in your advise and links I hope to make good my en devour to get set up.

---

### Post by CharlesA on 2012-03-13
Word of advice, start small and make sure one thing is working correctly before trying something else, and make sure you make backups of your config files before you edit them, in case something breaks.

---

### Post by Jacob72 on 2012-03-13
OK

What is a 'web dev box' , is it the same as LAMP?

---

### Post by CharlesA on 2012-03-13
> **Jacob72 said:**
> OK

What is a 'web dev box' , is it the same as LAMP?
Yes, that's just want I call it.

---

### Post by Jacob72 on 2012-03-17
>  Using gksu instead of sudo for graphical apps prevents permission problems.
 Please can I get some direction on using gksu. 

What do you mean by Graphical apps, is that software like bluefish?

Thank you

---

### Post by Jacob72 on 2012-03-17
Is gksu the same as gksudo?

---

### Post by CharlesA on 2012-03-17
> **Jacob72 said:**
> Please can I get some direction on using gksu. 

What do you mean by Graphical apps, is that software like bluefish?

Thank you

Yes.

> **Jacob72 said:**
> Is gksu the same as gksudo?

And yes.

---

### Post by Jacob72 on 2012-03-18
Does opening bluefish via gksudo, give me permissions  to edit files in /var/www/mysite?

---

### Post by CharlesA on 2012-03-18
> **Jacob72 said:**
> Does opening bluefish via gksudo, give me permissions  to edit files in /var/www/mysite?
Yes, but I would not recommend it.

I just pointed the DocumentRoot to a folder in my home directory so I wouldn't have to deal with permission problems.

[http://www.ajopaul.com/2010/05/01/ubuntu-apache2-change-default-documentroot-varwww/](http://www.ajopaul.com/2010/05/01/ubuntu-apache2-change-default-documentroot-varwww/)

---

### Post by Jacob72 on 2012-03-20
> Yes, but I would not recommend it.

Then I am not sure about the purpose of gksudo?

>  I just pointed the DocumentRoot to a folder in my home directory so I wouldn't have to deal with permission problems.

Is the home dir the only place that does not require permissions? I have my folders on a separate drive, can I not point the docroot there? 

Thanks, I feel I am almost there :p

---

### Post by CharlesA on 2012-03-20
> **Jacob72 said:**
> Then I am not sure about the purpose of gksudo?

The purpose of gksu/gksudo is to give a program temp root privlages, which would allow you to move/delete files where you normally wouldn't be able to.

> Is the home dir the only place that does not require permissions? I have my folders on a separate drive, can I not point the docroot there?

As long as you have read and write access to that folder, you can use that as your document root without permissions problems and without having to give programs superuser rights to access those folders.

---

### Post by Jacob72 on 2012-03-22
> I just pointed the DocumentRoot to a folder in my home directory so I wouldn't have to deal with permission problems.

[http://www.ajopaul.com/2010/05/01/ub...ntroot-varwww/]("http://www.ajopaul.com/2010/05/01/ubuntu-apache2-change-default-documentroot-varwww/")

Cool, got that working :)

---

### Post by CharlesA on 2012-03-22
> **Jacob72 said:**
> Cool, got that working :)
Glad you got it working.

---

### Post by Jacob72 on 2012-03-23
What set up do you have for cross browser checking? On windows I ran most common browsers and  used adobe browser lab. Do you recommend using Wine or installing windows on a virtual box/parallels?

Edit:

I see Parallels is mac software, is there an Ubuntu equivalent?

Thanks

---

### Post by CharlesA on 2012-03-23
I've been testing firefox on *nix and IE/Firefox on Windows mostly.

---

### Post by Jacob72 on 2012-03-23
> For monitoring/security I use webmin:
[https://www.facebook.com/note.php?no...76203469101587]("https://www.facebook.com/note.php?note_id=276203469101587")I have set up a virtual host for testing, I am not hosting websites, I do have a dev.mysite.com subdomain set up on hosting companie's server. Do I need to use webmin or any security other than is generally advised for Ubuntu users?

Thanks

---

### Post by acc61287 on 2012-03-26
> **Jacob72 said:**
> I have set up a virtual host for testing, I am not hosting websites, I do have a dev.mysite.com subdomain set up on hosting companie's server. Do I need to use webmin or any security other than is generally advised for Ubuntu users?

Thanks


It's up to you. It's not necessary. But I have question for you:

How you will know if your website has no error? or not working as you expected?

Even you working in local you have to study the log file(not only the log file but the whole system), the error it make so you can configure it your own and no help with others.

Why I recommend webmin?
Because It's easy to work in gui :)

---

### Post by CharlesA on 2012-03-26
If apache has problems the web browser will tell you with 403 errors, 404 errors, etc.

Checking the logs is a good idea, but normally if something is messed up and causes an error, you will know it.

---

### Post by Jacob72 on 2012-04-29
I think this question still fits the thread.

I am buying a new laptop and am hoping I can transfer my current set up (mainly the Lamp server enviroment) to the new machine? The post bellow offers three easy steps to do this and was wondering if anyone had any experience with this?

Thanks again :)

[http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/)

---

### Post by Jacob72 on 2012-05-04
> **Jacob72 said:**
> I think this question still fits the thread.

I am buying a new laptop and am hoping I can transfer my current set up (mainly the Lamp server enviroment) to the new machine? The post bellow offers three easy steps to do this and was wondering if anyone had any experience with this?

Thanks again :)

[http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/](http://eggsonbread.com/2010/01/28/move-ubuntu-to-another-computer-in-3-simple-steps/)

As I am not getting any help with this last post should I create a new thread?

Thanks

---

### Post by CharlesA on 2012-05-04
> **Jacob72 said:**
> As I am not getting any help with this last post should I create a new thread?

Thanks
I would say go with clonezilla, but the destination drive needs to at least the same size as the source drive.

I use clonezilla, but running the commands listed in the link should work fine too.

---

### Post by Jacob72 on 2012-05-04
> **CharlesA said:**
> I would say go with clonezilla, but the destination drive needs to at least the same size as the source drive.

I use clonezilla, but running the commands listed in the link should work fine too.
Nice one, will give it a go.

---

