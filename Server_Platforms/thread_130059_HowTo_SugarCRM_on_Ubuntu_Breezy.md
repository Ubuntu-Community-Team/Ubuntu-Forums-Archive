---
title: "HowTo: SugarCRM on Ubuntu Breezy"
date: 2006-02-15
forum: Server Platforms
---

### Post by alamba on 2006-02-15
Hi All,

Let's just dive in straight into the steps taken to install:

1. Built a clean machine with ubuntu "regular" install.
2. Updated packages and kernel as told by synaptic.
3. Installed the header files for the kernel being used.
4. sudo apt-get install ssh
5. sudo apt-get install apache2
6. sudo apt-get install mysql
7. sudo apt-get install php5
8. Downloaded Full Installation Package for SugarCRM 4.0.1
9. sudo apt-get install postfix
10. sudo apt-get install php5-mysql
11. sudo apt-get install php5-common
12. sudo apt-get install php5-imap
13. sudo apt-get install php5-curl
14. sudo apt-get install curl
15. Copy the SugarCRM package into /var/www/apache2
16. unzip sugarsuite-4.01a.zip
17. chown -R www-data sugarsuite-4.01a.zip
18. vi /etc/php5/apache2/php.ini
19. In the memory allowed section, change from 8M to 20M
20. From a brower: [http://localhost](http://localhost)
21. Browser to the sugarcrm directory...follow straight forward instructions...couple of next next next...and u're done!!

Good luck!

Akshay Lamba

---

### Post by snowjunkie on 2006-02-24
It will be good to see the final version of this HowTo.  It would be good to include which steps are optional (e.g. SSH).  I appreciate you sharing this with us.

---

### Post by alamba on 2006-02-25
Will do buddy. I have to do another installation of SugarCRM shortly, currently getting the physical server in place. As soon as I have that I'll update this howto. Thanks for the suggestion - I'll definately mark the steps that are optional. From memory, the following are a must:
1. Curl
2. PHP
3. Apache
4. mysql
5. php-curl

Some steps are optional in terms of functionality of the package, i.e. postfix is needed only if you wish to run email campaigns from within sugar. Also I believe the php.ini memory setting from 8M to >20M is optional but highly recommended (even the sugar installer checks for this however allows you to proceed even if this condition is not met). I have had a few cases of the installation failing specially when loading demo data if this number is not >20.

Akshay

---

### Post by brok3n on 2006-03-08
<--- anxiously awaits your update on this howto. :D

---

### Post by 11hjpphty76lkjj on 2006-03-08
Any reason you don't put the command in this sort of sequence?

```

sudo apt-get install ssh apache2 mysql php5

```

instead of

sudo apt-get install ssh
sudo apt-get install apache2
and so forth.

Just curious.

Aaron

---

### Post by alamba on 2006-03-09
Kalo: No buddy...no specific reason. I just listed out commands I use. Easier on the eye for a newbie to understand what's being accomplished by those commands. Structures the thought process a bit.

A

---

### Post by 11hjpphty76lkjj on 2006-03-09
Good point!  And good for repetition so they remember the command in the future.

Aaron

---

### Post by alamba on 2006-03-12
Just realized some very interesting coding done by SugarCRM team. They have a "Powered by SugarCRM" logo on every page and if you try to remove that logo the system doesn't let you log in until you restore it. Ofcourse this isn't true for the company logo and sugarsuite logo. 

A

---

### Post by snowjunkie on 2006-03-29
I installed mysql and curl, but sugar crm can't see them...  any ideas?  Also I'm pretty sure I changed the memory to 20MB in the php.ini file, but sugar crm is not seeing that either.

Update:
Ok, I rebooted and all is fine now except for Writeable Custom Directory, Writable Modules Sub-Directories and Files, Writeable Data Sub-Directories and Writeable Cache Sub-Directories.

Can anyone help...  I tried chmod -R www-data sugarsuite-4.01a.zip but it didn't like the "www-data" part.  What is the purpose of this command anyway?

---

### Post by alamba on 2006-03-30
Hi Snow, the purpose of the chown command is to change the ownership of the sugarsuite directory to the apache user. This way the web server is able to get access to those files. www-data is the user used for apache2, incase you've installed another version the user might be different. Do the following:
1. ps -ef | grep apache 
2. ps -ef | grep httpd

One of them should give you a few lines of output that would give a username on the left most column. See that username and substitute in the above chown command and you should be good to go. 

A

---

### Post by snowjunkie on 2006-03-30
Hi alamba,
Should it be chown, rather than chmod?  I used chown and it worked ok for me.  Sugar CRM is now up and running just fine.  Thanks for the HOWTO...

---

### Post by alamba on 2006-03-31
You're abosultely right snow. It should be chown. I have corrected the post.

A

---

### Post by snowjunkie on 2006-04-02
[QUOTE=alamba]You're abosultely right snow. It should be chown. I have corrected the post.

A[/QUOTE]

You need to correct your original post also!  :)

