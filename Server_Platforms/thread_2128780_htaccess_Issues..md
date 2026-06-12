---
title: "htaccess Issues."
date: 2013-03-24
forum: Server Platforms
---

### Post by apatheticrory on 2013-03-24
First of all, i'd like to apologize for how stupid this question may be (i'm unsure)

i installed Ubuntu Server 12.10 on an old PC last week (for something to do) and everything up until now has been going smoothly. please note that i have no previous experience with any server - just thought it could be a little project

i've got an open ssh server installed, with apache2, php5 and mysql. 

last night i set up a very simple website and started hosting it - when i came to .htaccess it started getting messy! no online tutorials seem to include how to actually create these files (in notepad and drag and drop or with the actual server!?) 

so i made them using notepad on my pc and dragged them over, placing them in the directory i wanted to protect (this is simply called Data and is held in my /var/www folder. The authentication pop-up works great but no matter how many times i input my username and password, it just pops up again. I've looked through pretty much every site i can find and after changing something to AllowOverride All, there's nothing else i can find to help me. when i have the htaccess and htpasswd files in the directory now, it tells me there is a server error. i dont know whether i have completely messed it up and considered re-installing the entire server system and starting again! :(

i was hoping one of you kind people could save me from hitting my head against the wall again - couldn't sleep last night because of the headache! ha.

Thank you

---

### Post by SeijiSensei on 2013-03-24
Have you looked in /var/log/apache2/error.log to see if there are more details?

Are both the .htaccess and .htpasswd files in locations that the "www-data" user can read?  Do they have proper permissions to allow that user to read them?  Make sure that all references to files are absolute ones with full paths (see below).

It's never a good idea to move text files directly from Windows to *nix machines because they differ in how they designate the end of lines.  Install the package [tofrodos]("http://manpages.ubuntu.com/manpages/natty/man1/fromdos.1.html") and apply it to the files to strip any extraneous line terminators.  In the future use a text editor on the local machine like gedit or kate, or command-line tools like nano or emacs.

```

AuthUserFile /path/to/.htpasswd
AuthGroupFile /dev/null
AuthName "Friends Only!"
AuthType Basic

<Limit GET>
require valid-user
</Limit>

```

Notice the full path to the password file, called .htpasswd here.  Also, for security purposes, the file should not be kept in the same directory as the web site files.  You can place it anywhere in the system as long as the www-data user can read it.

---

### Post by apatheticrory on 2013-03-24
this is what i got from the error log (didn't know there was one, so thank you for that)...

[Sun Mar 24 13:42:02 2013] [crit] [client 176.248.2.241] (13)Permission denied: /var/www/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
[Sun Mar 24 13:43:21 2013] [error] [client 176.248.2.241] (2)No such file or directory: Could not open password file: /var/www/Data/.htpasswd, referer: [http://94.5.254.186/index.html](http://94.5.254.186/index.html)
[Sun Mar 24 13:43:21 2013] [error] [client 176.248.2.241] (2)No such file or directory: Could not open password file: /var/www/Data/.htpasswd


i have just dragged and dropped both ht files to the /Data folder which i am trying to password protect. i've tried storing it somewhere else on the machine but i think i only have access to the var/www file and don't know how to give myself access :(

thank you for your help, it's much appreciated.

Rory

---

### Post by SeijiSensei on 2013-03-24
You need to grant the www-user permission to read the file.  For details on how to manage permissions, read: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions).

---

