---
title: "SMF(simple machine forum) on ubuntu server?"
date: 2007-09-15
forum: Server Platforms
---

### Post by bone2006 on 2007-09-15
I've been wanting to put SMF ([www.simplemachines.org](www.simplemachines.org)) forum on my server for hours and hours now without any luck.
I've only seen one tutorial here, which is the same one that's over at SMF forum as well, but the problem is that one extracts to the default directory

/var/www  in which is not where I want to put the forum.   I created a directory called forum then I did sudo chmod 777 forum, transfer the files and extracted everything to the forum directory.
When I open the install.php it still shows the file as needing to have the 777 permission.

With a few tools I can see that the directory and everything in it is writable.  I login with a regular user and created a directory, yet I can't get any further in installing the forum.

Is this something to do with apache or possibly mysql?

Any help is greatly appreciated

---

### Post by freebeer on 2007-09-15
I started playing with SMF, too.

My guess is that if you look at the file permissions of install.php, it isn't set to 777 as you think... I get the impression that you managed to change the directory permissions to 777 but not the files contained therein.

---

### Post by bone2006 on 2007-09-16
Originally I put it in regular folder, had problems so then
I went to /var/www and created the folder and then changed it to 777 the entire folder. Then I went into the first folder that needs the permission, which is attachments and did chmod 777, I went into the folder and change the permissions on the 2 files in there, one is hidden and one is not.  I've changed all of these and the install.php still shows the files below as needing to be changed.  I've changed install.php to 777 as well. 

    *  attachments
    * avatars
    * Packages
    * Packages/installed.list
    * Smileys
    * Themes
    * agreement.txt
    * Settings.php
    * Settings_bak.php

really not sure what else to do, but SMF does seem like the best FOSS forum solution out there and really would like to get it on my server.

---

### Post by bone2006 on 2007-09-16
I ended up doing chmod 777 -R /var/www/forum 

and it works, but I'm kind of worried, is it alright for the entire folder to be 777?

---

### Post by bone2006 on 2007-09-16
now I'm stuck at the mysql stage LOL

I'm getting this error
Lost connection to MySQL server at 'reading initial communication packet', system error: 111

I found a way to change my mysql password, but not sure what my username is. I tried my regular username and mysql, but can't get it to connect. any recommendations?

---

### Post by bone2006 on 2007-09-16
Ok I finally got the board up and running and it's much easier than I made it.

I simply uploaded the file, extracted everything into a folder called forum, so that it was in /var/www/forum
Then I navigated to /var/www/ and I typed in 

sudo chmod 777 -R /var/www/forum

Then I opened up the install.php by going to my site

[www.site.com/install.php](www.site.com/install.php)

Then it ask about mysql, which I used the default server and for username I typed in root and my password.  

It's all up and running.  After installation it asked me if I wanted to delete install.php, in which I did.

I went back to /var/www and then I typed this in to make it 755, which is what www was and the other folders

sudo chmod 755 -R /var/www/forum

Hopefully this helps somebody out there.  SMF in my opinion is the best forum that's free out there, I've been using it for awhile now, just never installed it before :)

---

### Post by lenswipe on 2008-01-25
> **bone2006 said:**
> Ok I finally got the board up and running and it's much easier than I made it.

I simply uploaded the file, extracted everything into a folder called forum, so that it was in /var/www/forum
Then I navigated to /var/www/ and I typed in 

sudo chmod 777 -R /var/www/forum

Then I opened up the install.php by going to my site

[www.site.com/install.php](www.site.com/install.php)

Then it ask about mysql, which I used the default server and for username I typed in root and my password.  

It's all up and running.  After installation it asked me if I wanted to delete install.php, in which I did.

I went back to /var/www and then I typed this in to make it 755, which is what www was and the other folders

sudo chmod 755 -R /var/www/forum

Hopefully this helps somebody out there.  SMF in my opinion is the best forum that's free out there, I've been using it for awhile now, just never installed it before :)

THANK YOU THANK YOU THANK YOU THANK YOU I CANT THANK YOU ENOUGH!!!!!!!!!!!


IVE BEEN TRYING TO GET THIS RUNNING FOR AGES AND AGES!!!
*presses thank you button!*

I CANT THANK YOU ENOUGH

-lenswipe

---

