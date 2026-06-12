---
title: "Ubuntu-hylafax-avantfax"
date: 2008-08-04
forum: Server Platforms
---

### Post by VdubZA on 2008-08-04
Can someone put together a step by step guide on this installation please.
I have gone thru a couple on the web and there seem to be bits missing where it is assumed you should know what to do next.
I am new to the Linux scene so need to be spoon fed.:)

I have got the server up and running with Hylafax and modems connected and configured. The fun begins when Avantfax has be installed this is where the wheels fall off.

Any assistance will be appreciated.

---

### Post by VdubZA on 2008-08-06
New to Ubuntu and Linux for that matter so can't give an exact reason how I fixed it.
But I downgraded to Ubuntu Server 7.10 and all is working!!

---

### Post by pkombala on 2008-08-16
Fatal error: Smarty error: unable to write to $compile_dir '/var/www/avantfax/includes/templates/main_theme/templates_c'. Be sure $compile_dir is writable by the web server user. in /var/www/avantfax/includes/Smarty/Smarty.class.php on line 1092



please give avant help two weeks i am trying ti install avantfax for hylafax I have phpmyadmin installed and working fine please give me how to intall avantfax on ubuntu 8   help me

---

### Post by pkombala on 2008-08-16
please help me to install avantfax on ubutu 8.....  two weeks i am trying ..
hylafax is working fine with win print client.....LAMB server installed 
phpmyadmin is working fine ........give me step by step help 

i am not a Linux expert ... time wested ......



Fatal error: Smarty error: unable to write to $compile_dir '/var/www/avantfax/includes/templates/main_theme/templates_c'. Be sure $compile_dir is writable by the web server user. in /var/www/avantfax/includes/Smarty/Smarty.class.php on line 1092

---

### Post by pkombala on 2008-08-17
I found this link after two days 

[http://howtoforge.com/build-a-hylafax-server-with-avantfax-on-debian-etch](http://howtoforge.com/build-a-hylafax-server-with-avantfax-on-debian-etch)

some command I don't know .....


Edit create_tables.sql to use avantfax database:

# nano create_tables.sql

Add "USE avantfax;" to top.

Edit setup.sh to chown to "root.root":

# nano setup.sh

Change apache.apache to "root.root".

Run the setup script:

# ./setup.sh

Add two scripts to root's crontab:

# crontab -e



please check that link and let me now  how to solve 


My self I contact avantfax website thy told they don't have 
any support for ubuntu .....
please help me .......

---

### Post by dark_to on 2008-09-26
Its a file permission problem. I solved the problem doing this:

cd /var/www/avantfax/includes/templates/
chown -R www-data main_theme/


This can also be done at a higher level in the directory structure (/var/www), as it's safer that all files served by apache are owned by the user running apache service (in this case www-data)

Hope this helps 

:guitar:

---

### Post by comprx on 2008-09-28
Here is a question I feel must have an easy answer however I dont know it. Once the server is installed and up. how do you tell it where to send the incoming fax's? (IE the email address)

I searched hi and low and found this thread:
[http://ubuntuforums.org/showthread.p...hlight=hylafax](http://ubuntuforums.org/showthread.p...hlight=hylafax)

which led me to these directions:
> "Create the file etc/FaxDispatch (usually /var/spool/hylafax/etc/FaxDispatch) so that it contains the following lines:

FILETYPE=tif;
SENDTO=FaxMaster;

Substitute pdf or ps for tif as you desire. "

Does this just mean I substitute "faxmaster" with the email address of the fax recipient?

---

### Post by mamut0o1 on 2008-10-09
> **comprx said:**
> Here is a question I feel must have an easy answer however I dont know it. Once the server is installed and up. how do you tell it where to send the incoming fax's? (IE the email address)

I searched hi and low and found this thread:
[http://ubuntuforums.org/showthread.p...hlight=hylafax](http://ubuntuforums.org/showthread.p...hlight=hylafax)

which led me to these directions:


Does this just mean I substitute "faxmaster" with the email address of the fax recipient?

Once you installed Hylafax; you can install a webinterface such as avantfax and your email get deliver straigh to your "inbox".
from there you can even tell avantfax to send faxes to different e-mail accounts by setting up rules.

mamut

---

### Post by comspol on 2008-10-12
New to Linux in general, but I have gotten pretty far with this setup reading these forums.  Thanks to everyone who gives their time to educate the rest of us!

Background:

I have successfully setup Ubuntu server, with Hylafax.  I used Winprint Hylafax as the client.  Everything worked great!  Then we decided to add Avantfax as a front end to monitor the queues, have web based faxing available, and have a central point to manage inbound faxed on the web.

So far I have it all up and working except just a few minor tweaks, that I cannot seem to find out how to work out.

#1.  We cannot delete killed or failed faxes out of the outbox on Avantfax .  In the logs I get an error like so: 

FQ>killjob (jid 35): Admin failed: 530 Password incorrect. (userID)

I have matched userID PW’s for Avantfax, and hylafax, I have tried making users Admins in Hylafax, then back to standard users, I have checked to see that www-data is a user in hylafax.

If I send a fax from computer A using Winprint it goes to the outbox queue visible in Avantfax.  If I try and kill that job using the Avantfax web interface it generates the above error.

#2  The # of times it is listed as retrys is 12, I’ve changed that in the config files, but it still shows up as 1:12  in the outbox (indicating 1 of 12 retries I suppose?) of Avantfax web interface.

I’ve tried to fix this myself, but I can’t seem to find the issue.  Any help would be greatly appreciated.

AA

---

### Post by gizmobay on 2008-11-03
1. AvantFax is fussy on where your user is in the hosts.faxd file. The www-data must be the first line after the comments and then the next line must be 127.0.0.1. I also found that it works better if you use the faxadduser command versus manually editing the file.

2. There's a setting in the hylafax config file that you can change the number of retries.

---

