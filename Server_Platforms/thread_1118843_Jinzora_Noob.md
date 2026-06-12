---
title: "Jinzora Noob"
date: 2009-04-07
forum: Server Platforms
---

### Post by GirlofTime on 2009-04-07
Mornin,

I want to set up Jinzora on my home server that has ubuntu 8.10 server edition on it. FYI-  When installing it i chose the option to install LAMP and SSH.  Can you give me any good links on how to set up Jinzora.  Im decently new with linux but i will be working with the command line on my server.  I still have the keyboard and monitor hooked up until i figure out how to get rid of them hehe .  :KS  Thanks for the help!

---

### Post by HermanAB on 2009-04-07
Jinzora probably works, but is very complicated if all you want to do is play music from a web browser.

Have a look at Edna.  It is as simple as it gets and accomplishes the same thing:
[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

I've had an Edna server running for years in my basement and can listen to my music from anywhere in the world using just a web browser for access.

---

### Post by GirlofTime on 2009-04-07
> **HermanAB said:**
> Jinzora probably works, but is very complicated if all you want to do is play music from a web browser.

Have a look at Edna.  It is as simple as it gets and accomplishes the same thing:
[http://edna.sourceforge.net/](http://edna.sourceforge.net/)

I've had an Edna server running for years in my basement and can listen to my music from anywhere in the world using just a web browser for access.

Hows the GUI for Edna?  Cant seem to find any screenshots for Edna. :p

---

### Post by volkswagner on 2009-04-07
Jinzora is really slick.  It is not difficult to install.  Trying to get advanced functions with lack of documentation is frustrating.

For install instructions the [wiki]("http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access") has a how-to.

You will need to adjust your php.ini file to increase some of the default resource limits.

My advice is take the install slowly.  Make sure all your settings are considered acceptable by the installer self check.  Trying to go back can be difficult.  

Make sure you have all the needed items, like mysql root password, php packages.

I think it is slick.

---

### Post by Lori700698 on 2009-04-07
I simply love Jinzora, the only thing is that my music is not well tagged and I wound up install and re-installing a couple of times to get Jinzora to pull my music over the way I wanted it (which was a little daunting) But after it was up it's very self sufficient, I like the http:// set up, that made things much easier.  Once you install just point a browser to your outside domain (you don't have to do the actual set up with ssh) and it walks you through the set up.  If you want to access Jinzora from the outside world don't forget to open a port.  I even use it on my cell phone (but downloads are SLOW) 

Lori

---

### Post by GirlofTime on 2009-04-07
Hey thanks for the replies.  I'm going to try using that wiki tonight to set it up.  Wish me luck!

---

### Post by HermanAB on 2009-04-08
Here are some Edna shots.  Edna is incredibly easy to set up and works like a charm - been using it for years.  I have accounts with password access and can play my music from anywhere I go.

I also have an Eeee PC netbook plugged into my hi-fi amplifier, always sitting there with Firefox on my Edna service.

---

### Post by GirlofTime on 2009-04-08
Im following the steps from here.  [http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access](http://en.jinzorahelp.com/wiki/Linux_Installation_with_shell_access)

Ive unpacked the jinzora file in my home/username area.  When i try to "cd" to the file it says "permission denied".  I thought it was a sudo thing so typed "sudo cd jinzora2" and then it says "command not found".  

any ideas what im doing wrong?

---

### Post by R.Bucky on 2009-04-08
If I understand correctly, you are trying to ssh into your server? If so, sounds like you need to open up port 22 on your server with > sudo ufw allow 22

---

### Post by GirlofTime on 2009-04-08
> **R.Bucky said:**
> If I understand correctly, you are trying to ssh into your server? If so, sounds like you need to open up port 22 on your server with

I've successfully SSHed into the server.  I just cant "cd" to a folder.

---

### Post by GirlofTime on 2009-04-08
This fixed it. 

sudo chown -hR <username> <folder location>

---

### Post by redonwhite on 2009-04-08
Im on the last step.  I type 

$  chmod 744 configure.sh

then 

$  sh ./configure.sh

You are now in setup mode.
Please direct your web browser to the directory where you installed Jinzora
and load index.php - you will then be taken through the complete setup


Then i direct my browser to [http://serveripaddress/jinzora2](http://serveripaddress/jinzora2)

i get 403 Forbidden Error. You don't have permission to access /jinzora2/ on this server.

Anyone know what im doing wrong? Thanks for the help!

---

### Post by Lori700698 on 2009-04-10
You probably need to sudo chown Jinzora2 folder as well.  And one last thing that will make you nuts so I will tell you before you get there, the install folder needs to be deleted before it will let you start running the http set up.

---

### Post by GirlofTime on 2009-04-10
I was able to get access to the jinzora folder by inputing this command

```
chmod 777 -R /var/www/jinzora2
```

But then when i was going through the set up I got stuck where it created the database.  Said it couldnt connect. =/.  Guess i gotta reconfigure Mysql.  Gotta look that up.

---

### Post by Lori700698 on 2009-04-10
The only thing I remember about the mysql is that I had to set up a password during the ubuntu install then I had to input that in during the set up.  You will have to remove Jinzora completely and then put it back in.  This is the bad part about the install design, no room for any errors, you have to start over.  But I really like it because I can access it at work or anywhere that I want.  I hope you get it running!  I use webmin and it really made the install/uninstall 200 times until I got what I wanted very simple.  I use a combo of webmin and putty from my laptop for everything with my server.

Good Luck!
Lori

---

### Post by GirlofTime on 2009-04-10
> **Lori700698 said:**
> The only thing I remember about the mysql is that I had to set up a password during the ubuntu install then I had to input that in during the set up.  You will have to remove Jinzora completely and then put it back in.  This is the bad part about the install design, no room for any errors, you have to start over.  But I really like it because I can access it at work or anywhere that I want.  I hope you get it running!  I use webmin and it really made the install/uninstall 200 times until I got what I wanted very simple.  I use a combo of webmin and putty from my laptop for everything with my server.

Good Luck!
Lori

Yeah i remember setting up MySQL during the ubuntu server set up with the password.  But even when i input during the Jinzora set up i get an Error Cant connect to the data base.  I was thinking maybe it had to do with the access or something of that nature not sure.  I had to start the install over a couple times too.  I just had to delete some lock" folder everytime i wanted to start over. Almost there! haha

---

### Post by GirlofTime on 2009-04-10
I got to the part where you pick your media file directory.  Does that have to be in a certain Location.  Because i made one on my home folder and it cant seem to create a database there. =///.

---

### Post by Lori700698 on 2009-04-10
no, mine is in my home files directory.  Did you make a new folder for the music?  Maybe it need 777 to so it doesn't have restrictions either.

---

### Post by GirlofTime on 2009-04-10
Haha.  Now I cant get through the "backend" part again. =)  Keeps saying 

Creating Database
    - jinzora2 - Failed!

could not connect to database.

Thats weird because one step ago I had gotten past this part.  Now it wont connect.  And when i type the permission commands again to initiate the install i get this out put.

```

$:/var/www/jinzora2$ chmod 744 configure.sh
$:/var/www/jinzora2$ sh ./configure.sh
chmod: changing permissions of `temp/access.log': Operation not permitted
chmod: changing permissions of `temp/jinzora-words-.log': Operation not permitted
chmod: changing permissions of `temp/messages.log': Operation not permitted
chmod: changing permissions of `data/database/backend-userclasses': Operation not permitted
chmod: changing permissions of `data/database/user_settings': Operation not permitted
chmod: changing permissions of `data/database/backend': Operation not permitted
chmod: changing permissions of `data/database/groups': Operation not permitted
chmod: changing permissions of `data/database/constants.php': Operation not permitted
chmod: changing permissions of `data/database/users': Operation not permitted

You are now in setup mode.
Please direct your web browser to the directory where you installed Jinzora
and load index.php - you will then be taken through the complete setup
```

Im so confuzzelded now hahaha.

---

### Post by Lori700698 on 2009-04-10
I think because you already created them, when you run through again there is a question about creating the databases and this time you won't need to.  look at the drop downs around the creating database page.

---

### Post by GirlofTime on 2009-04-10
> **Lori700698 said:**
> I think because you already created them, when you run through again there is a question about creating the databases and this time you won't need to.  look at the drop downs around the creating database page.

Selected False for the "create database option"  Then i got the old "could not connect to database."

---

### Post by GirlofTime on 2009-04-10
Next wave i chose "True (dropped existing database)"  Then i got this....

Dropping database
    - jinzora2 - Successful!

Creating Database
    - jinzora2 - Failed!

could not connect to database.

---

### Post by Lori700698 on 2009-04-10
see if this helps at all?
[http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25](http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25)

---

### Post by GirlofTime on 2009-04-11
> **Lori700698 said:**
> see if this helps at all?
[http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25](http://maketecheasier.com/how-to-install-and-setup-jinzora-media-server-in-ubuntu/2008/08/25)

Thanks Lori :KS .  Im going to do a clean install and try this "how to" out.

---

### Post by HDave on 2009-06-29
Did you ever get this working?  I am interested in the same thing and was wondering how hard it is to set up...

---

### Post by GirlofTime on 2009-07-13
> **HDave said:**
> Did you ever get this working?  I am interested in the same thing and was wondering how hard it is to set up...

Hey dave.  I couldn't get it working and gave up on it for the time being.  But other people have gotten it to work.  I just didn't have the patience for it at the time.  Good luck.

---

### Post by HDave on 2009-07-13
Sorry to hear that.

In the meantime I did get it up and running...albeit in a virtual machine.  It runs well from within VMWare Server.

If you try again and need help, I'll try to provide any answers.  A couple things I learned the hard way was:

1) With the latest version of Jinzora, don't run the configure.sh script...it'll kill ya.  Just do:   
sudo chown -R www-data:www-data jinzora2

2) You need to fix up your PHP settings.  Try: 
sudo nano /etc/php5/apache2/php.ini

and then change the following lines:
memory_limit = 64M
max_execution_time = 300
post_max_size = 32M
upload_max_filesize = 32M

3) You need to snag GD2 for the display of album art
apt-get install php5-gd

4) The easiest way to get to a LAMP setup is to install the base Jaunty and do a:
sudo tasksel
and then select LAMP server and hit OK

5) if UFW is enabled you need to create a hole in the firewall via:
sudo ufw allow "Apache Full"

good luck...

---

### Post by GirlofTime on 2009-07-14
> **HDave said:**
> Sorry to hear that.

In the meantime I did get it up and running...albeit in a virtual machine.  It runs well from within VMWare Server.

If you try again and need help, I'll try to provide any answers.  A couple things I learned the hard way was:

1) With the latest version of Jinzora, don't run the configure.sh script...it'll kill ya.  Just do:   
sudo chown -R www-data:www-data jinzora2

2) You need to fix up your PHP settings.  Try: 
sudo nano /etc/php5/apache2/php.ini

and then change the following lines:
memory_limit = 64M
max_execution_time = 300
post_max_size = 32M
upload_max_filesize = 32M

3) You need to snag GD2 for the display of album art
apt-get install php5-gd

4) The easiest way to get to a LAMP setup is to install the base Jaunty and do a:
sudo tasksel
and then select LAMP server and hit OK

5) if UFW is enabled you need to create a hole in the firewall via:
sudo ufw allow "Apache Full"

good luck...

Thanks dave.  I'm gonna wait till it cools down around here (my pc room gets hot as heck in the summer) and try your steps.  Thanks!

---

### Post by Psycam on 2009-08-02
> **HDave said:**
> 
1) With the latest version of Jinzora, don't run the configure.sh script...it'll kill ya.  Just do:   
sudo chown -R www-data:www-data jinzora2


That one had been getting me for a few hours now. THANK YOU!!!

---

### Post by HDave on 2009-08-02
You'd think they update their site by now...anyway...good luck.  It really is cool once it's up and running.  I'm listening to mine right now from within a virtual machine...and the servers virtual too!

---

### Post by sixstorm on 2009-08-06
I'm having some issues myself with setting up Jinzora.

After everything has been installed, I get this in my web browser:

> Security breach detected

I've deleted the install folder under /var/www/jinzora and I can't find anything else related to this.  Any help?

---

### Post by sixstorm on 2009-08-10
bump

Anyone ever got the error I posted a few days ago?

---

### Post by HDave on 2009-08-10
Never seen it.  You need to provide more details re the error from the browser.  Also you need to check appropriate logs on the server.  Sorry, I can't help more.

---

### Post by sixstorm on 2009-08-11
> **HDave said:**
> Never seen it.  You need to provide more details re the error from the browser.  Also you need to check appropriate logs on the server.  Sorry, I can't help more.

Since we are in a Jinzora noob thread ;) I'll have to ask where the log files are.  

Here is a screenshot of what I'm seeing:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124429&stc=1&d=1249993909[/IMG]

Falcon is the name of my server.  I've also tried "http://falcon/jinzora2/" (with one forward-slash between falcon and jinzora2).  No worky.

Can you tell me where the log files are?  I'll be glad to post them up.

---

