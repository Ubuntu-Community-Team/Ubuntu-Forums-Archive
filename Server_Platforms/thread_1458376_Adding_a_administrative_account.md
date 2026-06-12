---
title: "Adding a administrative account"
date: 2010-04-19
forum: Server Platforms
---

### Post by tigress1123 on 2010-04-19
I'm running Ubuntu 8.04 LTS as a web server, and I am trying to create a second user with all the same privileges as my initial user. I have already tried adding him to the admin group, but he still not allowed access, specifically to the /var/www/ directory.
 
I'll be honest - I really am new to all this! Any help is appreciated! :)

---

### Post by iissmart on 2010-04-20
If the owner of /var/www is www-data:www-data, all you need to do is add yourself to the www-data group. Edit the /etc/group file, find the line that starts with www-data, and after the colon at the end type your username (the second user that you're trying to give access to). This will put them in the www-data group and should give that user access to the files in /var/www.

---

### Post by Iowan on 2010-04-20
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") help page (which has been superseded by the Server Guide) mentions moving DocumentRoot to a directory where the user has access. Just another option...

---

### Post by tigress1123 on 2010-04-20
Thanks for the help! I went ahead and just gave him access to the /var/www/ folder, but I'll probably go with the other reccomendation once I have a little more experience!

---