---

### Post by alamba on 2006-04-03
Done. Thanks!

A

---

### Post by alamba on 2006-04-09
Just installed ver 4.2.0. Will post some code I learnt for an effective mysql backup and installing a clean install rather than an upgrade. The upgrade broke for me.

A

---

### Post by alamba on 2006-04-22
One technique I used to backup and upgrade the SugarCRM installation when the upgrade broke from 4.0.1e to 4.2.0:

1. Backup the database:
mysqldump -u root --opt sugarcrm > backup-file.sql

2. Restore to a new mysql database:
mysql sugarcrm < backup-file.sql

3. Post installation of the 4.2.0 version in a similar manner as stated above, you can log in with users created in the old database.

A

---

### Post by antiliphe on 2006-04-22
Thanks for your help :D 
Im not getting any errors from my Sugar Installation now.
I'll test it out later and see how it works out :)

---

### Post by alamba on 2006-04-25
antiliphe: Make sure that you change your root passwd for mysql. It is blank by default.

A

---

### Post by Pauliehaha on 2006-04-30
Hi, 

Is PHP 5 a requirement for SugarCRM?

I have PHP 4.4.0 which I need for another web application I am running on Apache. Does anybody know if I can install SugarCRM with this version?

An older version of SugarCRM would do as I just want to try it out first.

Alternatively can I run multiple versions of PHP with my other app using the older version, 4.4.0 and the CRM using the newer version, 5?

I think my box meets the other requirements, where can I find these by the way? I had a scoot around the SugarCRM site but couldn't find any details.

Kind Regards,

Paulie

---

### Post by Pauliehaha on 2006-04-30
[QUOTE=Pauliehaha]Hi, 

Is PHP 5 a requirement for SugarCRM?

I have PHP 4.4.0 which I need for another web application I am running on Apache. Does anybody know if I can install SugarCRM with this version?

An older version of SugarCRM would do as I just want to try it out first.

Alternatively can I run multiple versions of PHP with my other app using the older version, 4.4.0 and the CRM using the newer version, 5?

I think my box meets the other requirements, where can I find these by the way? I had a scoot around the SugarCRM site but couldn't find any details.

Kind Regards,

Paulie[/QUOTE]
OK, I should have RTFM! 

The Installation Guide has a pretty picture of the dependency check which shows that version 4.4.0 is unsupported.

Guess I'll go take a look at the previous versions, although if anybody knows if I can run different versions of PHP side-by-side that would be useful.

Many Thanks,

Paulie

---

### Post by alamba on 2006-05-01
I tried that once and went into configuration hell. Wasn't able to figure out which app was using which php installation and which php.ini to make changes to!! 

However, in your case, this is what I found "SugarCRM doesn't offically support PHP4.4 or 5.0.5". Now there's a big difference between unsupported and doesn't officially support. If you give the installation a try you might just find that it works. This link might help you [http://www.sugarcrm.com/forums/showthread.php?t=6794](http://www.sugarcrm.com/forums/showthread.php?t=6794)

Good luck and let us know how it goes.

A

---

### Post by Pauliehaha on 2006-05-01
Thanks for the advice Alamba,

You're right, I'm not sure I really want to go there with multiple versions of PHP!

I gave version 3.5.1a a try on my development box and so far I'm mighty impressed. 

I'm certain I'll use this application so once I've learned my way around it and tested it out for a while I'll install it on a production server and get the latest version.

Best Wishes,

Paulie

---

### Post by alamba on 2006-07-01
Tried the installation on dapper. The above howto should work on this too. Hence, not updating/creating a new thread for dapper installation unless specifically asked for.

A

---

### Post by faultyCPU on 2006-07-03
Just need few points of help.

I am unix guy (solaris/linux) about 8 years. haven’t done any CRM. I look at vtiger CRM now as a hobby. Does this help in real world? Any good employment prospects by it??


Thanks

---

### Post by alamba on 2006-07-04
Sorry faulty. Don't really know the market for vtiger.

A

---

### Post by faultyCPU on 2006-07-04
Thanks man.

cheers

---

