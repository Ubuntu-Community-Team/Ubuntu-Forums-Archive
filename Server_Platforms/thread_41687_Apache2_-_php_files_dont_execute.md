---
title: "Apache2 - php files dont execute"
date: 2005-06-14
forum: Server Platforms
---

### Post by Nada_Surf on 2005-06-14
Ive just installed apache2 and php4 as directed at [http://ubuntuguide.org/#installapachehttpserver](http://ubuntuguide.org/#installapachehttpserver)

Apache seems to install fine, but when i try to test the php my browser downloads the php file instead of running it on the server!

What could be the problem?  I have shared the /var/www directory via samba, but even when disabling this share it still doesnt work.  I also tried changing the access permissions on /var/www - no help.

Any ideas?

Thanks

Me <---- n00b

---

### Post by msgyrd on 2005-06-15
Append these two lines to the bottom of /etc/apache2/apache2.conf
```

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps

``` 
That fixed it for me.  Before I did that my browser just tried to download the php files.

---

### Post by LordHunter317 on 2005-06-15
If you have to edit a configuration file, you're doing something wrong.  Debian and Ubuntu comes out of the box to just work for this, no configuration changes needed.

Anyway, you probably need to run:```
sudo a2enmod php4
sudo /etc/init.d/apache2 restart
```And if you broke your permissions, fix them.  This is a configuration issue, not a permissions one.

---

### Post by zaphod288 on 2005-06-15
I am also having this problem with apache2 and php4.

I have installed Gallery,  I have tried both the Ubuntu package (gallery) and the latest stable source download from Gallery’s SF site.  Firefox, when I type the url with index.php on either install, wants to save the index.php and omitting the index.php firefox wants to download a random .phtml file. (I havent tried from a windows box yet)

I can't see how adding the AddType directive to the apache2.conf file makes any difference as they are (as said above out of the box) configured in /etc/apache2/mods-available/php4.conf which is parsed when the module is loaded, but I have tried this. Also the DirectoryIndex directive in the apache2.conf is already present, which also noticed has been mentioned alot.

I have done a test with an index.php (phpinfo) in the /var/www and strangely works ok, with all combinations, including index.php at the end url and omitting it.  This to me is indicating its not a problem with the config, apache is filtering .php files ok and working with directory index files ok. I then backed up the /var/www/gallery/index.php file and copy the one that works to this directory and the problem is there. But here it gets strange I use the same source for gallery on another linux distro and gallery works fine, using firefox on the ubuntu to browse it.

If anyone has any ideas I would love to hear from them as I am completely stumped, I can only assume that a default setting is causing something strange to happen.  Gallery forums, apache documents and these forums haven’t yielded any success.


Thanks

---

### Post by LordHunter317 on 2005-06-15
[QUOTE=zaphod288]
I can't see how adding the AddType directive to the apache2.conf file makes any difference as they are (as said above out of the box) configured in /etc/apache2/mods-available/php4.conf which is parsed when the module is loaded,[/quote]And it didn't do a thing.

>  I then backed up the /var/www/gallery/index.php file and copy the one that works to this directory and the problem is there.This implies one of a few things:[list][*]A mime type issue: where that file isn't being reconginized as PHP for some reason.  If you have mod_mime_magic enabled, disable it to see if the problem corrects itself.[*]A PHP bug where it's sending out the wrong content type for the generated script, but actually running it.  What type of file does Firefox say what it wants to download is.[*]It's also possible you have a configuration file overriding the setup badly.  I'd have to see the file containing the vhost with the gallery install and any related <Directory>, <File>, <Location> options that might be elsewhere to verify though.[*]Finally, if you somehow still have the worker MPM running (which ought to be impossible) it would cause no end of bad behavior.  Last time I checked, the packages explictly dep'd on apache2-mpm-prefork[/list]

---

### Post by zaphod288 on 2005-06-16
[QUOTE=LordHunter317]This implies one of a few things:[list][*]A mime type issue: where that file isn't being reconginized as PHP for some reason.  If you have mod_mime_magic enabled, disable it to see if the problem corrects itself.[*]A PHP bug where it's sending out the wrong content type for the generated script, but actually running it.  What type of file does Firefox say what it wants to download is.[*]It's also possible you have a configuration file overriding the setup badly.  I'd have to see the file containing the vhost with the gallery install and any related <Directory>, <File>, <Location> options that might be elsewhere to verify though.[*]Finally, if you somehow still have the worker MPM running (which ought to be impossible) it would cause no end of bad behavior.  Last time I checked, the packages explictly dep'd on apache2-mpm-prefork[/list][/QUOTE]

For mime type, that doesnt explain why the index.php works fine in the www root directory but wants to be downloaded when it is placed in the gallery directory.  I also dont have mod_mime_magic enabled.

Modules I have running are:

Loaded Modules 	core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_actions mod_cgi mod_include mod_php4 mod_rewrite mod_userdir


PHP bug is possible as I have found a lot of people in forums with the same problem, but I doubt it.


Firefox wants to download a .PHTML file from [http://xxxx.com/gallery/](http://xxxx.com/gallery/)  but if I specify index.php it works.  If I try and use the setup [http://xxx.com/gallery/setup/index.php](http://xxx.com/gallery/setup/index.php) it tries to download the index.php, but if I drop the index.php everything works ok. The problem with this is the setup is linked from gallery with the index.php.  As stated before gallery works fine on another linux distro, and I should be able to execute the index.php if I state it or not in the url as I have specified index.php in the DirectoryIndex directive in the apache2.conf.


For a config file overiding something regarding stuff outside of the webspace root directory, this is what I think the problem is, but I am unable to determine what I need to be looking for to fix this problem, I have tried just about everything I have come across that has to do with mime types and Index directories but nothing has made a difference. Exactly what conifg files regarding vhost could I post for you to have a look at?  I dont think gallery has any vhost related files, all other config files are at the moment in default.

As for MPM I have not come across this before, I will have to go and do some investigation (googling) about this, phpinfo doesnt indicate that i have this running.

Thanks

---

### Post by LordHunter317 on 2005-06-16
Your MPM is fine.

Post the /etc/apache2/sites-enabled/000-default file.  That's the default virtual host being served.  Post your DirectoryIndex line as is as well.

If there is an .htaccess file in the gallery webroot, post that as well.

Also, look for any messages in the error_log.

---

### Post by zaphod288 on 2005-06-17
Thanks for your reply, it got me thinking.  I found that I hadn't put an AllowOverride directive for the gallery directories in /etc/apache2/sites-available/default, it was indeed ignoring the gallery .htaccess files which gallery relies on.  By default the default file has /var/www/ set to AllowOverride None which would ignore all .htaccess files.

The interesting thing is that some of my other problems went away like my mod_rewrite issue, which I was sure would solve itself as soon as I worked out this index.php problem.

The index.php problem is still there though, Firefox is still trying to download the .php file rather than displaying it. I then tried from my XP machine and contected to Ubuntus apache2 server over the LAN and all works ok.  Im now know that this problem of not displaying index.php in gallery only exists with localhost from firefox, from any remote machine it works like its meant too, including a Debian machine.

I am still unsure what is causing this, the config files that you have asked for are all in default from install, I can still post them if you like but since remote machines can browse the server fine I can live with this little problem.  Im now unsure if its a Firefox config issue or a server issue.

Thanks

---

### Post by LordHunter317 on 2005-06-17
[QUOTE=zaphod288]  By default the default file has /var/www/ set to AllowOverride None which would ignore all .htaccess files.[/quote]And with good cause. I hope you created a new <Directory> entry for gallery and changed AllowOverride there, and didn't do it globally.

> The index.php problem is still there though, Firefox is still trying to download the .php file rather than displaying it.Did you hit F5 to force a refresh?

---

### Post by zaphod288 on 2005-06-18
Dont worry I did create directory entries to only allow overide on the gallery directory and setup directory.  Though it wouldnt matter too much, as this is for development and is only internal to my private LAN, so no security risk, but still nice to do it properly..  and for the F5 its not that, Ubuntu been on my laptop I have rebooted the box several times and still persists, Y it does it on localhost and 127.0.0.1 only, but works fine from a remote machine I still don't know and if I ever work it out I will post the reason, but as I stated before I have it working enough not to be a problem for me now and I can live with it the way it is.  Thanks for your help.

---

### Post by TheDanMan on 2005-08-30
Just wanted to say that this thread was very helpful.  I've used Ubuntu since just before Hoary was released and have loved it ever so much.  I just started switching away from RHEL for my servers here at work and decided to give Ubuntu a go on the server side too.  I couldn't believe how much easier it was to manage.  First hickup I had was PHP files downloading instead of rendering.  While I wasn't having the exact problems of anyone here, it did get me looking in the right places.

THANKS!

---

### Post by munkt0n on 2005-10-21
> If you have to edit a configuration file, you're doing something wrong. Debian and Ubuntu comes out of the box to just work for this, no configuration changes needed.

I've had exactly the same sort of problems, getting apache, php, mysql & phpmyadmin up and running has been a complete nightmare.
still to fix :

apache2 won't run at startup
mod_rewrite still not working

I seriously do not recommend breezy as a server, far too much hassle.

---

### Post by LordHunter317 on 2005-10-21
[QUOTE=zaphod288]D  and for the F5 its not that, Ubuntu been on my laptop I have rebooted the box several times and still persists,[/quote]You can't use a reboot to clear cache on a webbrowser.  You *must* hit F5.

---

### Post by irv on 2005-11-15
Sometimes the brain goes numb, and sometimes the light come on. I was having a problem with Apache2 and PHP4 and PHP5 on my desktop. I wanted to use it to test PHP coded pages before uploading them to my server. I had everthing loaded, I thought but I was wrong. I loaded php, MySQL, Apache2 etc but I loaded it on the server. The reason I was having problem on my desktop was because I forgot to load PHP on the desktop. After loading and restarting Apache, everything worked. Now you know why I said, sometimes the brain goes numb  ](*,)

---

### Post by PokerFacePenguin on 2005-11-16
[QUOTE=Nada_Surf]Ive just installed apache2 and php4 as directed at [http://ubuntuguide.org/#installapachehttpserver](http://ubuntuguide.org/#installapachehttpserver)

Apache seems to install fine, but when i try to test the php my browser downloads the php file instead of running it on the server!

What could be the problem?  I have shared the /var/www directory via samba, but even when disabling this share it still doesnt work.  I also tried changing the access permissions on /var/www - no help.

Any ideas?

Thanks

Me <---- n00b[/QUOTE]


Before I found this post I further borked my firefox by choosing "open file with firefox" and checked the box that keeps doing that in the future...how would I undo this stupid thing I did?

---

### Post by PokerFacePenguin on 2005-11-16
I fixed this one by going into firefox and choosing edit >> preferences >> downloads

stupid stupid me......lol

---

### Post by circlecast on 2005-11-25
OK I have done everthing everyone has posted on here and I am still getting the same problem the php files download. But I decided to try using IE and some of my other browsers to see if I can get something through them and in IE I am getting this
> 
**Warning**:  Unknown: failed to open stream: Permission denied in **Unknown** on line **0**
 
 **Warning**:  Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in **Unknown** on line [B]0
[/B]
 in Opera I get the samething So maybe this will help

---

### Post by PokerFacePenguin on 2005-11-25
[QUOTE=circlecast]OK I have done everthing everyone has posted on here and I am still getting the same problem the php files download. But I decided to try using IE and some of my other browsers to see if I can get something through them and in IE I am getting this

 in Opera I get the samething So maybe this will help[/QUOTE]


I wrestled with this problem for days.  Ultimately what it came down to for me...even after I had PHP working under apache2 was that an install of regular apache will break your php by whacking your configuration filies even after you have it working.  So my suggestion is to uninstall them all.....full uninstall....all config files...uninstall apache, apache2, php, not really necessary for MYSQL, and reinstall the ones that you want.  Dont let the dependencies get taken care of by installing meta packages....

---

### Post by Zaitzev on 2005-11-29
Hi.

I have basically the same problems on my newly installed Apache2;

After following the guides, installing all the necessary packages (and probably then some!), the server works, except from PHP.
I also did put in the 'AddType' in apache2.conf, without any change.
Then, I tried the ' sudo a2enmod php4' command, which resulted in "This module does not exist!" - What's up with that?

I believe I have installed everything necessary. However, I haven't configured anything. I've heard that compiling php manually is necessary?

So, after banging my head on a brick wall over this, I can't say that I have come any further than having lots of bruises on my forehead :P

---

### Post by circlecast on 2005-11-29
I have looked at this and come close to getting banned by google for hitting the site too much looking for a reason as to why this is coming about. the only thing I can think of is reinstall hoary and wait about another month and try it again. I am not giving up I will still be looking but I have to have my testing server back

---

### Post by ndtoan13 on 2005-11-29
[QUOTE=zaphod288]Dont worry I did create directory entries to only allow overide on the gallery directory and setup directory.  Though it wouldnt matter too much, as this is for development and is only internal to my private LAN, so no security risk, but still nice to do it properly..  and for the F5 its not that, Ubuntu been on my laptop I have rebooted the box several times and still persists, Y it does it on localhost and 127.0.0.1 only, but works fine from a remote machine I still don't know and if I ever work it out I will post the reason, but as I stated before I have it working enough not to be a problem for me now and I can live with it the way it is.  Thanks for your help.[/QUOTE]

Try to by pass this in firefox Lan Setting (even you dont need proxy, but turn it on then bypass localhost, then turn it off). 
Hope this help.

---

### Post by djpeanut on 2005-11-30
Just thought I'd add my version of this problem/solution.  I began by uninstalling php5 in favour of 4 so I could test my web development project under the same conditions as my hosting provider.  Using Synaptic, I uninstalled 5 and installed 4 at the same time (probably the first mistake).

After having done that, PHP4 didn't load as a module in Apache2, meaning that Firefox tried to download index.php contained within when I clicked on a subdirectory within localhost/~user/.  This also happened with the phpMyAdmin subfolder.  I tried to get PHP4 working and couldn't.  When I tried uninstalling it I hit an error with phpmyadmin's installation script, which I fixed using the technique above.  

So I then reinstalled PHP5, got it working, and found that Firefox was still trying to download my index.php files from the aforementioned directories.  It worked fine if I specified the filename, and worked fine with other subdirectories.  I solved the problem by changing the names of the 2 affected subdirectories.  (The problem returns, however, when I change them back - most mysterious!)

---

### Post by goneskiing on 2005-11-30
[I]circlecast
I have looked at this and come close to getting banned by google for hitting the site too much looking for a reason as to why this is coming about. the only thing I can think of is reinstall hoary and wait about another month and try it again. I am not giving up I will still be looking but I have to have my testing server back[/I]


Yeah, we've been doing the same thing hoping to avoid wasting time switching to another distro but the witching hour has come - we tested Fedora 4 and everything works fine so it's time to say goodbye to Breezy.

---

### Post by el_joelo on 2005-12-13
Ok,
I'm going to throw in my two cents about this problem...  my when I try and start apache2 it fails however running /etc/init.d/apache start works fine.

Where is what starts at boot specified anyways??  
inetd.conf doesn't even mention apache.

I don't know if this will cast any light on the issue, deepen the mystery or maybe just make me look ignorant :-)

edit: actually apache2 was a perl problem looking at the logs.  It didn't fix anything, now instead of saying the type of file is phtml firefox claims that it is wml.

---

### Post by danaktivix on 2005-12-13
Allo! Newbie here. 

Having tried everything the various forums say, I still can't get PHP 4 working. (I want to use 4 coz I want a dev version of a PHP4 joomla site I'm running...)

Someone else has mentioned this:  I installed apache 2, but apache tells me its running Apache/1.3.33 Server at localhost Port 80, not Apache 2.

That would seem to be the obvious thing - which someone mentioned on a forum - or am I missing something really obvious?

How do we get apache 2 to actually run? Tried uninstalling 1, but then everything went awry.  Am I being daft?

---

### Post by PokerFacePenguin on 2005-12-13
Try uninstalling all apaches and install apache2-mpm-prefork instead of just plain apache2 package.  Then install php4....if apache gets installed over apache2 it really borks up your configuration...at least that has been my experience.

---

### Post by andlinux21 on 2005-12-14
i tried all the above and still cant get php recognized it keeps trying to download the file.  I am trying to install mambo i had it running before on my SuSE box but  this is really becoming difficult on ubuntu
:confused:

---

### Post by nisit on 2006-02-25
Ok Linux free ,good
but when config it like talk Alean!
why hard to install some Prgram
windows i click next and ok
I don't khow why developer like
key gdfhggfjgfj???????
and asdgg???????
for take it

---

### Post by dbee on 2006-02-26
I've been wrestling with LAMP on ubuntu for ages now. And have wasted countless hours on it's eccentricities. Using RH couldn't be simpler for the same tasks and allows me to get on with my real work.

I wish someone would sort out this issue once and for all...

---

### Post by krewemaynard on 2006-02-28
[QUOTE=dbee]I've been wrestling with LAMP on ubuntu for ages now. And have wasted countless hours on it's eccentricities. Using RH couldn't be simpler for the same tasks and allows me to get on with my real work.

I wish someone would sort out this issue once and for all...[/QUOTE]

Done: [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

I was hitting a wall after I re-installed my server recently, when I stumbled across this page. Simple, straight forward, and I can honestly say it works.

---

### Post by RSchrock on 2007-12-08
After I made sure I had all of the packages installed (from the posts above), this is what finally did it for me:

Troubleshooting

Does your browser ask if you want to download the php file instead of displaying it? If Apache is not actually parsing the php after you restarted it, install libapache2-mod-php5. It is installed when you install the php5 package, but may have been removed inadvertently by packages which need to run a different version of php. You may also need to actually enable it, by doing sudo a2enmod php5 followed by sudo /etc/init.d/apache2 restart. Be sure to clear your browser's cache before testing your site again. 

Good Luck!

---

