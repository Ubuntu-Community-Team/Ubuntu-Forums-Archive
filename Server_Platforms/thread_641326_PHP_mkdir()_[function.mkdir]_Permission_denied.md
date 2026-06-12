---
title: "PHP mkdir() [function.mkdir]: Permission denied"
date: 2007-12-15
forum: Server Platforms
---

### Post by s3lnt0 on 2007-12-15
Hi,

I have set up a server with apache 2 and php5 which almost works. PHP seems to work fine but for some reason does not have write access. phpinfo() does come up and safe mode is off.

When I try to run in my /home/s3lnt0/ns folder,

[HTML]<?php
mkdir("test",0755);
?>[/HTML]

it does not work. I have tried changing the script to everything possible and it still does not work. I have tried running the same script in /var/www/ and it still does not work.

I have searched the web but have come up with no solution. I've tried changing the permissions on the files and folders but it does not work.

My /etc/apache2/httpd.conf is blank, which I don't know if thats a problem or not. 

Thanks.
Anthony

---

### Post by Samhain13 on 2007-12-15
The directory that php is trying to make a directory in needs to have read/write access for "www" or "world", or "777". But I'd use caution applying those permissions because it allows others to write to that directory as well.

---

### Post by bproven on 2007-12-15
Yep what Samhain13 said is probably the issue.  Just chown the dir to whatever your user your web server runs as and then chmod it to only allow that user access (just to be safe).  At min remove the permissions on "other"/(anybody) as I would assume only the web server needs access to that dir.

Examples  in case you need them):

sudo chown www-data.www-data <yourdir> -R
sudo chmod o-rwx <yourdir> -R

---

### Post by s3lnt0 on 2007-12-15
So just to make sure I understand, if I have a php script that is trying to make a directory in "user_files", then "user_files" needs to have a permission of "777"?

---

### Post by Samhain13 on 2007-12-15
s3lnt0: yes and no. It really depends on who the owner of "user_files" is.

For example, by default (and someone should correct me if I'm wrong), the directory "/var/www" is owned by "root". So if "/var/www" has "755" permissions, it means that 1) "root" can read and write into it, 2) users in the group of "root" can only read files in it, but not write, and 3) the world in general can read but not write files into it.

When you reassign the ownership of that directory, say, as per **bproven**'s example, to "www-data" and giving the directory the same "755" permissions, it's going to me 1) "www-data" has read and write access, 2) users in the group of "www-data" can read but not write, and 3) the world can also read but not write.

Ok, here's the **no** part. If you assign the owner of "user_files" as "www-data", you only need to give it "755" permissions as the PHP script is (normally) run by "www-data".

---

### Post by s3lnt0 on 2007-12-15
What exactly is the "www-data" user? Why would switching it to that fix it? I'm not at my computer yet so can't say for sure if it will work or not, but I want to learn all I can about the linux server. Thanks for all the help.  :)

---

### Post by Samhain13 on 2007-12-15
"www-data" basically refers to the web server, it's like the web server's username. Although someone else may be able to explain this better, I'll try to write an explanation:

You can just imagine the web server to be another person that has an account, "www-data", on your computer much like yourself. And because it's user like you, it can run its own instances of the applications your computer has available like PHP and Python scripts, stuff like ImageMagick, ffmpeg, etc. It will also need to have its own directories where it can put data in as well, much like how you have your own home directory where nobody else can write to-- unless you give them permission.

Now, suppose you've built a PHP applicaiton that you access through your browser via "http://localhost/yourapplication.php". The user that executes the instance of that application is the web server (even if you were the one who typed in the URI). And everything that results from running that application is owned by the web server.

It's much like creating a folder in your home directory by your right-clicking and selecting "create new folder"-- you will be the owner of that folder. The PHP application that you built, if executed by the web server, will not be able to write to that folder (create a new file or sub-folder or modify files) because the web server, being another user, does not have sufficient permissions.

So you can do either of two things: 1) transfer the ownership of that folder to the web server, or 2) retain ownership of that folder but give the web server the proper permissions to write to that folder.

-----

Sorry if that turned out to me more confusing than helpful. :)

---

### Post by s3lnt0 on 2007-12-16
That makes sense, I gave the folders that PHP needed to write to, www-data ownership and that seemed to work.

Thanks.

---

### Post by Samhain13 on 2007-12-16
Ok then, glad to be of service. :)

---

