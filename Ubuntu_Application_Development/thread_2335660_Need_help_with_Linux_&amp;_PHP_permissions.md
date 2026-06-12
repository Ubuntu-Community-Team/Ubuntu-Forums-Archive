---
title: "Need help with Linux &amp; PHP permissions"
date: 2016-08-31
forum: Ubuntu Application Development
---

### Post by la.khan on 2016-08-31
Hi all,

I learnt PHP 5.6 using Windows 10 & WAMPServer (64 bit) and recently moved to Ubuntu Linux. I am trying to setup my Linux machine to continue learning PHP. My setup is:

Ubuntu Linux 16.04.1 (64 bit)
Firefox: 48.0
Apache: Apache/2.4.18 (Ubuntu)
MySQL: 5.7.13
PHP: 7.0.8

I have some questions and I have them below in [COLOR=#0000ff]BLUE[/COLOR].

Issue 1: apache2 & mysql start automatically when I turn on my laptop; I prefer to start apache2 & mysql service when I need them. [COLOR=#0000ff]How do I ensure these services don't start automatically on startup?[/COLOR]

Issue 2:
My work folder is: /eBooks/PHP/Chapxx and my PHP server folder is: /var/www/html/php/chapxx/

For the PHP server folder /var/www/html, owner is www-data and group is www-data; all sub-folders & files under html have owner as www-data and group as www-data. For permissions, I started off with 'rwxrwxrwx'. For these permissions, I found I could access my PHP files using my browser ([http://localhost/php/chapxx/filename.php](http://localhost/php/chapxx/filename.php)). Since this is bad practice, through trial & error, I realized I could restrict permissions to 'r-xrwx---' and yet access the PHP file. Currently,
```
$pwd
/var/www/html
$ls -l
dr-xrwx--- 3 www-data www-data  4096 Aug 30 23:45 php
```
[COLOR=#0000ff]Is this the right way to setup PHP server folder(s)? While this seems to work fine, can the setup be improved upon (permissions wise)?[/COLOR]

Issue 3.
When I copied some more files from my work folder to PHP server folder, files were copied as:
```
-rw-r--r-- 1 la.khan la.khan 1143 Aug 31 07:36 PHP Test for accessing constants and static variables.php
-rw-r--r-- 1 la.khan la.khan 2397 Aug 31 07:41 PHP Use inheritance to create shape classes.php
```
These files were created using Windows 10 & WAMPServer and hence the long names :oops: A couple of things - file copied with my username and group; secondly, file has different permissions. When I accessed the files, the browser loaded them fine; I expected to see error '403 permission denied'. [COLOR=#0000ff]Permissions wise, user wise, group wise, these files shouldn't load in a browser, but they do; any idea why? Permissions wise, which is better 'r-xrwx---' vs. 'rw-r--r--'?[/COLOR]

Issue 4.
Just as a test, using my Firefox browser (v.48), I accessed URL [http://localhost/php/Chapxx/filename.php](http://localhost/php/Chapxx/filename.php) (with upper case C), I see a '404 file not found' error. I do know that Linux is case sensitive and can't find Chapxx folder. However, in the real world, URL case is ignored (browsers ignore URL case and web servers ignore URL case). As long as the path is correct, filename exists and file extension is correct, the page is sent back to browser. [COLOR=#0000ff]So, how is my Linux/PHP setup different from application web servers on the internet? Is there a setting where I can instruct Linux to ignore case for all sub-folders of /var/www/html/? Or, use regular expressions to convert URLs to correct case?[/COLOR]

Any comments/insights/pointers to articles/web sites/blogs welcome.

Thanks in advance for your effort & time!

---

### Post by TheFu on 2016-08-31
Lots of opinions below ... some facts too.

a) learn Unix permissions.  Do this soon, now, today.  It is the cornerstone of all Unix system security.  The goal is to have exactly the permissions needed and no more for every file, every directory.   r-xrwx--- is VERY ODD. Think about what those permissions mean and you'll see why I say that. Unix and Linux is a multi-user OS from the ground up. users, groups, permissions and ACLs are critical.

b) Your linux username is a poor choice. It will probably break some commands (chown for example) due to the period.  Change it. No funny characters. 7-bit ascii, no punctuation please. 

c) there aren't any "correct permissions for php".  The required permissions, and no more, are what they should be.  Permissions include the owner and group as well. [https://thehackernews.com/2015/12/programming-language-security.html](https://thehackernews.com/2015/12/programming-language-security.html) php is the most hacked web-app language used.

d) Php has a very low barrier to starting, but that doesn't remove the need to actually learn Linux to make a working, secure, webapp.  Learning Linux: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - some ISPs around the work are blocking my blog (for some unknown reason) - use google cache or the wayback machine to see the article if any issues.

e) All Unix OSes are case sensitive. Get over it. The majority of OSes are case sensitive. If you expect Linux (or any other OS) to work like Windows, you will be disappointed.

f) Don't use spaces in directory or file names. While it is completely supported, it will make your life hard and many scripts just won't work. It is possible to to make a script work with odd filenames, but it is a little harder.  Don't, just don't use filenames with funny characters or spaces.

That's all I know. Hope it is help.

---

### Post by la.khan on 2016-09-02
Hi TheFu,

Thanks for your reply.

I do have a broad understanding of folder/file permissions and, based on your comments, I worked on my PHP folders/files a little bit more; now, they are setup as 'rw-r--r--' and I can view my PHP pages fine.

I could visit your blog [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) and I found the links in there very informative.

I downloaded the free PDF book on Linux CLI and plan to go through it in the next few days/weeks. I also looked at the URL for minimal Ubuntu system maintenance (setting up a firewall, clamAV, update patches, upgrade kernels, backup files etc). Next, I plan to start reading the PDF book I downloaded and setup antivirus, ufw firewall.

---

### Post by TheFu on 2016-09-02
Sounds like you are well on the way.  BTW, did you try 640 permissions for the files and 750 for the directories?  Being more restrictive to the point that it works and isn't inconvenient for you, but is inconvenient for others is best.  Don't forget about the sgid bit for directories. That can make your life easier too. There are subtle permissions that the beginning knowledge doesn't cover, but will make your life easier.

BTW, have you looked at different groups?  Perhaps considered putting your userid into the same group as whatever web server you choose?

Also, apache isn't always the best web server.  We stopped using it around 2008 here.

---

### Post by la.khan on 2016-09-03
Hi TheFu,

I have folder permissions set to 750 (rwxr-x---); when I tried to set file permissions to 640 (rw-r-----), my pages do not load. So, I set them to 644 (rw-r--r--) and they load fine.

On my Linux machine, folder /var/www/html/php owner and group is set to www-data; I added my Linux login to this group.

It is news to me that Apache isn't used here. I am aware of 2 web servers - Apache & MS IIS :rolleyes: I am certain you don't use MS IIS. Okay, Google tells me there is Nginx. So, what would you recommend that I use?

---

### Post by TheFu on 2016-09-03
Permissions aren't just the bits. The owner and group matter too.  Your testing says that "other" needs read to access the pages, but doesn't have any access to the directory?  That doesn't make any sense.  I think we have an interpretation error happening. That is the risk with describing things and not actually showing the real output from an **ls -al** command.

"here" is my company. I can't speak for UbuntuForums.  There are 20+ web servers for Linux. [A list.]("https://en.wikipedia.org/wiki/Comparison_of_web_server_software") You can create your own in bash, perl, python, ruby, C, C++, Java, erlang, FORTRAN, javascript, ... or other languages too.  Just depends on what you need and the risks you are willing to accept.

People still use IIS?  Eeewwww. I can't imagine allowing any Windows machine direct internet access, much less let one run as a server. Not recommending anything, since only you know the setup there. Just say what we don't use apache here for any external sites.  You can google for "why NOT to use apache" to see reasons.  "Why not use nginx" is another good google search. There are valid reasons to use apache, in certain situations. Will also say that we don't allow php to be used for internet facing sites either - security concerns. The average php web-apps is much more likely to be hacked than those from other languages. We mitigate that risk by not allowing php.

Getting paid is always a good reason to use apache, IMHO. ;) If a company has standardized on apache, suggesting they use something else, even if it is better for their needs, by a Jr. Admin, isn't too bright.  I've been around a very long time and work as an enterprise architect. With a few others, we set the standards for a company to deploy. To use apache needs an approved variance - which basically means there is a good reason to use apache instead of the tool we like.  In a huge organization, apache is the easy answer and the lower performance and higher RAM requirements are a reasonable trade-off.

