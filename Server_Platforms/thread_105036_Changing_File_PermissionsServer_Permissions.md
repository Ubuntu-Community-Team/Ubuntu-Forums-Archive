---
title: "Changing File Permissions/Server Permissions"
date: 2005-12-17
forum: Server Platforms
---

### Post by orev on 2005-12-17
I have an kubuntu apache/php/mysql server setup and running @ localhost. (var/www/)

I don't think I understand how to set the server permissions/access so that I can save/edit/transfer files to and from the /www/ directory as a non root user.

I can edit and save files if I open them as root from the konsole, but, of course, I would like to edit and save them from quanta/bluefish.

I have read the [wiki article]("http://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=Apache") regarding this...and I think this is the appropriate section related to what I am looking to do:

[B]Edit Apache Configuration

You may want your current user to be the PHP pages administrator. To do so, edit the Apache configuration file :

$ sudo gedit /etc/apache2/apache2.conf

Search both the strings starting by "User" and "Group", and change the names by the current username and groupname you are using. Then you'll need to restart Apache. (look at the next chapter concerning apache commands)

Configuration options relating specifically to user websites (accessed through localhost/~username) are in /etc/apache2/mods-enabled/userdir.conf. [/B]

I don't really understand how to apply this though...here is the section of my /etc/apache2/apache2.conf that applies to "User" and "Group":
```

User www-data
Group www-data

# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
```

I'm sure the answer is quite simple...

Thank you.

---

### Post by LordHunter317 on 2005-12-17
**Don't do that, that's *piss-poor advice***.

**Services should always, *always, ALWAYS*** be run as root (and only if they must) or an account that is ***unique*** to that service.  

Never, ever have a service run as an interactive user.  It's just begging for trouble.  Don't do it.

Here's the correct way:
**If multiple people need to edit the files in the webroot**:[list][*]Create a group that will have all the users that need to perform this task.  Call it www-editors or similiar:```
sudo groupadd www-editors
```Then, add the users to the group:```
sudo adduser bob www-editors
```Replacing 'bob' with the correct username.  Repeat for each user who needs to be in the group.  Logged in users will have to logout/login to see the new group membership.[*]Give group ownership to all the files/directories people need to edit in the webroot.  Assuming that's all of them:```
sudo chgrp -R www-editors /var/www
```Then, give the group write permission:```
sudo chmod -R g+w /var/www
```Set the 'setgid' bit on all directories, so newly created files/directories will have 'www-editor' as owner.  This ensures that no matter who creates the file, the whole group can edit it:```
find /var/www -type d -print0 | xargs -0 sudo chmod 2775
```[*]Finally, give the world read permissions.  This is necessary so that Apache can read the files:```
chmod -R o+rX /var/www
```If the world permissions are removed, Apache will return 403 (Forbidden) on the files.[/list]**If only you need to edit the files, do the following:**```
sudo chown -R bob /var/www
sudo chmod -R o+rX /var/www
```And the same rule about giving world permissions applies.

---

### Post by orev on 2005-12-17
This worked perfectly.  Thank you very much.

---

### Post by muz1 on 2006-11-02
Hey. 
I also wanted to say thanks as well.
Have been majorly struggling with that to.
Thanks for the advice and insight.
Cheers
muz

---

### Post by tobyh on 2007-10-12
Thank you very much for this solution.  Not only did you solve the problem I learnt something.

Advice gratefully received!

Many thanks,

Toby

---

### Post by bibionic on 2007-11-01
And I'll add my thanks as well. I've been wrestling with the same problem for several hours over the past few days. Thanks:rolleyes:

---

### Post by Zalbor on 2007-11-06
Thanks for this from me as well. It's exactly what I was thinking of doing (except the setgid part, so thanks for that too) but I wasn't sure if it would "break" anything.

---

### Post by ScottLij on 2007-12-14
Thanks!

---

### Post by dbqp on 2008-01-30
Thanks! I had another thread open until finding this one...GREAT advice and instructions

:guitar:

dbqp

---

