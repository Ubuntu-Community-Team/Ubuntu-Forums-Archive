---
title: "Apache2.2 PHP5 create session with wrong permission"
date: 2010-02-09
forum: Server Platforms
---

### Post by ausrasul on 2010-02-09
Hey there,
I've installed LAMP stack on ubuntu9.10, latest apache2.2 and latest php5 and MySql.
in my web application, I used sessions for login.
in each page I added session_start(), the webpage should check if there is existing session and so on.
 
the problem is that the log in page keep comming no matter how many times I enter user/pass.
it is like it doesn't find the session file.
to support this idea, I can see three or two new session files everytime I try to log it.
 
now I checked /var/lib/php5 , the session file permission is something like:
-wr------ www-data www-data sess_xxxxxxxxxxxxxxx
 
I think there is something wrong with the permission. do you think so?
 
if I sudo to root then sudo to www-data and run command umask I get 0022 or 022 I don't rememeber.
 
I changed the umask to 0022 in /etc/apache2/envvars and restarted the service and the server but no success.
 
also changed then rolled back /etc/profile umask value which is 022 initially.
 
also changed the session.save_path to my home folder /home/aus/sessions and changed chmod 777 but nothing happened.
 
however I can read the content of the session file when I "sudo more" and it look all in order.
 
I checked everything I can find on the interenet but nothing worked.
any ideas?
 
Thanks alot

---

