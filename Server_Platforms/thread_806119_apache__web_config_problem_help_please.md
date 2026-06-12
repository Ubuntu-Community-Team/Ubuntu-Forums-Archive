---
title: "apache / web config problem help please"
date: 2008-05-24
forum: Server Platforms
---

### Post by Corrupter on 2008-05-24
Hey guys, i was wondering if anyone here had any experience with the guide for the perfect web server over at [http://howtoforge.com/perfect-server-ubuntu8.04-lts](http://howtoforge.com/perfect-server-ubuntu8.04-lts)

I followed it through to completion quite easily and am pleased with the result however i suspect the guide was missing something and i'm not quite sure what, perhaps you can help me solve the problem.

Ok, so i'll try to lay this out as best i can:

all is installed and configure to the letter, no errors, server works flawless, one exception, i have ISPConfig installed, configured a reseller, no problem, client, again, no problem, website, again, no problem... heres where i get stuck.

The website is up and running on my local network, dns name and all... i copy SMF over via ftp using the username i created in ispconfig and touched [www.myweb.com/install.php](www.myweb.com/install.php)   followed steps (no problem)  sql database is also already made in ispconfig so everything up to this point is flawless, one exception however.

i go into the admin panel of smf, upload tiny portal as a new package, says tiny portal 0.98 is in but the forum never applies... ok maybe a refresh, reboot, sometihng (tried those)  nothing, then i tried to apply a new theme, uploaded it via the browse button, says it goes in, recognizes the files etc... i force it as the theme... and the forum goes to text mode since it cant find the theme files... ok, so all that prep reading for my problem, im sorry =P

the problem is, even though i was able to copy over the original smf files and install successfully, when using the forum to upload new packages / themes it either doesnt install them properly or something because when i go back to ftp and look at the theme directory to see if the files are there the directory is made but the forum wasnt able to extract the new files into the new theme directory, is this some kind of permission lacking in ISPConfig or perhaps some kind of permission for the .zip files they need?

i also (as a side note)  tried to unzip the files manually on my end and upload them via ftp to the directories where they are suppose to go and i get permission denied, tried chmod'in the directories, nothing... im at a stand still.

thoughts?  if this was hard to understand i can perhaps fraps a video from start to finish of everything i try... i just gotta download fraps lol.

---

### Post by windependence on 2008-05-24
It looks like a permissions issue. Read the SMF and TinyPortal instructions very carefully. Somewhere in there they tell you to set some files to 775 or 777 I can't remember, but I am pretty sure your TP can't install because of permissions. Also you can go in and view your error log in SMF, it's in the admin panel. Good luck!

-Tim

---

### Post by Corrupter on 2008-05-25
well SMF wouldnt have the ability to not allow new files to be copied to the server via ftp using the admin account right?

so wouldnt that point to some kind of misconfiguration or error with apache or user permissions? 

there is an error in the server log but its not related to TP at all only when i attempted to use a theme that wasnt there.

thoughts?

---

### Post by windependence on 2008-05-25
> **Corrupter said:**
> well SMF wouldnt have the ability to not allow new files to be copied to the server via ftp using the admin account right?

so wouldnt that point to some kind of misconfiguration or error with apache or user permissions? 

there is an error in the server log but its not related to TP at all only when i attempted to use a theme that wasnt there.

thoughts?

In your first post you said you copied everything over and installed it but it just wasn't applying to your SMF installation. maybe I misunderstood you. I am running the same setup you are and although it was back in November, I seem to remember changing some permissions on the files. So you are saying that you can't even upload TP, or just that when you install nothing happens. If that's the case the admin panel canot access your uploaded files because of a permissions issue. It could also be an ownership issue, but I think if you chmod thm to 775 or 777 that should work.

-Tim

---

### Post by Corrupter on 2008-05-25
yea odd, i tried chmod'in the themes directory, but then also i'd have to chmod the temp dir that it unpacks the new themes to, i have a post in at the smf forums and so far they are scratching their heads too.

the bottom line is that it seems like something doesnt have a permission to unpack the files to their new location, the forum says its installed them correctly which would indicate that the forum is going through the steps to extract the files to their new location.

i am getting some forum errors, the first one is:
[http://www.apoworking.org/index.php?action=theme;sa=settings;th=4;sesc](http://www.apoworking.org/index.php?action=theme;sa=settings;th=4;sesc)  
2: file_exists() [<a href='function.file-exists'>function.file-exists</a>]: open_basedir restriction in effect. File(/Themes/mesh114/Settings.template.php) is not within the allowed path(s): (/var/www/web9/)
File: /var/www/web9/web/Sources/Load.php
Line: 1453 

funny thing is i know that the safe mode is set to off in php.ini so i dont know why that second error is occuring...
 
then i tried a different theme and got:
[http://www.apoworking.org/index.php?action=theme;sa=install](http://www.apoworking.org/index.php?action=theme;sa=install)  
2: mkdir() [<a href='function.mkdir'>function.mkdir</a>]: SAFE MODE Restriction in effect. The script whose uid is 10006 is not allowed to access /var/www/web9/web/Themes/invazion114 owned by uid 33
File: /var/www/web9/web/Sources/Subs-Package.php
Line: 1232

---

### Post by windependence on 2008-05-26
OK, Paste the following code into a text editor. and save it as phpinfo.php:

```
<?php

phpinfo ();

?>
```

Then, put the file in the root directory of your web server. After you do that, go to [http://yoursite.com/phpinfo.php](http://yoursite.com/phpinfo.php) but substitute your actual site name for "yoursite". You will get a page displaying all of your php options. Check to make sure it says safe mode is NOT enabled and let me know. If it is enabled we have more work to do.

-Tim

---

### Post by Corrupter on 2008-05-26
i remember making sure it was set to OFF in php.ini when i installed smf but i'll make a phpinfo page just for kicks (who names maybe i hit a comma or something =))

Edit::

local value set to on, master value is off... now im confused =P

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> i remember making sure it was set to OFF in php.ini when i installed smf but i'll make a phpinfo page just for kicks (who names maybe i hit a comma or something =))

Edit::

local value set to on, master value is off... now im confused =P


If I remember right Apache2 has some sort of double configuration and you may have turned it off in the wrong file....there's a number of possibilities, but we have to test with the script to see if it's actually ON or OFF and then we can go from there.

-Tim

---

### Post by Corrupter on 2008-05-26
local value set to on, master value is off... now im confused =P

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> local value set to on, master value is off... now im confused =P


Hmmmm, not sure myself. I host all my sites on Apache 1.3 which is still a current release. There is an Apache 1 branch and an Apache 2 branch and everyone has their own opinion but I think Apache 1 is much simpler. 

Anyway, let me research this and get back to you as soon as I find an asnwer.

-Tim

---

### Post by Corrupter on 2008-05-26
Tim, you sir, are the man, i appreciate you helping me out like this.

Thanks windependence !

frankly i understand the basics of web hosting and web administration but im no guru, i really do appreciate your help.

---

### Post by windependence on 2008-05-26
By any chance are you running ISPconfig?

-Tim

---

### Post by Corrupter on 2008-05-26
yea ISPConfig2.2.23 i think is the release.

---

### Post by windependence on 2008-05-26
Ahhh answered my own question by re-reading your first post. 

You have to turn off safe mode in ISPconfig. There is a setting in ISPconfig for safe mode. You need to uncheck the box.

-Tim

---

### Post by Corrupter on 2008-05-26
ok so Tim, i feel like a total jacka$$, you know how sometimes you get in such a haste to get things done you breeze through some things, when i made a new hosting plan i checked all the boxes thinking i wanted everything, never even saw the safe-mode setting... i feel just silly.

regardles i really appreciate you pointing this out, think i'll go toy with the site to make sure there are no more bugs.

Thanks again... i really appreciate you taking the time to baby me a bit.. some days we just have those days... =)

now all i have to do is figure out if its safe to try and load ubuntu desktop onto this box so i can use some other window type based applications... any suggestions?  hehe

---

### Post by Corrupter on 2008-05-26
well it looks like you solved my problem as far as themes and such are concerned Tim, thanks pal.  However i seem to have a new problem which appears to be the last problem i should have, regardless it doesnt really apply to ubuntu but i'll ask you since you seem knowledgable however i have posts in at SMF and Tinyportal to see if anyone there knows the answer.

The only problem i have now is i am able to upload Tinyportal .9.8 to the web, it now shows that i can apply the mod, so i hit it, it asks for ftp info so it can do its thing, i give it, it goes through its test page where it shows everything is successful as a test, i hit install and i get an Internal Server Error 500 and a timeout.  i refresh, nothing.  i go back to basic index.php and back into admin and it shows mod not applied.  the errors listed are basically the same 2 over again.. 

 [http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip](http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip)  
2: gzwrite(): supplied argument is not a valid stream resource
File: /var/www/web9/web/Sources/Subs-Package.php
Line: 2091 

and

[http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip](http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip)  
2: require(/var/www/web9/web/Packages/temp/./tp_install.php) [<a href='function.require'>function.require</a>]: failed to open stream: No such file or directory
File: /var/www/web9/web/Sources/Packages.php
Line: 552 

i really wish i had more experience, i'll understand if you point me to smf or tinyportal site =)

---

### Post by windependence on 2008-05-26
Hey don't worry, how would you have known? 

I wouldn't run a GUI on my server if it was me but if you must run something like that, I would install Wemin and access it from another machine, or if you must, use XCFE or WindowMaker.

Good Luck!

-Tim

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> well it looks like you solved my problem as far as themes and such are concerned Tim, thanks pal.  However i seem to have a new problem which appears to be the last problem i should have, regardless it doesnt really apply to ubuntu but i'll ask you since you seem knowledgable however i have posts in at SMF and Tinyportal to see if anyone there knows the answer.

The only problem i have now is i am able to upload Tinyportal .9.8 to the web, it now shows that i can apply the mod, so i hit it, it asks for ftp info so it can do its thing, i give it, it goes through its test page where it shows everything is successful as a test, i hit install and i get an Internal Server Error 500 and a timeout.  i refresh, nothing.  i go back to basic index.php and back into admin and it shows mod not applied.  the errors listed are basically the same 2 over again.. 

 [http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip](http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip)  
2: gzwrite(): supplied argument is not a valid stream resource
File: /var/www/web9/web/Sources/Subs-Package.php
Line: 2091 

and

[http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip](http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip)  
2: require(/var/www/web9/web/Packages/temp/./tp_install.php) [<a href='function.require'>function.require</a>]: failed to open stream: No such file or directory
File: /var/www/web9/web/Sources/Packages.php
Line: 552 

i really wish i had more experience, i'll understand if you point me to smf or tinyportal site =)

Hey we're not giving up here man. Have you googled any of those errors you are getting? Try them exactly as you are seeing them and see what you find. Meantime I will see what I can find also.

-Tim

---

### Post by Corrupter on 2008-05-26
ok i did google some things but my in-experience with php errors and such didnt get me much further, however i began to thinking about my previous problem and the fact it was basically permission based (aside from the fact the permissions were restricted by safe mode)  the symptoms are somewhat similiar.  So i checked the packages directory, no temp directory which should be created every time a package is uploaded and attempted to be extracted... i checked the Packages dir chmod and it says 777, so i thought hmm... why no temp dir then.  i made a temp dir, attempted to install the package and it went in... but it didnt seem to be actually in so i removed it, im trying to replicate what happened cause frankly im confused as hell.

yea confirm it goes in when i manually make a temp dir and set its chmod to 777 however the mod says its in as i can now uninstall it but i do not see any tiny portal effects, the forum seems to just be the forum with a new error message
[http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip](http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip)  
512: package_flush_cache(): some files are still not writable
File: /var/www/web9/web/Sources/Subs-Package.php
Line: 1905 

which if i am assuming correctly has something to do with yet another permission not being able to purge the forum files to load in the new ones...

im beating my head on this one, why am i the only one having so many permission related problems... lol  i followed the perfect server stuff to the T.

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> ok i did google some things but my in-experience with php errors and such didnt get me much further, however i began to thinking about my previous problem and the fact it was basically permission based (aside from the fact the permissions were restricted by safe mode)  the symptoms are somewhat similiar.  So i checked the packages directory, no temp directory which should be created every time a package is uploaded and attempted to be extracted... i checked the Packages dir chmod and it says 777, so i thought hmm... why no temp dir then.  i made a temp dir, attempted to install the package and it went in... but it didnt seem to be actually in so i removed it, im trying to replicate what happened cause frankly im confused as hell.

yea confirm it goes in when i manually make a temp dir and set its chmod to 777 however the mod says its in as i can now uninstall it but i do not see any tiny portal effects, the forum seems to just be the forum with a new error message
[http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip](http://www.apoworking.org/index.php?action=packages;sa=install2;package=TP_0983.zip)  
512: package_flush_cache(): some files are still not writable
File: /var/www/web9/web/Sources/Subs-Package.php
Line: 1905 

which if i am assuming correctly has something to do with yet another permission not being able to purge the forum files to load in the new ones...

im beating my head on this one, why am i the only one having so many permission related problems... lol  i followed the perfect server stuff to the T.

You should not have to create any directories when installing TP or SMF (which are both great BTW). Check the ownership of the directories as well, and I'm talking about the directories under your web root directory. You may also want to repost over on the TP forums as well with your current error. I am still working on this also, but since things are pretty mucked up, you may want to consider doing a fresh install of SMF and TP after removing all the old files, but read the installation instructions carefully, I am sure there were permissions I had to either check or change to install TP.

-Tim

---

### Post by Corrupter on 2008-05-26
yea i have posts in at both smf and tp, and i love both of those btw, i've used them before for some time however never had to configure the server side of these things because i've always used a paid server.  Now that im a bit shorter on change and i have the tech to host a local server i figured it'd be a great place to work on my projects till i can afford they be live.

Anyway TP says its definitly a server permission problem... kinda obvious although i asked if they know which and where so i can change it, no response yet... and on a side note both installs for SMF and TP permission wise state that the package manager should be able to handle any thing that the forum is dealt as long as it has the permissions... so it would almost seem that some other php option or permission in ispconfig or something is screwing with my install.

I am this close to blasting it all away (server and all) and starting from scratch but i'd much rather learn from this problem then face the potential of running into it again. =)

Thanks again Tim, btw when this is all over im gonna offer you my first born.

---

### Post by Corrupter on 2008-05-26
just curious, what version of SMF are you using?  i think im begingin to see a pattern for people posting problems with the 1.1.5 smf that perhaps there may be something screwy.

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> just curious, what version of SMF are you using?  i think im begingin to see a pattern for people posting problems with the 1.1.5 smf that perhaps there may be something screwy.

I'm using 1.1.4 for a while now, and 0.98 TP. 

I'm not sure why everybody seems to be installing ISPconfig. Maybe it's in the perfect web server tutorial, I'll have to look at that but for just a single server, it's not necessary and probably gets in your way a bit.

I just got off from work (I work mostly nights and have a consulting biz on the side) so I will be sleeping soon but I will be on the forums again tonight so we can work on this more then also. First born not necessary, thank you is fine. :) People have helped me many times on forums so this is my way of giving back if you wanna put it that way.

-Tim

---

### Post by Corrupter on 2008-05-26
the only reason i chose to go with the ISPConfig is for the unlimited sites i can host and when i create a new site there are alot of things i would of had to do for each that is done automatically.  I wouldnt say its super, but for hosting 3-5 sites on the same server for testing and config purposes it seems like it could work well, just as soon as i iron out these few glitches.

Rest well.

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> the only reason i chose to go with the ISPConfig is for the unlimited sites i can host and when i create a new site there are alot of things i would of had to do for each that is done automatically.  I wouldnt say its super, but for hosting 3-5 sites on the same server for testing and config purposes it seems like it could work well, just as soon as i iron out these few glitches.

Rest well.

Virtual hosting is rather simple, you just add another <virtualhost> directive to your httpd.conf and create the root directory for your new site and your done. I can understand if you were hosting 100s of sites but for 3-5 sites I think it's probably overkill.

-Tim

---

### Post by Corrupter on 2008-05-26
i'd have to make a dns record as well.

and im not too keen on ftp permissions and usernames atm as it would be nice to access all sites from one ftp username but i also like that they are seperate as that allows me to keep things organized and seperate.

much above that i dont know what else i'd have to do.

---

### Post by windependence on 2008-05-26
> **Corrupter said:**
> i'd have to make a dns record as well.

and im not too keen on ftp permissions and usernames atm as it would be nice to access all sites from one ftp username but i also like that they are seperate as that allows me to keep things organized and seperate.

much above that i dont know what else i'd have to do.

Well you shouldn't have to muck with DNS at all, just point your new site's A record at your server's IP, which you have to do anyway.

I don't ftp to any of my sites, I use ssh or winscp (from a Windoze box) and I push the files that way....much more secure. Of course, I use a text editor to develop my site too, but I'm a bit hard core :)

-Tim

---

### Post by Corrupter on 2008-05-26
t-e-x-t eh-di-tor?

whats one of those?

lol awesome man, yea i use ftp cause its easier to manage for me and most of my friends (on the odd chance i need them to log into something) already know how to use ftp, re-training them on even the simpliest things is like trying to teach a monk what a television is.

---

### Post by Corrupter on 2008-05-29
ok so i've been experimenting with this thing for 2 days and im STILL having trouble.  I am completely out of ideas as well as stumped, frustrated and confused.

I decided to blast away the entire forum and sql database and start from scratch as far as the web forum is concerned.  i had permissions to delete all the folders but the Themes folder, however i never changed the permissions on the Themes folder.  Kept saying permission denied on the ftp client.  Same thing when i tried to chmod it to 777 so i could delete it.

still didnt delete but since it was only the themes directory i copied in the smf 1.1.4 version, tried the TP and still got a internal 500 error.

Maybe something isnt chown'd right somewhere?  i have no idea.

Any thoughts?

---

