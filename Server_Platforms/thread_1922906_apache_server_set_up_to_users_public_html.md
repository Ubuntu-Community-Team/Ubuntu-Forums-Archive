---
title: "apache server set up to users public_html"
date: 2012-02-09
forum: Server Platforms
---

### Post by clearwood on 2012-02-09
Hello you ubuntu users

I have tried looking around for an answar for this question, but so far with no success, so therefore this thread.

Can anyone give me advise on how to set up the directory 'public_html', that I make, for every user to be connected to the apache servers 'servername/~username'.

Thanks a lot in advance.

---

### Post by iainjames88 on 2012-02-09
I think you would have to setup Apache Virtual Hosts for this. Check out Google for a few tutorials there should be plenty around on how to do it but if I remember correctly it is possible to setup Virtual Hosts so that any request to [www.example.com/dir](www.example.com/dir) is forwarded to /home/user/public_html (where */dir is your users public_html folder)

---

### Post by volkswagner on 2012-02-09
What you may be looking for is Apache [mod_userdir]("http://httpd.apache.org/docs/2.0/mod/mod_userdir.html") or apache [userdir]("http://httpd.apache.org/docs/2.0/howto/public_html.html").

Some good general apache help can also be found in the [sticky]("https://help.ubuntu.com/10.04/serverguide/C/httpd.html") at the top of this forum.

---

### Post by clearwood on 2012-02-11
OK I have spent a lot of time trying to find out trough the links you showed me. even the IRC with still no luck.

do I have to modify the .htaccess file?

have used comand:

sudo a2enmod userdir

if anyone has a direct recomendation please let me know

best regards

---

### Post by clearwood on 2012-02-11
by the way where should the .htaccess file be?

---

### Post by clearwood on 2012-02-11
when I try to access I get the message 403 forbidden

Forbidden

You don't have permission to access /~rub on this server.
Apache/2.2.20 (Ubuntu) Server at 127.0.1.1 Port 80

---

### Post by Doug S on 2012-02-11
Starting from a default installation, two things are required for the users public-html directories to work properly: First, and as you have disicovered, you need to enable it via:```
sudo a2enmod userdir
```Second the default access permissions for the user folders does not allow access via the apache server. There are a couple of ways to fix this: Change the permissions, keeping in mind that the higher level permissions might need to be changed also; Make all users that want to have public_html directories members of the www-data group (I think, I use the first method). On my system I have public_html set to 755 and my home directory set to 755 (note: some recommend against this method.) [This isn't the best reference]("http://ubuntuforums.org/showthread.php?t=1201236"), there are others but I am having trouble finding them.

---

### Post by clearwood on 2012-02-11
ok how do I make them members of the www-data-group ?

---

### Post by Doug S on 2012-02-11
See this: [http://ubuntuforums.org/showthread.php?t=1849111](http://ubuntuforums.org/showthread.php?t=1849111) , particulary post number 9.

---

### Post by clearwood on 2012-02-13
the strange thing is that it worked before I added rub to www-data and so on.
All I did was to do the 755 thing. :)

But I asume that this way here is for making things easier.

I am on the road so this is just a quick message I have to look into the www-data link that you send me a bit more - it looks really smart.

Best regards and thank you.

---