---

### Post by la.khan on 2016-09-05
Hi TheFu,

Here is the output for ls -al for all three folders (/var/www/html, /var/www/html/php, /var/www/html/php/chap08).
```

root@Hobbes:~# ls -al /var/www/html
total 32
drwxr-xr-x  4 root     root      4096 Sep  2 23:33 .
drwxr-xr-x  3 root     root      4096 Aug 28 18:23 ..
drwxr-x--- 11 www-data www-data  4096 Sep  2 23:55 ajax
-r--r--r--  1 root     root     11321 Aug 28 18:24 index.html
drwxr-x---  3 www-data www-data  4096 Aug 30 23:45 php
-r--r--r--  1 root     root        20 Aug 28 18:45 testphp.php
root@Hobbes:~# ls -al /var/www/html/php
total 12
drwxr-x--- 3 www-data www-data 4096 Aug 30 23:45 .
drwxr-xr-x 4 root     root     4096 Sep  2 23:33 ..
drwxr-x--- 2 www-data www-data 4096 Sep  1 19:19 chap08
root@Hobbes:~# ls -al /var/www/html/php/chap08
total 60
drwxr-x--- 2 www-data www-data 4096 Sep  1 19:19 .
drwxr-x--- 3 www-data www-data 4096 Aug 30 23:45 ..
-rw-r--r-- 1 la.khan   la.khan   1460 Sep  1 19:19 PHP A Simple Car Simulator.php

```
Please let me know if you need any more info.

