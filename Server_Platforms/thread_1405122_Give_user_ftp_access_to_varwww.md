---
title: "Give user ftp access to /var/www?"
date: 2010-02-12
forum: Server Platforms
---

### Post by dwessell on 2010-02-12
HI all,

Apache by defaults points to /var/www/eachdomain. I need to be able to give users ftp access to /var/www/specific domains.

It seems that if I change the owner of /var/www/specificdomains/ to the user in question, then www:data no longer owns the directory and Apache starts to have issues..

What's the best way to set this such that I can allow users to FTP into specific directories, and still have www:data own them? I'm currently using vsftp, but that can easily change.

Thanks
David

---

### Post by Porter200el on 2010-02-12
> **dwessell said:**
> HI all,

Apache by defaults points to /var/www/eachdomain. I need to be able to give users ftp access to /var/www/specific domains.

It seems that if I change the owner of /var/www/specificdomains/ to the user in question, then www:data no longer owns the directory and Apache starts to have issues..

What's the best way to set this such that I can allow users to FTP into specific directories, and still have www:data own them? I'm currently using vsftp, but that can easily change.

Thanks
David

Create an administer group and add the users into that group, make sure you give those user the right permissions on the directory though and do that for each dir, so you would have a group called: admins-www-example-com for the domain [www.example.com](www.example.com).

---

### Post by dwessell on 2010-02-12
So from reading around, I found another way that I think will fit my situation better.

Create users and point the virtual hosts to /home/user/public_html.

However, I still can't figure out, find documention for one thing.. How do I get apache to run correctly? Do I need apache to run as user in those directories? Or give the www:data user access in that directory?

Thanks
david

---

### Post by Porter200el on 2010-02-12
> **dwessell said:**
> So from reading around, I found another way that I think will fit my situation better.

Create users and point the virtual hosts to /home/user/public_html.

However, I still can't figure out, find documention for one thing.. How do I get apache to run correctly? Do I need apache to run as user in those directories? Or give the www:data user access in that directory?

Thanks
david

If you are asking me, for ease of use and implementation, set up the groups and then point the ftp host to /var/www/sitename for the home dir for the particular user.  I have done this many times with success.  I would recommend running FileZilla though, that has been the easiest sFTP setup for me, but use what you are comfortable with.

---

### Post by yknivag on 2010-02-12
If you run Apache with "mod_userdir" then it will automatically look at /home/user/public_html/ when a browser is pointer at [http://server/~user/](http://server/~user/)

All you need then is a re-write rule for each user to point [http://server/url_you_want/](http://server/url_you_want/) to [http://server/~user/](http://server/~user/)

/home/user/public_html can then be owned as normal by the user.

When setting up your ftp you can then jail your users to their home directories and they can't see or interfere with other users' files or sites.

---

### Post by dwessell on 2010-02-13
> **Porter200el said:**
> If you are asking me, for ease of use and implementation, set up the groups and then point the ftp host to /var/www/sitename for the home dir for the particular user.  I have done this many times with success.  I would recommend running FileZilla though, that has been the easiest sFTP setup for me, but use what you are comfortable with.


Porter200el, I'm with you. But then how can the user edit the files? Since the owner of everything in /var/www is owned by the apache user? That's where I'm getting lost.


yknivag, I need it to work for multiple domains.. And from what I can tell mod_userdir won't do that for me..


> **yknivag said:**
> If you run Apache with "mod_userdir" then it will automatically look at /home/user/public_html/ when a browser is pointer at [http://server/~user/](http://server/~user/)

All you need then is a re-write rule for each user to point [http://server/url_you_want/](http://server/url_you_want/) to [http://server/~user/](http://server/~user/)

/home/user/public_html can then be owned as normal by the user.

When setting up your ftp you can then jail your users to their home directories and they can't see or interfere with other users' files or sites.

Thanks to everyone who has taken the time to assist.

thanks
david

---

### Post by AngelOfMercy on 2010-09-05
Hey, Thesres a easier way than that i do believe. Create a folder in the var/www/here Now create a user and point it to that directory, Then change file permissions to 777. I have a problem i deleted my www folder by accident. I recreated it and made a user called www-data and made it www folder user. But not no matter what i cannot create a user in var/www/here and give it ftp access but i can home :/

---

### Post by isma_ on 2013-01-22
> **AngelOfMercy said:**
> Hey, Thesres a easier way than that i do believe. Create a folder in the var/www/here Now create a user and point it to that directory, Then change file permissions to 777. I have a problem i deleted my www folder by accident. I recreated it and made a user called www-data and made it www folder user. But not no matter what i cannot create a user in var/www/here and give it ftp access but i can home :/

file permissions 777 is never an acceptable solution.
I'm also trying to accomplish this, and so far the best idea anyone has offered is:
```
ln -s /home/ftpuser/domain.com /var/www/domain.com
```
and add ftpuser to the www-data group

I haven't tried it yet, but I'll post results in a bit. Doing tests as we speak

---

