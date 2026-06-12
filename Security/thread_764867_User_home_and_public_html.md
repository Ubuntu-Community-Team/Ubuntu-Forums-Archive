---
title: "User /home and public_html"
date: 2008-04-24
forum: Security
---

### Post by knichel on 2008-04-24
Greetings.  I am trying to figure out the best way to protect users from other users while allowing public_html access.

I have /home owned by the admin and group set to "users" where each user is a member of "users" and so is "www-data".  

Each of the users /home/username is  owned by user and group is set to user.
Each of the users /home/username/public_html is owned by user and group is public_html.

I am not sure if this is good or not.  Can someone please tell me what is best/safest so my users cannot mess with each others stuff, but the public_html folders work as intended.


Thanks,
Mike

---

### Post by Dr Small on 2008-04-24
Hrm, let's see here.

Users Home Folders should be set to rwx-rwx- ( 770 ) and owned by user:user
The public_html directory should probably be set to rwx-r-x- ( 750 ) and owned by user:www-data

That would prevent others who do not own the directory, and are not in the group to read, write or execute files, and on the pubilc_html directory, the group www-data would be able to read and execute.

Dr Small

---

### Post by knichel on 2008-04-24
Thanks for the reply.

Currenlty I have 

/home is chown admin:users chmod 740
drwxr-x---  29 admin users     4096 2008-04-21 09:02 home

/home/username is chown username:username chmod 770
drwxrwx--- 33 username username   4096 2008-04-24 10:55 username

/home/username/public_html chown username:www-data chmod 740 (r-x)
drwxr-x---  7 username www-data   4096 2008-04-24 10:02 public_html

www-data is a member of the "users" group.


I cannot web to [www.server.com/~user](www.server.com/~user) , getting 403 Forbidden error.

I am thinking it must be something with /home itself.  Doe the web server need read access to /home ?  What am I missing?

Thank again,
Mike

---

### Post by Dr Small on 2008-04-24
The public_html directory needs Executable Permissions for the group.

740 (rwx-r----)
750 (rwx-r-x--)

---

### Post by knichel on 2008-04-24
My bad, I have it set to that,  just used the wrong numbers.  Still does not work.

drwxr-x--- 7 username www-data 4096 2008-04-24 10:02 public_html


--
Mike

---

### Post by Dr Small on 2008-04-24
Is there any files in this directory, that may perhaps have the wrong permission, like an index file?

---

### Post by crashie on 2008-04-24
You also need to set /home/user to have www-data (or users as you put www-data in that group) as it's group, and grant it execute permission (on directories means access to subdirectories and files). Otherwise the web server won't have access to *any* in that user's directory.

```

sudo chmod 710 /home/user
sudo chgrp www-data /home/user

```

---

### Post by knichel on 2008-04-25
Thanks again.  Sorry to report, no change.

On the server, I su www-data and was able to 

cd /home/user/public_html
more index.html
 
just fine, but still get 403 error from browser.  Very strange.

I checked to see if apache2 was configured to allow userdir's and it is.

I just tried a test.  I have a user called test.  Here is what I did...

sudo su
cd 
chmod o+r /home
chmod -R 777 /home/test // figured this *should* allow to www

Still cannot view ~test/index.html  in web browser

Mike

---

### Post by crashie on 2008-04-25
Do you get any error messages in the Apache error log? Error messages are logged to /var/log/apache2/error.log

---

### Post by knichel on 2008-04-25
Thanks for the help. Got it fixed.

Mike

---

### Post by crashie on 2008-04-25
> **knichel said:**
> Thanks for the help. Got it fixed.

Mike
Would you mind writing what you did to solve the problem? Because there's probably other people who have this problem ;)

---

### Post by knichel on 2008-04-25
I would, but I am not sure what I did that corrected it.  It seems that there was a power failure on Monday night that caused some weird behavior.

Basically, I went through and set the /home & /home/user & /home/user/public_html to have enough privs for www-data to be able to read.  I must have phat fingered some of the suggestions previously and it did not do what I was expecting.

Thanks.

---

### Post by mahtar on 2009-12-28
I had the same problem; installed apache, enabled userdir mod, created public_html with permissions to access and execute by others and was getting 403 error.

I solved it by adding my user to www-data group and then setting www-data as my home folder group with files access and execute permissions.

Not sure if that's the way to do it but it worked for me.

---

