---
title: "File Permissions on Web Server for PHP commands"
date: 2008-06-11
forum: Security
---

### Post by JameoPotato on 2008-06-11
Hi,
I am building my own website and using my own ubuntu apache2 server.

I was writing a script(PHP) that opens a text file containing a password (encrypted). 

My problem is a don't know how to set permissions on this file to allow my PHP command to open it and not EVERYONE visiting my site. 
I tried chmod and chown but my original thought of php commands running as root, i now see were wrong. 

I would like to access this file as a PHP command, and my Local User.



Another question kinda relating to this is I would like to learn more about "Group" permission setting and how to put a user in a group and then give that group access to the "Group" permission on a file/folder. (Just a link to a tutorial or documentation on group file permissions would be great, I tried googling but didn't seem to find anything useful)

Thanks


EDIT:
Okay I kinda fixed the first problem. All PHP commands are run under the www-data user so I just chown www-data *mydirectory/file* and the php runs fine now.
BUT, now my local user that I connect via FTP with cannot access it. 
I would still really like to learn more about groups and users. If anyone has a good link please share, or a good quick explanation would be greatly appreciated. :)

---

### Post by molotov00 on 2008-06-11
You said you fixed the first problem. Based on your explanation, you didn't. Any user going to the site will still be able to view the file as long as it is in /var/www. See this thread:

[http://ubuntuforums.org/showthread.php?t=826402](http://ubuntuforums.org/showthread.php?t=826402)

As far as the second problem... You can set your sites up like this:

/somedir/molotov/www/ < put website files in here
/somedir/molotov < give ftp access
/somedir/molotov < put password file in here

chown /somedir/molotov to molotov
give read to www-data to /somedir/molotov

That way, people can't get to the password file by going to somesite.com/blah because that will be /somedir/molotov/www that they are looking at. A PHP script can still traverse upwards and grab the file.

---

### Post by hyper_ch on 2008-06-12
default folder for webpages in apache is /var/www

If you don't use suPHP then the .php files should be owned by Apache and they must be executable and readable by apache.

---

### Post by kevdog on 2008-06-12
hyper_ch

Good advice -- very concise.  Wish every piece of documentation was this way!

---

