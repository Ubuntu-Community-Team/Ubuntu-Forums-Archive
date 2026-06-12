---
title: "Home Permissions &amp; Users"
date: 2009-02-23
forum: Security
---

### Post by RaymondBeaudoin on 2009-02-23
Hi there,

I have setup my system as a basic LAMP install + email + Webmin and such, but in any case, when I built the system I honestly built it as a single-user environment sort of place. Now, after a great few months, I need to allow other users into the server, the only issue is after I create a user, they can login to their account via SSH and leave their home directory. That would be okay with me, except for the fact that they can read my master home "devcube" and included in there are tons of password files, client data, and a live www directory.

To combat against this, I tried setting each home to 700 for permissions, but then when trying to go the website, I received a forbidden error.

I feel like I'm missing something very small here, and your help would be much appreciated. Thank you!

Ray 

P.S. Free e-popcorn to whoever gets it first. :popcorn:

---

### Post by bodhi.zazen on 2009-02-23
I presume your web server errors are because you are serving documents from your home directory.

The user www-data needs access to the information you are serving.

You have several options, probably easiest to move your web data out of your home and into /var/www (you will likely need to re-configure your apache configuration).

Another option is to use Apparmor to limit where and what guests can do.

jdong has a nice blog on doing exactly this, he uses a shell he terms "jailbash" which restricts what users can do.

[http://www.friedcpu.net/?p=70](http://www.friedcpu.net/?p=70)

---

### Post by RaymondBeaudoin on 2009-02-23
I knew it was something. 

When you said www-data it reminded me.

I set the folder permissions to 700 for home directory "devcube"

Under that directory is a folder called www which serves all the web documents. 

Solution: Secure "devcube" folder by chmod'ing to 700.

Chown "www" to www-data:www-data so that permissions for apache are used on the folder and kaboom! It all works!

Thanks for your help!

---

