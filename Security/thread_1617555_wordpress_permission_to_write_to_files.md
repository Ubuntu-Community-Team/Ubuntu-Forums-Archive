---
title: "wordpress permission to write to files"
date: 2010-11-09
forum: Security
---

### Post by spindler on 2010-11-09
I am having difficulties assigning permission for wordpress to write files.
 I am having problems with the permalink within wordpress and I think it might be because  of the level of permission wordpress has. Currently on my system I need  to set permission to 777 in order for wordpress to write to the  .htaccess file.


 I am running my website on a Ubuntu machine.  Version 10.10  Apache2 2.2.4


 However, when I leave the permission level set to 777 I still cannot  get the permalink to point to the corrent page......See my discussion on  this here.
 [http://wordpress.org/support/topic/permalink-changed-after-moving-website?replies=1#post-1780444](http://wordpress.org/support/topic/permalink-changed-after-moving-website?replies=1#post-1780444)
 

I think what I need to do is change wordpress to use a user  permission or a group permission and not "everyone". I would rather have  wordpress setup to login as a specific user before it can write over a  file.


 Any idea how to set this up?

---

### Post by SeijiSensei on 2010-11-09
Wordpress runs with user and group "www-data" because that's the user that Apache runs as.  Change the ownership of the writable files and directories to www-data with group www-data and use 700 permissions to grant that user rights to the needed directories and 600 permissions on the files.  

To grant specific users rights to these files from the filesystem, you can add them to the www-data group, then use 770 and 660 permissions respectively.  To limit them to just reading these files, use 750 and 640.

---

### Post by spindler on 2010-11-09
This is interesting.

From what I gather i should not need to create a new user www-data, since apache  already recognizes this user. ....So I did not create the user www-data.

instead I went to the folder that contains my wordpress website and typed the following:

chown  -R www-data:www-data *.*

This should change the user and group for each file to www-data.  However, instead I get an error message for each file of the form.

chown: changing owner of  'file name' : Operation not permitted.
 
I am not using the ROOT user to make this change.  However the user I am using has administrator privileges  and when i want to make a change I have asked for the password.  This time I was not asked for a password.....and not allowed to change the user. 

How do I make this change?

---

### Post by cariboo on 2010-11-09
If you typed the command exactly as typed in your post, you forgot to use sudo. You have to have root privileges to make changes to any files ownership and permissions that aren't in your home directory. You probably know this, but we all make mistakes on occasion. :)

---

### Post by spindler on 2010-11-09
Opps.  I guess i was asleep.

.... In the words of my computer science professor ...." I haven't made a mistake since 1978.....I must be getting old. "

Thanks for pointing out the obvious.  :)

---

### Post by spindler on 2010-11-09
Thanks everyone,

By changing the user and group to www-data  I was able to isolate the wordpress activity to a single user. 

i am still having problems with my permalinks...But that is a new topic.

---

