---
title: "apache2 mysql php5 on ubuntu"
date: 2008-07-20
forum: Server Platforms
---

### Post by caymahallesi on 2008-07-20
Hi guys,

I hope this is right place to post my question.

I have ubuntu 8.04 hardy I am trying to setup and practice web server with ;
apache2
mysql
php5

also installed joomla. 

When I first visit to my own home page of course joomla prompted me for setup and mentioned that mysql is not available. before I continue working on it I moved my joomla files to a subfolder. 

Now when I tried to visit my subfolder example; [http://localhost/mysubfolder](http://localhost/mysubfolder) I get forbidden error. 

Please let me know what I can do ?

thanks
Cemal

---

### Post by mbeach on 2008-07-20
if the files were originally in /var/www, and you created /var/www/mysubfolder, I suspect you used sudo to do so.  As such perhaps the www-data user needs some access to the /var/www/mysubfolder

You may need to change the permissions on the mysubfolder and its contents.  I recall back before joomla I setup a few mambo sites, the config files are right alongside all the other php files, so after you change the ownership and make things readable, there are probably a few files containing passwords which you'll want to change back to unreadable.  That is if Joomla is still doing things that way.

I'd try this first and see if it works.  This will change the ownership to the www-data user.
```

cd /var/www
sudo chown -R www-data:www-data mysubfolder
```

EDIT: use caution here, the -R says do this for all contents and subfolders (recursively).  Ensure you are in the right folder, or you could cause yourself some serious grief - always try and understand the commands given before simply typing them in.  Even with the best intentions, occasionally a post can give you some harmful code if executed in the wrong place.
Use:
```
man chown
```
to learn about chown and the -R flag before proceeding.

---

### Post by caymahallesi on 2008-07-20
Thanks, it worked.

---

### Post by mbeach on 2008-07-20
great - good to hear, if you mark the post as solved (under the thread tools link I think) you'll save some time for others in here.

welcome to the forum.

---