I am a beginner at UL & PHP; let me get my feet wet and then I will look at Apache vs. Nginx vs. building my own webserver. Thanks for your thoughts on this :)

---

### Post by TheFu on 2016-09-05
I don't know much about php, but I do have a deep understanding of file and directory permissions.

There are 3 different userids in your lists above.  There should be 1, ideally.  The group should be www-data for all.  root should be the owner in 1 situation - when the files will never change and are static.

I'll leave it as an exercise for you to figure out which commands and options to make this happen. Basic Linux stuff that every user should know. Permissions ARE NOT just the 775 or 644 or whatever permissions bits. The owner and group are MORE IMPORTANT.

---

### Post by la.khan on 2016-09-05
I plan to leave folders /var/www/html as they are (with root as owner & group); however, for folder php and below (folder chap08 and PHP files), I plan to change owner & group to www-data. Since my username is part of group www-data, I should be able to access each of the files. I believe the Linux command to change owner/group recursively is 'chown -R'.

With this setup, I need to see if I can have  640 permissions on files and 750 on directories.

---

### Post by TheFu on 2016-09-05
Don't forget to use the set-group-id bit on the directories.  Being in-the-group, is just a start, but the files still need to be set to be in-the-group too.

---

### Post by la.khan on 2016-09-07
Deleted by original poster; duplicate [IMG]https://ubuntuforums.org/images/smilies/icon_redface.gif[/IMG] [IMG]https://ubuntuforums.org/images/smilies/confused.gif[/IMG]

---

### Post by la.khan on 2016-09-07
Deleted by original poster; duplicate [IMG]https://ubuntuforums.org/images/smilies/icon_redface.gif[/IMG] [IMG]https://ubuntuforums.org/images/smilies/confused.gif[/IMG]

---

### Post by la.khan on 2016-09-07
Deleted by original poster; duplicate :oops: :confused:

---

### Post by la.khan on 2016-09-07
TheFu,

I have looked up set-group-id on Google to understand what it does,  applied to my PHP folder, using chmod g+s <directory_name>. My  folders are setup as 750 and files as 640.

Since we are discussing permissions, I have another question regarding  my web server folder (/var/www/html). To copy my PHP files from my work  folder to web server folder, I need to give write and/or execute  privileges to group 'www-data' to my web server folder; currently, it  has permissions set to 750. 

My preference is set permissions to 070 (login IDs part of group  www-data be given full access; no access to individual users/owners or  others); is this advisable? Or, is there any other way to do it?

Thanks for your time & patience!

---

### Post by TheFu on 2016-09-07
> is this advisable?

No. If the userid does not have permissions, then the group, even if it is a member, won't help.
Always look at the owner, group AND permissions bits.

Also ... please delete the contents of all the duplicate posts above, except 1. I only read the first 1.

---

### Post by la.khan on 2016-09-07
Sorry for the multiple duplicate posts :oops:

Thanks for the reply! Let me mark this thread as solved.

---

