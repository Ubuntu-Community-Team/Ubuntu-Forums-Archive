---
title: "stupid problem involving squirrelmail"
date: 2010-02-15
forum: Server Platforms
---

### Post by CCG121 on 2010-02-15
Help Me please i was messing with the settings for squirrelmail in the admin control panel and suddenly it disappeared when i hit submit i then went and uninstalled it and removed all the files in /etc/squirrelmail and the directory i then reinstalled it and most of my files aren't there. can someone please help me fix this

---

### Post by noway2 on 2010-02-16
Ok, what files do you have and what are you expecting that is missing?  For example, in my configuration I have six .PHP files and three configuration files; one for apache, one in Perl for squirrelmail, and one for defaults.

You also didn't say whether or not squirrelmail is working.  If it is not working, did you try to reconfigure it after deleting and re-installing?  If no, then do.  If yes, what exactly is happening?

---

### Post by CCG121 on 2010-02-16
I deleted all the files and tried to reinstall it using apt-get install squirrelmail and then configuring but all the files were gone except the conf.pl file and it wanted a config.php or somewhat file like that so i created it but no other files were in the /etc/squirrelmail folder and there had been 6 or 7 before 

I finally tried reinstalling it in /var/www/sitename/Mail and got it reconfigured there.

Thanks for your help.

---

