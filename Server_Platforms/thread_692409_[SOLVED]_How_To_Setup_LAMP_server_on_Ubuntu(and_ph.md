---
title: "[SOLVED] How To: Setup LAMP server on Ubuntu(and phpbb3)"
date: 2008-02-09
forum: Server Platforms
---

### Post by RadiationHazard on 2008-02-09
**_[COLOR="Red"]I'll Update Later. If Your Use This It Should Still Work But I Still Have People Who're Having Problems. So I'm Closing It Till Update This How To Make A Better One[/COLOR]_**


Ok, this if my first how to. So if i do something wrong just tell me I will try and fix it.

Ok, so for starters the whole reason I'm writing this how too is because i just installed a LAMP server onto my box and phpbb. And I had a really hard time with it because i was trying to follow other sites tutorials and they used terminal. Now don't get me wrong i love terminal and have nothing at all against it. but i learned the hard way that you should check synaptic package manager and add/remove programs first. because if you use synaptic or add/remove you're ensured that the packages will be installed correctly unlike with the terminal where it's easier for you to mess up somewhere.

So back to setting up your LAMP server. Got to System>Administration>Synaptic Package Manager. Then put in your password and when it comes up go to Edit>Mark Packages by Task... then it will open up something that looks like this

[[IMG]http://i32.tinypic.com/2nh0wf8.png[/IMG]]("http://i28.tinypic.com/szhkhx.png")
(click picture to enlarge.)

Now mark "LAMP server" as you can see I've done. Click Ok. then click apply. It will install the packages. While it's installing something should pop up asking you to set your mysql password. Make sure to set it as something that you will remember. When it gets done to make sure everything is installed correctly and working the way it should go to

[COLOR="Navy"][http://localhost/]("http://localhost/")[/COLOR]

Now that should take you to your Apache Directory. Now if everything is working right go to Synaptic Package Manager again (System>Administration>Synaptic Package Manager)
and now search "phpmyadmin" but without the quotes. One package should pop up.

[[IMG]http://i25.tinypic.com/n6sx1h.png[/IMG]]("http://i32.tinypic.com/14tbwcn.png")
(click picture to enlarge.)

Mark the package for installation and then click Apply. Once that is done installing to to 

[COLOR="Navy"][http://localhost/phpmyadmin]("http://localhost/phpmyadmin")[/COLOR]

and it should take you to this page

[[IMG]http://i27.tinypic.com/33wb3eo.png[/IMG]]("http://i28.tinypic.com/6z8nbk.png")
(click picture to enlarge.)

Now, for the username it should be "root". and then password is whatever you set your mysql password as remember I told you to remember that you'd be needing it! :)
ha ha. So any ways. Once you are logged in go to "Privileges" Then go to "Add a new User" in the "User name:" put whatever you'd like your username to be. Something that's easy for you to remember. then for the "Host:" click the drop down box and select "Local" it should also put "localhost" in the black. Then for the password type the same password you used earlier or one that you'll remember and then retype it. Where it says "Database for user" select the option that says "Create database with same name and grant all privileges" once you're done scroll all the way to the bottom and in the bottom right hand corner there is a button that says "Go" click it. It should take you to a new page and on that page it should say something along the lines of "New User Added." or something like that.

Now that we're done with that click [COLOR="Navy"][here]("http://downloads.sourceforge.net/phpbb/phpBB-3.0.0.zip?download")[/COLOR] to download phpbb 3.

for the options click "Save to Disk" and then ok. Save it to your desktop if it does not do that already. When it is done downloading extract the package to your desktop.

Now go to the terminal and type in 

```
sudo nautilus
```

this will bring up a window that looks like this...

[[IMG]http://i32.tinypic.com/29c7v2g.png[/IMG]]("http://i25.tinypic.com/dvom6d.png")
(click picture to enlarge.)

Now click File System then open the folder in there called "var" and then the folder in there called "www" there should be a folder in there that says Apache-2 or something along those lines. Delete it. you don't need. That is not actually your Apache. It's just the  index file that comes with it.


Now on to setting up phpbb3. Go to he folder that you downloaded. Extract it to you desktop and then enter this command into the terminal again if you've already closed that window that had opened 

```
sudo nautilus
```

then go to your severs folder. (File System>var>www) and open the phpbb3 folder, copy all the folders that are in it and cut and paste them into your servers folder. Now minimize all that and open your browser and go to [http://localhost/]("http://localhost/") again and it should bring you to the phpbb3 installation page. Now click the install tab. It will take you to the introduction then go to the requirements. If you did everything right you will meet the requirements so scroll down to click the button at the bottom and continue to Database Settings. For the "Database server hostname or DSN:" put "localhost" then for the "Database server port:" just leave it blank. You don't need to file that in. Then for the "Database name:" and the "Database username:" put the name that you mad in phpmyadmin that i told you to remember. now for the password put the password that you made in phpmyadmin. Now that you're done filling all that out click proceed to next step. Put in your administration details. That's all up to you. Now that you've set up the administrative stuff you come to the spot where it says download config.php file. download that file to your desktop. Go to you desktop cut it and past the file in your servers root folder(www folder) a pop up will come up saying that there is already a file in that folder with at name it will give you the options of skip or replace. Select replace. Now close that file. Unminimze your browser and click done. Now for the rest of the set up it's just pereference. The way it is set was fine for me and will probably be fine for you too,

Now that you're done with the set up. Open your terminal again and type the 

```
sudo nautilus
```

in one last time to complete the set up. Go to your servers folder.(File System>var>www) and delete the folder that says install. Now close that window and you're done. Phpbb3 in now completely installed. you're free to edit it and make it like you want. Enjoy your new site and please post feed back on this. Sorry if it's not the best how to but at least i tried right? :)



-RadiationHazard

---

### Post by SoggyCornflake on 2008-02-11
Nice tutorial. (One might say it rocks :guitar:)

At least I thought so until I ran into this minor hiccup.
I found that my php files aren't getting caught by apache, so konqueror tries to find a program to use with them.

---

### Post by stock1232 on 2008-02-11
I followed your directions specifically. I went to localhost/phpmyadmin and attempted to login in. I know what my mysql password is. however when I put the username as root and my password in. I get this: 

Error
#1045 - Access denied for user 'root'@'localhost' (using password: YES)

Again I am positive what my password is. Any help to resolve this issue would be great.

Thanks

---

### Post by an93l on 2008-02-12
i installed the LAMP as you advised but no password screen came up for mysql, also whenever i put in any localhoast address in my browser it wants to download the phtml file what have i done wrong?

---

### Post by torgrot on 2008-02-12
Same problem here FireFox doesn't know what to do with phpmyadmin.phtml  During the install of phpmyadmin there was a configuration screen for which web server you wanted to use it for.  Help said it only supported apache, I chose that, but there were serveral other variants of apache listed.

torgrot

---

### Post by RadiationHazard on 2008-02-12
it's appatche 2 that you pick when you set up phpmyadmin. and you go to localhost/phpmyadmin idk what that other crap like .phtml you were talking about. as far as i'm aware of that's not a language... oh and it should be root... i'd ask for help on that one. your root may be called something else if you renamed it...idk but it should be root. and idk why all these problems are coming up. =[ it worked for everyone perfect they said when i put it up in new users or whatever so they told me to move  it here. if you guys are still having problems let me know and i will try and redo it and make it better.

---

### Post by Steveway on 2008-02-12
Also: Never use sudo to start a graphical application.
If you start a graphical application then use gksu (or gksudo but gksudo is only a symlink to gksu) or kdesu on KDE respectively.

---

### Post by RadiationHazard on 2008-02-12
please explain what you mean because i'm redoing the tut right now..

---

### Post by torgrot on 2008-02-12
If you are writing a tutorial including screen shots then you probably need to include such pertinent information as what to select if there are any choices during the installation.  Leaving out apache2 when installing phpmyadmin was/is a glaring omission.

torgrot

---

### Post by an93l on 2008-02-13
ok how would i unistall all this to try again from scrach, as i tried unticking LAMP but it won't let me uninstall it.

---

### Post by az on 2008-02-13
> **RadiationHazard said:**
> please explain what you mean because i'm redoing the tut right now..

Gksudo is safer than sudo for desktop applications.  Using sudo to launch nautilus may create some configuration files that you will not be able to change as a normal user.  YOu should use

gksudo nautilus

instead of 
sudo nautilus.

As well, you should not grant all privs to the new mysql user.  The new user should also have a strong password, and not the same password as the root user.

You should only grant as many privileges that you web application needs and no more:
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, INDEX, ALTER, CREATE TEMPORARY TABLES, LOCK TABLES

---

### Post by az on 2008-02-13
> **an93l said:**
> ok how would i unistall all this to try again from scrach, as i tried unticking LAMP but it won't let me uninstall it.

Purge the apache2.2-common package.

---

### Post by torgrot on 2008-02-13
I have uninstalled and re-installed several times now and it still asks what I want to do with phpmyadmin.phtml when I go to this link [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  I have attempted to attach a screen shot of Firefox

torgrot

---

### Post by torgrot on 2008-02-13
Well there is no joy in mudville,  I guess it is time to use the standard method of fixing all things Ubuntu, wipe the disk and re-install the operating system.  What a piece of crap.

torgrot

---

### Post by az on 2008-02-13
Clear your browser cache.

CTRL-F5 to reload the page.

It's a common phenomenon.  Your browser cache doesn't know that you changed your server-side configuration.

And reinstalling your entire OS is a pretty silly way to fix a small problem.  Oh well, do what you want!  It's your time to waste...

---

### Post by Steveway on 2008-02-13
> **RadiationHazard said:**
> please explain what you mean because i'm redoing the tut right now..

I mean, use gksu nautilus instead of sudo nautilus.
Using sudo with a graphical application can mess with your permissions and the ICEauthority file etc...
EDIT: Didn't see that az allready answered.

---

### Post by torgrot on 2008-02-13
Well clearing the cache and reloading the page didn't work.  Since this is a test box with nothing on it, I re-installed the OS again.  Followed through the installation of phpbb and now I get an error message when I connect to http:\\localhost, I am not able to look at it right this minute, but it says something about the table not existing.

torgrot

---

### Post by jackwhite on 2008-02-18
weird. When i go to Synaptic and do the following:

>System
>Administration
>Synaptic Package Manager.
>Edit
>Mark Packages by Task

I am only presented with two options: 'Print server' and 'Ubuntu desktop'.

Both are greyed out and cannot be unselected or even installed (presumably because they're already installed).

Any ideas?(this is a totally fresh install btw)

---

### Post by torgrot on 2008-02-18
Make sure you have all the repositories selected except for the source code ones.

torgrot

---

### Post by stoneybroke on 2008-02-19
Well the install went great no problems at all, everything got installed and is working fine. But being new to Ubuntu I have dropped a clanger as all I wanted was instructions to install a LAMP SERVER to allow me to create a website. Now I have a BBS that I don't want!! can you please tell me how to uninstall the PHPBB3 and if possible direct or tell me how to create the website with LAMP installed.

Any help is better than none... Thanks

---

### Post by booyip on 2008-02-19
Thanks RadiationHazard - Got it working with no problems.  Great little guide.

---

### Post by youaredoome0 on 2008-02-20
```
Fatal error: Unknown: Failed opening required '/var/www/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```
I got this error with a PHP test file. I checked and neither of those files/folders exist.

---

### Post by CFBauer on 2008-02-20
Thanks radiation hazard, worked for me.  I'd love to see the tutorial updated with the clarifications listed so far.  Use gksu, apache2, etc.

---

### Post by robertmf on 2008-03-05
> **booyip said:**
> Thanks RadiationHazard - Got it working with no problems.  Great little guide.

ditto that here :guitar:  

Esp. the clue** Sys -> Admin -> Synaptic -> Edit **

---

### Post by robertmf on 2008-03-05
Once the LAMP is installed and [http://localhost](http://localhost) and [http://localhost/phpmyadmin](http://localhost/phpmyadmin) are found you can also check the setup using 
the php function phpinfo.

```
<?php
// php.net
phpinfo()  
?>
```

sudo chown [yourusername] /var/www/ 
Save file as like phpinfo.php in /var/www/ 
Change file permissions to allow execution

And access at [http://localhost/phpinfo.php](http://localhost/phpinfo.php)  which should list your LAMP system.

---

### Post by robertmf on 2008-03-05
Another useful utility is webmin.  This how-to is for "feisty", but works in "gutsy".

[http://howtoforge.com/installing_webmin_ubuntu_feisty](http://howtoforge.com/installing_webmin_ubuntu_feisty)

---

